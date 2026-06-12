---
title: "New Ubuntu User: (initramfs) Prompt After Alternate CD Installation 9.10 w/ RAID"
date: 2010-01-14
forum: New to Ubuntu
---

### Post by WhiteyWan on 2010-01-14
Originally posted in the Installations Forum but no response there.  I'll post here as it really is a Absolute Beginner question, heh.
 
I am trying to install Ubuntu on a nvidia board which, based on the forums I have perused, is a FAKERaid chipset. Originally I tried to install according to [[COLOR=#444444]https://help.ubuntu.com/community/FakeRaidHowto[/COLOR]]("https://help.ubuntu.com/community/FakeRaidHowto") to no avail. I gave up and am resorting to breaking down my raid setup (thus losing my Windows XP installation) and using Linux's software raid (which seems to be the recommended method) with the Alternate CD install. 

I went in to the bios and completely disabled my board's RAID function. I then followed the instructions here: [[COLOR=#444444]https://help.ubuntu.com/community/In...n/SoftwareRAID[/COLOR]]("https://help.ubuntu.com/community/Installation/SoftwareRAID") , except it popped up with a window advising me "one or more serial ATA RAID configurations have been found. Do you wish to activate these RAID devices?" which that page didn't mention. I believe I selected "Yes". Setting up the partitions I made (from beginning of disk to end of disk) a RAID1 200MB /boot partition, a RAID0 / partition (90GB?), free space not set up in RAID (approx 20GB for each SATA drive to later install Windows on [if that's even possible]) & then the SWAP partition 2GB at the end of one of the disks (is it OK that this one wasn't in RAID?).

The installation completed, as far as I can tell, without a hitch. Except also of note: my network card doesn't work in the installer (gives an error message about unable to configure dhcp) so i'm not connected to the internet. Then I restart and the following appears:

[B]grub loading:
error: biosdisk read error.[/B]

Followed by what appears to be the Ubuntu loading splash (just a small white shape in the middle of the screen), and then: 

[B]gave up waiting for root device. *Common problems:*
- boot args (cat /proc/cmdline)
- check rootdelay= (did the system wait long enough?)
-check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/XXXXXXXXXXXXXXXX does not exist. Dropping to a shell!
BusyBox v1.13.3 (ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)
(initramfs)[/B]

I have no idea what this prompt even means. I then attempt to go back into the installer with a hunch that maybe I need to de-RAID my /boot file partition and set up an individual /boot on each SATA disk. I boot the installer and ALL the previously configured partitions are gone.

I'm at a loss. I keep trying to do research on the web but most everything I can find is either far too technical for someone completely new to Ubuntu or does not apply to my set up as far as I can tell (coupled with the gross probability that I'm making numerous fatal mistakes). I lost my Windows installation and my desktop is the only one in my five person household. My mother is nagging at me because she has to do her Farmville on my Macbook without a mouse...and thus I plead my case here. Can anyone help? If you have something for me to try that requires working from the (initramfs) command prompt you will have to give me step by step instructions as I have very minimal experience with any command prompt style systems & none whatsoever with Linux. Any help would be greatly appreciated.

---

### Post by WhiteyWan on 2010-01-14
Since originally posting this in the other forum, I have tried a new installation with partitions configured such that all free space was at beginning of disk and the /boot partition is not a RAID partition.  My /boot is a .ext3 file system (I changed the "Bootable Flag" to 'yes', which I think is necessary) that I mounted on the first SATA drive listed in the partition managing part of the installer.  I'm assuming the first SATA drive listed would be the one that the system attempts to boot from by default but is this necessarily true? Regardless, I ended up with the exact same:
[B]grub loading:
error: biosdisk read error.

[/B]Followed by what appears to be the Ubuntu loading splash (just a small white shape in the middle of the screen), and then: 

[B]gave up waiting for root device. *Common problems:*
- boot args (cat /proc/cmdline)
- check rootdelay= (did the system wait long enough?)
-check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/XXXXXXXXXXXXXXXX does not exist. Dropping to a shell!
BusyBox v1.13.3 (ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)
(initramfs)[/B]

Any help for an Ubuntu n00bie?

---

### Post by WhiteyWan on 2010-01-14
New info:
After the 

grub loading:
error: biosdisk read error.

I am now getting a new error message:

udevd-work[123]: pipe failed: Too many open files

Not sure if this was coming up before but I just now noticed it...

---

