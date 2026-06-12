---
title: "Dual boot query.."
date: 2009-08-26
forum: New to Ubuntu
---

### Post by T.C. on 2009-08-26
Ubuntu absolute beginner ...  Don't mind being told to RTFM if you also tell me which manual.

Dual boot Win XP Pro/Ubuntu 9.04 on separate physical hard drives on the same IDE, XP on the "Master" drive, Ubuntu on the "Slave".

All well except that if the Slave drive is removed the boot sequence fails with Grub error 21

> 
Error 21 : Selected disk does not exist
This error is returned if the device part of a device - or full file name refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system. If the Master drive is removed and the Slave changed to Master, Ubuntu boots without problem.

Is there a way of installing the Grub loader on the XP partition (as well as on the Ubuntu partition) so that XP can be booted if the Slave drive fails without having to reconstruct the MBR or whatever?

Thanks.

---

### Post by brunogirin on 2009-08-26
From your description, I assume that you have GRUB installed in the MBR of the master drive but because Ubuntu is installed on the slave drive, it needs to be able to read from it in order to present you with the Ubuntu boot options.

One solution would be to install GRUB in the MBR of both the master drive and the slave drive, then have the master menu changed to chainload GRUB on the slave drive. So you would have something similar to this:

(hd0)
- Windows -> (hd0,0)
- Ubuntu -> chainload (hd1)

(hd1)
all the Ubuntu options

The downside to this is that you would need to go through one extra step when booting Ubuntu because you'd have two levels of menu but that looks to me like the only way to delay access to the slave drive until you know you're going to use it.

---

### Post by nothingspecial on 2009-08-26
[[COLOR="Magenta"]Here[/COLOR]]("http://www.supergrubdisk.org/w/index.php5?title=Boot_Problems") is the manual :)

---

### Post by Bartender on 2009-08-26
Man, it seems like we're getting a lot of GRUB questions lately.

Maybe some of the real basic points need to be taped to the box.

When you do a standard, default, run-of-the-mill, boilerplate dual boot, you allow GRUB to install a tiny bit of code to the Windows MBR.

Once you've done that, **the two operating systems need each other**.  If you remove Ubuntu, then Windows won't start and you'll see a GRUB error.  If you remove Windows, then the computer will quit at POST, probly with a "no bootable device" error or something similar.

What if you dual-boot with two HDD's, Windows on one and Linux on the other?  Same thing.  As long as GRUB is allowed to tweak the Windows MBR, the two OS'es need each other.  I almost said they're "joined at the hip", but that sounded a little weird.

---

### Post by LewRockwell on 2009-08-26
> **Bartender said:**
> Man, it seems like we're getting a lot of GRUB questions lately.

Maybe some of the real basic points need to be taped to the box.

When you do a standard, default, run-of-the-mill, boilerplate dual boot, you allow GRUB to install a tiny bit of code to the Windows MBR.

Once you've done that, **the two operating systems need each other**.  If you remove Ubuntu, then Windows won't start and you'll see a GRUB error.  If you remove Windows, then the computer will quit at POST, probly with a "no bootable device" error or something similar.

What if you dual-boot with two HDD's, Windows on one and Linux on the other?  Same thing.  As long as GRUB is allowed to tweak the Windows MBR, the two OS'es need each other.  I almost said they're "joined at the hip", but that sounded a little weird.

only because those search engines are so very scary...

{{sigh}}

.

---

### Post by Bartender on 2009-08-26
Perhaps I was unfair to the OP.  He said that Ubuntu boots up when it's the only drive, so my harangue wasn't relevant.

I don't understand what's going on, but it doesn't sound typical.  If Ubuntu boots up when jumpered as the Master, then all of GRUB is on that drive.

T.C., I'd suggest resetting.  Remove the Ubuntu drive, and use SuperGRUB Disc or whatever to fix the Windows MBR.  That *should* get Windows working again.  Then hook up the Ubuntu drive as Master on the second IDE bus.  Pop in the LiveCD, reboot, tell Ubuntu to install to the entire second drive (probly hdb) and let it install GRUB Stage 1 to the Windows drive.

---

### Post by egalvan on 2009-08-26
> **Bartender said:**
> 
Maybe some of the real basic points need to be taped to the box.

When you do a standard, default, run-of-the-mill, boilerplate dual boot, you allow GRUB to install a tiny bit of code to the Windows MBR.

Once you've done that, **the two operating systems need each other**.  If you remove Ubuntu, then Windows won't start and you'll see a GRUB error.  If you remove Windows, then the computer will quit at POST, probably with a "no bootable device" error or something similar.

What if you dual-boot with two HDD's, Windows on one and Linux on the other?  Same thing. ** As long as GRUB is allowed to tweak the Windows MBR, the two OS'es need each other.**  I almost said they're "joined at the hip", but that sounded a little weird.


Sorry, but this is hogwash... :)

OK, here is the REAL SCOOP.

[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_](http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_)

Yes, this works.
Yes, I use it.

hermanzone is loaded with excellent information.
An excellent "manual"


Another excellent "manual"
[http://ubuntuforums.org/showthread.php?t=1052065](http://ubuntuforums.org/showthread.php?t=1052065)

---

### Post by T.C. on 2009-08-26
Thank you all for the very informative responses, lots more printing, reading and experimenting to do:roll:

---

### Post by Bartender on 2009-08-26
egalvan -
I bow to Herman.  He seems like a really nice guy, and he's put a lot of time and effort into helping people out.  Herman helped me with md5sum questions back in the Breezy Badger era.

The link you provided, wow.  I bookmarked it.  A lot of information there.  Can you please point out the part that discredits what I said?  Remember, my statement was in the context of a standard, default, dual-boot.  No separate /boot partition or any other geeky tweaks.  

I hate to think I've given bad advice on these forums, but it's probly happened.  If I'm wrong I need to know.  If you're saying I'm full of it because a person could set up a separate GRUB or boot partition, well, I'm skeptical that the average newcomer could do it even though Herman does an excellent job of describing the process.

Maybe we should try replying to all GRUB questions with nothing more than a link to Herman's page, then wait to see how many folks come back going "Huh"?

EDIT: I'll slap together a test box and see if I can follow Herman's directions.

---

### Post by Mark Phelps on 2009-08-27
In my own system, I have multiple drives, also.  I can boot from either the MS Windows drive or the Ubuntu drive, even if the other drive is disconnected. But I can do that because I installed Ubuntu with the MS Windows drive disconnected.  When the Ubuntu drive is connected, I boot from it and use the GRUB menu to select the Windows drive.

I suspect this might be the same situation.

---

### Post by T.C. on 2009-09-03
Thank you Mark.  I don't understand yet how you can select the Windows OS in the Grub menu if the Windows system disk was not connected when the Grub installer went looking for other operating systems.  How does the Grub loader installer know that another OS will be present?

Anyways, dilemma resolved by installing the Windows system disk as Master, rewriting the MBR (Fixmbr in Recovery Console), then reversing the order of the disks making the Ubuntu system disk Master and the Windows system disk Slave.  This allowed the Grub menu to be selected from the boot disk.   Just to confirm I deleted and re-installed Ubuntu then changed back to having the Windows system disk as master without a slave and re-booting.  Windows started with no problems.  A real simple cure for what appeared to be a large problem.

Again, thanks to all who assisted.:redface:

T.C.

---

