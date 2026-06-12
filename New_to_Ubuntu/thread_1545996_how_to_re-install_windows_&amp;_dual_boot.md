---
title: "how to re-install windows &amp; dual boot"
date: 2010-08-04
forum: New to Ubuntu
---

### Post by FlightFollower on 2010-08-04
I have an Acer Aspire One Netbook. I installed Ubuntu UNR 9.04 so when 10.04 came out I wanted to upgrade, however when I did I lost connection to the internet.

Basically Im hoping to get some advice on how to re-install windows ( I did not go with dual boot at the time *facepalm ). I bought an external optical drive to use my Recovery CD but it is not working 10.04 other than the network issue works but because I was playing around I dont have a top menu anymore and am having a heck of a time getting around 

When I try to boot from the system CD it says no drives found then goes to a red screen which says The Unknown status for CD-ROM => e000d000

and if I try to boot from the Linux 10.04 CD I get to the main screen but cannot get any further Install, Try without installing etc

I would ideally like to get Windows installed and then a dual boot with Linux but I am just dumbfounded I likely did something wrong.

Luckily I WAS smart enough to back up all my files ( only files ) to an external hard drive so I dont not care if I have to re-format my HD and start over but I am not sure where to begin

If anyone could help me out I would appreciate it greatly

Thanks

---

### Post by FlightFollower on 2010-08-04
Update:

So I switched back to the UNR desktop, and was able to restore wired connection to the internet by right clicking ( like I read in another post ) and enabling networking.

So I guess my question would be on how to re-install windows.

but my wireless connection does still seem to not work

---

### Post by cj13579 on 2010-08-04
My advice would be that if you were to start again, to make sure that Windows is the primary OS on your system as its bootloader is quite funny about being second!! 

Then install Ubuntu and use the liveCD/USB to partition your drive.

---

### Post by FlightFollower on 2010-08-04
> **cj13579 said:**
> My advice would be that if you were to start again, to make sure that Windows is the primary OS on your system as its bootloader is quite funny about being second!! 

Then install Ubuntu and use the liveCD/USB to partition your drive.

Thanks for the reply, that is ideally what I would like to do however Im having issues re-installing windows from the Recovery CD. 

Do I have to Format my HD first ?

---

### Post by cj13579 on 2010-08-04
I wouldn't have thought so because I would have thought your CD would have done that. But, if you have everything backed up you could always give it a whirl!

---

### Post by ajgreeny on 2010-08-04
I'm afraid it is often necessary to format away from a linux file system, or at least make some unallocated space before the windows CD will work.

Windows is not very clever and can not see a hard disk if it is full of linux file systems.  So use the live CD/USB and gparted to shrink your current ubuntu partition, and leave it as free space.  The windows install CD should see that.

Regarding your wireless problem see [https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks) where just about all the Acer Aspire netbooks are discussed along with some solutions to wireless and other problems.

---

### Post by FlightFollower on 2010-08-04
> **ajgreeny said:**
> I'm afraid it is often necessary to format away from a linux file system, or at least make some unallocated space before the windows CD will work.

Windows is not very clever and can not see a hard disk if it is full of linux file systems.  So use the live CD/USB and gparted to shrink your current ubuntu partition, and leave it as free space.  The windows install CD should see that.

Regarding your wireless problem see [https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks) where just about all the Acer Aspire netbooks are discussed along with some solutions to wireless and other problems.


So I tried to run the live CD but I cannot get past the main screen none of the options other than the boot from HD will work. 

Also not sure if it has any relevance but when I put in the recovery CD, and boot from the CD it gives me the error listed in my first post.

---

### Post by Mark Phelps on 2010-08-05
If you're running Win7, it's too small to fit on a CD, so in that case, your Recovery CD is probably a custom WinPE boot CD that then launches the reinstall using the image contained in a Recovery partition on your drive.

Do you still have the Recovery partition and is it intact?

