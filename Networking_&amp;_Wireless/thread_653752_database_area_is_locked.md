---
title: "database area is locked"
date: 2007-12-30
forum: Networking &amp; Wireless
---

### Post by timboellis on 2007-12-30
I am getting a database error, I was downloading from the add/remove but it could not download it so I had to force quit I have rebooted tried the various options on the forum including

sudo dpkg --configure -a and

tim@Timbo:~$ sudo sudo kill -9 PID
ERROR: garbage process ID "PID".
Usage:
  kill pid ...              Send SIGTERM to every process listed.
  kill signal pid ...       Send a signal to every process listed.
  kill -s signal pid ...    Send a signal to every process listed.
  kill -l                   List all signal names.
  kill -L                   List all signal names in a nice table.
  kill -l signal            Convert between signal numbers and names.
tim@Timbo:~$ sudo killall synaptic
synaptic: no process killed
tim@Timbo:~$ sudo kill -9 7048
tim@Timbo:~$ ps -ef |grep synaptic
tim       6114  5878  0 15:53 pts/0    00:00:00 grep synaptic
tim@Timbo:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
tim@Timbo:~$ sudo dpkg --configure -a
dpkg: status database area is locked by another process
tim@Timbo:~$ sudo dpkg --configure -a
dpkg: status database area is locked by another process
tim@Timbo:~$ sudo killall synaptic
synaptic: no process killed
tim@Timbo:~$ sudo dpkg --configure -a
dpkg: status database area is locked by another process
  

andy help

I am trying to install skype

---

### Post by greendragonfire on 2008-01-19
please, someone help
I have this exact problem

---

