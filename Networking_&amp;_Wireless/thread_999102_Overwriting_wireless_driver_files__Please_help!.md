---
title: "Overwriting wireless driver files??  Please help!"
date: 2008-12-01
forum: Networking &amp; Wireless
---

### Post by random turnip on 2008-12-01
Hi, I'm fairly new to Ubuntu and I have been having problems with my wiresless. i finally found someone on here who has the same laptop as me and they put up the solution to the wireless problems.

This is the link to the thread...
[http://ubuntuforums.org/showthread.php?t=862321](http://ubuntuforums.org/showthread.php?t=862321)

I have downloaded the "broadcom wireless LAN driver".
Now I am installing it, through WINE and it has come up with the message
"The following file is already on your computer:
c:\SWSetup\SP34152A\bcm1xsup.dll
Do you wish to overwrite this file?"

I this a good idea.
I cannot afford for this to affect the wireless on my windows partition, will this only affect Ubuntu or will it affect Vista as well?

A quick response would really be apreciated, I'm half way through the installation now.
All I really need to know is that my Windows wireless internet won't be affected.
__________________

---

### Post by McMajik on 2008-12-01
Have you specifically set your wine C drive to the location of your windows partition? If not, then it definately won't make a difference. Wine sets up its own folder in your user space, which it tells all programs running under it is the root of the C drive. This is entirely seperate from a windows partition you may have, unless you set that folders location to the mount point of the windows partition.

If you have, it shouldn't make a difference anyway - it'll be overwriting it with the same file (or at least, it should be). Check the sizes of both files. If their the same, do it. If their not, come back here :D

Good luck,
McMajik

---

### Post by random turnip on 2008-12-01
Ok thanks, I was just worried that it meant my Windows C drive, and I really don't wonn kill windows as well.

Also, I havent changed any of the settings in it.
But if the files are already there that means that this driver is already there I just realised.

---

### Post by dxlwebs on 2008-12-01
hey man,
first of the comment is true windows and the ubuntu wintray are two very differant areas and on differant partitions so you should not be effected there as for this darn wireless problem its self i found this 
> 97.)  	What are the Linux tg3, bnx2 and b44 drivers?

To better support users, Broadcom has been actively supporting, maintaining, and testing the in-kernel Linux drivers for the NetXtreme, NetXtreme II, NetLink and 4401 product lines. The following is list of drivers supported for each product line:

    * NetXtreme and NetLink - tg3
    * NetXtreme II - bnx2
    * 4401 - b44

Broadcom officially releases the Linux drivers as packages. The Linux driver packages released by Broadcom are based on the latest in-kernel drivers with some added compatibility code to make it backwards compatible with most 2.6 kernels and some 2.4 kernels (generally newer than 2.4.24). If you are using the latest upstream kernel from [www.kernel.org](www.kernel.org), you generally do not need to download the Linux driver packages from Broadcom as the latest upstream kernel has the latest Linux driver patches.

For the NetXtreme and NetLink product lines, the tg3 driver is now the only Linux driver that Broadcom supports. Accordingly, Broadcom has discontinued support for the bcm5700 driver and no longer provides updates.

There are a few minor differences to be aware of if you are migrating from the bcm5700 driver to the tg3 driver. The tg3 driver does not support the Broadcom proprietary load balancing software module known as BASP. The Linux bonding driver and 802.1q driver provide similar functionalities and can be used with tg3. BASP will also be discontinued. The tg3 driver also does not support module parameters to configure the device (line speed, flow control, ring sizes, etc) but relies on standard Linux utilities such as ethtool. Other than these differences, the two drivers are very similar in terms of hardware support, robustness, and performance.

 so i believe they acturally have linux drivers now so ifyou know what Broadcom Wireless LAN product youhave then you can find the driver there other wise i would over right it and see what happens imean you can'treally lose anything as longasyou have back ups also check to see if your ubuntu needs any updates that might help but im guessing its a problem with the actural driver you never know it might have not installed correctly the first time  as ubuntu really does install practically everything with out aid

p.s. i also found these
[http://ubuntuforums.org/showthread.php?p=1071920&mode=linear](http://ubuntuforums.org/showthread.php?p=1071920&mode=linear)
[http://ubuntuforums.org/showthread.php?t=25683](http://ubuntuforums.org/showthread.php?t=25683)
they both look promising!

---

