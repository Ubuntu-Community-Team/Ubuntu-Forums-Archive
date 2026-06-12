---
title: "printer driver"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by ibbill on 2009-11-16
I have extracted pixma-0.4.5.tar.gz to my desktop and I now have see pic. on my desk top what command do I need to install the drive please.

Thanks Bill

---

### Post by halitech on 2009-11-16
what printer do you have? There may be an easier way then using the tar file

---

### Post by blazemore on 2009-11-16
Where did you get that file? Were there any instructions that go with it?

---

### Post by ukripper on 2009-11-16
> **ibbill said:**
> I have extracted pixma-0.4.5.tar.gz to my desktop and I now have see pic. on my desk top what command do I need to install the drive please.

Thanks Bill

Looks like you are using canon pixma printer. Can you post output of the following command in terminal:
```
lsusb
```

---

### Post by ibbill on 2009-11-16
hi thanks for the quick reply I have a pixma 160 Cannon.

9.04 installed automatically using the  Cannon 150 driver.

9.10 did not pick the printer up this time.

Bill

---

### Post by ukripper on 2009-11-16
are you using 64 bit or 32 bit 9.10?

---

### Post by halitech on 2009-11-16
there are drivers and info here on getting this printer installed

[http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP160_-_Canon_Drivers](http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP160_-_Canon_Drivers)

---

### Post by ibbill on 2009-11-16
> **ukripper said:**
> are you using 64 bit or 32 bit 9.10?

9.10 32 bit

---

### Post by ibbill on 2009-11-16
> **halitech said:**
> there are drivers and info here on getting this printer installed

[http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP160_-_Canon_Drivers](http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP160_-_Canon_Drivers)

Thanks looked there earlier its all Asia stuff.

---

### Post by ibbill on 2009-11-16
> **ukripper said:**
> Looks like you are using canon pixma printer. Can you post output of the following command in terminal:
```
lsusb
```

ibbill@ibbill-desktop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 15d9:0a37 Unknown Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 049f:000e Compaq Computer Corp. Internet Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by ukripper on 2009-11-16
> **ibbill said:**
> ibbill@ibbill-desktop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 15d9:0a37 Unknown Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 049f:000e Compaq Computer Corp. Internet Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

can you attach your printer and then do the lsusb again. And turn your printer on.

---

### Post by ibbill on 2009-11-16
> **ukripper said:**
> can you attach your printer and then do the lsusb again. And turn your printer on.

Okay now this is just great  lol thanks again to all for your help and thanks for being here.

Removed the usb connection and inserted in another slot the 9.10 system picked up the printer and installed it:p

Looks like I have a dud usb port or who knows going to try another item in that port.

Thanks to all again.Marking solved

Bill

---

### Post by ukripper on 2009-11-16
> **ibbill said:**
> Okay now this is just great  lol thanks again to all for your help and thanks for being here.

Removed the usb connection and inserted in another slot the 9.10 system picked up the printer and installed it:p

Looks like I have a dud usb port or who knows going to try another item in that port.

Thanks to all again.Marking solved

Bill

i m glad it worked out for you. No wonder i couldn't see your printer in your lsusb output. Thought it was turned off!

---

### Post by ibbill on 2009-11-16
saving that code for future references thanks again.

Bill

---

### Post by halitech on 2009-11-16
> **ibbill said:**
> Thanks looked there earlier its all Asia stuff.

I see you got it fixed up but just wanted to let you know that Canon is one of those companies that only seems to support Linux overseas so thats where you can find the drivers if you need them in the future.

---

### Post by ukripper on 2009-11-16
i have got canon pixma mp210. It works great on ubuntu 64bit even the scanner works with the drivers provided by canon. I really like canon for that.

---

