---
title: "Major Bug with Ubuntu 9.10 on Raid Controller"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by Lvcoyote on 2009-11-03
I've been messing with this for a few days now and it appears there is no fix.  Here is what happening.....

I have a Motherboard with the Intel ICH10R controller set to Raid.  I have two drives in a Raid0 array and windows7 is loaded to that array, working fine.  I disconnected the HDD's in the raid array and plugged in a 160gb WD drive to install Ubuntu to, it is the only drive attached to the system at this point, and the controller is still set to Raid.  Installation went off without a hitch and everything looked good.

I re attached the two HDD's that make my Raid0 array, now I have Win7 on the Raid0 array and Ubuntu on the 160gb WD drive, by hitting the "ESC" key during boot I can choose what drive to boot from, all that works just fine!

Now here is the problem, when I choose to boot from the HDD that houses Ubuntu 9.10 it boots to the desktop just fine and I can use it without issue.  When I reboot the system I get a drive failed error on one of the HDD's in the Raid0 array.  So thinking maybe one of those drives is bad, I ran the "Full Media" test using Western Digital's utility, both drives came up clean, no errors.  Now, If I remove the HDD that houses Ubuntu I no longer get the "drive Failed" message and the system works fine.  Some how when running Ubuntu its doing something to the Windows7 Raid array.  I have tried moving the Ubuntu disk to the onboard JMB controller, and again it boots to the desktop, but when I restart the "failed Drive" error on my Raid array pops up again.  So at this point I am unable to enjoy the new version of Ubuntu.... I have run this configuration of HDD's for the last several versions of Ubuntu without this issue, it just popped up with 9.10.

Anyway, I guess I'll have to wait for the next version, 10.04??  Just thought I'd let you all know about this, I'll submit a bug report but I don't expect anything to come of that.

---

### Post by kansasnoob on 2009-11-03
I know nothing about RAID, so I'm just thinking out loud here, and perhaps incoherently at that.

I remembered reading this in the release notes:

> Automatic boot from a degraded RAID array not configured upon installation

The installer option to support "boot from a degraded array" does not properly configure the installed system. To correct this after installation, run dpkg-reconfigure mdadm after installation and select the option again.   

And it references this bug report:

[https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/462258](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/462258)

That however sounds to me like an unrelated issue but thought I'd mention it.

I also wonder if you'd been able to run any prior Ubuntu or Linux OS in the same arrangement but using legacy grub. I made some fairly specific notes regarding how to revert to legacy grub:

