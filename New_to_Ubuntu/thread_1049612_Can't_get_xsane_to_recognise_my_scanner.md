---
title: "Can't get xsane to recognise my scanner"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by mrwaistcoat on 2009-01-24
I've got an "all in one" Epson DX7400,  which works as a printer fine.

I've followed every thread I can find re getting the scanner to work, and have installed "pipslite" - but no joy.

And ideas ?

From other threads, I know it is possible for this scanner to work

Thanks

---

### Post by Peter09 on 2009-01-24
what does sane-find-scanner show?

---

### Post by mrwaistcoat on 2009-01-25
Cheers Peter.  I get


# sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

---

### Post by Peter09 on 2009-01-25
Try running this with sudo

```
sudo sane-find-scanner
```

if it sees your scanner then, its a permission problem.

---

### Post by mrwaistcoat on 2009-01-25
Thanks again Peter, now I get

found USB scanner (vendor=0x04b8, product=0x0838) at libusb:001:004
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

And then

scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

---

### Post by Peter09 on 2009-01-26
Check that your user is in the 'scanners' group.

System->Admin->Users and Groups

---

### Post by mrwaistcoat on 2009-01-26
Thanks Peter.   I have now added myself in users to the scanners group

I now get

sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04b8, product=0x0838) at libusb:001:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

~$ scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

---

### Post by bwang on 2009-01-26
Try this site: [http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do)
The drivers don't seem to be SANE drivers, but at least you'll be able to scan.

---

### Post by mrwaistcoat on 2009-01-27
I had already found this site and installed the package prior to posting - but still the scanner doesn't work!  This is confusing me, as the avasys site specifically lists my all in one as being supported!

Is xsane the only scanner application in Ubuntu ?

Anything else I can try ?

My best guess is that I have incorrectly installed the driver from avasys

Cheers

---

### Post by Peter09 on 2009-01-27
Try running scanimage with sudo. You may get some dire warnings, but proceed just to test it.

---

### Post by bwang on 2009-01-27
It seems like the pipslite package installs another program. Try running pipslite from the Terminal.

---

### Post by herdivet on 2009-01-28
> **mrwaistcoat said:**
> I had already found this site and installed the package prior to posting - but still the scanner doesn't work!  This is confusing me, as the avasys site specifically lists my all in one as being supported!

Is xsane the only scanner application in Ubuntu ?

Anything else I can try ?

My best guess is that I have incorrectly installed the driver from avasys

Cheers

I used the following instructions to install the V200 Scanner in 8.10:

