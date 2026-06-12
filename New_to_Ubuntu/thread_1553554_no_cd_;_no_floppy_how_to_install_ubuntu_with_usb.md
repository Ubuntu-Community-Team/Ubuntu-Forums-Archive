---
title: "no cd ; no floppy: how to install ubuntu with usb?"
date: 2010-08-15
forum: New to Ubuntu
---

### Post by frenchn00b on 2010-08-15
no cd ; no floppy: how to install ubuntu on a pc i386 with usb pendrive?

---

### Post by jakupl on 2010-08-15
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by MrWES on 2010-08-15
> **frenchn00b said:**
> no cd ; no floppy: how to install ubuntu on a pc i386 with usb pendrive?

[http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/")


Used it many times on my family memeber's computers.:D


Bill

---

### Post by SpockVulcan on 2010-08-15
Linux: use Startup disc creator 
WIndows: PenDriveLinux
Mac: See here ([http://j.mp/bpElBX]("http://j.mp/bpElBX"))

---

### Post by frenchn00b on 2010-08-15
> **jakupl said:**
> [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

great so the solution is windows - based. 
[http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/](http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/)

great :(  We need windows to install linux on a pendrive :( so why linux then?
how can we do if we havent windows?

I try this solution... bit complicated
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

I wish we had a simple > dd if=imageubuntupendrive.img of=/dev/sdXX 

 
the method here [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)  is  hopeless complicated, ... 
> sudo apt-get install usb-creator needs a X11 even ... how can you do that with a linux live pendrive bootable damn small linux even?
 
So Ubuntu is simple and made for n00bs?

---

### Post by jakupl on 2010-08-15
> **frenchn00b said:**
> great so the solution is windows - based. 
[http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/](http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/)

great :(  We need windows to install linux on a pendrive :( so why linux then?
how can we do if we havent windows?

I try this solution... bit complicated
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

I wish we had a simple

You don't need windows. It just lists how to do it in windows. Look below the windows thing. It altso lists how to do it in linux and mac

---

### Post by davidmohammed on 2010-08-15
eh? - the [https://help.ubuntu.com/community/In...n/FromUSBStick](https://help.ubuntu.com/community/In...n/FromUSBStick) makes it clear that you can do this from linux...

---

### Post by frenchn00b on 2010-08-15
> **davidmohammed said:**
> eh? - the [https://help.ubuntu.com/community/In...n/FromUSBStick](https://help.ubuntu.com/community/In...n/FromUSBStick) makes it clear that you can do this from linux...

this is certainly not an Human Ubuntu  solution: 
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

far too complicated to be done, by a new guy arrivign to linux world.

---

### Post by snowpine on 2010-08-15
> **frenchn00b said:**
> this is certainly not an Human Ubuntu  solution: 
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

far too complicated to be done, by a new guy arrivign to linux world.

And yet we have new Ubuntu users every day on the forums, so clearly the instructions make sense to some people. ;)

---

### Post by jakupl on 2010-08-15
Is this really that complicated?

> The usb-creator utility can be installed using Synaptic Package Manager if not already present on your system. Some people have problems with usb-creator. You can also install and use UNetbootin to do the same thing.
Run usb-creator
Top pane, you will have to click "other", locate and select the ISO image
Plug the to-be-nuked USB stick into the computer, it should show up in the bottom pane titled "USB disk to use". (You may have to use GParted to format the USB Stick--I used 'ext3' as the format and it worked.)
Make sure you have the correct device selected before proceeding to create a USB startup disk!
There may be bugs during the formatting which will show up as two partitions when booting from the USB stick. Try selecting each of them and one should work. If not, restart the computer and try booting from the USB stick again.

---

