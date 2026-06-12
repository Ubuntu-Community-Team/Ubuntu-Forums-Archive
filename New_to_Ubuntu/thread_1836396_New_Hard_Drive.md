---
title: "New Hard Drive"
date: 2011-08-31
forum: New to Ubuntu
---

### Post by tb75252 on 2011-08-31
I am using Ubuntu 11.04, 32-bit, with GNOME.

I just bought a brand-new, unformatted internal hard drive.  I hooked it up to an external HD enclosure (USB 2.0 interface) and then started up Ubuntu with the intention of formatting the drive.

But Ubuntu would not see it!  System -> Administration -> Disk Utility would not show the drive.

So I started up Windows 7, an icon appeared automatically in the System Tray informing me that a device driver was being installed and then another message informed me that the drive was ready to be used.  (I guess it did some sort of initialization of the drive.)  A quick check showed that indeed Windows could see the drive.  (At this point the HD is still not formatted but the initialization that Windows did automatically was enough for the operating system to be aware of the drive.)

I then booted up Ubuntu and Disk Utility now shows the hard drive too...

So, what exactly do I need to do in Ubuntu next time when I need to initialize a brand-new, unformatted hard drive?  I certainly would like to avoid having to go through Windows 7 again...

Thanks.

---

### Post by fdrake on 2011-08-31
> **tb75252 said:**
> I am using Ubuntu 11.04, 32-bit, with GNOME.

I just bought a brand-new, unformatted internal hard drive.  I hooked it up to an external HD enclosure (USB 2.0 interface) and then started up Ubuntu with the intention of formatting the drive.

But Ubuntu would not see it!  System -> Administration -> Disk Utility would not show the drive.

So I started up Windows 7, an icon appeared automatically in the System Tray informing me that a device driver was being installed and then another message informed me that the drive was ready to be used.  (I guess it did some sort of initialization of the drive.)  A quick check showed that indeed Windows could see the drive.  (At this point the HD is still not formatted but the initialization that Windows did automatically was enough for the operating system to be aware of the drive.)

I then booted up Ubuntu and Disk Utility now shows the hard drive too...

So, what exactly do I need to do in Ubuntu next time when I need to initialize a brand-new, unformatted hard drive?  I certainly would like to avoid having to go through Windows 7 again...

Thanks.

you can run command like :
```

sudo lsusb -v #if your usb hdd is being recognized or is ready to be used
sudo fdisk -l # to see the mass storage of the device names

```

 i do not know why disk utility did not work... however..  . Does your usb-drive has its own AC power cable or it uses the usb to power up? using the usb to power-up a device is a problem sometimes.

---

### Post by jtarin on 2011-08-31
[http://www.thelinuxpimp.com/main/node/561](http://www.thelinuxpimp.com/main/node/561)

---

