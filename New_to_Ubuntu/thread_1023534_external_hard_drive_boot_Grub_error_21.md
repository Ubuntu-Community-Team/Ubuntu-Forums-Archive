---
title: "external hard drive boot Grub error 21"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by big_D131 on 2008-12-28
I installed Ubuntu 8.1 from the CD in my laptop to my external hard drive. However my laptop still has Windows vista installed on it. Now whenever I boot my laptop without my external hard drive connected, I get the message 

 Grub loading stage 1.5

Grub loading, please wait

Error 21

and cannot boot anything.
Is there a way I could make it to open normally in vista when my hard drive is not connected?

---

### Post by Sealbhach on 2008-12-28
Hi, first, using a Live CD try this here:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)


.

---

### Post by Scunnered on 2008-12-28
big_D131

Like you I experienced this grub error and have as yet still to find a way to use the external HD in the way I intended.

What I had to do was to re-install Windows as the MBR needed sorting. It appears that grub rules the roost and doz will only work with their MBR.

I in the end totally gave up on even trying to setup an external HD.  Additionally I have totally comitted myself to Linux and am loving it.

Hope this assists

PS I remember looking at "USB External HD booting problems" on [www.linuxformat.co.uk](www.linuxformat.co.uk) which might assist.

---

### Post by gn2 on 2008-12-28
First thing you need to do is repair the Vista bootloader.

This can be done with a [Vista Recovery CD]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/")

Next, you need to install Grub _onto the external USB hard drive_.
The easiest way to make sure that Grub gets installed onto the external drive is to disconnect the internal drive(s).

There are a few ways to do this, it can be done [with an Ubuntu Live CD]("http://ubuntuforums.org/showthread.php?t=224351&highlight=grub") or [a SuperGrub CD]("http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html").

The next thing to do is to set USB before internal in the BIOS boot list.

Then when you want to boot the external drive, plug it in before booting, when you want to boot Vista, leave the USB drive disconnected.

USB hard drives are not particularly good for using as bootable devices because they can fail to spin up in time for the BIOS to find them.
Sometimes it can take a few attempts to get them to boot each time you want to use them.
Flash drives do not suffer from this problem and are far better for use as external bootable devices.

---

### Post by caljohnsmith on 2008-12-28
[QUOTE=gn2]The easiest way to make sure that Grub gets installed onto the external drive is to disconnect the internal drive(s).[/QUOTE]
Although disconnecting the internal drive is one way to guarantee Grub won't be installed to it, it is not necessary to do so, and in big_D131's case I think it would be highly inconvenient to disconnect the internal drive when the computer is a laptop. 

Big_D131, to install Grub to the MBR of your external drive, how about first opening a terminal (Applications > Accessories > Terminal) and then doing:
```
sudo grub
grub> find /boot/grub/stage1
```
The command above should return your main Ubuntu partition in the form of (hdX,Y) where X and Y are numbers, for example (hd1,0), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Please post the output of all the above commands, then reboot, set your BIOS to boot the external Ubuntu drive, and you should get the Grub menu. If that works OK, you can also restore a Windows equivalent MBR to your Vista drive by doing:
```
sudo lilo -M  /dev/sda mbr
```
And then when you boot the internal Vista drive, you should boot directly into Vista. How about giving the above steps a shot, and let me know how it goes or if you run into problems.

---

### Post by gn2 on 2008-12-28
> **caljohnsmith said:**
> Although disconnecting the internal drive is one way to guarantee Grub won't be installed to it, it is not necessary to do so, and in big_D131's case I think it would be highly inconvenient to disconnect the internal drive when the computer is a laptop. 

Much depends on the model of laptop.
On some laptops the hard drive is held in by just a single screw and is far easier to remove than a desktop PC hard drive, on many laptops it's easily accessed behind a removable panel.

---

### Post by big_D131 on 2008-12-28
caljohnsmith's solution worked perfectly
everything is now functional

Thanks a lot

---

### Post by caljohnsmith on 2008-12-28
Glad to hear that worked OK for you, big_D131; cheers and have fun with Ubuntu. :)

---

