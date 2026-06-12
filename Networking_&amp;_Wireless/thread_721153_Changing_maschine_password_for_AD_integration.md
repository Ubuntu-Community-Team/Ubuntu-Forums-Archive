---
title: "Changing maschine password for AD integration"
date: 2008-03-11
forum: Networking &amp; Wireless
---

### Post by mo0on on 2008-03-11
Hello,

the problem is that I have one computer with 2 operating systems on it. windows and ubuntu. Both should be able to join one AD. So the machine password, wich is used for authentifikation, must be the same on the windows and on the linux side.

How could I see the machine password in the Linux OS. Can it be fixed to a value? Without these password I'm not be able to join both to a domain, so please help me . ;)

thanks

---

### Post by PhrygianCat on 2008-03-12
Have you try this:
[ActiveDirectoryWinbindHowto]("https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto")

---

### Post by mo0on on 2008-03-13
I've tried not excactly this one, but "Samba_ADAuth" which is nearly the same. The logon from just Linux isn't the problem, this works great. The Problem is that there is also Windows on this machine.
And to use both with the AD I have to figure out how to change or see the machine password which is used from Linux to authenticate against the AD.
In Windows I can easily change this password, but Linux is more tricky.

The prblem is that both, Windows and Linux, need to have the same password, but when you integrate them into an AD they get different passwords for authentication.

---

### Post by PhrygianCat on 2008-03-13
You can try changing the Linux password by doing this:
* Boot using Live CD
* Mount the file system
* Make the mounted file system as the root file system using chroot command
* Use passwd command to delete or change password

---

