---
title: "stymied by jargon"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by nnjond on 2009-11-24
Hi, 

I wish to follow these instructions:

Kill X
Now, it's time to stop X and the gdm (or kdm for Kubuntu Users)
This requires that you logout and switch to another tty console ( Ctrl+Alt+F1 ).

Login to the shell, and kill gdm:
Code:

sudo /etc/init.d/gdm stop

But this command throws up options i don't understand...

"Rather than invoking init scripts through /etc/init.d, use service(8) utilty, eg service gdm stop

Since the script you are attempting to invoke has been converted to an Upstart job, you may also use the stop(8) utility, e.g. stop gdm
gdm stop/waiting"

~$ stop gdm

returns:

stop: Unknown instance
~$

---

### Post by harfa on 2009-11-24
The instructions you wish to follow have been written for a previous version of ubuntu. I suggest you find instructions that have been written for karmic, even if you manage to stop gdm there is no guarantee that whatever instructions you are following haven't failed silently and you might be finding yourself in trouble.

what is the procedure you are attempting to follow meant to do?

---

### Post by pbrane on 2009-11-24
**sudo /etc/init.d/gdm stop** shows that same message to me. The reason you got the **Unknown instance** error is because gdm was already stopped by the first command.

Typing the command **sudo /etc/init.d/gdm stop** will work to kill the X server, but I think using **stop** is the prefered way now.

---

### Post by harfa on 2009-11-24
The init.d system has been replaced by upstart in karmic. a lot of changes have occurred under the hood, so to speak.

That is why I suggest not to follow outdated instructions, because you don't know what else has been changed that relates to the outdated instructions.

---

### Post by nnjond on 2009-11-24
thanks for your help.

I have lost my preferd scrn res. and have failed to install the recomended Nvidia  185 driver.

---

### Post by jimmy the saint on 2009-11-24
Just use the restricted drivers tool

System>Administration> Hardware Drivers

---

