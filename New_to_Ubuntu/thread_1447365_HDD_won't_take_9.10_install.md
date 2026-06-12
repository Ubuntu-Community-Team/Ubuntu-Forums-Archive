---
title: "HDD won't take 9.10 install"
date: 2010-04-05
forum: New to Ubuntu
---

### Post by Garthhh on 2010-04-05
Pentium III 1g ram, 1.2ghz processor
western digital 160g HDD [new] pri
seagate maxtor [8.04 lts] 40g slave

I've been using the 8.04 40g hdd as the primary, for a few months
I got the bigger HDD & did a 8,04 install, seemed ok
upgraded all the way to 9.10, had some weirdness going on, OO wouldn't convert a file to doc, just kept crashing, couldn't get songbird to install

so I burned a cd w/9.10, hash checked good. booted from it & let it check the integrity that way too.  Installed, won't run with out the cd
reinstalled same result.  reinstalled as a dual boot, same.

reinstalled the 40g HDD as slave, with the existing 8.04 install.

how do get a 9.10 install working?
suggestions?

---

### Post by J V on 2010-04-05
Reinstall grub from the live cd (Google it)

---

### Post by Paqman on 2010-04-05
> **Garthhh said:**
> Installed, won't run with out the cd
reinstalled same result.  reinstalled as a dual boot, same.


Can you be a bit more specific? After installing and removing the CD from the tray, what happens when you boot? Does the machine POST? Do you get Grub? Does your other install boot? Does it begin to boot and then just black screen? Or something else?

---

### Post by Garthhh on 2010-04-05
> **Paqman said:**
> Can you be a bit more specific? After installing and removing the CD from the tray, what happens when you boot? Does the machine POST? Do you get Grub? Does your other install boot? Does it begin to boot and then just black screen? Or something else?

grub loads, but the version numbers are like 1.6
if I click on it, file doesn't exist

I had a working 8.04 install on the new hdd
my old install on the 40g hdd [old] works fine

All 3 of the 9.10 installs seemed normal
after the 1st went to bios & changed the boot order to hdd.  I tried to open the cd, it wouldn't [not that unusual] restarted, didn't realize that I was running on the cd until I did a restart [after installing an app] & was able to remove the cd.
The 1st 2 installs I choose to use the entire hdd...

---

### Post by Garthhh on 2010-04-08
> **Garthhh said:**
> grub loads, but the version numbers are like 1.6
if I click on it, file doesn't exist

I had a working 8.04 install on the new hdd
my old install on the 40g hdd [old] works fine

All 3 of the 9.10 installs seemed normal
after the 1st went to bios & changed the boot order to hdd.  I tried to open the cd, it wouldn't [not that unusual] restarted, didn't realize that I was running on the cd until I did a restart [after installing an app] & was able to remove the cd.
The 1st 2 installs I choose to use the entire hdd...

I did a new 9.10 CD burn from a bit torrent download, same result
grub showing 1.6...

I did a new 8.04lts install
put the 9.10 cd in, asked me if I wanted to upgrade
I did the upgrade with the cd
everything seems to be working fine
I burned a new 8.04 cd
so now I have a method that is:
install target HDD into my Pentium III desk top [I have an adapter for notebooks], install 8.04  upgrade to 9.10  customize layout for end user.  

I have a couple of older friends who have trouble keeping up with the windows madness.  They don't want to much more than email & pics of the grandkids.  I'll probably just leave them on 8.04lts until the 10.04lts comes out.  

I haven't had much luck with the usb install process on any of my old beater machines.

---

