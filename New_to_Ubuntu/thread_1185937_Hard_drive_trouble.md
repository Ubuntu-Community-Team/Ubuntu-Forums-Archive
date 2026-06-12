---
title: "Hard drive trouble"
date: 2009-06-12
forum: New to Ubuntu
---

### Post by rls53 on 2009-06-12
**:(Figure this one out please**. Had installed Ubuntu on virgin Hard drive(new seagate). Needed to use HD in another system. I was doing DOD wipe to run new XP OS. Would not wipe so I put HD back in computer and it is telling me HD is Dell password protected. Never entered any passwords for this computer neither admin or bios. HD is now locked with no way in.
When I installed Ubuntu I used User as owner and 12345678 as password neither of which will unlock HD. Help!!! now HD is useless.What went wrong??
Thanks
Ray

---

### Post by nandemonai on 2009-06-13
> **rls53 said:**
> **:(Figure this one out please**. Had installed Ubuntu on virgin Hard drive(new seagate). Needed to use HD in another system. I was doing DOD wipe to run new XP OS. Would not wipe so I put HD back in computer and it is telling me HD is Dell password protected. Never entered any passwords for this computer neither admin or bios. HD is now locked with no way in.
When I installed Ubuntu I used User as owner and 12345678 as password neither of which will unlock HD. Help!!! now HD is useless.What went wrong??
Thanks
Ray

Umm.. as far as I know there is no way to lock a hard disk from being formatted or repartitioned. Why not just use the Live CD and partition editor to nuke the disk partitions?

It sounds to me like maybe a vendor BIOS password or perhaps a recovery partition though if this disk was new and you installed Ubuntu to it then there is no way it would have a recovery partition on it.

Colour me confused.

---

### Post by Ocxic on 2009-06-13
Unfortuatly it is possible to place a password on a hard drive directly, it's a security feature for some models contained within the drives firmware.

Unfortunately I'm unsure if it's possible to remove the password without knowing it. you may want to contact the manufacturer to see if there is any way to bypass this feature.
"hdparm" has options to lock/unlock the drive providing that you have the password that was used, since you say that a password was never entered I would trry using a blank password if possible.
it's also possible that the hard drive itself has become bad or has corrupt firmware. 
I know there were problemes with the 1TB & 1.5TB models of seagate hard drives firmware becomming corrupt making the drive un-useable.

"hdparm --security-unlock PWD" or "hdparm --security-disable PWD" replace PWD with the password for the drive.

---

### Post by nandemonai on 2009-06-13
> **Ocxic said:**
> Unfortuatly it is possible to place a password on a hard drive directly, it's a security feature for some models contained within the drives firmware.

Unfortunately I'm unsure if it's possible to remove the password without knowing it. you may want to contact the manufacturer to see if there is any way to bypass this feature.
"hdparm" has options to lock/unlock the drive providing that you have the password that was used, since you say that a password was never entered I would trry using a blank password if possible.
it's also possible that the hard drive itself has become bad or has corrupt firmware. 
I know there were problemes with the 1TB & 1.5TB models of seagate hard drives firmware becomming corrupt making the drive un-useable.

"hdparm --security-unlock PWD" or "hdparm --security-disable PWD" replace PWD with the password for the drive.

Oh wow serious foot in mouth. I had no idea they were doing that now. Seems like a bad idea to me. I've not come across a drive with firmware security on it (maybe living in AU has something to do with it :P). Me thinks I'll be steering clear of them in the future.

---

### Post by Ocxic on 2009-06-13
The firmware security on an HD must be enabled manually, and I think it's great. If anyone gets ahold of the drive, even in a new system the thief/police would not be able to read the drive without some serious cleanroom work.

---

### Post by nandemonai on 2009-06-13
> **Ocxic said:**
> The firmware security on an HD must be enabled manually, and I think it's great. If anyone gets ahold of the drive, even in a new system the thief/police would not be able to read the drive without some serious cleanroom work.

Mmm, I can certainly see the benefits but I don't particularly like the idea of relying on firmware without an easy way of resetting it.

Anyway, to the OP, as said previously your best bet would likely be to contact the manufacturer and see if they can help you with it.

---

### Post by rls53 on 2009-06-14
Thanks for the info. The HD is a Momentus 60gig. I tried last night to run the Live CD and check the partitions,there is a partition dev/sda  at the beginning of the HD that I can not seem to get rid of. My lack of experiance with commands is probably the problem. I tryed the most common commands and was unable to do anything meaningful to delete this partition. Tried your hdprams and several others but just cannot access this partition any help would be greatly appreciated .
 I tried to re-install Ubuntu and the partition is there( dev/sda )giving me the option of setting up new partition on /dev/sda1 with 60011mb of free space. I believe the password is in the first partition but just cant get to it.
thanks for your help

---

### Post by Cheesemill on 2009-06-14
You might want to give DBAN a try (this won't work if it is a firmware issue though).
[http://www.dban.org/](http://www.dban.org/)

---

### Post by H2SO_four on 2009-06-14
> **Cheesemill said:**
> You might want to give DBAN a try (this won't work if it is a firmware issue though).
[http://www.dban.org/](http://www.dban.org/)

Great site. Sorry I can't help solve OP's issue, but DBAN will come in handy for me :)

---

### Post by lkraemer on 2009-06-15
Most Drive manufacturers have utilities to restore the drive to
original condition.  Why not look on the manufacturers site for this software. You may have to register to get access to their software.

lkraemer

---

