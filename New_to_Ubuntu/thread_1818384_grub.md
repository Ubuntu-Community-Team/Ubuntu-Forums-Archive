---
title: "grub"
date: 2011-08-04
forum: New to Ubuntu
---

### Post by shirl on 2011-08-04
Hi
 
I have a 4/5 year old Toshiba P3500 tablet PC which had XP tablet OS, it is my granddaughters. She has not been able to use it for some time now as it kept rebooting when Windows was loading. 
 
I have tried all sorts and installed Ubuntu, this got it going but I could not see the C drive, so after reading a thread on a forum I installed GPorted Live as I thought I could reformat the drive using this, but somehow I have deleted Windows and Ubuntu and now I am left with a laptop which sticks at the startup screen.
 
Message says
PXE-E61: Media test failure, check cable
PXE-M0F: Exiting Intel Boot Agent
error: no such partition
grub rescue>
 
She cannot find original Windows tablet CD but I have a Windows XP, Vista & Win 7 CD, also have the Ubuntu CD but I tried booting from all of these and still get the same message as above have also downloaded an ISO of kill disk but this will not load and again get the same message as above.
 
I have set the BIOS to boot from the CD first but none of the above CDs will boot, so I am at a loss as what to try next - think it is a case of a bit of knowledge is a dangerous thing. 
 
Any help would be appreciated, I am not a technician but know a bit about DOS as I have been using PCs for years but new to Ubuntu (it recently saved my life when my PC harddrive failed).  I do not have a clue what Grub is or does :-(
 
Thanks
Shirl

---

### Post by cariboo on 2011-08-04
From the message you are getting, the system is trying to boot from the network. There are several things you should check in the BIOS.

[LIST]
[*]First make sure the hard drive and CD-ROm driver are detected
[*]Second make sure the boot order is set properly
[*]Third, make sure that boot from CD-Rom is set first.
[/LIST]

---

### Post by shirl on 2011-08-05
I did have the CD set to boot first, but strangely when I turned on the laptop this morning and put in the Windows CD it installed fine - so happy bunny now.
 
Not sure how you mark a message solved so have tick a couple of icons.:KS
 
Thanks
Shirley
 
> **cariboo907 said:**
> From the message you are getting, the system is trying to boot from the network. There are several things you should check in the BIOS.

[LIST]
[*]First make sure the hard drive and CD-ROm driver are detected
[*]Second make sure the boot order is set properly
[*]Third, make sure that boot from CD-Rom is set first.
[/LIST]

---

### Post by Wim Sturkenboom on 2011-08-05
> **shirl said:**
> Not sure how you mark a message solved so have tick a couple of icons.:KS
Use the *thread tools* link just above the first post of the thread.

---

