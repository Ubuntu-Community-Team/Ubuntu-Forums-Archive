---
title: "Installing USB Components"
date: 2009-07-22
forum: New to Ubuntu
---

### Post by B16MCC on 2009-07-22
Hi guys here's my first post. I'm learning Ubuntu and Linux for the first time at the moment and picking things up ok so far. I have it running on a standalone PC but that's not networked yet because of where it is. I'll get a cable run in hopefully this weekend. Until then I'm also running it in a VM on my MAC.  I've setup FTP access and telnet access and thats working fine.

I'm looking at installing a USB smartcard reader and I'm having a little trouble setting up the prerequisites required. Could anyone help me out with this please.

The reader is an Omnikey 3121 PCSC smartcard reader. The driver readme is as follows.

------------------------------
 What you need
------------------------------

[1] Kernel with USB support either compiled in or as modules

[2] Mounted /usbfs (/usbdevfs)
    For more detailed informations see [http://www.linux-usb.org/](http://www.linux-usb.org/)

[3] libusb >= Version 0.1.12 available at
    [http://libusb.sourceforge.net/](http://libusb.sourceforge.net/)

[4] PCSCLite >= Version 1.4.102 available at 
    [http://www.linuxnet.com/](http://www.linuxnet.com/) 
      and/or 
    [http://alioth.debian.org/projects/pcsclite/](http://alioth.debian.org/projects/pcsclite/)

[5] In order to use new SCardControl-API use PCSCLite > 1.3.2

[6] This driver supports our CT-API and our Synchronous API.
    So, if you like to use one of them, you must download
    the API in question from [www.omnikey.com]("http://www.omnikey.com").

Could anyone help me get this setup please.
Many thanks
B16MCC.

---

### Post by Stebalien on 2009-07-22
Conditions 1, 3, 4, and 5 are satisfied in the default ubuntu setup.
Condition 2 can be satisfied by running: ```
sudo mount -t usbfs none /proc/bus/usb
```
To make condition 2 permanent, add: ```
none  /proc/bus/usb  usbfs  defaults  0  0
``` to your /etc/fstab
Also, have a look at [this]("http://ubuntuforums.org/showthread.php?t=894566") thread.

I can not help with condition 6 but hopefully someone else can.

---

### Post by sandyd on 2009-07-22
nvm

---

