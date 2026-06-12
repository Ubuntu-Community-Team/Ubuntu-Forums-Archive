---
title: "Can't install Epson EPL-6200L printer"
date: 2011-07-04
forum: New to Ubuntu
---

### Post by EVILCOOKIE on 2011-07-04
Hello, everyone. I'm having trouble installing my Epson EPL-6200L printer. I've downloaded the epsonepl 0.4.1 driver and followed the instructions detailed [in this post]("http://ubuntuforums.org/showpost.php?p=9758051&postcount=4")  but it's no use.

The driver also includes a PPD file for my printer but when I try adding my printer using that PPD I get:
```
Failed to read PPD file. Possible reason follows:
/home/andrew/Downloads/Epson/epsoneplijs-0.4.1/
foomatic_PPDs/Epson-EPL-6200L-epl6200l-cups.ppd.gz: FAIL
**FAIL** Unable to open PPD file - line longer than the maximum allowed (255 characters) on line 202.
REF: Page 15, section 3.1.
WARN  Line 44 only contains whitespace!
```If I understood correctly, there's too long a line in the file. I could edit it, but I don't know how. I've also tried with earlier versions of the driver (0.4.0) but I get the same prompt.

The offending line looks like this:
```
*% COMDATA #  'cmd' => 'gs -q -dBATCH -dSAFER -dNOPAUSE -sProcessColorModel=DeviceGray -dBitsPerSample=1 -sDEVICE=ijs %A %Z -sIjsServer=ijs_server_epsonepl -dIjsUseOutputFD -sDeviceManufacturer=Epson -sDeviceModel=EPL6200L -sIjsParams="%B" -sOutputFile=- -',
```Please help me, I'm a new 11.04 x64 user.

---

### Post by EVILCOOKIE on 2011-07-08
Bump. Any help? Sorry for double-posting.

---

### Post by EVILCOOKIE on 2011-08-06
Please help me. I don't know what to do. Sorry for bumping but I still couldn't get it working.

EDIT: I could finally get it to work following the instructions in [http://ubuntuforums.org/showpost.php?p=4932980&postcount=3](http://ubuntuforums.org/showpost.php?p=4932980&postcount=3) and using this PPD [http://www.nemesys.fi/tiedostot/ubuntu/EPL-6200L-Hardy.ppd](http://www.nemesys.fi/tiedostot/ubuntu/EPL-6200L-Hardy.ppd)

---

### Post by crott on 2012-02-06
Thank you for this, Sir! ;-) I've been out of the printer for the months now! 
BIG thanks!

---

