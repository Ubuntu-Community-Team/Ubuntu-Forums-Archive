---
title: "USB Issues"
date: 2009-05-31
forum: New to Ubuntu
---

### Post by ToucanSam on 2009-05-31
I am having some usb issues. It would be great if someone could offer some advice.

I mainly use two devices. An Ipod 5th generation (ipod photo) and a samsung printer. Both devices have worked before on this computer, on this  distribution (8.04).

Intermittently the printer shows on lsub and connects to the computer

```
@desktop:~$ lsusb
Bus 001 Device 002: ID 04e8:323a Samsung Electronics Co., Ltd ML-1710 Printer
Bus 001 Device 001: ID 0000:0000  

```

dmesg constantly spits out this when its working

> 
[  186.020782] usb 1-3: new full speed USB device using ohci_hcd and address 122
[  186.436347] usb 1-3: new full speed USB device using ohci_hcd and address 123
[  186.867890] usb 1-3: new full speed USB device using ohci_hcd and address 124
[  187.284460] usb 1-3: new full speed USB device using ohci_hcd and address 125
[  187.715004] usb 1-3: new full speed USB device using ohci_hcd and address 126
[  188.146551] usb 1-3: new full speed USB device using ohci_hcd and address 127
[  188.579104] usb 1-3: new full speed USB device using ohci_hcd and address 3
[  189.010165] usb 1-3: new full speed USB device using ohci_hcd and address 4
[  189.425210] usb 1-3: new full speed USB device using ohci_hcd and address 5


As you can see it goes to addr 127 and restarts

When its not working i get something like this a bunch of times:

>  
[ 3072.330748] usb 1-6: new full speed USB device using ohci_hcd and address 49
[ 3072.514555] usb 1-6: device descriptor read/64, error -62


I have tried. Modprobr -r ohci_hcd and that did not work. I tried disabling usb 2.0 in bios, didnt work.

This seems to happen alot. I get lucky on occasion and get the use of my printer, never my ipod. Anyone have any ideas what is happening? Need additional info?

---

### Post by durand on 2009-06-04
Maybe try the Hardware and Multimedia forums?
[http://ubuntuforums.org/forumdisplay.php?f=332](http://ubuntuforums.org/forumdisplay.php?f=332)
[http://ubuntuforums.org/forumdisplay.php?f=334](http://ubuntuforums.org/forumdisplay.php?f=334)

---

