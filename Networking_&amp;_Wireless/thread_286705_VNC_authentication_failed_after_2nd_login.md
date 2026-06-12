---
title: "VNC authentication failed after 2nd login"
date: 2006-10-28
forum: Networking &amp; Wireless
---

### Post by btrotter on 2006-10-28
Here is my scenario:
PC1: Ubuntu 6.10.1, Remote Desktop Preferences is set to allow a connection upon entering the session password.

PC2: Windows XP, running TightVNC

The very first time I try to connect from PC2 to PC1, I use TightVNC, put in the IP address of the Ubuntu server, type in the session password and it connects perfectly. 

Then it seems that a lot of times when I disconnect and try to reconnect, I follow the same procedure and I get a "VNC authentication failed" error message when I type in the session password.

When I get that, I can go onto PC1 and run the Netstat tool and still see it listening on port 5900. 
I can keep trying numerous times and always get the same error.

However, if I go to System > Preferences > Remote Desktop and change the session password to be the same thing it already was, I can then connect again.

I am not sure which error log the VNC faield attempts go to, or else I may be able to figure it out by that. 

Anyone have any insight as to why it is doing this?

Thank you kindly!

By the way...this is my first ever post. Look forward to many more!

Brian

---

### Post by wpwood3 on 2006-10-28
I am having the exact same problem with Edgy. (this was not an issue in Dapper).

What I have noticed is that the TightVNC client on my Windows machine will connect to my Edgy Ubuntu box just fine until I reboot the Ubuntu box.

After a reboot, I get Authentication errors when trying to connect. If I go to System > Preferences > Remote Desktop Preferences and reenter the same Password it fixes the problem until I reboot again.

Anybody have a fix for this?

---

### Post by castor_fou on 2006-10-28
I am in the exact same situation since my upgrade to edgy (was working fine without any pb with dapper) and don't have a clue how to solve it

---

### Post by btrotter on 2006-10-28
Sounds like a bug to me. How do you submit bug reports for things like this?

---

### Post by wpwood3 on 2006-10-28
> **btrotter said:**
> Sounds like a bug to me. How do you submit bug reports for things like this?
Bugs are reported [HERE]("https://launchpad.net/distros/ubuntu/+filebug").

It looks like this is a known bug. [READ THIS]("https://launchpad.net/distros/ubuntu/+source/vino/+bug/65795").

---

### Post by btrotter on 2006-10-30
Does anyone know if it is possible to change the session password through a command line? I have ssh capabilities to the box, and could change it remotely when I get locked out of the GUI.

I am going out of town on Wednesday and would like to have a way to connect to it without worrying when it was going to lock me out.

---

### Post by yoburtu on 2006-11-02
Hello,

is there any solution at problem with "VNC authentication failed"?.

Best regards.

---

### Post by sirmrmatt on 2006-11-03
Yeah, have been having this problem too!

Well I applied the patch as per the tutorial and restarted the computer remotely via ssh, but now I need someone at home to log me into a Gnome session! Can't seem to get a solid answer on how to do that remotely via ssh! :-k 

- Matt
[http://www.thecastleclothing.com](http://www.thecastleclothing.com)

---

### Post by yoburtu on 2006-11-16
Hello,

this bug is fixed with this package, I think:

Format: 1.7
Date: Tue, 24 Oct 2006 16:02:41 -0700
Source: vino
Binary: vino
Architecture: source
Version: 2.16.0-0ubuntu2.1
Distribution: edgy-proposed
Urgency: low
Maintainer: Jordi Mallach <jordi@debian.org>
Changed-By: Kees Cook <kees@ubuntu.com>
Description:
 vino - VNC server for GNOME
Changes:
 vino (2.16.0-0ubuntu2.1) edgy-proposed; urgency=low
 .
   * debian/patches/01_fix_password_free.patch:
     - don't g_free vnc server password at all (Ubuntu: #65795)
Files:
 6877e33ff4b97a4c4b79eba7046e3a69 1548 gnome optional vino_2.16.0-0ubuntu2.1.dsc
 fa62d4c765eaf03e6200debceeee2992 3512 gnome optional vino_2.16.0-0ubuntu2.1.diff.gz

How can I install this package in edgy?. I don't find in repos.

Best regards.

---

### Post by sibijv on 2006-11-21
hi sirmrmatt, I am new to ubuntu. I have the same authentication failure problem.

where can i find the tutorial u mentioned?

yoburtu could you give the url of the patch?

thanks and regards
sibi

---

### Post by sirmrmatt on 2006-11-22
This lists the fix:

[https://wiki.ubuntu.com/UbuntuPackagingGuide/BuildFromDebdiff](https://wiki.ubuntu.com/UbuntuPackagingGuide/BuildFromDebdiff)

It is the tutorial's bug at the very bottom, "Bug 65795." This fix is still working great for me now. 

- Matt :KS

---

