---
title: "grub rescue&gt; remove winXP and install 10.10 (64bit)"
date: 2011-02-06
forum: New to Ubuntu
---

### Post by kbrand on 2011-02-06
Update:

reposted to "Main Support Categories > Installation & Upgrades"

Dear New and Esteemed Ubuntu users,

Yet another-

error: no such device: e7be........
grub rescue>

However i failed to find any threads detailing simply how to install ubuntu 10.10 obliterating a previously installed WinXP.

It cant be so hard, but id really appreciate some tips getting past this error. Some details which will no doubt be needed to help any one with the patience to help me:

1. First attempt to install 10.10 (64bit) from USB went smoothly, until the inital restart and failure to boot into Ubuntu.
2. I fiddled around with the SCSI config utility thinking ubuntu was having trouble with the PERC 320/DC SCSI controller i was trying to install ubuntu onto (2x SCSI dives in RAID0 as XP was previously installed onto, and as ubtunu detected as a single drive (array?) in 1. above). Failure to boot into Ubuntu.
3. Repeated 1. above, failure to boot into Ubuntu.
4. At this point i got the error mesage:

error: no such device: e7be........
grub rescue>

and couldn't even boot from the USB-thumb drive

5. Burned a Ubuntu 10.10 (64bit) live-CD, but it also failed to boot fromt eh live-CD, and again yielded only the message:
error: no such device: e7be........
grub rescue>

6. At the grub rescue> prompt, ls returns:

(hd0) (hd0,msdos5) (hd1) (hd1,msdos1) (hd2) (hd3) (hd3,msdos5) (fd0)

7. System details:
-Dell Precision 670 with dual monitor video card
-PERC 320/DC SCSI controller with 2x maxtor SCSI drives attached
-XP was installed here as RAID0
-2x NTSF formatted SATA drives
-1x cd-rom drive
-1x floppy drive

I geuss the MBR is mixed up. But why i cant boot from USB or CD-ROM is perplexing. And an impasse to getting 10.10 up and running!!

Would very much appreciate suggestions poitners to recources to remove the XP scrouge from this system permanently and get ubuntu running sweet on the SCSI drives.

tia, Karl

---

### Post by YesWeCan on 2011-02-09
You originally had XP installed on a RAID 0 array?
This may be the cause of problems, see [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

So, enter the bios and disable all RAID options.
Then boot off a live CD or USB and use the "disk utility" to erase both disks completely and renew their MBRs. I assume there is no data you need to keep. Then try installing Ubuntu on sda.

If you want to use RAID 0 for Ubuntu you can. You will need to install Ubuntu using the alternative CD (which is not a live CD). See [https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)


If you are still having trouble booting a live CD/USB then please elaborate on how the boot fails.

---

### Post by kbrand on 2011-02-09
Thanks alot YesWeCan.

I actually progressed to disabling all RAID options and CAN boot from USB again. Hoping that after installing onto one of the SATA drives i can then undertake your final suggestion for installing onto the array.

cheers, kb

---

### Post by kbrand on 2011-02-10
UPDATE:

Having scanned [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
i'm thinking my Perc 320/DC SCSI raid controller is actually bona fide hardware raid. Though i could be wrong, i'm sufficiently sure to try to install a version of Ubuntu that supports this device under a raid0 configuration. Which the desktop version, despite my attempts, has failed to so far.

If i'm correct, is the server version of Ubuntu what i should be attempting this with? If so can this be achieved via a GUI from a USB stick?

FWIW:

Desktop ubuntu booted from USB and detected the SCSI drives when they were- 
1. Wiped and unconfigured using Ubuntus nice "disk utility"
2. Wiped and configured as RAID1 using the raid controller bios during statup.

But as soon as i changed the configuration to RAID0, i could no longer boot from the Ubuntu USB.

Disclosure:

I've only installed an OS (winXP) on RAID0 (on board fakeraid) twice. I've never tried this with Ubuntu. These problems could thus arise from my ignorance to correctly setup a bootable raid0 array. However, through trial and error im working my way through all the raid0 possibilities...

Further hints or pointers *greatly* appreciated, kb

---

### Post by YesWeCan on 2011-02-10
Is this what you have in your PC?
[http://www.jjwei.com/shop/item.asp?itemid=65](http://www.jjwei.com/shop/item.asp?itemid=65)

This is a nice bit of real hardware raid.
The idea is that the card does all the work and presents a single drive to the OS. Therefore, the OS does not do any raid at all.

So, in this case, you need to enable the card in its bios and set it up for whateve raid type you want. Then when you boot Ubuntu off the usb it should only see one hard disk instead of two.
I am not sure why you cannot boot off the usb when the raid card is enabled. Can you try a CD instead?
You dont need Ubuntu server for any of this. Use desktop live.

---

### Post by YesWeCan on 2011-02-10
ok, so I just read your first post again and realised my responses are those of a person who failed to read your first post! Its been a long day.

In brief, you can boot Ubuntu live off USB or CD when the Hardware RAID is set to 1 but not when it is set to 0.

You can install Ubuntu to the RAID 0 but it won't boot.

Can you install Ubuntu to RAID 1 and have it boot; did you try this?

---

### Post by kbrand on 2011-08-05
YesWeCan, sorry to drop you into the void for 5 months*, finally time to mark this thread 'solved'. A few notes for posterity's sake.

"Is this what you have in your PC?
http://www.jjwei.com/shop/item.asp?itemid=65"
Yes.

I succeeded getting 64bit Ubuntu desktop running with the following actions:

1. Initializing each of the SCSI's in the array using the Perc utilities after the bios finished loading.

2. Booting from the 'Alternate CD' version of 64bit Ubuntu.

3. Creating a logical volume on the array by following the Ubuntu alt-cd install menus. And yes, it was 'seen' by ubuntu as a single drive.

I have little idea which of these (or all of these) steps were required to get ubuntu running on this machine, but as it was repeated at least a second time (due to an unrelated issue), i can verify it's success. I suspect 1. was needed to wipe out the remnants of the XP boot loader properly which was causing issues during my first attempts. I wont speculate further, but at no point during many attempts was I able to successfully install Ubuntu from the standard USB or CD .iso's (including after performing 1.). So either my hardware configuration, &/or my lack of knowledge must be responsible. But the 'alternate CD' couldn't have been easier. Finally, i have no problem booting and running live from the standard USB .iso now, but to access the scsi array, i need to install the lvm2 package during the 'live session'.

Love 11.04, but need to start a new thread about non-functioning Ubuntu one...

*to start and finish a PhD thesis which was required to live in the windows world throughout its creation

---

