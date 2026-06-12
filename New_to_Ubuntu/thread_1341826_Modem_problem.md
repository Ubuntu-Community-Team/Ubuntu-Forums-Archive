---
title: "Modem problem"
date: 2009-11-30
forum: New to Ubuntu
---

### Post by attchibhatt on 2009-11-30
Absolute Beginner, french, living in india,
I'm really interested to join Ubuntu (version 9.04 (jaunty) 2.6.28.15.generic gnome 2.26.1 on Asus laptop and : memory 2,9 gio ; 2 Processors O & 1 : intel (R) ; core (TM) 2duo CPU T5870@2.00GHZ
But only windows vista is responding when I plug a stick modem huawei EC121 through RELIANCE network cause only this is working in my valley
Windows install the CD driver withouth problem ; Ubunto give always this message without even detecting any usb plugged:
"[/media/cdrom0/Mobile Partner/Setup.exe]
End-of-central-directory signature not found. Either this file is not
a zipfile, or it constitutes one disk of a multi-part archive. In the
latter case the central directory and zipfile comment will be found on
the last disk(s) of this archive.
note: /media/cdrom0/Mobile Partner/Setup.exe may be a plain executable, not an archive
zipinfo: cannot find zipfile directory in one of /media/cdrom0/Mobile Partner/Setup.exe or
/media/cdrom0/Mobile Partner/Setup.exe.zip, and cannot find /media/cdrom0/Mobile Partner/Setup.exe.ZIP, period."
 
. [/ Quote]

---

### Post by Perfect Storm on 2009-11-30
post moved to Absolute Beginner Talk forum.

---

### Post by lkraemer on 2009-12-01
You can't insert a Windows CD with drivers for some modem and expect
Ubuntu to read, Install, and make your device functional, by executing
some setup file that is designed for Windows.  

Having said that, there are commands that will help you determine if
Linux detects the device, and ways to use the Windows Drivers to make
a Device function.

BEFORE PLUGGING IN YOUR DEVICE:
In a terminal Window: (copy and paste these commands to find out more information on your device)
lspci
lsusb
dmesg | tail
 
PLUG IN YOUR USB MODEM: (wait 15 seconds)
lspci
lsusb
dmesg | tail

Notice any differences?  Was the device detected?

Post your results.

lk

---

