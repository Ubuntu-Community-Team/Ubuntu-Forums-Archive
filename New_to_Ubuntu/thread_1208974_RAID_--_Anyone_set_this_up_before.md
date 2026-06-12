---
title: "RAID -- Anyone set this up before?"
date: 2009-07-09
forum: New to Ubuntu
---

### Post by beetlejuice_masterson on 2009-07-09
So I acquired this sony vaio with 2x 160GB HDD (very weird).  They were previously in a RAID configuration.  I tried installing ubuntu 9.04 and it managed to install properly but upon reboot GRUB dies (error 2).

My hard-drives are /dev/sda and /dev/sdb .  /dev/sda is the one with ubuntu and all that jazz on it.

Anybody got any ideas about why GRUB is failing?  I tried supergrub to no avail.

---

### Post by whitethorn on 2009-07-09
I have to Tb HDs in my computer with a raid 0, I used this page to get ubuntu installed and running

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

It works.  I needed to use this when I reinstalled Windows 7, to get grub working again.

---

### Post by orlox on 2009-07-09
Actually, the ubuntu alternate installer detects RAID arrays, so if you want to install a clean system, and have a RAID setted up in your BIOS, just use the ubuntu alternate installer and it will be easy...

---

### Post by beetlejuice_masterson on 2009-07-11
Thanks for the help.  I tried a couple methods, including alternate install (both manually partitioning & letting it do automatically).  Still getting GRUB errors (2, 21, and 17 depending on how i install ubuntu).

Apparently, this Vaio is notorious.  It has 2 seagate SATA drives that MUST be in a RAID0 configuration.  I tried unplugging one or the other and the BIOS failed to detect a hard disk...It only detects a disk if both are installed (and then it considers it "1" hard drive).  So that's weird.

I installed Ubuntu in a RAID0 configuration and started getting GRUB Error 17.

I tried using SuperGRUB to no avail.

What the heck is going on?  This guy seems to have gotten Fedora Core 4 to work on his machine -- but I don't know how to make a startup CD in ubuntu.  I know at least linux is possible -- just not sure how to do it with ubuntu.

[http://linux.derkeiler.com/Newsgroups/comp.os.linux.setup/2005-11/0326.html](http://linux.derkeiler.com/Newsgroups/comp.os.linux.setup/2005-11/0326.html)

---

### Post by beetlejuice_masterson on 2009-07-11
OK - just an update.  I was able to get Fedora Core 4 working using the above instructions (link).

The problem is it's fedora core 4.

I want to use ubuntu 9.04!!

So how would I go about making a bootdisk iso (for a CD) using ubuntu?

What worked on the FC4 install:
Install as usual
Re-insert disc 1 and get to a recovery terminal
Filesystem is mounted in /mnt/
cd to /mnt/sysimage/
mkbootdisk --iso --device boot.iso `uname -r`

Worked like a charm.  Problem is Ubuntu has no mkbootdisk.  Any ideas?

---

### Post by beetlejuice_masterson on 2009-07-26
Bump.

Anybody got any ideas?  Need to install ubuntu in RAID0 -- on a very persnickety sony vaio.

---

