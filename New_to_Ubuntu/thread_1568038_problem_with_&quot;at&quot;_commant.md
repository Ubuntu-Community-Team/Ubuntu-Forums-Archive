---
title: "problem with &quot;at&quot; commant"
date: 2010-09-04
forum: New to Ubuntu
---

### Post by Samic on 2010-09-04
hi
I want to use "at commant but none of these works:

```
samic@F29:~$ at 23:37
warning: commands will be executed using /bin/sh
at> bash -c "gedit"
at> <EOT>


samic@F29:~$ bash -c "gedit" | at 23:37


samic@F29:~$ echo 'gedit' | at 23:37
```

it shows a  job 33 at Sat Sep  4 23:37:00 2010 but nothings happen at the time!

---

### Post by scorp123 on 2010-09-04
Did you read the manual? Please open a terminal and type:
```
man at
```

Use the cursor keys to navigate, press "Q" to quit. The manual will explain how to correctly schedule jobs and how to correctly check for job statuses.

---

### Post by spjackson on 2010-09-04
> **Samic said:**
> 
```
samic@F29:~$ at 23:37
warning: commands will be executed using /bin/sh
at> bash -c "gedit"
at> <EOT>


samic@F29:~$ bash -c "gedit" | at 23:37


samic@F29:~$ echo 'gedit' | at 23:37
```it shows a  job 33 at Sat Sep  4 23:37:00 2010 but nothings happen at the time!
As per the man page for 'at', the DISPLAY environment variable is not transferred to the at job. gedit cannot do anything without a DISPLAY.

---

### Post by Samic on 2010-09-05
actually I want to hibernate at a specific time
when I use this command in terminal
```
pmi action hibernate
```
It hibernates immediately but when I use Gnome Schedule nothing happens
I wanted to use "at" instead!
If you can help me any of them I would be thankful

---

### Post by Samic on 2010-09-05
there must be a problem with something that "at" and "Gnome Schedule" are related to!
please help!

---

### Post by kwacka on 2010-09-05
```
pmi action hibernate at 23:15
```

worked for me.

But you'll need to enter daily (I assume). I've never used Gnome Schedule, but checkout 'cron'.

I'm also confused about the comment regarding gedit when querying the 'at' man page.


Checking out man pages, etc it seems that Gnome-Scheduler is a front-end for cron, whilst pmi's behaviour is governed by pm-utils (see /usr/share/doc/pm-utils/README)

*Correction Gnome-Schedule is a front-end for both cron and at

---

### Post by Samic on 2010-09-06
hi
when I use this command
```
pmi action hibernate at 23:15
```or any other time, It will hibernate immediately!

---

### Post by The Cog on 2010-09-06
If you are running an X (GUI) program under the at command, you must set the DISPLAY first or it won't know where to display to. This works (I just tried it):
> steve@steve-desktop:~$ at 21:16
warning: commands will be executed using /bin/sh
at> export DISPLAY=:0.0
at> xeyes
at> <EOT>
job 3 at Mon Sep  6 21:16:00 2010


---

### Post by cake nom nom on 2010-09-06
> **Samic said:**
> actually I want to hibernate at a specific time
when I use this command in terminal
```
pmi action hibernate
```
It hibernates immediately but when I use Gnome Schedule nothing happens
I wanted to use "at" instead!
If you can help me any of them I would be thankful

to turn your computer off at a certain time just do

```
 sudo shutdown -P (TIME) 
```

---

### Post by Samic on 2010-09-08
Thanks everyone
;)

---

