---
title: "Ubuntu Won't Start After Login Screen"
date: 2011-01-09
forum: New to Ubuntu
---

### Post by Mr. Eggplant Man on 2011-01-09
I am using WUBI on a an HP Dell, and when the welcome screen comes up, followed by the OS list, I click Ubuntu. It displays: Auto Detect: Entering Power Save, goes black, then about 3 seconds later, goes back to the welcome screen. What do I do?

---

### Post by bcbc on 2011-01-09
See the [wubi megathread]("http://ubuntuforums.org/showthread.php?t=1639198"), problem #2, solution #1. When it's booting apply the Permanent Fix.

---

### Post by Mr. Eggplant Man on 2011-01-09
...? I had NO idea what that guy was talking about, but I don't have any kind of disk or USB to try and boot it on.

---

### Post by bcbc on 2011-01-09
So in simple terms, Ubuntu has broken itself due to problems with it's bootloader Grub.

Your options are:
1. to obtain an Ubuntu CD/USB to repair it
2. to recover data from it and remove it

1. Go to [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) and go to step 2, select I want to create a CD or USB and click on SHOW ME HOW.
2. There is a tool [http://ext2read.blogspot.com/](http://ext2read.blogspot.com/) that you can install on Windows and point it at c:\ubuntu\disks\root.disk and then copy data off it.

---

### Post by Mr. Eggplant Man on 2011-01-10
This is really unfortunate, and it will probably sound disappointing, but I'm running WUBI on my family computer. I'm 13. I'm the only one who uses it, and everyone else in my family is basically afraid of it. Within 2 months I'll probably have my own laptop, and be able to dual boot and run it fine. But for now, I have basically no access to any other software or extensions/downloads of any kind. I've had this problem before, and it resolved itself; I think it MIGHT have to do with external devices, like my iPod in particular. I'll experiment. But thanks for the help, you're all MUCH nicer than the people at Mythbusters forums. And I'm SO glad the ad-man is GONE! UBUNTU FORUMS!

---

