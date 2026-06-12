---
title: "Multiple Boot Configuration"
date: 2009-07-07
forum: New to Ubuntu
---

### Post by FuaK on 2009-07-07
Hello, in the first place you will have to apologize for all the grammar error and the miss spells, feel free to correct any mistake I would appreciate it!
   
  Well, the name of the thread says everything, I have 3 HDD, one of them I installed Windows XP SP2 recently with no data on it, and the other 2 HDD are absolutely clear. What I have in mind is to have a Dual Boot, in one hand Windows XP and on the other one is Linux Ubuntu to start practicing, I was thinking to have both OS on different HDD so I don’t have any conflicts. I’ve been reading about the subject and I have some questions:
   
  1)[FONT=&quot]      [/FONT]I have been looking for some guides to create a Dual Boot, but I wanted to ask you to recommend a good source. I should use the GRUB or another Boot Loader?
  2)[FONT=&quot]      [/FONT]Which program to manage the Partitions do you recommend? I have downloaded Partition Magic, should I use this or another?
  3)[FONT=&quot]      [/FONT]I’m little confuse with the Format do I have to give for the Linux OS, I’ve been reading that I should  put ext3 or FAT32 to get a better data transfer. I read, if I’m not mistaken, that I can copy all my Windows data on a DVD and I can download it on o ext3 without a problem is it correct?
   
   
  Well, for now those are all the questions, soon I may add more!
   
  Thank you for reading, I hope you can help me out with some of this things!
   
  Cya!

---

### Post by sdlynx on 2009-07-07
1)GRUB is the easiest to use as it is the default for Ubuntu anyway.
2)Use GParted.  It comes with the Ubuntu live disc (go to System > Administration > Partition Editor).
3)ext3 or ext4 are ideal.  Yes, you can copy your files off of Windows and paste them onto your linux hard drive that is ext3.  In fact, if you want to you can just copy the things you want from your Windows HDD onto your Linux HDD since Ubuntu can view NTFS and Fat/32 partitions (Windows' journaling systems).

---

### Post by nhasian on 2009-07-07
no conflicts.  even if you install multiple operating systems on the same hard disk.  as long as you have enough space :)

1) yes use grub or grub2 if you install Karmic.  [here's]("http://www.psychocats.net/ubuntu/index") a detailed guide to installing ubuntu.

2) boot off the liveCD and go to System->Administration->Partition Editor or it may be called gparted depending on your version.  you can create or resize partitions with this.

3) FAT32 and NTFS is only for windows.  you should use EXT3 or EXT4 in ubuntu.

---

### Post by sdlynx on 2009-07-07
> **nhasian said:**
> no conflicts.  even if you install multiple operating systems on the same hard disk.  as long as you have enough space :)

1) yes use grub or grub2 if you install Karmic.  [here's]("http://www.psychocats.net/ubuntu/index") a detailed guide to installing ubuntu.

2) boot off the liveCD and go to System->Administration->Partition Editor or it may be called gparted depending on your version.  you can create or resize partitions with this.

3) FAT32 and NTFS is only for windows.  you should use EXT3 or EXT4 in ubuntu.

beat you to it =]

---

