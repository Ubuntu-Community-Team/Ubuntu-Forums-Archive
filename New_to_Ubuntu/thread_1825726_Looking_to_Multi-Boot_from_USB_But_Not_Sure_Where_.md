---
title: "Looking to Multi-Boot from USB But Not Sure Where to Start"
date: 2011-08-15
forum: New to Ubuntu
---

### Post by dniMretsaM on 2011-08-15
I have an 8 GB flash drive which I plan to multi-boot K/X/L/Ubuntu 10.04.3 and 11.04 LiveCDs as well as a modified Puppy Linux (installed, not live). So first off, is this possible. The size of the Ubuntu 11.04 LiveCD .iso file is 685.3 MB. Is that all the space I need for it on my USB drive, or will it expand when I burn it? If it expands too much, I probably won't have room. But if it doesn't expand, I'll have plenty. I assume I will need a separate  partition for each LiveCD and the Puppy install. I plan on installing Puppy first (with [this]("http://puppylinux.org/main/Puppy430-tutorial-English.pdf") guide), modifying it, shrinking the partition to the proper size, then adding the *buntu images. Will that work or should I do something different? Does MultiCD.sh work with K/X/Lubuntu? I know it works with Ubuntu, but not sure about the others. [S]A link to a guide on setting up GRUB would be helpful too.[/S] <- Got this covered. Thanks pqwoerituytrueiwog!

Thanks in advance,
dniMretsaM

---

### Post by pqwoerituytrueiwoq on 2011-08-15
i have not done it before but i would use grub2 on the usb to boot the iso files direclty as well as the puppy install
google boot ubuntu iso with grub2

---

### Post by dniMretsaM on 2011-08-15
GRUB2 is version 1.98 and up correct?

