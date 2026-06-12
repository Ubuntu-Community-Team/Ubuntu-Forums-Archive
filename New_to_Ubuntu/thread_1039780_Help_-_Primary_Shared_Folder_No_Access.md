---
title: "Help - Primary Shared Folder No Access"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by Kellemora on 2009-01-14
Hi Gang

Boy do I need your help now!

I have a Folder named File-Server that holds as the name implies, EVERYTHING!

I can access it from any Ubuntu Machine using my name and log-in password.  Can access it from 2 of 3 Windows XP boxes using my name and log-in.  But not the 4th Windows XP machine.

One of my employees cannot access the File-Server folder from any machine, while the other employees have no problem, except on the one Windows XP machine.

The Folder is obviously shared, even though it shows it's NOT SHARED and if I Share it from ROOT, the SHARE Disappears.
Nonetheless it's on the LAN, has been all week with no problems.

In Root Terminal, Using Nautilus, if I try to change the folder permission from ROOT to the group name, it immediately jumps back to root and if I close nautilus, the share disappears again.

In the past I would just create a new folder name, share it and add all the data back into it.  That is NOT an option this time as we do not have 2 terrabytes of spare disk space to do this with.

Probably not set up right from the git go I assume.  But as I said, it was working just fine until today.

ALL users screen names are in the smbusers file!

Now dig this.  From 2 of the Windows boxes, it does NOT ask for a password to access the shared folder and it appears plain as day in Network Places.  On the third windows box, when you select the folder it opens a pop-up window for username and password, but WILL NOT ACCEPT the password, NOT EVEN MY PASSWORD.

HELP!

TTUL
Gary

---

### Post by Kellemora on 2009-01-14
Forget it!

I finally found the problem in the BUG REPORTS!

It's Not Solved Yet!

FWIW:  chown -R user:user /media/etc doesn't take either!

TTUL
Gary

---

