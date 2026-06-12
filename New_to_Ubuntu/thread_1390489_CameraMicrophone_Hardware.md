---
title: "Camera/Microphone Hardware"
date: 2010-01-25
forum: New to Ubuntu
---

### Post by carlierae1123 on 2010-01-25
Hi,

I'm trying to rid my dependency on Windows and downloaded the Skype Beta for Linux.  However, I cannot seem to use my webcam/microphone with it.  Video sends just fine, the other person can see me, but I'm apparently completely mute to them.  I've gone through all the volume settings and put everything to max to see if it made a difference, and nothing has yet.  I'm using a Logitech camera (don't know exactly what model).  Is there some sort of driver I need to download to get the microphone working, or what?

Thanks for your help,
Carlie

---

### Post by Sealbhach on 2010-01-25
It may be that there is no driver for it, or that you need to download one from somewhere. Is it a USB webcam? If so, enter

```
lsusb
```

in the terminal and copy and paste the result here. It should give us some information about your webcam.

.

---

### Post by carlierae1123 on 2010-01-25
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

thats what i got for lsusb
yes it is a USB webcam

---

### Post by Sealbhach on 2010-01-25
It looks like it's not being detected by the OS, yet you say video works OK. Try booting up with the webcam attached, then run dmesg in a terminal

```
dmesg | grep USB
```Also, please look at the webcam, see if you can get the model number or product code, so then you can search on Google about it. Are you using Karmic?

.

---

### Post by Wataru8675 on 2010-01-25
Hi, I'm Carlie's friend.  I've been working on this with her.

I did some research and found she has a Logitech C200 webcam.  The only drivers I could find on the site are for either XP, Vista, or 7.  I then stumbled on this article:

[https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

It says the C200 needs to sound set up, but doesn't say how, so this must mean it's a driver issue (or something similar).

Should I be looking for an Ubuntu-specific driver, or can we use Wine or something to install the Windows drivers?

---

### Post by carlierae1123 on 2010-01-25
[    2.130401] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.130523] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    2.148009] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.148127] hub 1-0:1.0: USB hub found
[    2.148260] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.148277] uhci_hcd: USB Universal Host Controller Interface driver
[    2.148350] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.148478] hub 2-0:1.0: USB hub found
[    2.148621] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    2.148758] hub 3-0:1.0: USB hub found
[    2.148903] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    2.149053] hub 4-0:1.0: USB hub found
[    2.149206] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    2.149336] hub 5-0:1.0: USB hub found
[    2.460015] usb 1-8: new high speed USB device using ehci_hcd and address 2
[   11.755894] USB Video Class driver (v0.1.0)

that is what i got after doing  dmesg | grep USB

---

### Post by Wataru8675 on 2010-01-25
Bump.  We found this:

[http://ubuntuforums.org/showthread.php?t=1342189](http://ubuntuforums.org/showthread.php?t=1342189)

But now we can't get ******* Pulse to ******* work.  Is there any other way?

---

### Post by nmyrick on 2010-01-25
I was just working on my Acer laptop, and I had trouble getting my microphone to work, and this is what finally worked for me.

Open Pulse Audio Volume control, then go to the Configuration tab, then select Analog Stereo Duplex.  

This allows for both your speakers and your micorphone to work at the same time.  It seems pretty stupid that this is not the default, but the default is Analog Stereo Output; which only allows your speakers to work and turns off your microphone.

---