If not, I seriously doubt that you will be able to fully reinstall Win7 from just the Recovery CD.

---

### Post by FlightFollower on 2010-08-06
> **Mark Phelps said:**
> If you're running Win7, it's too small to fit on a CD, so in that case, your Recovery CD is probably a custom WinPE boot CD that then launches the reinstall using the image contained in a Recovery partition on your drive.

Do you still have the Recovery partition and is it intact?

If not, I seriously doubt that you will be able to fully reinstall Win7 from just the Recovery CD.

It was not Windows 7 it was XP, and the recovery image on the HD is not working, I have spoken with Acer and in order to get one I have to PAY to get the physical copy, correct me if I am wrong but does that not violate the EULA for Windows? 

So in order to get windows back on my Netbook I have to pay about $20 for them to ship me a CD. does anyone know if there is a version available to DL with a torrent? 

This is the reason I went with Linux in the first place to much cash grab from greedy corporations. The only reason I wish to put Windows back on is to stream my media from my HD to my Xbox so I can watch it on my big screen. Or if this is possible at all on Ubuntu 10.04 ( my google-fu leads me to believe it is not possible yet ).

Any help would be appreciated 


Thanks 

Del

---

### Post by FlightFollower on 2010-08-06
So after searching for HOURS..... I have found a place to download to ISO images that ACER is charging for. 


so I will post it here to help anyone who may be having the same problem that I am having.



[http://www.technews.biz/download-acer-aspire-one-windows-xp-restore-discs-3372/](http://www.technews.biz/download-acer-aspire-one-windows-xp-restore-discs-3372/)

as it says its not for pirates but for people who have PAID for their copies of Windows but not get a physical copy

---

### Post by complexplasma on 2010-08-06
> **FlightFollower said:**
> So after searching for HOURS..... I have found a place to download to ISO images that ACER is charging for. 


so I will post it here to help anyone who may be having the same problem that I am having.



[http://www.technews.biz/download-acer-aspire-one-windows-xp-restore-discs-3372/](http://www.technews.biz/download-acer-aspire-one-windows-xp-restore-discs-3372/)

as it says its not for pirates but for people who have PAID for their copies of Windows but not get a physical copy

test:(

---

### Post by FlightFollower on 2010-08-06
> **complexplasma said:**
> test:(

test?

I am currently downloading it, and will post with results, the comments on the page overall seem to be positive.

---

### Post by cj13579 on 2010-08-07
It is DEFINATELY possible to stream from 10.04 to xBox as I do it myself. I used the following HOWTO:

[http://ubuntuforums.org/showthread.php?t=848144](http://ubuntuforums.org/showthread.php?t=848144)

I originally set this up when I was on Jaunty and it hasn't broken when i have upgraded and am now running Lucid and it works perfectly still.

---

### Post by FlightFollower on 2010-08-25
So, I had to bite the bullet and PAY Acer for a recovery disk,  

But now the problem that I am having is I have tried to re-install windows, but it is still trying to load the GRUB loader, not going to windows and I not able to get any further.


Does anyone know how I can format my HD?? to wipe it clean then start fresh with my windows disk?

---

### Post by Mark Phelps on 2010-08-25
> **FlightFollower said:**
> It was not Windows 7 it was XP, and the recovery image on the HD is not working, I have spoken with Acer and in order to get one I have to PAY to get the physical copy, correct me if I am wrong but does that not violate the EULA for Windows? 
Basically ... NO.  All they are obligated to do is provide you a way of restoring your original setup.  If they have a recovery partition configured, they have satisfied that.  The fact that the recovery partition does not work is, unfortunately, YOUR problem because you've messed around with the partitions.

> So in order to get windows back on my Netbook I have to pay about $20 for them to ship me a CD. does anyone know if there is a version available to DL with a torrent? 
Considering that XP still costs around $100 in some locations, that is quite a bargain.

---

