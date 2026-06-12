---
title: "Boot to Ubuntu from external USB (eSATA) drive?"
date: 2010-08-30
forum: New to Ubuntu
---

### Post by const451 on 2010-08-30
I have a laptop and I am thinking to keep Win 7 on primary internal HDD and install Ubuntu  on external USB 3.0 ( or eSATA ) HDD so when I want to work with Ubuntu I  would plug the external HDD and boot from it. My laptop can boot from  USB.

What do you guys say, is it possible? Will Ubuntu be running too slow off of the external HD?

I do not want to have dual-boot, I have it right now and Win 7 sometimes  fails to boot in this config. I am afraid Win 7 will fail on day and  I'll have to reinstall it with all my school applications, it will be  bad if it happens in the middle of the semester.

THX

---

### Post by C.S.Cameron on 2010-08-30
If possible I would suggest removing your internal drive before installing to your external drive.
If this is not possible use the advanced tab after partitioning and select the external drive for location of grub.

---

### Post by kwacka on 2010-08-30
I would suggest the first step would be to find out why Windows fails to start - there may be no problem regarding Ubuntu (seems to be a fairly common problem with & & Vista/XP dual booting).

Use fixmbr (or whatever MS's latest incarnation is) to 'repair' the MBR and see if Windows continues to operate intermittently.

---

### Post by const451 on 2010-08-30
> **C.S.Cameron said:**
> If possible I would suggest removing your internal drive before installing to your external drive.
If this is not possible use the advanced tab after partitioning and select the external drive for location of grub.

That's what I was thinking too!! - disconnect my internal hard drive before installing Ubuntu on external hard drive, this way I will avoid Ubuntu configuring my mbr for dual-boot.

From your post I am assuming my idea is not outright crazy :smile:

---

### Post by const451 on 2010-08-30
> **kwacka said:**
> I would suggest the first step would be to find out why Windows fails to start - there may be no problem regarding Ubuntu (seems to be a fairly common problem with & & Vista/XP dual booting).

Use fixmbr (or whatever MS's latest incarnation is) to 'repair' the MBR and see if Windows continues to operate intermittently.

I really do not have time (graduate school is very demanding) and more importantly I really do not want to investigate what's (again) wrong with Windows. I know Vista and Win 7 are not very good neighbors to other OSs. I did run bootrec /FixMbr but did not help.

---

### Post by kwacka on 2010-08-30
> **const451 said:**
> I really do not have time (graduate school is very demanding) and more importantly I really do not want to investigate what's (again) wrong with Windows. I know Vista and Win 7 are not very good neighbors to other OSs. I did run bootrec /FixMbr but did not help.

Sort your priorities out.

If your school work requires Windows 7, & Windows 7 fails to boot you won't have any choice about spending time on putting it right; whether or not Ubuntu is or isn't installed (you can always use the Ubuntu live CD to get your coursework from your harddrive if Windows let you down).

For installing Ubuntu to an external device see: [http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html](http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html) although the section on GRUB will need updating.

---

### Post by C.S.Cameron on 2010-08-31
> **const451 said:**
> That's what I was thinking too!! - disconnect my internal hard drive before installing Ubuntu on external hard drive, this way I will avoid Ubuntu configuring my mbr for dual-boot.

From your post I am assuming my idea is not outright crazy :smile:

Lots of people run Ubuntu from external USB drives for the same reason you want to.
USB2 is slower than SATA though.

---

### Post by const451 on 2010-08-31
> **kwacka said:**
> Sort your priorities out.

If your school work requires Windows 7, & Windows 7 fails to boot you won't have any choice about spending time on putting it right; whether or not Ubuntu is or isn't installed (you can always use the Ubuntu live CD to get your coursework from your harddrive if Windows let you down).

For installing Ubuntu to an external device see: [http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html](http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html) although the section on GRUB will need updating.

It is a nice guide - thank you!! Right what I needed.

School is my priority that's why I want to wipe the drive and install Win 7 solely on internal drive so I won't have any surprises down the road. Then install Ubuntu on external usb drive.

Thanks again for your help!

---

### Post by Paddy Landau on 2010-08-31
In addition to the previous posts, do you know that you can back up your entire drive (or just a single partition on the drive)? I do this. Once Windows is set up the way you want it, back up the entire drive.

Then, if Windows does its "thing" on you, or if a virus or other malware completely messes it up, you can restore the entire drive, and obviously restore your data from your backups (you do make daily backups, right?).

I use [CloneZilla]("http://www.clonezilla.org/") for this. It's the best free clone manager that I've found; not entirely user-friendly, but easy once you get your head around it. You need an external hard drive to back up onto. CloneZilla saves only the used portions of the drive, and compresses it on the fly, so it doesn't take too much space. It saves into a subdirectory on the hard drive.

I've used CloneZilla to back up and restore both Windows and Ubuntu several times (mostly Windows, I have to say!). It's saved me tons of time, because it takes so long to reinstall Windows and all the programs that I use. I back up all partitions once a month, so I'm never more than a month out of date.

(Actually, recently my last remaining Windows computer died, so I don't use Windows at all now!)

---

### Post by SimonJones on 2010-09-29
I have bought a new laptop with Windows 7 on, last night I plugged an eSata drive and installed Xubuntu 10.04. Rebooted after the updates and everything worked perfectly. Shut down, unplugged the eSata cable and windows blue screens! :-(

After much fiddling with repairs I decided it's only new and installed Win7 again. 

Anyone know if this is common, or did I do something to make it happen, or, was it just random chance?

TIA.

---

### Post by C.S.Cameron on 2010-09-29
> **SimonJones said:**
> I have bought a new laptop with Windows 7 on, last night I plugged an eSata drive and installed Xubuntu 10.04. Rebooted after the updates and everything worked perfectly. Shut down, unplugged the eSata cable and windows blue screens! :-(

After much fiddling with repairs I decided it's only new and installed Win7 again. 

Anyone know if this is common, or did I do something to make it happen, or, was it just random chance?

TIA.

It is safest to unplug the internal drive when installing to external drive and it makes a neater grub.cfg file also.
If you can't unplug the internal drive, when you finishing the partitioning part of the install select the Advanced tab and make sure grub is installed to the external drive.

---

### Post by SimonJones on 2010-09-30
I put grub on the external drive (sdb here) and it did boot Linux happily.

It was only after I had unplugged the drive, a I can't easily remove the internal drive, so I though eSata would be the answer. 

Windows went through to Starting Windows and then BSOD, before rebooting. Of course the BSOD was too quick to read. :-(

It can't be a grub problem though.

---

### Post by C.S.Cameron on 2010-09-30
There are instructions on the web for fixing Win 7 MBRs.
You will need the Win 7 install disk.

---

### Post by SimonJones on 2010-09-30
Sorry, I am obviously not making myself clear. 

Windows did boot, so no problem with grub, mbr or partitions.

Something in the Ubuntu installation (or not) upset the Windows installation to the point that it BSOD'd just before loading the desktop.

---

