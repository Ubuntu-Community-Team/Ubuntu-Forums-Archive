---
title: "Getting Ubuntu running on an old laptop, interesting restrictions"
date: 2009-12-21
forum: New to Ubuntu
---

### Post by ddarz on 2009-12-21
Hello,

I have a Sony Vaio PCG-C1VE laptop, it doesn't have a cd drive, only a  USB floppy drive and can only boot from that, the bios does not support  booting from usb. Network access is through the PCMCIA slot

I have been trying to install a linux distro in order to breathe some  life into it the problem is that my options for installing are rather  limited, as seen above. 

I managed to install OpenBSD 4.6 by running the bsd boot floppy that  managed to recognize a USB CDROM I had available. 

Being a complete newbie it took me some time to mount the usb cd rom in  bsd but finally i managed to access the Ubuntu 9.10 alternative  installation... but now what? I am not sure how to proceed...

Does anyone have any suggestions on how to get this laptop running? I  have been trying for days to get bootable floppies to have usb support, i  have tried plop boot manager (always hangs when selecting usb) and so  on...

Any help and/or suggestions would be greatly appreciated, Thanks!

---

### Post by halitech on 2009-12-21
not many distros support booting from floppy anymore as the kernel is just too big to get on them. You could try Debian 4.0 as it has a set of boot floppies and either see if it will install from the USB floppy or do a net install and then upgrade to 5.0 over the internet.

---

### Post by sdpiowa on 2009-12-21
Can the laptop boot from the network?  You could also install Ubuntu on a different computer and transfer it over right after it finishes copying, I think.

---

### Post by NESFreak on 2009-12-21
you might consider doing a networkinstall. Also a quick google gave this as a result [http://www.plop.at/en/bootmanager.html](http://www.plop.at/en/bootmanager.html) Don't know if it's usefull. You could also swap harddrives and install ubuntu on another system, then swap them back.

---

### Post by ddarz on 2009-12-21
Hi, Thank you for the replies

I have tried plop boot manager, installed fine to the hard disk but it freezes with any combination of usb :( 

I would not bet on booting from the network but I found two floppy images for debian and I will give them a go.

Since I have a working environment in openbsd and can see the usb cd isn't there any way of starting the linux installation from there?

Thanks again!

---

### Post by lkraemer on 2009-12-21
Why don't you try Smart Boot Manager (SBM).  I've used it on an HP
to get the CDROM drive to boot when the original BIOS wouldn't
boot it.  I don't know if it will boot from USB but it won't take
you long to find out.

[https://help.ubuntu.com/community/SmartBootManager](https://help.ubuntu.com/community/SmartBootManager)
[http://sourceforge.net/projects/btmgr/](http://sourceforge.net/projects/btmgr/)

In Linux
```

dd if=sbm.bin of=/dev/fd0 

```

Then boot from floppy first, and then boots from CDROM for LiveCD install.

Or Terabyteunlimited has this Bootit NG (BING) software.

[http://www.terabyteunlimited.com/index.htm](http://www.terabyteunlimited.com/index.htm)

And don't forget to check out their free download software that
is located on their website.  (I've used Bootit NG software also
to boot from floppy, then finish booting from a 256 USB Flash Drive
on my old Compaq Presario 1672 Laptop that wouldn't boot from USB.)

[http://www.terabyteunlimited.com/downloads-free-software.htm](http://www.terabyteunlimited.com/downloads-free-software.htm)
[http://www.terabyteunlimited.com/downloads-bootit-next-generation.htm](http://www.terabyteunlimited.com/downloads-bootit-next-generation.htm)

One of the above will work, but the last choice will cost you a bit of
cash after the 30 day free trial.


lk

---

### Post by Rex Bouwense on 2009-12-21
I'm not sure if this will help, but I have read that Linex Puppy will boot from a floppy.  It is tiny and will run from RAM if you do not want to install.  That may be your way to start.

---

### Post by ddarz on 2009-12-21
Thanks for the tip :D I got puppy linux and it looks promising but I cant get wakepup whch is required to make the boot floppy, the site (murga-linux) is dead :( 

Any links? or workarounds?

Thanks

Gonna give BootIt a go, thanx for the heads up :)

---

### Post by folabiklan on 2009-12-21
if u did manage to use puppylinux, u might explore using a usb pen drive option! though if i remember correctly wake pup is in the puppylinux distro all u need a to put in a floppy and run it!!!!  

or else u might try a flavour of puppy linux like lighthouse pup. now that is full featured and is a real os , it comes with EVERYTHING u might need in puppy. u can get that at lhpup.com (thats L) and while ur at it get the spare .sfs files, they contain different desktop environments and softwares


which then brings to my mind, does karmic have some sort of aversion for old hardware? cos i have a deskpro which iv run maybe like 5 distros on flawlessly incl jaunty but iv installed karic twice and both times whenever i restart, the desktop gets broken and it only boots to terminal. all the cmds to start graphics do not work!!!!!!!!

---

### Post by ddarz on 2009-12-21
No luck :(

Bootit cant do it, its all set up but it cant seem to find anything usb related...

puppy linux seems fine, i used the live cd on another machine, made a bootable flash drive easily but it fails to make a wakepup floppy disk, it cant seem to find the usb floppy. dsmeg reports it though. Any ideas?

Is there really no way to get linux installed through openbsd? (the only thing i could get running...)

Thank a lot for your help so far guys :)

---

### Post by lkraemer on 2009-12-21
ddarz,
Why don't you use [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) to create a
USB Flash Drive that should be able to boot from USB.  You can do this 
on any computer.  

[http://www.plop.at/en/bootmanager.html#plpcfgbt](http://www.plop.at/en/bootmanager.html#plpcfgbt)

To build a boot floppy go to the above link and download the (plpbt.bin) file
in Section #7.

Use the following command to build the floppy:
```

dd if=/home/login/ppbt.bin of=/dev/fd0

```

Then boot from foppy, and select USB from the menu which will boot
the USB Flash drive. 

I tested it on my old Compaq Presario 1672 with DSL 4.4.9

lk

---

### Post by ddarz on 2009-12-22
Hi all 

I finally got it to work :D

after the puppy linux forum was back up  managed to make a wakepup boot floppy that was able to see the USB cd rom!!! It was smooth sailing from there!

Thank you for all your help guys!

---

