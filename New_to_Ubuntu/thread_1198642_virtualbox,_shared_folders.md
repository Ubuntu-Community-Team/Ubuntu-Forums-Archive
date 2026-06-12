---
title: "virtualbox, shared folders"
date: 2009-06-27
forum: New to Ubuntu
---

### Post by mpennell on 2009-06-27
Hi gang. Getting very frustrated here. Drives me nuts when I follow directions to the letter and things still don't work as people promise me they will.

I installed virtualbox. I want a shared folder with my Xubuntu and XP (this is simply an attempt at using my Lexmark printer). Ok, I follow to a tee- but cannot create a working shared folder. I've read the virtualbox help, done EXACTLY as stated, but when I click "Install Guest Additions" absolutely nothing happens. No error message, no activity whatsoever. NOTHING.

Does ANYTHING in cyberland work as advertised?!!!

Any help would be appreciated.

---

### Post by MasterProg on 2009-06-27
Which of these operating systems is the host and which is the guest?

I guess XP is the guest.
In this case, make sure that you have a CD drive in your configuration and autorun enabled (or install it yourself then).

---

### Post by 4Orbs on 2009-06-27
When you first install guest additions, you click on the button outside the virtual machine (host). This puts the guest-additions folder for the guest inside the virtual machine. Then as the guest, you need to open your file manager and there should be a prominent GUEST-ADDITIONS link over in the leftside pane of thunar. You need to open that and double click on the executable for your particular version of Linux. Then your shared folders should work.

I'm assuming that you dual boot XP and Xubuntu and that Xubuntu is the host and you have another Xubuntu installation running inside the Virtualbox as guest.

---

### Post by mpennell on 2009-06-27
Never mind-- I seem to have blundered my way to a solution. I found a mention online that if you click INstall Guest Additions and nothing happens, then you have to Unmount the CD Drive (might have been nice is this was mentioned in the virtualbox help). Why this is so, I have no clue. But it worked. I had a pain getting the Printer running but eventually got it though I literally don't remember the exact steps I took.

Mainly I did this b/c I wanted the experience. Qui-Gon James, the Super Cool IT Guy, is coming over tomorrow and is going to help get my Lexmark running straight from Xubuntu. I will feed him, of course. Definitely make it worth his while! But if it turns out he's wrong and he can't get it, then there's this to fall back on.

---

