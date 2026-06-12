---
title: "No background processes: Only command line"
date: 2010-09-25
forum: New to Ubuntu
---

### Post by kroq-gar78 on 2010-09-25
Hello Ubuntu Forums Community,

I would like to run a program with no background processes running. I want to do a test so that it can be as accurate as possible. Is there any way I can do this? I can be run only using the command line.

Thanks in advance.

---

### Post by gzarkadas on 2010-09-25
1. Reboot in single user mode (type `sudo telinit 1' in a command prompt). This will drop you to a console only mode, with minimal number of services activated.

2. Do a `ps -A | less' to view your running processes. Select which ones you want to shut down and write their PIDs (the number beside the name). Be careful to not make mistakes there, else you will be shutting down processes you want to keep.

3. For each process you want to shut down, do a `kill -s TERM [PID]'. Wait a few seconds and do a `ps -A | grep [PID or process name]'. If you see output from this, then the process hasn't terminated nicely, so you must become not-nice: do a `kill -s KILL [PID]'.

4. Run your test.

5. If you manually shut down processes in step #3, then it is better to reboot; issue `shutdown -r now'. Else do a `telinit 2' to leave single user mode.

---

### Post by kroq-gar78 on 2010-09-25
how do I reboot into single user mode? What do I do after I shut down? Sorry for the noobish question

EDIT: oops sorry just reread the post

---

