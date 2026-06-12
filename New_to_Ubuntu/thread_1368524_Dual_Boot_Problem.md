---
title: "Dual Boot Problem"
date: 2009-12-30
forum: New to Ubuntu
---

### Post by Moonlitflower on 2009-12-30
Hi I'm new to the forum and new to Ubuntu ^__^ At first I wasnt sure if I was going to like Ubuntu so I did a dual boot. I previously used Windows Xp. The first time I booted my computer after the initial installation was the only time that my computer actually gave me the option of choosing between Xp and Ubuntu at the startup. Therefore, I havent logged back into XP. Is that normal? How do I switch between the two? I am satisfied with Ubuntu though and I want to get rid of XP permanently. The Linux side of my hard drive is after all, running out of space. So how do I get rid of it once and for all?

---

### Post by tom.swartz07 on 2009-12-30
> **Moonlitflower said:**
> Hi I'm new to the forum and new to Ubuntu ^__^ At first I wasnt sure if I was going to like Ubuntu so I did a dual boot. I previously used Windows Xp. The first time I booted my computer after the initial installation was the only time that my computer actually gave me the option of choosing between Xp and Ubuntu at the startup. Therefore, I havent logged back into XP. Is that normal? How do I switch between the two? I am satisfied with Ubuntu though and I want to get rid of XP permanently. The Linux side of my hard drive is after all, running out of space. So how do I get rid of it once and for all?

Hi and welcome!

Im glad to hear about your flawless install. 
When you choose to boot into your Ubuntu Operating System, that is what you will use until you restart your computer. Just like Windows XP, Ubuntu is an environment that allows you to run programs quickly and easily.

If you are **completely certain** that you no longer need Windows XP, I would suggest Re-Installing Ubuntu and selecting the option to 'Use entire disk'. This will prevent some problems that you might encounter that challenge even seasoned Ubuntu users.

---

### Post by DasEi on 2009-12-30
Do you still need files from the xp-install ?
Else use gparted to format the partition to ext3 or 4 ,
create a mountpoint and put an entry in fstab, so the space
gets mounted at bootup

---

### Post by Merk42 on 2009-12-30
You should be able to choose XP or Ubuntu any time you start your computer.

As for switching to 100% that depends on how you installed it.
If you did it via WUBI, you'd need to do a full fresh install
If you did it via LiveCD and made a seperate partition, you'd be able to erease the NTFS (Windows) partition and extent the Ext3 or Ext4 (Ubunut) partition

**In either case you would at least lose everything you had in Windows, files, etc, so backup documents and the like before proceeding**

---

