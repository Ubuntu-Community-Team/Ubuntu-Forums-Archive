---
title: "trying to apply solution to mysql problem"
date: 2010-08-04
forum: New to Ubuntu
---

### Post by thorbs on 2010-08-04
Hi I am trying to apply the solution from this thread [http://ubuntuforums.org/showthread.php?t=1488763&page=3](http://ubuntuforums.org/showthread.php?t=1488763&page=3)
to my mysql problems. 

It says I need to kill the PID that comes up in this line

Root 2348 0.0 0.0 3792 1088 pts/1    s+ 17:57 0:00 stop mysql

What is the pid in that? and do I just write kill and the the number in the terminal?

---

### Post by ajgreeny on 2010-08-04
Where did that line come from?  I thought from "top" at first, but it does not look quite right for that.  Maybe from "ps aux"?  If so the PID is the 2348.

The answer to your question however is simply ```
kill xxxx
``` but you need to get the number right or could cause problems if it's wrong and is a system process.

---

### Post by thorbs on 2010-08-05
Hi I used this command     ps auxww | grep mysql


I got more than just the line here, but I do not know how to copy the lines from the terminal so I just copied it by hand.
 

Can you specify what is the logics that makes it possible to identify the PID in the string? I tried to read the ubuntu manual and it did not help.

t.

---

### Post by ajgreeny on 2010-08-05
If you had used ps aux without the pipe to grep, you would have seen the top line of the command's output:-
```
~$ ps aux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   2792  1588 ?        Ss   12:05   0:00 /sbin/init
root         2  0.0  0.0      0     0 ?        S    12:05   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    12:05   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S    12:05   0:00 [ksoftirqd/0]
               etc
               etc
```which shows what all the columns are.

So the second column is the PID of the processes.

---

### Post by thorbs on 2010-08-06
Ok, for some reason the top line does not show in my terminal, can there be a reason for this? 

However I was able to solve my problem, how do I change status of the thread to solved?

---

### Post by konqueror7 on 2010-08-06
just a suggestion, use instead 'pgrep' to get the PID then kill, its easier...

```
pgrep mysql
```

hope it helps, and oh, you can find it upper right, in the menu 'Thread Tools'

---

