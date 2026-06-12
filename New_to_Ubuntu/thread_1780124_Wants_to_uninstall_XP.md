---
title: "Wants to uninstall XP"
date: 2011-06-11
forum: New to Ubuntu
---

### Post by BystanderLC on 2011-06-11
I just installed Ubuntu 11.04 using Wubi, because my computer could not read empty disks nor could it boot from my USB flash drive.

I'm very new to this and I want to uninstall Windows and everything on it, because spyware and malware has been getting through my firewall.  I've already made backups all over the Internet, so how do I uninstall Windows?

---

### Post by VOT Productions on 2011-06-11
You are in luck. [https://wiki.ubuntu.com/WubiGuide#How do I migrate to a real partition, and/or get rid of Windows entirely?]("https://wiki.ubuntu.com/WubiGuide#How do I migrate to a real partition, and/or get rid of Windows entirely?")

---

### Post by BystanderLC on 2011-06-11
Right.  I've tried to follow that, but I don't understand a lot of it.

I downloaded wubi-move-2.0.sh.tar.gz.

Extracted wubi-move-2.0.sh to my desktop.

Dunno what to do next.

---

### Post by VOT Productions on 2011-06-11
Now you need to create a partition using the program "GParted", and shink Windows to the very least. The file format is ext4. Also... it's a good time to move your files to the new partition.

You be better off erasing Windows and starting again.

---

### Post by 3xp10r3r|X13 on 2011-06-11
well, basically if you just went through a wubi installation, Ubuntu is running through windows.

You--> doing something in ubuntu --> ubuntu running under windows --> windows doing changes to you hard drive

WUBI = windows-based ubuntu installer

This means, that your ubuntu OS is stored somewhere in the windows partition. (you can even uninstall it as any program you're having on windows "system panel --> programs --> uninstall")

I think you would agree that erasing the Windows partitions would be a very bad idea. (you would end up with no OS at all)
Wubi is really unstable anyway and a bit slower, because it is always accessing windows, while doing something. You can't even put your pc to sleep/standby.

The whole thing leaves you with a little problem. Your only way out is to perform a fresh installation of Ubuntu.

Sry, but that's WUBI

---

### Post by VOT Productions on 2011-06-11
I don't recommend using Wubi at all. It is better off a dualboot.

---

### Post by avuser on 2011-06-11
Need to reinstall. You can go into advanced partition options and redo all your partitions the way you want them. ie. swap, /, home, or something else like a storage partition. Experiment have fun that's what linux is all about. Just make sure you back up all your important data.

---

### Post by BystanderLC on 2011-06-11
Well, I would've gone with installing it from the CD, but my disk drive couldn't find anything in it.  And well, I was hoping my USB flash drive would be automatically detected when I restarted the computer, but I guess since it's old it wouldn't work that way.

I'm downloading ubuntu-11.04-desktop-i386.iso again.  And gparted-live-0.8-1.3.iso (didn't see a ext4 anywhere)

I hope this time my computer will see the CD in there so I can copy and paste the iso on the CD.

Also, on startup Ubuntu said some hardware wasn't found and that I have to switch to classic or something.

---

### Post by VOT Productions on 2011-06-11
No... you need to shrink Windows and make a new partition.
You'll be better backing up and deleting Windows and making a new ext4 instead.

---

### Post by avuser on 2011-06-11
0

---

### Post by BystanderLC on 2011-06-11
Sorry, but what do you mean by shrinking Windows?

Okay, the download's finished, but there's no exe file, so I'm still pretty much confused.

---

### Post by VOT Productions on 2011-06-11
> **BystanderLC said:**
> Sorry, but what do you mean by shrinking Windows?

Okay, the download's finished, but there's no exe file, so I'm still pretty much confused.

I recommend you wipe your computer off every OS and you install Ubuntu. While it is possible to migrate Wubi to a partition, you won't understand it. Make sure to backup.

---

### Post by kurok on 2011-06-11
> **BystanderLC said:**
> 

I hope this time my computer will see the CD in there so I can copy and paste the iso on the CD.
 Thats part of your problem. You need to burn the iso as an ISO image just copying and pasting wont work properly. I use a program called cdburnerxp. After you do that come back with any more questions.

---

### Post by VOT Productions on 2011-06-11
The Ubuntu equivalent is Brasero

---

### Post by webmasterpride on 2011-06-11
Thanks for sharing the info.  I got my Windows XP uninstalled.

---

### Post by VOT Productions on 2011-06-11
Was it successful?

---

### Post by BystanderLC on 2011-06-12
Okay, I got my friend to come over and help me out.  The reason my computer didn't pick up the iso from the USB flash drive was because I didn't have the Universal USB Installer on there.  We did the second option which was to run it and now, I have only Ubuntu on my computer.

---

