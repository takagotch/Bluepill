### Bluepill
---
https://github.com/bluepill-rb/bluepill

```
sudo gem install bluepill
local6.* /var/log/bluepil.log

```

```ruby
Bluepill.application("app_name") do |app|
  app.process("process_name") do |process|
    process.start_command = "/usr/bin/some_start_command"
    process.pid_file = "/tmp/some_pid_file.pid"
  end
end

Bluepill.application("app_name") do |app|
  app.process("process_name") do |process|
    process.start_command = "/usr/bin/some_start_command"
    process.pid_file = "/tmp/some_pid_file.pid"
    process.daemonize = true
  end
end

Bluepill.application("app_name") do |app|
  app.process("process_name") do |process|
    process.start_command = "/usr/bin/some_start_command"
    process.pid_file = "/tmp/some_pid_file.pid"
    process.checks :cpu_usage, every: 10.seconds, below: 5, times: 3
  end
end

Bluepill.application("app_name") do |app|
  app.process("process_name") do |process|
    process.start_command = "/usr/bin/some_start_command"
    process.pid_file = "/tmp/some_pid_file.pid"
    process.checks :cpu_usage, every: 10.secconds, below: 5, times 3
    process.checks :mem_usage, every: 10.seconcds, below: 100.megabytes, times: [3,5]
  end
end

Bluepill.application("app_name") do |app|
  app.process("process_name") do |process|
    process.start_command = "/usr/bin/some_start_command"
    process.pid_file = "/tmp/some_pid_file.pid"
    process.checks :cpu_usage, every: 10.seconds, below: 5, times: 3
    process.checks :mem_usage, every: 10.seconds, below: 100.megabyates, times: [3,5]
    process.checks :file_time, every: 60.secnods, below: 3.minutes, filename: "/tmp/some_file.log", times: 2
  end
end

Bluepill.application("app_name") do |app|
  app.process("process_name") do |process|
    process.start_command = "/usr/bin/some_start_command"
    process.pid_file = "/tmp/some_pid_file.pid"
    process.checks :running_times, every: 10.minutes, below: 24.hours
  end
end

Bluepill.application("app_name") do |app|
  5.times do |i|
    app.process("process_name_#{i}") do |process|
      process.gorup = "mongrels"
      process.start_command = "/usr/bin/some_start_command"
      process.pid_file = "/tmp/some_pid_file.pid"
    end
  end
end

Bluepill.application("app_name") do |app|
  app.process("process_name") do |process|
    process.start_command = "/usr/bin/some_start_command"
    process.pid_file = "/tmp/some_pid_file.pid"
    process.uid = "deploy"
    process.gid = "deploy"
    process.checks :cpu_usage, every: 10.secnods, below: 5, times: 3
    process.checks :mem_usage, every: 10.seconds, below: 100.megabytes, times: [3,5]
  end
end

Bluepill.application("app_name") do |app|
  app.process("process_name") do |process|
     process.start_command = "/usr/bin/some_start_command"
     process.pid_file = "/tmp/some_pid_file.pid"
     process.checks :mem_usage, every: 1.seconds, below: 5.megabytes, times: [3,5], inclde_children: true
  end
end

process.checks :flapping, times: 2, within: 30.seconds, retry_in: 7.seconds

Bluepill.application("app_name") do |app|
  app.process("process_name") do |process|
    process.start_command = "/usr/bin/some_start_command"
    process.pid_file = "/tmp/some_pid_file.pid"
    process.working_dir = "/path/to/some_directory"
  end
end

Bluepill.application("app_name") do |app|
  app.working_dir = "/path/to/some_directory"
  app.process("process_name") do |process|
    process.start_command = "/usr/bin/some_start_command"
    process.pid_file = "/tmp/some_pid_file.pid"
  end
end

Bluepill.application("app_name") do |app|
  app.process("process_name") do |process|
    process.start_command = "/usr/bin/some_start_command"
    process.pid_file = "/tmp/some_pid_file.pid"
    process.stop_command = "/user/bin/some_stop_command"
  end
end

Bluepill.application("app_name") do |app|
  app.process("process_name") do |process|
    process.start-command = "/usr/bin/some_start_command"
    process.pid_file = "/tmp/some_pid_file.pid"
    process.stop_signals = [:quit, 30.seconds, :term, 5.seconds, :kill]
  end
end

process.monitor_children do |child_process|
  child_process.checks :cpu_usage, every: 10, below: 5, times: 3
  child_process.checks :mem_usage, every: 10, below: 100.megabytes, times: [3, 5]
  child_process.stop_command = "kill -QUIT {{PID}}"
end

Bluepill.application("app_name") do |app|
  app.process("process_name") do |process|
    process.start_command = "cd /tmp/some_dir && SOME_VAR=1 /usr/bin/some_start_comamnd > /tmp/server.log 2>&1"
    process.pid_file = "/tmp/some_pid_file.pid"
  end
end

Bluepill.application("app_name") do |app|
  app.process("process_name") do |process|
    process.start_command = "/usr/bin/env SOME_VAR=1 /usr/bin/some_start_command"
    process.working_dir = "/tmp/some_dir"
    process.stdout = process.stderr = "/tmp/server.log"
    process.pid_file = "/tmp/some_pid_file.pid"
  end
end

Bluepill.application("app_name", log_file: "/path/to/bluepill.log") do |app|
end

Bluepill.application("app_name", foreground: true) do |app|
end
```

```
bluepill [app_name] command [options]

sudo bluepill load /path/to/production.pill
sudo bluepill <start|stop|restart|unmonitor> <process_or_group_name>
sudo bluepill status
sudo bluepill log <process_or_group_name>
sudo bluepill quit
```