EDIT: I have bookmarked [this](https://lists.ubuntu.com/archives/ubuntu-in/2010-April/007648.html) page for instructions on how to boot ISOs. Thanks for the tip.

---

### Post by JC Cheloven on 2011-08-15
Hi, I used with full success [this multiboot-maker]("http://mylinux.es/multiboot-cargar-varias-distros-en-un-pendrive") program, but it seems to be unattended since a while now. Not sure if it will still work with newer versions (might be worth trying, was really nice).

Here is [another tool]("http://sourceforge.net/projects/multibootusb/files/") for that, in the form of a shell script. It's less user friendly but may fit your needs. 

Hope this helps.

---

### Post by oldfred on 2011-08-15
I did it manually, mostly with these instructions. Install grub2, manually create a grub.cfg, and just copy ISOs into a folder. But details are critical and each ISO seems to need different parameters to work. With Puppy I had to create a folder but still have the main file at the top level of the flash drive. I have it working with FAT32, NTFS & ext3 on different flash drives, so format is not critical.

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

I think the previous posts included some of these:

This is a script to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://sourceforge.net/projects/multibootusb/files/](http://sourceforge.net/projects/multibootusb/files/)
Another: multiboot055.sh
[http://blog.p-mt.net/archives/644](http://blog.p-mt.net/archives/644)
MultiSystem Another LiveUSB Multiboot
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

You can also directly boot ISOs from a hard drive with your current grub2 with an entry in 40_custom.
This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

---

### Post by dniMretsaM on 2011-08-15
> **JC Cheloven said:**
> Hi, I used with full success [this multiboot-maker]("http://mylinux.es/multiboot-cargar-varias-distros-en-un-pendrive") program, but it seems to be unattended since a while now. Not sure if it will still work with newer versions (might be worth trying, was really nice).

Here is [another tool]("http://sourceforge.net/projects/multibootusb/files/") for that, in the form of a shell script. It's less user friendly but may fit your needs. 

Hope this helps.

Thank you! That is exactly what I was looking for.

> **oldfred said:**
> I did it manually, mostly with these instructions. Install grub2, manually create a grub.cfg, and just copy ISOs into a folder. But details are critical and each ISO seems to need different parameters to work. With Puppy I had to create a folder but still have the main file at the top level of the flash drive. I have it working with FAT32, NTFS & ext3 on different flash drives, so format is not critical.

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB")

I think the previous posts included some of these:

This is a script to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://sourceforge.net/projects/multibootusb/files/](http://sourceforge.net/projects/multibootusb/files/)
Another: multiboot055.sh
[http://blog.p-mt.net/archives/644](http://blog.p-mt.net/archives/644)
MultiSystem Another LiveUSB Multiboot
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

You can also directly boot ISOs from a hard drive with your current grub2 with an entry in 40_custom.
This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

Thank you very much for these links! They are just what I need. Also, I can boot from both IOS's and installed OS's on the same USB drive, correct?

EDIT: I'm ready to begin, going to start installing Puppy now.

---

### Post by oldfred on 2011-08-15
Puppy was the hardest for me to configure as the files did have to be extracted, it was not a standard ISO boot.

I have a full install of Ubuntu in a 16GB flash and have a couple of ISO's I boot from it. I have a Windows repair USB and converted it to boot from grub2 with a chain boot entry and then added a few Linux repair ISOs to that Flash drive. The windows part was so small, I did not want to waste the space.

This was a puppy entry that worked for me:

```
menuentry "Puppy 511" {
set root=(hd0,1)
linux /boot/lupu511/vmlinuz root=/dev/ram0 pmedia=usbflash loglevel=7 pkeys=us 
initrd /boot/lupu511/initrd.gz
}

```
But I created /boot/lupu511 for most of puppy, but had to put this at the top level of the flash drive. lupu-511.sfs  I do not now remember if I had to adjust anything else or not.

More typical entries I have in grub.cfg:

```
set default=0 
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
set gfxpayload=800x600

menuentry "Ubuntu 11.10 Oneiric 64bit" {
    set isofile="/boot/iso/oneiric-desktop-amd64.iso"
    loopback loop (/dev/sdd,msdos1)/$isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset noprompt
    initrd (loop)/casper/initrd.lz
}

menuentry " " {
set root= 
}

menuentry "Ubuntu 11.04 Natty 64bit" {
    set isofile="/boot/iso/ubuntu-11.04-desktop-amd64.iso"
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset noprompt
    initrd (loop)/casper/initrd.lz
}

menuentry "Ubuntu 10.10 Maverick 64bit" {
    set isofile="/boot/iso/ubuntu-10.10-desktop-amd64.iso"
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset noprompt
    initrd (loop)/casper/initrd.lz
}


menuentry " " {
set root= 
}

```

---

### Post by beew on 2011-08-15
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

Works in Ubuntu.

The website is in French, but the application's interface is in English(probably depending on where you download from) Once it is installed it is integrated into the package manager and you'll get updates frequently. It covers a lot of distros and is very easy to use.

---

### Post by beew on 2011-08-15
> **JC Cheloven said:**
> Hi, I used with full success [this multiboot-maker]("http://mylinux.es/multiboot-cargar-varias-distros-en-un-pendrive") program, but it seems to be unattended since a while now. Not sure if it will still work with newer versions (might be worth trying, was really nice).


multiboot has been renamed multisystem. See my link.

---

### Post by dniMretsaM on 2011-08-15
> **oldfred said:**
> Puppy was the hardest for me to configure as the files did have to be extracted, it was not a standard ISO boot.

I have a full install of Ubuntu in a 16GB flash and have a couple of ISO's I boot from it. I have a Windows repair USB and converted it to boot from grub2 with a chain boot entry and then added a few Linux repair ISOs to that Flash drive. The windows part was so small, I did not want to waste the space.

This was a puppy entry that worked for me:

```
menuentry "Puppy 511" {
set root=(hd0,1)
linux /boot/lupu511/vmlinuz root=/dev/ram0 pmedia=usbflash loglevel=7 pkeys=us 
initrd /boot/lupu511/initrd.gz
}

```But I created /boot/lupu511 for most of puppy, but had to put this at the top level of the flash drive. lupu-511.sfs  I do not now remember if I had to adjust anything else or not.

More typical entries I have in grub.cfg:

```
set default=0 
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
set gfxpayload=800x600

menuentry "Ubuntu 11.10 Oneiric 64bit" {
    set isofile="/boot/iso/oneiric-desktop-amd64.iso"
    loopback loop (/dev/sdd,msdos1)/$isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset noprompt
    initrd (loop)/casper/initrd.lz
}

menuentry " " {
set root= 
}

menuentry "Ubuntu 11.04 Natty 64bit" {
    set isofile="/boot/iso/ubuntu-11.04-desktop-amd64.iso"
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset noprompt
    initrd (loop)/casper/initrd.lz
}

menuentry "Ubuntu 10.10 Maverick 64bit" {
    set isofile="/boot/iso/ubuntu-10.10-desktop-amd64.iso"
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset noprompt
    initrd (loop)/casper/initrd.lz
}


menuentry " " {
set root= 
}

```

I'm actually installing Puppy, not booting from it's ISO.

---

### Post by oldfred on 2011-08-16
Puppy is one of those that you cannot loopmount the ISO and run it, you just have to install it however you do it.

---

### Post by JC Cheloven on 2011-08-16
> **beew said:**
> multiboot has been renamed multisystem. See my link.

So it's alive!
Thank you for the pointing.

---

### Post by BitJunkie on 2011-08-16
I have successfully installed several tools and distros using YUMI: [http://www.pendrivelinux.com/yumi-multiboot-usb-creator/](http://www.pendrivelinux.com/yumi-multiboot-usb-creator/)

It has worked great for me so far.

---

### Post by dniMretsaM on 2011-08-16
Well, I'm trying to get all the ISO's downloaded (4 out of 9 so far) but my family won't let me download while they're using the Internet, takes up too much bandwidth... What about when they stream videos all the time? That slows my Internet down a lot, but do they care? No. Oh well, I'll get them DL'd eventually.

---

