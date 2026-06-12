---
title: "Format usb flash drives in FAT32 using Ubuntu 10.10"
date: 2011-07-19
forum: New to Ubuntu
---

### Post by Advait on 2011-07-19
Hi All,

For security reasons, I want to Fat32 format some of my thumb drives using my Ubuntu 10.10. Is there a step-by-step guide somewhere to doing this? I'm not very good at downloading and installing files in Ubuntu. It seems pretty complicated to download and install files in Ubuntu. I'm a beginner.

Please be gentle! I need step-by-step instructions. I'm new with Ubuntu. Thanks!

Cheers,

Tom

---

### Post by jerrrys on 2011-07-20
to format a thumb drive go to:

System>Administration>DiskUtility>FormatVolume or FormatDrive

be sure you are on your thumb drive.  it should be on left side of window and keep in mind that formatting will erase all data on that drive.

for downloading software, just use the software center.  are you having trouble downloading something?

---

### Post by Bodsda on 2011-07-20
> **Advait said:**
> Hi All,
 
For security reasons, I want to Fat32 format some of my thumb drives using my Ubuntu 10.10. Is there a step-by-step guide somewhere to doing this? I'm not very good at downloading and installing files in Ubuntu. It seems pretty complicated to download and install files in Ubuntu. I'm a beginner.
 
Please be gentle! I need step-by-step instructions. I'm new with Ubuntu. Thanks!
 
Cheers,
 
Tom
 
Funny, Fat32, and security, don't really go in the same sentence very well... If you are after a secure file system for use on windows, you should use ntfs. If you are trying to wipe the data on the thumb drives, you will probably want to use dd or shred. In either case, if you want more info, let me know.
 
If it was just formatting to Fat32, then jerrrys' suggestion should suffuce, or you can use gparted.
 
HTH,
Bodsda

---

### Post by Advait on 2011-07-28
> **jerrrys said:**
> to format a thumb drive go to:

System>Administration>DiskUtility>FormatVolume or FormatDrive

be sure you are on your thumb drive.  it should be on left side of window and keep in mind that formatting will erase all data on that drive.

for downloading software, just use the software center.  are you having trouble downloading something?
Hello jerrys,

Thanks for the instructions. When I try to format the thumb drive in Ubuntu it lays "Device busy." I have no idea what's keeping it busy. See screenshot for details.

[http://img809.imageshack.us/img809/6625/20110728ubuntudevicebus.png](http://img809.imageshack.us/img809/6625/20110728ubuntudevicebus.png)

How can I fix this? I want to format my thumb drive in Ubuntu after it's been exposed to an unknown Windows PC.

Thanks!

Tom

---

### Post by jerrrys on 2011-07-28
you must unmount the flash drive first.  this may help you

[http://gparted.sourceforge.net/larry/generalities/gparted.htm](http://gparted.sourceforge.net/larry/generalities/gparted.htm)

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