[http://ubuntuforums.org/showpost.php?p=8071880&postcount=18](http://ubuntuforums.org/showpost.php?p=8071880&postcount=18)

However, I'm not recommending anything. As I said, I'm just thinking out loud. I should also note that I'll be around very little the next few days.

---

### Post by Lvcoyote on 2009-11-03
Hi kansasnoob and thanks for taking the time to respond.  I looked over the links you provided and it does not appear that they pertain to my situation but rather to a Ubuntu install to a raid array.  As stated above, the Ubuntu install in my case is not on a raid array per-sey but on a single drive attached to a controller that is set to raid, but I also tried moving the hard drive to a different controller on the motherboard and the issue remained.

For some reason Ubuntu 9.10 is doing something to upset the Raid0 array once its booted.  I have run this exact configuration on Ubuntu 8.04, 8.10, and 9.04 with out this problem, this is the first distro this issue has happened on.

Anyway, I'll keep looking around, thanks again!

---

### Post by LowSky on 2009-11-03
Check the SATA ports your using. Most likely your BIOS setting are wrong and corrupting the Ubuntu config. But it could be something else.

Are the drives you using made for RAID. WD  actually tells customers that certain drives should not be put into RAID configs because of their power saving technique.

Your also mixing type of drives on one chipset which might be the issue too. I know little of Intel's new motherboards but this could be a problem on their end.

Why not set up the raid and have Ubuntu and windows installed in the same drives? see if that causes issues.

---

### Post by Lvcoyote on 2009-11-03
> **LowSky said:**
> Check the SATA ports your using. Most likely your BIOS setting are wrong and corrupting the Ubuntu config. But it could be something else.

Are the drives you using made for RAID. WD  actually tells customers that certain drives should not be put into RAID configs because of their power saving technique.

Your also mixing type of drives on one chipset which might be the issue too. I know little of Intel's new motherboards but this could be a problem on their end.

Why not set up the raid and have Ubuntu and windows installed in the same drives? see if that causes issues.

Trust me, the BIOS settings are perfect, and the same ones used on 9.04, and they worked fine.  This is not a new build and has been running flawless for months with these exact settings and 9.04.  I'm using two raptor 150gb drives for the raid0 that houses Win7.  Like I said, If I remove the HDD that houses Ubuntu the issue goes away.

---

### Post by jonah1980 on 2009-11-04
hi guys i have the same issue with the raid array. i have two samsung 1tb drives in the computer with bios set to raid striped, i've ran the raid bios utility to make them a bootable drive and cleared the MBR etc. then I tried to install kubuntu from the new 9.10 live cd.

The first few attempts it said it was unable to install grub to /target/

then a couple more goes and i didn't get any errors, so i restarted after successful install and it starts to boot and then drops to initramfs prompt with some kind of error saying that the drive path doesn't exist and there's no /dev/ or something like that.

Can anyone please help me install this!? My computer is currently useless with all my files backed up over two external hard disks...

---

### Post by Dev_Singh on 2009-11-04
I'm also having issues with RAID. My PC has 2 x 1TB drives.

I was running 9.04 without issues but after upgrading to 9.10 my PC refused to boot up. I then did a fresh install of 9.10 and saw a message indicating that it couldn't install grub to target. Subsequent installation attempts saw messages related to drive failure, invalid path, I/O errors, unable to read....

I then installed Windows 7 (twice) just to test and it installed without a single error message. After that I tried installing 9.10 again with similar errors. I'm without my PC at the moment :( and hope there will be a solution soon.

---

### Post by Dev_Singh on 2009-11-04
> **kansasnoob said:**
> 

[https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/462258](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/462258)



On one of my several attempts I did see the message shown in the link above.

---

### Post by ukripper on 2009-11-04
[https://wiki.ubuntu.com/KarmicKoala/ReleaseNotes#Automatic%20boot%20from%20a%20degraded%20RAID%20array%20not%20configured%20upon%20installation](https://wiki.ubuntu.com/KarmicKoala/ReleaseNotes#Automatic%20boot%20from%20a%20degraded%20RAID%20array%20not%20configured%20upon%20installation)

This may fix the issue:

The installer option to support "boot from a degraded array" does not properly configure the installed system. To correct this after installation, run **dpkg-reconfigure mdadm** after installation and select the option again.

---

### Post by jonah1980 on 2009-11-05
I can't run this dpkg configure command to try and fix mdadm as i'm stuck at initframs...

---

### Post by Dev_Singh on 2009-11-05
Neither can I as the installation doesn't complete. It fails at different points due to errors mentioned above. Only once in perhaps a dozen attempts could I have done it but missed it because I hadn't seen the above post :(.

---

### Post by jonah1980 on 2009-11-08
i tried booting the live cd and updating by sudo aptitude update and upgrade to see if a newer version of ubiquity than that on the cd would help but i'm still stuck at initframs... i hope someone can fix this soon as i'm still without a pc.

---

### Post by ukripper on 2009-11-09
> **jonah1980 said:**
> i hope someone can fix this soon as i'm still without a pc.

Why not use 9.04 in the meantime? Why make yourself suffer till the fix is pushed through?

---

### Post by jonah1980 on 2009-11-09
> **ukripper said:**
> Why not use 9.04 in the meantime? Why make yourself suffer till the fix is pushed through?

hi, i tried 9.04 on new raid setup but the ubiquity installer doesn't even detect raid at all. it asks if i'd like to install on sda or sdb and shows them as seperate drives. but on 9.10 it does detect raid as one drive and installs it just doesn't then boot or set up grub properly etc and i get stuck at initramfs

---

### Post by ukripper on 2009-11-09
> **jonah1980 said:**
> hi, i tried 9.04 on new raid setup but the ubiquity installer doesn't even detect raid at all. it asks if i'd like to install on sda or sdb and shows them as seperate drives. but on 9.10 it does detect raid as one drive and installs it just doesn't then boot or set up grub properly etc and i get stuck at initramfs

What raid controller you are using?

---

### Post by jonah1980 on 2009-11-09
> **ukripper said:**
> What raid controller you are using?

hi i'm not too sure tbh. i have the m3n8200 motherboard and i set to raid in the bios. then when it boots an nvidia raid controller thing comes up which gives the option to start a setup utility by pressing f10. i've done that and set the raid to striped and made it bootable and cleared the mbr etc.

it's detected on installation as nvidia mapper something or other...

---

### Post by jonah1980 on 2009-11-14
ok as i've got a day off work i can finally post the exact error initramfs gives me, i've been blindly posting without being at my computer so hard to remember the errors hehe!

ok so this is the error i get:

> ALERT! /dev/mapper/nvidia_dcfadeef2 does not exist. Dropping to a shell!

---

### Post by jonah1980 on 2009-11-17
apparantly the bug mentioned earlier in this thread doesn't apply to my problem. after i posted there someone says my issue is a seperate one so i've made a new bug here: [https://bugs.launchpad.net/ubuntu/+bug/484185]("https://bugs.launchpad.net/ubuntu/+bug/484185")

---

