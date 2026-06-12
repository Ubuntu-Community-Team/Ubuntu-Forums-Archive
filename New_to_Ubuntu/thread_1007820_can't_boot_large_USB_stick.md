---
title: "can't boot large USB stick?"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by enricong on 2008-12-10
I'm trying to install crunchbang.

I used syslinux on a new 16GB USB stick formatted with fat32.
I copied on the initrd.gz, vmlinuz, and iso file to the stick

When I plug it in my laptop, it doesnt boot and goes straight to windows, even though it is detected and I select it.

However my 512MB stick can boot just fine with debian linux.

Am I doing something wrong or is there some sort of size limit?

---

### Post by cdtech on 2008-12-10
What instructions did you use? Here is a page of instructions that sounds pretty straight forward.
[http://syslinux.zytor.com/wiki/index.php/SYSLINUX](http://syslinux.zytor.com/wiki/index.php/SYSLINUX)

---

### Post by enricong on 2008-12-10
> **cdtech said:**
> What instructions did you use? Here is a page of instructions that sounds pretty straight forward.
[http://syslinux.zytor.com/wiki/index.php/SYSLINUX](http://syslinux.zytor.com/wiki/index.php/SYSLINUX)

I formatted using fat32
ran "syslinux -ma h:" (h: being my flash drive)
then copied the files I mentioned.

I plug the 16GB drive into my laptop, press the button to get to the bios boot menu, select the flash drive, but it still boots to windows.

I do the exact same thing with my 512MB drive, it works fine

---

### Post by networm1230 on 2008-12-10
I had the same thing happen to me my usb cruzer 4GB did not work on ubuntu so what i did was to install a program called Gnome Partition Editor formet the drive to a format that linux and windows understand

---

### Post by caljohnsmith on 2008-12-10
One thing I would check would be to see if your single FAT32 partition has the boot flag set; some BIOSes will refuse to boot a drive that doesn't have the boot flag set on one of the primary partitions, because the BIOS then assumes it is a data-only drive. You can check by doing:
```
sudo fdisk -l
```
And look for an asterisk * under the "boot" heading. If that is the problem, you can set the boot flag by doing:
```
sudo sfdisk -A1 /dev/sdX
```
That will set the boot flag on the first partition of drive sdX. Let me know if that happens to be your problem.

---

### Post by enricong on 2008-12-10
Seems my laptop bios just doesnt like the stick.  It is read in XP just fine.  My laptop can read my 512MB stick but not the 16GB one.
my main computer reads both.

Is there a way I can boot using the 512MB stick then plug in the 16GB one and have it boot from the iso?



My laptop has no CDROM drive so USB is the only way I can install.  I'm almost ready to just give up crunchbang and get the net install for debian but I dont even know if that will work with my wireless.

---

### Post by snowpine on 2008-12-11
Hi Enricong,

Have you tried re-partitioning your 16gb device so that it shows up as a 1gb device?

A couple of other suggestions if that doesn't work:

You can install a command line (CLI) Ubuntu using the Alternate Install or Mini iso (which should fit on your 512mb stick), then install Crunchbang using the alternate method: [http://crunchbanglinux.org/forums/topic/26/crunchbang-linux-81001-alternative-installation/](http://crunchbanglinux.org/forums/topic/26/crunchbang-linux-81001-alternative-installation/)

You could also try the Lite version of CrunchBang, which is less than 512mb.

You could use Unetbootin to prepare the USB stick.

Here is the exact model of USB stick I used to install CrunchBang; it only costs $5.99: [http://www.newegg.com/Product/Product.aspx?Item=N82E16820134043](http://www.newegg.com/Product/Product.aspx?Item=N82E16820134043)

---

### Post by enricong on 2008-12-11
> **snowpine said:**
> Hi Enricong,

Have you tried re-partitioning your 16gb device so that it shows up as a 1gb device?

A couple of other suggestions if that doesn't work:

You can install a command line (CLI) Ubuntu using the Alternate Install or Mini iso (which should fit on your 512mb stick), then install Crunchbang using the alternate method: [http://crunchbanglinux.org/forums/topic/26/crunchbang-linux-81001-alternative-installation/](http://crunchbanglinux.org/forums/topic/26/crunchbang-linux-81001-alternative-installation/)

You could also try the Lite version of CrunchBang, which is less than 512mb.

You could use Unetbootin to prepare the USB stick.

Here is the exact model of USB stick I used to install CrunchBang; it only costs $5.99: [http://www.newegg.com/Product/Product.aspx?Item=N82E16820134043](http://www.newegg.com/Product/Product.aspx?Item=N82E16820134043)

Yes, I tried making a 800MB partition and it was the same.  I think my laptop bios is not seeing it right as when I goto the boot menu it does not show the name of the USB stick as it does with my other one that works.

Oh I didnt know the lite edition was available.

Maybe I'll try that or get your stick, but I suspect my old laptop might not like certain sticks

---

### Post by networm1230 on 2008-12-11
this may be due to your pc  bios = Basic Input/Output = System update the bios make sure in the bios you have plug/play on or you can plug in the usb drive in the pc and reboot your pc with the usb drive on the pc the plug and play lats you plug in devices like usb drives or any externel drives

---

### Post by enricong on 2008-12-11
deleted

---

### Post by enricong on 2008-12-11
deleted

---

### Post by networm1230 on 2008-12-13
> **enricong said:**
> deleted

did you try to recover the data? form the usb drive

---

### Post by Cincinnatux on 2008-12-15
> **enricong said:**
> I'm trying to install crunchbang.

I used syslinux on a new 16GB USB stick formatted with fat32.
I copied on the initrd.gz, vmlinuz, and iso file to the stick

When I plug it in my laptop, it doesnt boot and goes straight to windows, even though it is detected and I select it.

However my 512MB stick can boot just fine with debian linux.

Am I doing something wrong or is there some sort of size limit?

enricong,

I've read in other newsgroups that some BIOSes can be picky when it comes to memory sector size on the bootable medium, and I understand that some of the larger flash drives have unusual sector sizes.  At least one poster claimed that by changing his USB drive's geometry, repartitioning, and reformatting, he was able to get his system to boot from his 8 GB Kingston Traveler (which had previously had the same problem you describe). 

Best of luck,

Cincinnatux

---

