---
title: "Blank screen after login."
date: 2008-12-22
forum: New to Ubuntu
---

### Post by wfwii on 2008-12-22
I installed Ubuntu 8.10 on a Dell C400 (Old system)from the download. Install seemed to go well, used the option to use the entire disc to get rid of old files, programs and XP Professional.
Set my user name and password and rebooted after removing the disc.
The system booted to Unbuntu and asked for user name and password, did both the system seemed to accept them, and after about 10 sec of hard drive activity, the beige screen background came up with the mouse pointer showing, but that is it. Nothing appears to be available. Rebooted several times all with the same result.

Any ideas on the problem or what to do next?

:confused:

---

### Post by fiddler616 on 2008-12-22
> **wfwii said:**
> I installed Ubuntu 8.10 on a Dell C400 (Old system)from the download. Install seemed to go well, used the option to use the entire disc to get rid of old files, programs and XP Professional.
Set my user name and password and rebooted after removing the disc.
The system booted to Unbuntu and asked for user name and password, did both the system seemed to accept them, and after about 10 sec of hard drive activity, the beige screen background came up with the mouse pointer showing, but that is it. Nothing appears to be available. Rebooted several times all with the same result.

Any ideas on the problem or what to do next?

:confused:
Define old. Does it meet the system requirements?
Try the Live CD--if GNOME loads all the way on that, then it may be a faulty install, or something. If it doesn't work on the Live CD either, then you have a hardware problem, probably with RAM or the video card.

---

### Post by Ender41 on 2008-12-22
> **wfwii said:**
> I installed Ubuntu 8.10 on a Dell C400 (Old system)from the download. Install seemed to go well, used the option to use the entire disc to get rid of old files, programs and XP Professional.
Set my user name and password and rebooted after removing the disc.
The system booted to Unbuntu and asked for user name and password, did both the system seemed to accept them, and after about 10 sec of hard drive activity, the beige screen background came up with the mouse pointer showing, but that is it. Nothing appears to be available. Rebooted several times all with the same result.

Any ideas on the problem or what to do next?

:confused:

 Sounds like a video/xserver problem, can you instead of logging in when the screen comes up. ctrl-alt-F2 and log in there ?

This will show you that the install has worked at least. Note you will not have a gui from the above method but it is fixable from there hopefully.

If that all works then sudo dpkg-reconfigure -phigh xserver-xorg might fix things for you.
Next hit ctrl-alt-F7 to get back to the gui login screen. ctrl-alt-backspace will restart the xserver and hopefully you can then login.
 If it throws errors at you then come back with those and we will try to be of better help.

Ender

---

### Post by wfwii on 2008-12-22
Intel 866MHz processor, Intel 830 graphics and 512 MB of memory.

---

### Post by wfwii on 2008-12-22
I was able to use the control-alt-F2 and login, but was not able to enter the sudo command as you suggested and the scrolling was inconsistent and it did seem to respond, but I did get back to main login screen. I think Ubuntu installed OK, but it may be a hardware issue? Although this system ran XP Professional and Office for several years with virtually no issues.

---

### Post by Ender41 on 2008-12-22
> **wfwii said:**
> I was able to use the control-alt-F2 and login, but was not able to enter the sudo command. I think Ubuntu installed OK, but it may be a hardware issue? Although this system ran XP Professional and Office for several years with virtually no issues.

What error did it throw at you ? 
Note linux is case sensitive so Sudo is different from sudo
typing that command should have asked for your password again

Ender

---

### Post by wfwii on 2008-12-22
It did, and then a command line became available and I attempted to type your recommended command and it was non-responsive. I hit enter several times and each time a new command line would come up. Tried to type in your command and nothing would show on the screen behind the command line.

---

