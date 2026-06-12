---
title: "boot from usb..."
date: 2009-03-22
forum: New to Ubuntu
---

### Post by twignation on 2009-03-22
I have ubuntu installed.

I want to reinstall it.

My USB disk won't boot (it is the very stick I used to install the OS in the first place).

It isn't the BIOS. The USB stick does work.

How do I make my USB stick boot again?

(I don't have a CD ROM on this computer)

ta.

---

### Post by neu2buntu on 2009-03-22
i take it you have your usb stick above your harddrive in boot order in the bios?

---

### Post by twignation on 2009-03-22
yep :)

---

### Post by neu2buntu on 2009-03-22
plug in your usb stick and do code ```
sudo fdisk -l
``` and paste the output in your next reply

---

### Post by twignation on 2009-03-22
```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe5e35636

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       23948   192362278+  83  Linux
/dev/sda2           23949       24321     2996122+   5  Extended
/dev/sda5           23949       24321     2996091   82  Linux swap / Solaris

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd657d657

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30060   241456918+  83  Linux
/dev/sdb2           30061       36481    51576682+   b  W95 FAT32

Disk /dev/sdc: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00012006

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       36481   293033601   83  Linux

Disk /dev/sdd: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdc61dc61

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       36481   293033601    7  HPFS/NTFS

Disk /dev/sde: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1ce21ce2

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       36481   293033601   83  Linux

Disk /dev/sdf: 2102 MB, 2102394880 bytes
154 heads, 26 sectors/track, 1025 cylinders
Units = cylinders of 4004 * 512 = 2050048 bytes
Disk identifier: 0x0000f55c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1        1026     2053119+   c  W95 FAT32 (LBA)
```

I took the boot flag off the main disk hoping that that would force the system to use the USB, But GRUB out witted me :|

err obviously the usb is sdf1 :)

---

### Post by neu2buntu on 2009-03-22
thats sort of where i was going here with this too ,i see the boot flag on sdf1, im just wondering what method you used to make the usb bootable, if like me you used unetbootin... and looking at my usb i have only 1 partition on it........could it be that your boot flag needs to be on /dev/sdf and not /dev/sdf1? what all is on the usb?  just realised there that sdf1 is the only partition on your usb....oooops silly me......  maybe try to set the mbr again using the grub command or wipe the usb disk and start again using unetbootin

---

### Post by twignation on 2009-03-22
The usb is a ubuntu usb startup disk as made by a different machine (ubuntu made it). It was used to install linux onto this computer, and onto a different machine.

I have just tried fiddling about in my BIOS - by only allowing the system to boot from the USB I get

SYSLINUX..........................blah blah blah.................Peter Anvin
boot:

and it just sits there.

(sorry peter)

---

### Post by Tobi-fp on 2009-03-22
You should try unetbootin..

Im also guessing you have a aspire one/ EEE or MSI WIND, anyways, if you hit F12 right when your computer boots, it lets you choose where you wanna boot from

---

### Post by twignation on 2009-03-22
Yep, you got it, I have the 'F12 to choose bootable media' thing at BIOS.

It comes up with the above when the usb is the only option.

Unetbootin is better than the standard unbuntu usb thing?

---

### Post by neu2buntu on 2009-03-22
you can use unetbootin from your driveless laptop/netbook to make a bootable live usb .it can load the image  into your usb straight from the net, just make sure you are carefull to choose the usb and not any other disk

---

### Post by twignation on 2009-03-22
Ack. How do you install Unetbootin? :oops:

And also - the usb stick is working fine, I just used it on a different computer..

_________________

---

### Post by UnknownFear on 2009-03-22
> **twignation said:**
> Ack. How do you install Unetbootin? :oops:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

At the top of the page, it gives you a choice between Windows or Linux installation. Scroll through the pages and you should find the installation methods for both Windows and Linux.

---

### Post by twignation on 2009-03-22
Now installed onto linux, thanks fear (the windows version was rubbish! it crashed..)

---

### Post by twignation on 2009-03-22
Nope still doesn't work.

And the usb works on two machines.

There must be something on the computer stopping the usb booting?

---

### Post by flyingsliverfin on 2009-03-22
there are many ways that you can use to install ubuntu (w/o a cd/dvd)

[https://help.ubuntu.com/community/Installation#Installing%20on%20external%20or%20RAID%20hard%20disks](https://help.ubuntu.com/community/Installation#Installing%20on%20external%20or%20RAID%20hard%20disks)

(I didn't even know there were so many until someone showed me)

hope that this works!

---

### Post by twignation on 2009-03-22
> **flyingsliverfin said:**
> there are many ways that you can use to install ubuntu (w/o a cd/dvd)

[https://help.ubuntu.com/community/Installation#Installing%20on%20external%20or%20RAID%20hard%20disks](https://help.ubuntu.com/community/Installation#Installing%20on%20external%20or%20RAID%20hard%20disks)

(I didn't even know there were so many until someone showed me)

hope that this works!


LEGEND!!

partitioned a section of one of my spare drives, and configured grub to load from there.

Sorted Thank you!!!!!!!! :KS

---

### Post by twignation on 2009-03-22
i spoke far too soon.

it loaded into the live desktop, i installed it, but it crashed at the end. Now i am stuck with the grub and it can only load 'file not found 15'..

rubbish.

---

### Post by twignation on 2009-03-22
why? why? why? why?](*,)](*,)](*,)

This makes no logical sense. I used this usb to set up this machine. 
The usb works on other machines. It doesn't even have an operating system.
Nothing is different.

ARGH.

---

### Post by twignation on 2009-03-23
Sorted.

I installed a CDROM and loaded ubuntu from there.. was a right pain in the..

ahh relief!

---

### Post by flyingsliverfin on 2009-03-23
glad you didn't commit suicide becuz of a comp

---

### Post by twignation on 2009-03-24
> **flyingsliverfin said:**
> glad you didn't commit suicide becuz of a comp

I was eyeing the window and calculating the weight of my computer..
[URL="http://thinkexist.com/quotation/never_trust_a_computer_you_can-t_throw_out_a/218953.html"]
"Never trust a machine you can't throw out of a window"[/URL]

---

### Post by flyingsliverfin on 2009-03-25
lol

---

