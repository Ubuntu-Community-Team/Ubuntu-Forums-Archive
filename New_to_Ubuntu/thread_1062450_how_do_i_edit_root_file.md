---
title: "how do i edit root file?"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by draughted on 2009-02-06
i am running 8.04 and enhanced machine control (EMC)
and i am set with the task of disabling SMI on my intel machine to reduce its latency performance.

[http://wiki.linuxcnc.org/cgi-bin/emcinfo.pl?FixingSMIIssues](http://wiki.linuxcnc.org/cgi-bin/emcinfo.pl?FixingSMIIssues)

in this site it describes, in step 7, editing the file
 /etc/emc2/rtapi.conf:

cleary it is a root file and i don't have permission.i have made a password for my root but know not how to use it.

---

### Post by punx45 on 2009-02-06
use sudo before any command that requires root, then enter password at the prompt.

eg in the case of your file

```
 sudo vi /etc/emc2/rtapi.conf
```

---

### Post by Old *ix Geek on 2009-02-06
First off, ALWAYS make a copy before you alter files like these!  Follow these steps:

1) To enter the directory the file's in:
```
cd /etc/emc2
```

2) To make a backup copy of the file before editing it:
```
sudo cp rtapi.conf rtapi.conf.orig
```

3) To edit the file:
```
sudo vi rtapi.conf
```

In step #2, you'll be prompted for YOUR password, NOT root's.

In step #3, I'm assuming that you know how to use the editor vi. If not...post again!

---

### Post by punx45 on 2009-02-06
oops, i usually remember caveats such as backups..   thanks for picking up the slack.   

seems like not many people like the vi anymore, but its what i use, and it was my example... :-D

---

### Post by MarblePanther on 2009-02-06
For him, I suggest not starting out with vi ;)

replace vi with gedit if you have trouble...

---

### Post by draughted on 2009-02-06
no i am a real beginner 
vi sounds foreign
but your still going to have to help with gedit

---

### Post by punx45 on 2009-02-06
im pretty sure gedit is like notepad.   you shouldnt have any trouble with that.    (no thumbs up emoticon?!)

---

### Post by draughted on 2009-02-06
no, i'm done 

thank you not only have you finished it 
but you've set me on my way to linux heaven.

---

