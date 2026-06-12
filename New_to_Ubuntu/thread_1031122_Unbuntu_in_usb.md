---
title: "Unbuntu in usb"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by sajixavier on 2009-01-05
Hi
i have doubt. If i install ubuntu directly to a pendrive, will it run on any machine. any machine with different processors(dual)...is there any way to make it run on any pc...

i tried creating ubuntu live usb from the menu..when i tried to plugin another machine, it didn't detect the sata hard disk....

---

### Post by Den_Citronen on 2009-01-05
The first requirement is that the computer can boot from USB, one of mine can't. I suppose it'd run on any computer using the same architecture (32-bit PC (x86), 64-bit PC (amd64) etc.). Drivers sure has something to do with it too, however, I'll refer to someone else to answer that one.

---

### Post by iaculallad on 2009-01-05
Try using [Unetbootin]("http://lubi.sourceforge.net/unetbootin.html") to create a bootable USB drive, and, be sure that you have a mobo which supports booting from USB.

---

### Post by Kevbert on 2009-01-05
You need to make sure the USB drive is persistent (that it saves information to the USB all at once rather than as it goes). A good source of info is [[COLOR="Red"]pendrivelinux[/COLOR]]("http://www.pendrivelinux.com/ubuntu-810-persistent-flash-drive-install-from-live-cd/"). It may be worth using the Hardy Heron version which is [[COLOR="Red"]here[/COLOR]]("http://www.pendrivelinux.com/usb-xubuntu-804-persistent-install-from-linux/") as it supports floppy drives and ntfs (windows drives) by default - no tweaking required. 
As mentioned before some PC will not boot from USB. 
The next problems are wireless internet and display adapters. Only a few adapters are supported by default and so it may mean you need to install new drivers as you go (for example Broadcom wireless, but this is improving and Nvidia graphics - both of these are normally installed as restricted extras). At least with graphics you should be able to boot into a low resolution mode and not the full capability of the graphics adapter.

---

### Post by tarps87 on 2009-01-05
If you are using Intrepid or have the Intrepid cd you can install a gui to create a live usb. It is called usb-creator, this should install it:
```

sudo apt-get install usb-creator

```
If not it will be in synaptic, this program will allow you to create a persistent live usb so it will store your data and also allow you to install Ubuntu from it.
I would suggest using the 32 bit version as this will run on 32 and 64 bit machines where as the 64 bit version will only run on a 64 bit machine

---

### Post by theozzlives on 2009-01-05
In theory yes. But all computers are different and may be picky about the drivers  your using. I suggest a generic install (similar to the live CD) but persistent.

---

