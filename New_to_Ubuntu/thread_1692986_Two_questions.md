---
title: "Two questions"
date: 2011-02-22
forum: New to Ubuntu
---

### Post by Lainie on 2011-02-22
I'm brand new to ubuntu and have been using it for about three weeks.  I have ubuntu installed in two places and need a bit of help for each one.

I have a gateway NV54 dual core laptop, and put ubuntu 10.10 on it.  I have the suspend/blank screen bug, and would like to know if there is a way to fix it.  I would need step by step instructions, unfortunately.  I have a high tech level ability (I've built my own computer), but have no understanding whatsoever of any programming language, including debian.

Second problem.  I have ubuntu installed on a second hard drive on my desktop, windows xp being my main hard drive, and I boot them via grub.  I have had ubuntu there for some time but barely used it.  I really learned what I know of ubuntu using my laptop these last three weeks.  My desktop hard drive has build 10.04 on it and I want to upgrade to 10.10.  I cannot do it in the normal way because I keep getting an irreversable error message and can't figure out how to fix whatever is causing the problem, so have decided to just do a clean reinstall.  I've made an iso flash drive which is ready for the install.  My problem is that I don't know what will happen to grub if I do a clean install, because it is my understanding that grub lives on my ubuntu drive.  Also I want to make sure that I don't accidentally wipe my xp drive, and don't know how to insure certainty that I have the right drive.  I need to know what to do so that I end up with ubuntu on the right drive and grub in good working order so that I can access both hard drives.

I would appreciate any help I could get for these two questions.

---

### Post by eriktheblu on 2011-02-22
Can't help you with the first, other than that Debian is a distribution, not a language.

2nd: Why do you want 10.10? 10.04 is the current LTS (Long Term Support) version. It is quite stable,less than a year old, and will continue to be supported until 2013. For those new to Ubuntu, the LTS version is often recommended as it typically has fewer bugs.

If you do a clean install, Grub will be reinstalled. 

Grub lives in the /boot directory of your Ubuntu file system. Depending on your file system, it could be physically located any number of places (Linux is cool like that). If you used a default install profile on your second hard drive, it will be in the main EXT partition of your second drive. 

You ought to be able to see the file system type before you format anything. Windows uses NTFS where Ubuntu prefers EXT4.

---

### Post by lykeion on 2011-02-22
There's a thread in this forum called Laptop compatibility list. In this thread I found this post: [http://ubuntuforums.org/showpost.php?p=10309450&postcount=365](http://ubuntuforums.org/showpost.php?p=10309450&postcount=365)

Regarding overwriting Windows partition when you do a clean Ubuntu installation: In the installation process you'll come to a step - "Prepare disk space" - where you are asked what to do with earlier partitions. You'll have the choice to "Specify partitions manually" and with that you can keep your Windows installation.
See these pages: 
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

About your irreversible error message when trying to update to 10.10, it could be just some issues with your repositories, or it could be something else. If you could paste the error message it would be easier to help.

---

### Post by Bucky Ball on 2011-02-22
Welcome.

> **eriktheblu said:**
> 

2nd: Why do you want 10.10? 10.04 is the current LTS (Long Term Support) version. It is quite stable,less than a year old, and will continue to be supported until 2013. For those new to Ubuntu, the LTS version is often recommended as it typically has fewer bugs.



+1. I'd stick with it.

---

