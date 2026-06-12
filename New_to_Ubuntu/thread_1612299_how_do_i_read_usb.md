---
title: "how do i read usb"
date: 2010-11-03
forum: New to Ubuntu
---

### Post by tbrownarcher on 2010-11-03
How do i get pictures off of a camera that is connected via usb?

I can't find the usp ports on a file manager or anything 


thanks
Nate

---

### Post by lisati on 2010-11-03
Cameras often appear as a disk drive on the "places" menu. On one of my cameras, I actually have to tell the camera to connect before my system will mount it.

---

### Post by tbrownarcher on 2010-11-03
this is a camera sd chip in a card reader ... it does not appear on the menu you referenced .. what else can i do ?... i had an mp3 player on it a while ago that also did not show in the menu.. 


thanks,
Nate

---

### Post by TNT1 on 2010-11-03
So, actually, the problem is with a card reader, not a usb connected device? Or is it a usb attached card reader?

---

### Post by tbrownarcher on 2010-11-03
Hmmmm !  well, the card reader is connecetd to a usb port via a cable as was the mp3 player .

I actually lost the usb cable for the camera so i take the card out of the camera, put it in a card reader and connect the card reader to a usb port..


thanks,
Nate

---

### Post by TNT1 on 2010-11-03
Ok, so connect it and post the output of ```
lsusb
```

---

### Post by tbrownarcher on 2010-11-03
here is the output you asked for ty 

nate@home2:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 03f0:4f11 Hewlett-Packard OfficeJet 5600 (USBHUB)
Bus 005 Device 002: ID 045e:00f9 Microsoft Corp. Wireless Desktop Receiver 3.1
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
nate@home2:~$ 



I don't see that my card reader is connected but it is. at least physicly.  I don't know which one it's on .



thanks,
Nate

---

### Post by TNT1 on 2010-11-03
> **tbrownarcher said:**
> 



I don't see that my card reader is connected but it is. at least physicly.  I don't know which one it's on .



thanks,
Nate

Yeah, it's not there.

post ```
dmesg | tail

```

---

### Post by tbrownarcher on 2010-11-03
results: dmesg \ tail

nate@home2:~$ dmesg | tail
[98869.536019] usb 7-1: new full speed USB device using uhci_hcd and address 2
[98870.064028] usb 7-1: device not accepting address 2, error -71
[98870.176019] usb 7-1: new full speed USB device using uhci_hcd and address 3
[98870.296023] usb 7-1: device descriptor read/64, error -71
[98870.520014] usb 7-1: device descriptor read/64, error -71
[98870.736021] usb 7-1: new full speed USB device using uhci_hcd and address 4
[98871.144016] usb 7-1: device not accepting address 4, error -71
[98871.256030] usb 7-1: new full speed USB device using uhci_hcd and address 5
[98871.664013] usb 7-1: device not accepting address 5, error -71
[98871.664036] hub 7-0:1.0: unable to enumerate USB device on port 1
nate@home2:~$ 

thanks again,
Nate

---

### Post by TNT1 on 2010-11-03
Ok, what hardware are you running, and does the card reader work on another machine?

---

### Post by tbrownarcher on 2010-11-03
my system is a desktop dell dimension 3000 and whatever was put in it ... 

I do not know what the specific hardware is .  The card reader is a dynex  it worked on this machine on the windows side.  Since I installed linux windows has not been accessable and i think it may be erased.  I know the card reader works though.  

thanks,

Nate

---

### Post by tbrownarcher on 2010-11-03
the usb is a card reader is a dynex
the computer is Dell Dimension 3000
     I don'tknow what the specific hardware is inside the computer except it originally
      has a 100 gig hard drive and i put a 300 gig hard drive in it along side of the   original

I know the card reader works in the windows side of this computer i have used it many times.  The mp3 also worked in windows.  However since i installed ubuntu into this computer the windows side has been unaccessable. 

thanks,
Nate


sorry for the similar posts .. did not realize it had began a new page so i thought it was lost and so i made a new one .. prolly a better one ... 

thanks again

---

### Post by TNT1 on 2010-11-03
[http://ubuntuforums.org/showthread.php?t=1308542&highlight=usb+card+reader&page=2](http://ubuntuforums.org/showthread.php?t=1308542&highlight=usb+card+reader&page=2)
Have a look at post #14, and check your BIOS settings as well.

---

### Post by tbrownarcher on 2012-08-16
the reader is a dynex 6-in-1 reader/writer.
it works on windows is all I know

thanks,
nate

---

