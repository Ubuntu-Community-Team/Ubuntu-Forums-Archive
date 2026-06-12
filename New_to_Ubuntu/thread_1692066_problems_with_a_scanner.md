---
title: "problems with a scanner"
date: 2011-02-20
forum: New to Ubuntu
---

### Post by MFoxx on 2011-02-20
p { margin-bottom: 0.08in; }  [SIZE=4]Hey ALL![/SIZE]
 [SIZE=4]I am a green user.[/SIZE]
 [SIZE=4]I have problems with Xsane or maybe with installation of drivers for a a scanner. I've managed to install the drivers. Then I checked the installation.
It seems to be right:

@ubuntuPolich-34095:~$ dpkg -l | grep Brother

ii brscan-skey 0.2.1-3 Brother Linux scanner S-KEY tool

ii brscan2 0.2.5-1 Brother Scanner Driver

r@ubuntuPolich-34095:~$ dpkg -l | grep Brother

ii brscan-skey 0.2.1-3 Brother Linux scanner S-KEY tool

ii brscan2 0.2.5-1 Brother Scanner Driver

r@ubuntuPolich-34095:~$

But Xsane reads the following:
Failed to open device "brother2;bus3;dev1/: invalid argument

Can anybody help me?

Thanks in advance.[/SIZE]

---

### Post by Hedgehog1 on 2011-02-20
The error you are seeing looks like the error in the second post of this thread:

[http://ubuntuforums.org/showthread.php?t=278923]("http://ubuntuforums.org/showthread.php?t=278923")

I have been scanning from a USB Cannon scanner in Ubuntu using xsane (no drivers loaded at all).  I wonder if you need drivers for a USB scanner anymore?

:KS

---

### Post by MFoxx on 2011-02-22
Thank u Hedgehog. I'm trying to make it work.

---

