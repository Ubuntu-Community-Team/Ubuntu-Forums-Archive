---
title: "Videocamera - USB does not work"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by j0natz on 2008-12-08
Hi, 

I'm having a video on my digital Videocamera (Panasonic NV-GS280) that I would like to copy/import to my 8.10 Ubuntu.

The camera is connected via USB.

How do I get started to copy? It always worked great on XP and their Moviemaker...

Best regards

Jonas

---

### Post by lisati on 2008-12-08
I'm not familiar with the GD280 model, but with the Panasoic NV-GS27 MiniDV camera I sometimes use, I've found that hooking up via firewire/i.link seems to work better than USB, and can be used with Kino under Linux.

---

### Post by j0natz on 2008-12-08
Hi, 

thanks for your fast reply. My problem is I do not have a cable for firewire. (I have one, but my Laptop has only a mini jack...

Any other options?

Best regards 

Jonas

---

### Post by scorp123 on 2008-12-08
> **j0natz said:**
>  My problem is I do not have a cable for firewire. (I have one, but my Laptop has only a mini jack... Get one from your local dealer. I am sure that Saturn and/or MediaMarkt stores have such cables. They just cost a couple of Euros. Once you got the cable copying stuff from the camera is very easy.

Read here ... this thread was about a Sony camera but what is said here should be true for any camera with a DV/i.Link/Firewire port (posting #19 and onwards ....):
[http://ubuntuforums.org/showthread.php?t=334024&page=2](http://ubuntuforums.org/showthread.php?t=334024&page=2)

---

### Post by j0natz on 2008-12-08
Allright so I'll get myself a cable.

Right now I'm again using Windows to copy it as it is a bit urgent :)

Thank you very much!

Best regards

Jonas

---

### Post by linux_tech on 2008-12-08
with camera plugged in post output of -
```
lsusb
```

---

### Post by j0natz on 2008-12-08
> **linux_tech said:**
> with camera plugged in post output of -
```
lsusb
```

here we go...

```

Bus 005 Device 017: ID 04da:231e Panasonic (Matsushita) DVC DV Stream Device
Bus 005 Device 008: ID 0b97:7762 O2 Micro, Inc. Oz776 SmartCard Reader
Bus 005 Device 007: ID 2101:020f ActionStar 
Bus 005 Device 006: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth
Bus 005 Device 005: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 005 Device 004: ID 413c:8116 Dell Computer Corp. Wireless 5505 Mobile Broadband (3G HSDPA) Minicard Modem
Bus 005 Device 003: ID 413c:0058 Dell Computer Corp. Port Replicator
Bus 005 Device 002: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by linux_tech on 2008-12-08
If your video software allows, try switching to ptp mode.  
Are you running any software to download video?
Normally camera software such as digicam allows you to switch modes, ptp, usb, etc which often helps getting digital cameras to work. 

If you install software (ie. Kino) it may help to get the camera to be seen.  Otherwise, trying a firewire cable instead may also work.
If you have a desktop and do not have a firewire port, you can add a firewire pci card.

---

### Post by j0natz on 2008-12-08
> **linux_tech said:**
> lsusb should show some thing like this-
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 04b0:0130 Nikon Corp. Coolpix 4600 
I don't see the Panasonic NV-GS280 camera on any of the usb. Is it plugged in?  It looks like the camera is not being recognized on usb.  
Are you running any software to download video?
Normally camera software such as digicam allows you to switch modes, ptp, usb, etc which often helps getting digital cameras to work. 

If you install software (ie. Kino) it may help to get the camera to be seen.  Otherwise, trying a firewire cable instead may also work.
If you have a desktop and do not have a firewire port, you can add a firewire pci card.

Hi, 

this "Bus 005 Device 017: ID 04da:231e Panasonic (Matsushita) DVC DV Stream Device" is the device.

It is recognized. But I cant tell Kino to rip from this source :(

---

### Post by linux_tech on 2008-12-08
Try ptp mode or firewire

---

### Post by j0natz on 2008-12-08
> **linux_tech said:**
> Try ptp mode or firewire

Sorry, ptp mode?

:)

---

### Post by scorp123 on 2008-12-08
> **linux_tech said:**
> Try ptp mode PTP = "_Picture_ Transfer Protocol" ...  Yeah right, that's gonna help with a **_video_** camera ....  ):P

---

### Post by scorp123 on 2008-12-08
> **j0natz said:**
> Sorry, ptp mode? :) He thinks you're using a digital photo camera. Newer digital photo cameras and printers should be capable to talk via "PTP" = "Picture Transfer Protocol" to each others ...

But that's not going to help here.

Video cameras work in a different way. And makers of video cameras usually keep their USB protocol proprietary, so there is hardly any video camera that works the same way when used via USB .... 

However: **Firewire**, **DV** or **i.Link** as it is called is a hardware standard: **IEEE1394**. Meaning that all devices that have such a port also talk via this protocol to each others.

Therefore your camera should work tip top with a Firewire cable and "kino" ... but trying to get this thing to work via USB is a waste of time. Sorry to say so.

---

