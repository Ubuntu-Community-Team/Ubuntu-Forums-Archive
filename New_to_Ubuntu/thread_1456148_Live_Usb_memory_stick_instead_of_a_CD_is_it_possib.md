---
title: "Live Usb memory stick instead of a CD is it possible"
date: 2010-04-16
forum: New to Ubuntu
---

### Post by Peterfc on 2010-04-16
Hi All

I would like to make a live Usb instead of a cd as it's easier to carry around. If it can be done any body explane how.

Thanks

---

### Post by I8NY on 2010-04-16
go get unetbootin and run it and a window will pop up, point it to the iso of linux and it will "burn" it to the thumb drive.

---

### Post by Directive 4 on 2010-04-16
0, you've got a live cd, right?

1, go to system>admin>usb startup disk creator

2. create usb startup disk.

3, ???????

4, profit.

---

### Post by quadproc on 2010-04-16
> **Peterfc said:**
> Hi All

I would like to make a live Usb instead of a cd as it's easier to carry around. If it can be done any body explane how.

Thanks
If you have a recent version of Ubuntu then there is a command in the System > Administration menu called USB Startup Disk Creator.  To use this, first choose a large enough USB flash drive (at least 1 GB for a Live CD setup, more if you do a full install on the USB drive) and plug it in.  Unmount it. Use Gparted to clean out whatever might be on the USB drive, create one or more partitions on the USB drive.  Have a copy of the file or CDROM with your desired system on it and put that copy in a handy place.  Run the Startup Creator.  After it is done, go back to Gparted and set the boot flag in the appropriate (or only) partition.

There is also a competing program called Unetbootin.  I have not tried it myself but it seems to do the same things as the Ubuntu offering.

There is some uncertainty regarding which boot system will be installed on the USB drive.  I have seen grub, grub2 (aka grub-pc), and syslinux get installed.  Any of these will work but they use different files and naming conventions.

A final note: my BIOS is a bit buggy and would not use the USB drive unless I used the F8 key during bootup.  Your BIOS probably uses a different key, or perhaps none is needed.

quadproc

---

### Post by C.S.Cameron on 2010-04-16
A Live USB is not only easier than a Live CD but much faster.
As you don't want to make a Live CD first the built in usb-creator is not an option.
Unetbootin is then probably the simplest of a dozen options.
The only problem is that an UNetbootin install does not automatically save changes.(no persistence).

---

### Post by sandyd on 2010-04-16
you can also just point the ubuntu installer to the memory stick / usb drive / sd card and just use ubuntu from there.

I got an extrenal eSATA/USB drive that I installed ubuntu on.

---

### Post by garvinrick4 on 2010-04-16
> **C.S.Cameron said:**
> A Live USB is not only easier than a Live CD but much faster.
As you don't want to make a Live CD first the built in usb-creator is not an option.
Unetbootin is then probably the simplest of a dozen options.
The only problem is that an UNetbootin install does not automatically save changes.(no persistence).Use a 8 gig if you can and format it in gparted to a 2 gig and a 6 gig
partition. Label the second partition something like home1 or something close to that so you can have a place on your live usb to keep all your notes and fixes and such. 
So first partition you download unetbooten and second partition you just label and leave alone. 

Or you can use a 4 gig in Ubuntu's Start-up disk creator and it has 4 gig of persistence where ubetbooten has none, I have both just because Flash drives are so cheap and having a fast USB live Cd if you would are just nice to have around.

---

### Post by Bigadada_saba on 2010-04-16
> **carlee said:**
> you can also just point the ubuntu installer to the memory stick / usb drive / sd card and just use ubuntu from there.

I got an extrenal eSATA/USB drive that I installed ubuntu on.


I agree with that and the installation proses is a lot easier and runs smother from a memory stick or a solid state drive.

---

### Post by oldfred on 2010-04-17
Still another option is to copy several ISOs to a USB key and boot any of them. I have several Ubuntu's, gparted, system rescue and parted magic all on one USB key. 

MultiBoot USB with Grub2 (boot directly from iso files)
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1288604](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1288604)

---

### Post by 2nubu on 2010-05-12
Wait a minute, ... so is it possible to use an SDHC Flash Memory Card as a Live CD... Partition the memory card into a few drives... then maybe reformat my netbook clean w/ 120GB...?

---

### Post by oldfred on 2010-05-13
You can do a full install to a USB flash or SSD:

Ubuntu Karmic Koala Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)

---

### Post by Kevanx on 2010-05-20
What's even cooler is having a persistent USB install, meaning that you can save settings, and install programs at your leisure! That way, not only is it your "restore" CD should something go wrong, BUT... you can also have your own settings, apps, and files on anyone elses computer (provided it can boot from USB). I generally use the tutorials at [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

