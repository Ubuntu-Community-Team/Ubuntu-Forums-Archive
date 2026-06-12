---
title: "Epson V 200 scanner"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by MZ250Supa5 on 2009-04-20
I have tried to set this scanner up as per various threads on the forum, but for some reason I can't get the bloomin' thing to work!  

I have the following output from Terminal after having followed Tanker Bob's instructions:

padi@padi-desktop:~$ sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04b8 [EPSON], product=0x012e [EPSON Scanner]) at libusb:005:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.
padi@padi-desktop:~$ scanimage -L
device `v4l:/dev/video0' is a Noname USB 2.0 Camera virtual device
padi@padi-desktop:~$ 

Any help would be very much appreciated.

---

### Post by MontelEdwards on 2009-05-06
> **MZ250Supa5 said:**
> I have tried to set this scanner up as per various threads on the forum, but for some reason I can't get the bloomin' thing to work!  

I have the following output from Terminal after having followed Tanker Bob's instructions:

padi@padi-desktop:~$ sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04b8 [EPSON], product=0x012e [EPSON Scanner]) at libusb:005:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.
padi@padi-desktop:~$ scanimage -L
device `v4l:/dev/video0' is a Noname USB 2.0 Camera virtual device
padi@padi-desktop:~$ 

Any help would be very much appreciated.
uh, this one got me.
*bump*

---

