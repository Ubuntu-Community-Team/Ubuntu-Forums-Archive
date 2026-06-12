---
title: "Windows XP &amp; Ubunto Dual?"
date: 2011-05-27
forum: New to Ubuntu
---

### Post by WebHome on 2011-05-27
It is possible that windows XP and ubuntu 11.04 ver. make a dual i heard some people that they can't install or one of the OS windows XP are not compatible with ubuntu?:(

---

### Post by Sef on 2011-05-27
> It is possible that windows XP and ubuntu 11.04 ver. make a dual i heard some people that they can't install or one of the OS windows XP are not compatible with ubuntu?

It is easier to dual boot XP and Ubuntu than with Vista or Windows 7.  Just back up your files as no 100% guarantees exist.

---

### Post by A Ghost In The Machine on 2011-05-27
Yes PLEASE back up your files. I just lost my windows XP to trying to separate partitions, between XP and Ubuntu.... I had to spent 30 bucks to get a recovery disk from HP. Just back everything up, watch the partitions, and happy trails

---

### Post by wildmanne39 on 2011-05-27
> **WebHome said:**
> It is possible that windows XP and ubuntu 11.04 ver. make a dual i heard some people that they can't install or one of the OS windows XP are not compatible with ubuntu?:(Hi, here is a link for dual booting. [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1)

---

### Post by khelben1979 on 2011-05-28
Having Ubuntu and Windows XP on 2 separate hard discs is the safest way, because the MBR cannot get messed up in case of some mistakes being done. So I would recommend that if your budget allows you to.

Otherwise, you haveto install Windows XP first and make sure to not partition up the whole hard disc, so you got free space for an Ubuntu installation afterwards.

If the [MBR]("http://en.wikipedia.org/wiki/Master_boot_record") gets messed up at some later point in time, then you can change boot priority in BIOS and by that having the 2 hard discs and make them boot up properly.

---

### Post by TAspr on 2011-05-28
> **WebHome said:**
> It is possible that windows XP and ubuntu 11.04 ver. make a dual i heard some people that they can't install or one of the OS windows XP are not compatible with ubuntu?:(

Install Windows first, then Ubuntu.  

The steps;

boot off of a "Gparted" CD to install a new ext4 partiton on the un-partitioned drive that you want to use for linux using "\" as the location, then create the new partiton.

If you need anymore help feel free to ask.  

Pls backup just in case.

---

### Post by Miljet on 2011-05-28
> you haveto install Windows XP first

Just for the record, this is absolutely UNTRUE! I will agree that it is easier to install Windows first, but by no means required.

---

### Post by eb3ha4el on 2011-05-28
> **A Ghost In The Machine said:**
> Yes PLEASE back up your files. I just lost my windows XP to trying to separate partitions, between XP and Ubuntu.... I had to spent 30 bucks to get a recovery disk from HP. Just back everything up, watch the partitions, and happy trails



So it does happen.. 
I should get a eHD..

---

### Post by 3rdalbum on 2011-05-28
> **eb3ha4el said:**
> So it does happen.. 
I should get a eHD..

Yes, resizing a partition does carry the risk of losing data. If you get an external HDD, use it for making a backup, not for installing Ubuntu onto. (a backup will also help if you lose data on the Windows side due to ordinary Windows corruption, electrical surges, natural disasters etc).

To Webhome (the OP): After you've made a backup, just boot up your computer from the Ubuntu CD (change the boot order in your BIOS setup so the CD is booted from). Select "Install Ubuntu" when asked. The installer will give you the option of resizing your Windows partition to make space for Ubuntu. Just follow the on-screen directions and you'll be fine.

---

### Post by khelben1979 on 2011-05-29
> **Miljet said:**
> Just for the record, this is absolutely UNTRUE! I will agree that it is easier to install Windows first, but by no means required.

Since this is the forum for Absolute Beginner Talk, I'm sure anyone in here are more interested to get things working a.s.a.p. Sure you can do things in many ways, thereby complicating it for newbies and making things worse for them.

Any way, thanks for your statement, I'm sure you're correct about that. And just for the record, I have messed up hard discs myself where I did not install Windows first, so I tried to be helpful preventing a possible bad scenario for him.

---

