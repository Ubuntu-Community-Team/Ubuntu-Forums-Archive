---
title: "Scanning"
date: 2010-08-06
forum: New to Ubuntu
---

### Post by muralysunam on 2010-08-06
I am using ubuntu 9.10. I can't scan with my scanner asus s2w 3300 u, which is a flatbed 22". I had read the conversation as shown in this link. [http://ubuntuforums.org/showthread.php?t=469756](http://ubuntuforums.org/showthread.php?t=469756).
As there advice i type command 
sane-find-scanner
I got a message given below

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04a5, product=0x20b0) at libusb:002:104
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

then i typed the command given below

scanimage -L

then it shows
WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

then I downloaded the file which is shown in that link, and copied the file u96v121.bin to the respective location. But I don't get scanner scanned. Then as the advice of [FreewheelinFrank]("http://ubuntuforums.org/member.php?u=377793") in that conversation, I changed that file to u222v067.bin. But it didn't helped me. Firstly I got a message when opening xsane scanner program is

scanner not found

I got the same message. I don't remember exactly when but I got an error message like  the device can' t be accessed or some thing like that.

Please help me. I am a student studying in Diploma in India.

---

### Post by corrytonapple on 2010-08-06
First go to **System>Administration>Hardware Drivers** and look for your driver. Did your printer come with an install disc? Second, if you give output of code, do it like this: {CODE}Code goes here {/CODE} (But instead of { } put [ ]).

---

