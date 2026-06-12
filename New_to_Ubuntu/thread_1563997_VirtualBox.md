---
title: "VirtualBox"
date: 2010-08-30
forum: New to Ubuntu
---

### Post by justin43384 on 2010-08-30
When I start my Windows XP VBox, I would get the error: "FATAL: Can not read from the boot medium!  System halted.
You guys can see the screen shots for more info...

Thanks in advance!!:P

---

### Post by Bachstelze on 2010-08-30
You have to insert your Windows CD and boot from it to install Windows. VirtualBox does not come with Windows preinstalled. ;)

---

### Post by soldier1st on 2010-08-30
Bachstelze: he has windows installed but according to his screenshots there are 2 issues. the first is 528mb of ram? it should be 512mb not 528mb and the system is only booting the cd and not the hard drive so you need to set it to boot from Hard drive then it will work.

---

### Post by ronnielsen1 on 2010-08-30
It looks like he did install it. One thing you have to change is the boot order. Once you install Windows in Virtualbox, you have to change the boot order back to booting from the virtual hard drive instead of the cd.

Say hello to Fremont for me! I lived on Charleston for about 6 years. My dad and sister still live there

---

### Post by ronnielsen1 on 2010-08-30
If possible add more memory to the virtual machine. My XP vm wasn't happy on my P4 until I gave it a Gig of memory but then again, you might have a newer computer than mine

---

### Post by soldier1st on 2010-08-30
> **ronnielsen1 said:**
> If possible add more memory to the virtual machine. My XP vm wasn't happy on my P4 until I gave it a Gig of memory but then again, you might have a newer computer than mine
when he installs windows or any os he needs to set it to boot from the cd/dvd/bootable image first then have the hard drive as the 2nd boot item so windows or any os will install. if he sets it up to boot from the cd only then whereis windows supposed to go or any os as it won't know where to go. some of the older systems would not boot the cd if the hard drive was selected as the 2nd boot item.

---

### Post by ronnielsen1 on 2010-08-30
> Once you install Windows in Virtualbox, you have to change the boot  order back to booting from the virtual hard drive instead of the cd.


This one? 

> when he installs windows or any os he needs to set it to boot from the  cd/dvd/bootable image first then have the hard drive as the 2nd boot  item so windows or any os will install. if he sets it up to boot from  the cd only then whereis windows supposed to go or any os as it won't  know where to go. some of the older systems would not boot the cd if the  hard drive was selected as the 2nd boot item. 	

If you're talking an actual computer. We're talking virtualbox. You do need to create a virtual hard drive but I don't think it's actually necessary to list the hard drive as a 2nd boot option before installing. VirtualBox will pick up on the hard drive. The only thing I was saying is to change the boot order back to the hard drive after installation.

---

### Post by justin43384 on 2010-08-31
Ok i set the Ram to 512 but haven't installed Windows in VBox yet.

I set the boot order to:
1.CD/DVD-ROM
2.Hard disk

I have the Windows install disk inserted

Even after the changes above, I still get the Error:
"FATAL: No bootable medium found! System halted."

See the screenshots for more info...

---

### Post by QIII on 2010-08-31
Try making your IDE Primary Master your CD/DVD drive and your SATA Controller your .vdi

---

### Post by CharlesA on 2010-08-31
You need to mount the ISO or "host drive" inside virtualbox.

Guest > Settings > Storage > CD/DVD > Host Drive

> **QIII said:**
> Try making your IDE Primary Master your CD/DVD drive and your SATA Controller your .vdi

Primary/secondary doesn't matter. Also, don't use SATA for Win XP, as it will BSOD after trying to detect the drives.

---

### Post by themusicalduck on 2010-08-31
According to your screenshot you don't have any kind of Windows CD in.

Are you installing from an ISO or from an actual CD?

If it is an actual CD, you can go to Settings and Storage then select the CD drive and tell it to use the host drive. Otherwise, select an ISO from your hard drive.

---

### Post by QIII on 2010-08-31
Ah.  OK.  Never mind then.  I guess my XP virtual machine isn't working, then.

Sorry.

I sure hope my 10 other virtual machines are working ...

;)

---

### Post by CharlesA on 2010-08-31
> **QIII said:**
> Ah.  OK.  Never mind then.  I guess my XP virtual machine isn't working, then.

Sorry.

I sure hope my 10 other virtual machines are working ...

;)
Hrm, how the VM for XP set up in Virtual Box? IDE or SATA controller? XP/Server 2K3 VMs default to IDE, Vista/7/Server 2K8 default to SATA.

---

### Post by QIII on 2010-08-31
Well, CharlesA, I'm going to have to eat crow.

I got off my Maverick machine and looked at my Lucid machine (where I use VirtualBox) and, indeed, the XP virtual disk is on an IDE controller.  Everything else is SATA.

Bah!  Now my record of never being wrong is ruined.  Curse you!

---

### Post by CharlesA on 2010-08-31
Happens to everyone. At least VBox is smart enought to know what will work and what won't. ;)

---

### Post by justin43384 on 2010-08-31
Ok i set the Ram to 512 but haven't installed Windows in VBox yet.

I set the boot order to:
1.CD/DVD-ROM
2.Hard disk

I have the Windows install disk inserted

And set the VBox guest additions to the IDE secondary master.

Even after the changes above, I get the Error:
"FATAL: No bootable medium found! System halted."

See the screenshots for more info...

---

### Post by charlier653 on 2010-08-31
When you first turn on that instance of VB, you see a short flash of Press F12 to set boot....

I was having that same problem today until I noticed that, and Pouf! it worked!

---

### Post by CharlesA on 2010-08-31
You still don't have the Windows disk "mounted" in virtualbox. You have the "VBoxGuestAdditions.iso" mounted.

---

### Post by Vaphell on 2010-09-01
yup, windows disk first to install xp, then vboxguestadditions so your fresh installation can get fullscreen and stuff. If VB doesn't show it in properties, virtual machine won't see it.

---

### Post by themusicalduck on 2010-09-01
Click on Settings for the virtual machine (the yellow cog). Then go to Storage, and click on the CD icon that'll probably say VBoxGuestAdditions.iso after it. Then click on the CD/DVD Device dropdown menu and select Host Drive.

Then the virtual machine will have access to your XP disc.

---

### Post by justin43384 on 2010-09-02
THANKS GUYS IT WORKS!!!!!!!!!:KS:popcorn:):P:p;):D:)

---

### Post by Sky Aisling on 2011-01-03
@QIII

You wrote:

> **Re: VirtualBox**             
                                                                Try making your IDE Primary Master your CD/DVD drive and your SATA Controller your .vdi
Thank you.

I've had a similar situation. Your solution worked to solved the issue.
Thanks to your tip, I've easily installed WIN7 as 'guest' OS into a virtual machine created in VirtualBox  on Lucid Lynx 10.04 running on a ZaReason Strata 3660 laptop.  

I too kept getting the black backside of the Penquin.  :)

---