[http://ubuntuguide.org/wiki/Dapper#Install_the_correct_drivers:_Epson_Perfection_V200_Photo_example](http://ubuntuguide.org/wiki/Dapper#Install_the_correct_drivers:_Epson_Perfection_V200_Photo_example)

I then added 'epkowa' to /etc/sane.d/dll.conf 

That had it working, except I always had to use sudo with scanimage -L or gksudo xsane.  I edited /etc/udev/rules.d/45-libsane.rules and changed 664 to 666 and then could scan without using sudo.  This fixed the problem that adding myself to the scanner group didn't.  

Hope this provides some help.

---

### Post by mrwaistcoat on 2009-01-28
Tried this, just says no sane device found

Thanks

---

### Post by mrwaistcoat on 2009-02-01
How do I run Pipslite from the terminal ? 


I've found this below re the dx7400 - could anyone tell me from below what exactley I need to put into terminal ?



Scanning works with SANE using "epson" backend. You may need to specify deviceid 0x0838 in /etc/sane.d/epson.conf. Also, add udev rule in /etc/udev/rules.d/45-libsane.rules: # Epson Corp.|Stylus DX7400 SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0838", MODE="664", GROUP="scanner"

---

### Post by gsocker on 2009-02-01
Actually, you probably want to use the "epson2" backend as the "epson" one is unmaintained. According to the SANE website, your scanner is supported by both.
Have you tried the suggestion to run scanimage as root via sudo? If this works, then the scanner is working, and we just need to get the permissions fixed. 

Did you logout and back in after adding yourself to the "scanners" group? If not, do so as the change will not take effect until you login again.

---

### Post by mrwaistcoat on 2009-02-01
> **gsocker said:**
> Actually, you probably want to use the "epson2" backend as the "epson" one is unmaintained. According to the SANE website, your scanner is supported by both.
Have you tried the suggestion to run scanimage as root via sudo? If this works, then the scanner is working, and we just need to get the permissions fixed. 

Did you logout and back in after adding yourself to the "scanners" group? If not, do so as the change will not take effect until you login again.


Yes, I've logged out.  As for scanimage, I get the message no sane device installed.  I typed "sudo scanimage" into terminal - is this right ?

---

### Post by gsocker on 2009-02-01
> I typed "sudo scanimage" into terminal - is this right ?
Yes, this is correct.
To answer your question about xsane: xsane is not the only scanner GUI, however almost all scanning programs use SANE libraries to talk to the scanner. It's basically the linux equivalent of TWAIN.
Your scanner should be working fine, as Epson scanners and printers are well-supported under Linux and it's listed as supported at the SANE website.
 Let's try adding the usb id to the epson2 config file.
Fire up your editor of choice as root:
```
sudo gedit
``` will work well, and open up /etc/sane.d/epson2.conf
Look for ```

# USB
usb

# For libusb support for unknown scanners use the following command
# usb <product ID> <device ID>
# e.g.:
# usb 0x4b8 0x110

```
and add your scanner's usb ids to it
```
usb 0x4b8 0x838
```
Save the file, then exit.
Run scanimage as root again and see if it finds your scanner.

---

### Post by mrwaistcoat on 2009-02-02
> **gsocker said:**
> Yes, this is correct.
To answer your question about xsane: xsane is not the only scanner GUI, however almost all scanning programs use SANE libraries to talk to the scanner. It's basically the linux equivalent of TWAIN.
Your scanner should be working fine, as Epson scanners and printers are well-supported under Linux and it's listed as supported at the SANE website.
 Let's try adding the usb id to the epson2 config file.
Fire up your editor of choice as root:
```
sudo gedit
``` will work well, and open up /etc/sane.d/epson2.conf
Look for ```

# USB
usb

# For libusb support for unknown scanners use the following command
# usb <product ID> <device ID>
# e.g.:
# usb 0x4b8 0x110

```
and add your scanner's usb ids to it
```
usb 0x4b8 0x838
```
Save the file, then exit.
Run scanimage as root again and see if it finds your scanner.

Sorry mate - this is probably just me being thick....

but when I open sudo gedit it opens a document - is this right ?

When you say "open up /etc/sane.d/epson2.conf" - what exactley do I do ? Is this a terminal command ?

---

### Post by gsocker on 2009-02-02
gedit is just a text editor. Use file/open as in most other GUI programs to open /etc/sane.d/epson2.conf .

---

### Post by gsocker on 2009-02-02
If you're coming from a windows background, it may seem strange to be editing text files. Most system configuration in Linux is done via text files. There is no Windows Registry equivalent, and no "regedit" program to change everything in one location.

---

### Post by sleepingdragon on 2009-02-02
have you tried to install the *libsane-extras* from the repos? That was the only way I could detect my DX8400.

---

### Post by mrwaistcoat on 2009-02-04
Thanks.  This is what I get when i open Epson2 - what do I do next ?  Thanks again.



# epson2.conf
#
# here are some examples for how to configure the EPSON2 backend

# SCSI
scsi EPSON
# for the GT-6500:
#scsi "EPSON SC"

# Parallel port
#pio 0x278
#pio 0x378
#pio 0x3BC

# USB
usb

# For libusb support for unknown scanners use the following command
# usb <product ID> <device ID>
# e.g.:
# usb 0x4b8 0x110

# Network
# 
# net 192.168.1.123
net autodiscovery

---

### Post by gsocker on 2009-02-04
Edit the file to look like this(change the bold line):
```
# epson2.conf
 #
 # here are some examples for how to configure the EPSON2 backend
 
 # SCSI
 scsi EPSON
 # for the GT-6500:
 #scsi "EPSON SC"
 
 # Parallel port
 #pio 0x278
 #pio 0x378
 #pio 0x3BC
 
 # USB
 **usb 0x4b8 0x838**
 
 # For libusb support for unknown scanners use the following command
 # usb <product ID> <device ID>
 # e.g.:
 # usb 0x4b8 0x110
 
 # Network
 # 
 # net 192.168.1.123
 net autodiscovery
```
Save, then try running sudo scanimage and see if it finds it.

---

### Post by mrwaistcoat on 2009-02-05
I get an error message when I try to save - it sais I don't have the necessary permissions to change epson2

---

### Post by mrwaistcoat on 2009-02-05
Aha, realised I needed to open with sudo gedit first !  

The good news is I have now saved successfully...

....the bad news is the scanner still isn't working !


Any ideas very welcome !!

---

### Post by mrwaistcoat on 2009-02-05
I have found this

 [http://forum.ubuntu-it.org/index.php?topic=142737.msg951555](http://forum.ubuntu-it.org/index.php?topic=142737.msg951555)

Which is an Italian guide to installing my scanner.  It must be possible

I've tried to follow it as best I can but obviously, it still isn't working!

---

### Post by gsocker on 2009-02-05
You are running scanimage via sudo, right? If so, and it still doesn't work, your best is probably  the SANE project's mailing lists at [http://www.sane-project.org/mailing-lists.html](http://www.sane-project.org/mailing-lists.html) 
These are the people that develop the scanner software.

---

### Post by efalk on 2009-03-25
> **gsocker said:**
> Actually, you probably want to use the "epson2" backend as the "epson" one is unmaintained.

How do you switch?

I'm having similar problems, but they're clearly related to permissions, and not backend versions.

My situation:

Ubuntu 8.04

Epson 2400

Sometimes it works, sometimes it didn't.  It worked last week, and now it doesn't.  I have not rebooted, logged out, or anything else.  I have turned the scanner off and on again.

Running as root, sane-find-scanner and scanimage -L both see the scanner just fine.

Running as me, sane-find-scanner finds the scanner and scanimage -L does not.  I am in the scanner group and have been all along.

When the scanner is turned on, three new entries are created in /dev: /dev/usbdev2.7_ep{00,02,81}.  Ownership is root.root and permissions are 660.  Changing permissions or ownership of these files does not help.

This used to work.  Now it doesn't.  I have changed absolutely nothing.  I haven't even logged out since it worked last week.

(<frustration>Will Linux *ever* understand hot-plugging?</frustration>)

---

### Post by gsocker on 2009-03-27
Libusb uses the files in /dev/bus/usb. These are the files you need to check permissions on, not /dev/usdevep*.

I have the same scanner. Here is what the permissions show:
Line with scanner is in bold. 
```

ls -lR /dev/bus/usb
/dev/bus/usb:
total 0
drwxr-xr-x 2 root root 200 2009-03-27 20:40 001
drwxr-xr-x 2 root root 100 2009-03-27 07:09 002

/dev/bus/usb/001:
total 0
crw-rw-r-- 1 root usb     189, 0 2009-03-27 07:09 001
crw-rw-r-- 1 root usb     189, 3 2009-03-27 07:09 004
crw-rw-r-- 1 root usb     189, 4 2009-03-27 07:09 005
crw-rw-r-- 1 root usb     189, 5 2009-03-27 20:53 006
crw-rw-r-- 1 root usb     189, 6 2009-03-27 07:09 007
crw-rw-r-- 1 root usb     189, 7 2009-03-27 07:09 008
crw-rw-r-- 1 root usb     189, 8 2009-03-27 07:09 009
**crw-rw-r-- 1 root scanner 189, 9 2009-03-27 20:43 010**

/dev/bus/usb/002:
total 0
crw-rw-r-- 1 root usb 189, 128 2009-03-27 07:09 001
crw-rw-r-- 1 root usb 189, 129 2009-03-27 07:09 002
crw-rw-r-- 1 root usb 189, 130 2009-03-27 07:09 003

```
Note: this is on a Gentoo system, but Ubuntu should be the same.
Works perfectly here, no idea why it would stop working suddenly.

---

### Post by efalk on 2009-03-28
Thanks; I'll check it out.

(Now, if I could only get the system to reliably recognize when I've plugged in a CF card.)

---

### Post by efalk on 2009-04-06
Hi; just a follow-on.  sane-find-scanner told me which /dev/bus/usb device was the one, and "chgrp scanner /dev/bus/usb/002/008" fixed the problem (at least temporarily.)

The question still remains as to why the hotplug system didn't do this automatically (when it obviously used to), but at least I know how to fix it when it happens again.

---

### Post by deathlok on 2009-05-12
same scanner same problem. Could you be more specific how you fix it? I am an newbie so your last post does not make any sense to me.

---

