---
title: "Xauthority and X11 forwarding"
date: 2010-09-16
forum: New to Ubuntu
---

### Post by geoliu on 2010-09-16
I just installed ubuntu 10.04 LTS as a virtual machine on my desktop running xp. After the installation, I have also installed openssh and xbase-clients and xauth. But after all these installation, there is no .Xauthority file in my /home/user/ directory. Therefore when I ssh -X [email]username@another.unix.server[/email], it gives the warnings below:

Warning: no Xauth data, using fake authentication data for x11 forwarding

and x11 forwarding is not working at all

Does anyone have the same experience? I am totally new to Linux, but I have been searching on internet for two days, still have no clue how to fix the problem. Any help is greatly appreciated.

---

### Post by BOK on 2010-09-16
Yep, same problem here, but not on all 10.04 systems.
X11 forwarding used to work on Ubuntu 9.10, on one particular system running 10.04 it's broken.
All settings for X11 are unchanged (set in both /etc/ssh/* and in $HOME/.ssh/config).
xauth says:
```
xauth:  creating new authority file /home/user/.Xauthority
```
but no .Xauthority file is created. Ever.
User rights OK, $HOME/.ssh is 700

Puzzled. :-k

**[COLOR="Red"]UPDATE[/COLOR]**
Adding the line

```
X11UseLocalHost no
```

to /etc/ssh/sshd_config and restarting sshd fixed my problem here.

---

### Post by geoliu on 2010-09-16
> **BOK said:**
> Yep, same problem here, but not on all 10.04 systems.
X11 forwarding used to work on Ubuntu 9.10, on one particular system running 10.04 it's broken.
All settings for X11 are unchanged (set in both /etc/ssh/* and in $HOME/.ssh/config).
xauth says:
```
xauth:  creating new authority file /home/user/.Xauthority
```
but no .Xauthority file is created. Ever.
User rights OK, $HOME/.ssh is 700
 
Puzzled. :-k
 
**[COLOR=red]UPDATE[/COLOR]**
Adding the line
 
```
X11UseLocalHost no
```
 
to /etc/ssh/sshd_config and restarting sshd fixed my problem here.
 
 
**Yours are working now? I added tbe line above to sshd_config and restarted sshd, but it didn't work. What settings did you have in /etc/ssh/* and $HOME/.ssh/config? I don't have config file in $HOME/.ssh/, strange.**
 
 
**Mine is now working too. It was a stupid problem, the data in my account on the server I was loging onto exceeded the quota. Ah~~~~, two days of hard work, such a small problem.**

---

