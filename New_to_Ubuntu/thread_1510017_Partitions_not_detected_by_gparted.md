---
title: "Partitions not detected by gparted"
date: 2010-06-15
forum: New to Ubuntu
---

### Post by Pas_sa on 2010-06-15
Hi guys,

Recently swapped a new drive into my Thinkpad and reinstalled everything from scratch. Installed Windows 7 first, then booted from the 10.04 Ubuntu CD and tried repartitioning my drive.

Gparted however claims my drive is blank and wants to allocate the whole thing to Ubuntu. In Windows, it detects the two partitions (a 100mb partition created by Windows 7 and the rest is just Windows 7).

Before installing Windows 7, I had experimented with hackintoshing, so the drive had a GUID table and a HFS partition. Windows 7 setup apparently wiped this all out and replaced it with a MBR and NTFS partition.

I've got a feeling there are remnants left over, hence confusing gparted (which says something about corrupted GUID tables in the console output). I've tried restoring the MBR with the Windows Recovery Console, I've tried shrinking the NTFS partition and creating space for Ubuntu.. still, gparted won't detect anything.

What can I do to get the dual boot running without wiping out my Windows 7 install?

---

### Post by garvinrick4 on 2010-06-15
```
sudo apt-get remove dmraid
```

While in Live CD give this code, then to straight to install.

---

### Post by srs5694 on 2010-06-15
garvinrick4's suggestion is unlikely to help. It sounds like the drive has leftover GPT data on it, which is confusing GParted. The easiest way to deal with this is to use my [GPT fdisk (aka gdisk)](http://www.rodsbooks.com/gdisk/) program, which you can can use via [PartedMagic](http://partedmagic.com) or [System Rescue CD.](http://www.sysresccd.org)

To fix your problem, follow these steps:


[list=1]
[*]Boot the emergency disk and open a text-mode shell.
[*]Type "gdisk /dev/sda" (change "/dev/sda" to whatever is appropriate to access your hard disk, if necessary). The program is likely to complain that it's found both MBR and GPT data, and will ask which to use. It doesn't matter which you tell it to use.
[*]At the "Command" prompt, type "x" to enter the experts' menu.
[*]At the "Expert command" prompt, type "z" to "zap" (destroy) the GPT data.
[*]Type "y" in response to the confirmation about destroying the GPT.
[*]Type "n" in response to the query about blanking the MBR. **Caution: If you answer "y" here, you'll destroy your Windows partition(s)!**
[/list]


The program will now exit. I recommend you test that this worked by using GParted. If GParted can now see your Windows partition(s), the Ubuntu installer should do so, too.

---

### Post by Pas_sa on 2010-06-18
Wow, thanks srs5694, that worked perfectly! Cleaned out the GPT data, preserved the MBR stuff. Awesome :)

---

### Post by northrrm on 2010-07-21
Thanks srs5694!  Same thing on this machine... failed hackintosh attempt.  Clean install of Windows 7.  Everything seemed fine until I tried to install Ubuntu.

I used GPT fdisk 64 bit under an Ubuntu 10.04 64 bit live disc.  Flawless victory.  :D  Informative and helpful website too.

---

### Post by jinjanjaa on 2010-11-21
i followed the procedure exactly as mentioned srs5694. Neither ubuntu install nor gparted detects my hard disk. I have a samsung 60gb hd; some 6yrs old. can any1 help me???

Btw i want to install ubuntu 10.10

---

### Post by randumnumber on 2010-11-21
> **jinjanjaa said:**
> i followed the procedure exactly as mentioned srs5694. Neither ubuntu install nor gparted detects my hard disk. I have a samsung 60gb hd; some 6yrs old. can any1 help me???

Btw i want to install ubuntu 10.10

This thread is a few months old and marked as solved which means few people are likely to respond to your request you should start a new thread, and be sure to give more detail about your issue.

---

### Post by jinjanjaa on 2010-11-21
i'll do that.......

---

