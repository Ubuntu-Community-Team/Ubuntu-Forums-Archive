---
title: "How to kill a job?"
date: 2011-02-09
forum: New to Ubuntu
---

### Post by crazyfuturamanoob on 2011-02-09
I had an unresponsive program which I wanted to kill.

```

$ ctrl+z
$ jobs
[1]+  Stopped                 ./motorsfx
$ sudo kill -s SIGABRT 1

```

Instead of killing the job that command killed the init process and my PC got a kernel panic. :lolflag:

The manual page of kill doesn't say anything useful.

So, how can I kill the job number #1 without rebooting or closing the terminal?

Thank you.

---

### Post by uRock on 2011-02-09
Use htop. Highlight the process you want to kill and kill it.

---

### Post by crazyfuturamanoob on 2011-02-09
Thanks. :)

---

### Post by apmcd47 on 2011-02-09
```

$ ctrl+z
$ jobs
[1]+  Stopped                 ./motorsfx
$ sudo kill -s SIGABRT **[COLOR="Red"]%[/COLOR]**1

```
The percent will tell bash to translate job 1 to the actual pid of the job. Without that you were killing pid 1, which you found to be init.

Look up the JOB CONTROL section of the bash man page.

Andrew

---

### Post by Nico-dk on 2011-02-09
You've got a few choices to kill processes

From GUI:
ALT + F2, type: xkill.
This will change the cursor into a cross.
Click the app you want to kill

From terminal:
```
ps -ef | [processname or part of it]
(copy PID)
kill PID or kill -9 PID (if it won't die)
``` 


> **uRock said:**
> Use htop. Highlight the process you want to kill and kill it.
htop is most of my fave apps rolled into one.
I salute you sir =D>

---

