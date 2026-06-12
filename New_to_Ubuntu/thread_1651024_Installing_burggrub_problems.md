---
title: "Installing burg/grub problems"
date: 2010-12-22
forum: New to Ubuntu
---

### Post by theflash21 on 2010-12-22
Hi all!
 
I just installed Windows 7 and Ubuntu 10.10, then installed Burg to replace the drab Grub. After doing so, I have a problem and a question:
 
**Problem/question**:
Since installing Burg, I have been getting a popup asking to unlock the keyring, because it was not unlocked on login. How can I get rid of it ... ideally, linking it back to my Ubuntu login?
 
**Question**:
How can I change the Menu Entry in Grub/Burg? I get:
"Ubuntu GNU/Linux, with Linux 2.6.35-22-generic", and 
"Windows 7 (loader) (on /dev/sda1)"
 
I'd like it just to change the string to read:
"Ubuntu 10.10" or "Ubuntu Maverick", and 
"Windows 7 Ultimate"
 
When I try and change it in burg.cfg or grub.cfg, it just reverts when I run update-grub/update-burg.
 
Thanks!

---

### Post by Megaptera on 2010-12-22
> **theflash21 said:**
> Hi all!
 **Question**:
How can I change the Menu Entry in Grub/Burg? I get:
"Ubuntu GNU/Linux, with Linux 2.6.35-22-generic", and 
"Windows 7 (loader) (on /dev/sda1)"
 
I'd like it just to change the string to read:
"Ubuntu 10.10" or "Ubuntu Maverick", and 
"Windows 7 Ultimate"

I think you need to be careful changing that wording, I did it once somehow and my system (dual boot) would not boot 'cos (I think) that "wording" is actually the wording that grub "looks for" and doesn't recognise changed wording ... if you see what I mean?
Unless anyone else knows different.... ??

---

### Post by theflash21 on 2010-12-27
Thanks Mega ... I was hoping that was not the case ... seems like such a simple thing to do.  I don't think I worded the subject very well.  I'm going to try posting it again ... no offense.  At least I've a heads up that that might be the case.  Thanks.

---

### Post by drs305 on 2010-12-27
If you want to take the plunge this guide will show you how to make the changes to the appropriate scripts in /etc/grub.d  Note is it for Grub.

You've been warned: it's pretty geeky stuff. Not difficult, just probably more time than a non-geek would want to [s]waste[/s] spend on it.
[Grub 2 Title Tweaks Thread]("http://ubuntuforums.org/showthread.php?t=1287602")

It would be far easier to just make a custom menu and disable the other scripts. Here's a good guide by *Cavsfan*
[http://ubuntuforums.org/showthread.php?t=1542338]("http://ubuntuforums.org/showthread.php?t=1542338")

---

### Post by drs305 on 2010-12-27
> **theflash21 said:**
> 
**Problem/question**:
Since installing Burg, I have been getting a popup asking to unlock the keyring, because it was not unlocked on login. How can I get rid of it ... ideally, linking it back to my Ubuntu login?


Assuming this isn't a BURG password on a menuentry, go to System, Preferences, Password & Encryption. Right click on PW Login, Change PW, enter blank PW as the new password (leave blank).

---

