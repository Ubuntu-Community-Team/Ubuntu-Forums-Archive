---
title: "LiveUSB of 10:10 using Unetbootin"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by farrow on 2010-10-12
i have downloaded the latest 10;10 .iso of Ubuntu, when I use Unetbootin to create a LiveUSB, I get the following error message:

[B]No init found. Try passing init=bootarg
BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntuv5) built-in shell (ash)

(inittramfs[/B]

Does anyone know how to overcome this problem, as it has outfoxed me.

thanks

---

### Post by beew on 2010-10-13
> **farrow said:**
> i have downloaded the latest 10;10 .iso of Ubuntu, when I use Unetbootin to create a LiveUSB, I get the following error message:

[B]No init found. Try passing init=bootarg
BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntuv5) built-in shell (ash)

(inittramfs[/B]

Does anyone know how to overcome this problem, as it has outfoxed me.

thanks

What OS do you use? If you are using Ubuntu 10.04 you can create a live usb (with persistence too) by using the Startup Disk Creator under the System > Administration drop down menu.

If you use Windows check this out.

[http://www.linuxliveusb.com/]("http://www.linuxliveusb.com/")

I don't use Unetbootin because it doesn't support persistence so I can't tell you how to trouble shoot it.

---

### Post by garvinrick4 on 2010-10-13
If you have a CD around use a burning program and burn the .iso file to a disk. Boot the disk and use Try Ubuntu when it starts up go to System/Admin/startup disk creator and use that program to make a flash drive install using the .iso file and a 4 gig drive.
You can make up to 4 gig of persistence so you can save changes.
Will be handy as a Live usb or if you just want to test 10.10.

---

### Post by AndyM3 on 2010-10-13
Try using the "Try Ubuntu" or "Install Ubuntu" entry from the bootup menu, not the "Default" entry. I remember that fixed it for me a couple of times.

---

### Post by amjjawad on 2010-10-13
> **AndyM3 said:**
> Try using the "Try Ubuntu" or "Install Ubuntu" entry from the bootup menu, not the "Default" entry. I remember that fixed it for me a couple of times.

He doesn't have a live media yet. He has problem with creating LiveCD and Live USB.

[http://ubuntuforums.org/showthread.php?t=1594576](http://ubuntuforums.org/showthread.php?t=1594576)

---

### Post by AndyM3 on 2010-10-13
> **amjjawad said:**
> He doesn't have a live media yet. He has problem with creating LiveCD and Live USB.

[http://ubuntuforums.org/showthread.php?t=1594576](http://ubuntuforums.org/showthread.php?t=1594576)

No, he can boot, but the kernel can't find something. So he gets dropped to a shell (ash).

---

### Post by amjjawad on 2010-10-13
> **AndyM3 said:**
> No, he can boot, but the kernel can't find something. So he gets dropped to a shell (ash).

> i have downloaded the latest 10;10 .iso of Ubuntu, **when I use Unetbootin _[SIZE=4]to create a LiveUSB[/SIZE]_, I get the following error message:**

[B]No init found. Try passing init=bootarg
BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntuv5) built-in shell (ash)

(inittramfs[/B]

At least, this is what I understood from his post. Maybe I'm wrong.

---

### Post by drpjkurian on 2010-10-13
See this [post]("http://ubuntuforums.org/showthread.php?p=9948033#post9948033") and this

[blog]("http://trentscott.com/2010/10/07/fixing-usb-install-issues-with-ubuntu-10-10-maverick-meerkat/")

---

### Post by farrow on 2010-10-13
thanks for all the responses, I will see if I can get the suggestions to work. I am using 10:04, I had installed Unetbootin and chose a downloaded .iso of 10:10 with the view of making a LiveUSB only to test out 10:10. It seems odd that i can't make a LiveUSB without these problems.

Does my experience count as a Bug? As I am not sure how I can get the problem resolved so other people don't end up with the problem.

---

### Post by DavePlummer on 2010-10-13
I had this problem, and solved it by first removing the stock version of syslinux, and then downloading and manally installing the Maverick Meerkat syslinux-common and syslinux packages.

---

### Post by spikoley on 2010-10-13
I ran into this bug when I was installing Meerkat.  It is a known bug with Unetbootin.  The solution is to use Startup Disk Creator and then edit syslinux.cfg.

From: [http://trentscott.com/2010/10/07/fixing-usb-install-issues-with-ubuntu-10-10-maverick-meerkat/](http://trentscott.com/2010/10/07/fixing-usb-install-issues-with-ubuntu-10-10-maverick-meerkat/)
> Using GParted to Format a USB Stick »
Fixing USB Install Issues with Ubuntu 10.10 Maverick Meerkat
Published on October 7, 2010 in Ubuntu. 2 Comments Tags: bootlogo, fix, gfxboot, maverick meerkat, ubuntu, ui, unknown keyword in configuration file.

This morning, I attempted to install Ubuntu 10.10 Maverick Meerkat from a USB drive but received an error message to my disdain. After using the USB Startup Disk Creator to create a bootable USB installer, I rebooted only to be confronted with the following fatal error message: &#8220;Unknown keyword in configuration file&#8221;. Here&#8217;s a fix for it (thanks to JackNocturne):

NOTE: This has only been tested and reported as working on the 32-bit version of Ubuntu 10.10. Compatibility issues have been reported with the 64-bit version.

1. Using the USB Startup Disk Creator, make a bootable USB disk with the latest Ubuntu 10.10 .ISO.
2. Once the process is complete, browse to the root directory of the USB disk, click on the /syslinux folder, and open the file entitled syslinux.cfg.
3. Using a text/code editor, find the line:
ui gfxboot bootlogo
4. Change it to:
gfxboot bootlogo
5. Save the file and reboot to test &#8212; it should work now.

From this [thread]("http://ubuntuforums.org/showthread.php?t=1592204").

---

### Post by farrow on 2010-10-13
> **DavePlummer said:**
> I had this problem, and solved it by first removing the stock version of syslinux, and then downloading and manally installing the Maverick Meerkat syslinux-common and syslinux packages.

 Thanks, I think I will report the issue as a Bug as most newbies will not know how to (me) act on your suggestions, though hopefully your ideas will be helpful to others.

---

### Post by beew on 2010-10-13
If you are running Lucid and want to create a live usb for Maverick, Luicd's startup disk creator is definitely better than Unetbootin, you can make the usb persistent.

I have no idea about the editing syslinux stuff. I have made a Maverick live usb with 3 g of persistence and I never have to edit syslinux.

---

### Post by farrow on 2010-10-13
Thanks, I burn a copy to a CD then used Ubuntu inbuilt start-up disk creator. I did not realise I could use the creator to create a LiveUSB (without persistence) and I do like not having the Unetbootin splash page.

---

### Post by gsf747 on 2010-10-14
I ran into this error with an older version of unetbootin (471) but a newer version (494, with the "Try Ubuntu Netbook" options) worked without flaw.

---

### Post by Ctrl-Alt-F1 on 2010-10-22
For those using Ubuntu to make your LiveUsb.  System > Administration > Startup Disk Creator worked for me in Ubuntu 10.04 for making a 10.10 usb bootable.

---

