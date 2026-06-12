---
title: "Ndiswrapper Help"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by BigNeek on 2007-04-25
I am a completely new to Linux and Ubuntu.  I'm a Windows man who has finally come to the dark side.  I've been struggling for a couple of days trying to get my wireless to work on my lapper.  I have a Dell Latitude D600 with a Dell 1300 (Broadcom) internal card.  I've Googled around and discovered that I'll probably have to use NDISWRAPPER to install the XP dirvers for the card.  That's fine.  I downloaded the two necessary driver files and have them on my desktop.  I tried for hours to manually install NDIS....NO JOY.......I then discovered Automatix2.  (AWESOME BABY!!!)  I used it to install NDISWRAPPER but still can't get it to work.  I tried using Automatix to uninstall and reinstall a few times.  NO JOY.

Here's what I'm doing in the terminal....As you will see, it tells me that I don't have NDISWRAPPER installed, but when I try to run the command it gives to install it, it tells me that I already have the latest version.

jniko@JNiko-Ubuntu:/$ ndiswrapper -l
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found
jniko@JNiko-Ubuntu:/$ sudo apt-get install ndiswrapper-common
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ndiswrapper-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jniko@JNiko-Ubuntu:/$ 

jniko@JNiko-Ubuntu:/$ sudo ndiswrapper-l
sudo: ndiswrapper-l: command not found
jniko@JNiko-Ubuntu:/$ 



Please help.  I must get UNWIRED!!!

Thank you,

Big Neek

---

### Post by ggratto on 2007-04-25
I was having similar issues.  I installed the GUI version of the Ndiswrapper and was ale to get it working.

---

### Post by dbott67 on 2007-04-25
I think you've got a typo in the command:
```
jniko@JNiko-Ubuntu:/$ sudo ndiswrapper-l
sudo: ndiswrapper-l: command not found
```There should be a space between ndiswrapper & the -l.  Try copying & pasting this into the terminal:
```
sudo ndiswrapper -l
```-Dave

---

### Post by divague on 2007-04-25
> **BigNeek said:**
> jniko@JNiko-Ubuntu:/$ sudo ndiswrapper-l
sudo: ndiswrapper-l: command not found

You are missing a space between ndiswrapper and -l, should be
$sudo ndiswrapper -l

---

