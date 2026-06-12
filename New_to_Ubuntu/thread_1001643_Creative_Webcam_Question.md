---
title: "Creative Webcam Question"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by Zenmij on 2008-12-04
I am using 8.04 and have connected my webcam. On entering lsusb -v in terminal I get:

```
Bus 004 Device 007: ID 041e:4039 Creative Technology, Ltd 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x041e Creative Technology, Ltd
  idProduct          0x4039 
  bcdDevice            1.02
  iManufacturer           0 
  iProduct                1 
  iSerial                 0 
  bNumConfigurations      1

```

but when entering dmesg after connecting my Creative Live! cam, all I see is:
```

[ 4911.582572] usb 4-3: new high speed USB device using ehci_hcd and address 7
[ 4911.765946] usb 4-3: configuration #1 chosen from 1 choice
```

no more than that, which doesn't seem particularly hopeful. No v4l mentions and no /dev/video to check to see if anything is loaded  (Ekiga also has nothing in video devices listed for my cam). 

Is it my rudimentary understanding that, although 041e:4039 is visibly connected, it is not recognised by any modules? Which means it isn't supported?

For clarity, it is a Creative Live! Effects

I have just compiled the gspca code and after sudo modprobe gspca it is now running, the spca5xx was kinda my last resort but will keep looking

---

### Post by Zenmij on 2008-12-05
Well after a little more digging it appears there exists no support for this particular cam.

The same gspca module that works for Live! will not work for Live! Effects possibly because it uses a different bridge(!)

There exists something in development here that could work:

Reading this post: [HTML]http://osdir.com/ml/linux.drivers.spca50x.devel/2007-11/msg00040.html[/HTML]

it seems some work is in development. I'll wait and see.

---

