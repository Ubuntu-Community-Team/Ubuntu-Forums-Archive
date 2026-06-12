---
title: "whats the terminal command to tell how long your computer is on for?"
date: 2009-05-30
forum: New to Ubuntu
---

### Post by shiningkenmonster on 2009-05-30
just to figure out how long my battery really last for.

---

### Post by Elfy on 2009-05-30
uptime

---

### Post by shiningkenmonster on 2009-05-30
thanks, why does it say i have 3 users logged on?

I have only 1 account on my ubuntu

---

### Post by kpkeerthi on 2009-05-30
Can you post the output of
```
who -aH
``` ?

---

### Post by Elfy on 2009-05-30
> **shiningkenmonster said:**
> thanks, why does it say i have 3 users logged on?

I have only 1 account on my ubuntu

Bear in mind that each time you open a terminal it adds one user to how many are logged in.

---

### Post by shiningkenmonster on 2009-05-30
this is with one terminal open.

```
kenny@kenny-netbook:~$ uptime
 00:13:40 up  3:14,  2 users,  load average: 3.93, 3.17, 1.62
kenny@kenny-netbook:~$ who -aH
NAME       LINE         TIME             IDLE          PID COMMENT  EXIT
           system boot  2009-05-29 20:59
           run-level 2  2009-05-29 20:59                   last=
LOGIN      tty4         2009-05-29 20:59              2135 id=4
LOGIN      tty5         2009-05-29 20:59              2136 id=5
LOGIN      tty2         2009-05-29 20:59              2140 id=2
LOGIN      tty6         2009-05-29 20:59              2149 id=6
LOGIN      tty3         2009-05-29 20:59              2148 id=3
LOGIN      tty1         2009-05-29 20:59              2889 id=1
kenny    + tty7         2009-05-29 20:59  old         2921 (:0)
kenny    + pts/0        2009-05-29 21:00   .          3840 (:0.0)
           pts/1        2009-05-30 00:13                 0 id=/1    term=0 exit=0

```

---

### Post by lncoll on 2009-05-30
> **shiningkenmonster said:**
> this is with one terminal open.

```
kenny@kenny-netbook:~$ uptime
 00:13:40 up  3:14,  2 users,  load average: 3.93, 3.17, 1.62
kenny@kenny-netbook:~$ who -aH
NAME       LINE         TIME             IDLE          PID COMMENT  EXIT
           system boot  2009-05-29 20:59
           run-level 2  2009-05-29 20:59                   last=
LOGIN      tty4         2009-05-29 20:59              2135 id=4
LOGIN      tty5         2009-05-29 20:59              2136 id=5
LOGIN      tty2         2009-05-29 20:59              2140 id=2
LOGIN      tty6         2009-05-29 20:59              2149 id=6
LOGIN      tty3         2009-05-29 20:59              2148 id=3
LOGIN      tty1         2009-05-29 20:59              2889 id=1
kenny    + tty7         2009-05-29 20:59  old         2921 (:0)
kenny    + pts/0        2009-05-29 21:00   .          3840 (:0.0)
           pts/1        2009-05-30 00:13                 0 id=/1    term=0 exit=0

```

Here you have 2 users, the first kenny is the terminal window where you did the command, every terminal counts as a user logged, and the second kenny is your gnome session.

---

### Post by StOoZ on 2009-05-30
To make it nicer (geee im bored...)
> uptime | awk '{ print "Its "$1 " and Im up for the last "$3 " hours" }'


---

### Post by jowilkin on 2009-05-30
> **StOoZ said:**
> To make it nicer (geee im bored...)

That won't work if the uptime is over 1 day.  Look what I get: ```
jowilkin@bubba ~ $ uptime
 11:32:57 up 2 days,  4:38,  2 users,  load average: 1.34, 1.68, 1.78
```
```
jowilkin@bubba ~ $ uptime | awk '{ print "Its "$1 " and Im up for the last "$3 " hours" }' 
Its 11:32:49 and Im up for the last 2 hours
```

---

