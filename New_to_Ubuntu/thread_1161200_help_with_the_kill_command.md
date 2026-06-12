---
title: "help with the kill command"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by wlraider70 on 2009-05-16
can someone explain the kill command to me.


when i try it, it say this....


what is a sigspec, signum, ect 

uke@vaio:~$ kill
kill: usage: kill [-s sigspec | -n signum | -sigspec] pid | jobspec ... or kill -l [sigspec]
luke@vaio:~$ kill -help
bash: kill: help: invalid signal specification
luke@vaio:~$ kill --help
bash: kill: -help: invalid signal specification
luke@vaio:~$

---

### Post by days_of_ruin on 2009-05-16
For more info on it type:
```
man kill
```

to read the manual for kill.

---

### Post by lswb on 2009-05-16
kill is used to send a signal to a running process, probably most commonly used to "kill" or terminate a process that has stopped responding normally or cannot be ended in some other way.

The kill command requires a process id # to act on, that is the pid or jobspec. The sigspec or signum is the "signal" that the kill command will send to the specified process. Different processes may have different responses to different signals. Try "man kill" for a detailed explanation. There are related commands killall and pkill that will send a signal based on process name or other characteristics.

---

### Post by Sir Jasper on 2009-05-16
In Xubuntu  Alt+F2 and type xkill then move the x over the program to kill and click.

In case it helps, when I was using Ubuntu I added a kill icon to my panel. I don't remember the name of it but I'm pretty sure it was obvious.

My regards

---

### Post by Michael.Godawski on 2009-05-16
hi,

many light-years ago I wrote a little how-to dealing with stopping a process:


[LIST]
[*][http://ubunturesources.ub.ohost.de/stopprocess.html](http://ubunturesources.ub.ohost.de/stopprocess.html)
[/LIST]

I have to either update that page or move the posts to my new one... this one was just for me, thinking aloud.;)

---

### Post by Sarai the Geek on 2009-05-16
If you want to kill a process the simplest way is to use killall:

i.e...
```
killall firefox
```

```
killall conky
```

```
killall pidgin
```

etc. Sometimes the process name isn't quite so obvious, but most of the time it works well just like that. :)

---

### Post by XCan on 2009-05-16
When I use kill, I usually grab the process id from 'ps'. You could issue 'ps aux' and find the id of the process you want to kill. For convenience, you can pipe the output of ps into grep to quickly identify the process. If I wanted to kill firefox I would do the following:

```
ps aux | grep firefox
```

Output:
```
fel       2731  0.0  0.0   7524   896 pts/0    S+   00:29   0:00 grep firefox
fel      14103  2.1  5.6 788012 222960 ?       Sl   May16  14:21 /usr/lib/firefo
```

Kill command:
```
kill 14103
```

Sometimes, the process doesn't respond to kill alone issuing
```
kill -9 14103
```
can solve the issue. Issuing only kill is a 'softer' way to kill a process, as it in principle allows it to finish what it's doing and wipe its traces from the memory.

---

