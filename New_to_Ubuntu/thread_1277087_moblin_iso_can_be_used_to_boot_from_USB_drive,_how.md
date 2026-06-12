---
title: "moblin iso can be used to boot from USB drive, how about ubuntu?"
date: 2009-09-27
forum: New to Ubuntu
---

### Post by say2sky on 2009-09-27
Many cds were used to burn ubuntu iso for install new release.
Now moblin iso can be used to boot either from cd or from usb flash drive.

I hope to know how moblin can achieve this and how user can do to install other linux iso without cd burning.

---

### Post by j.bell730 on 2009-09-27
Yes, Ubuntu [can]("https://help.ubuntu.com/community/Installation/FromUSBStick") too.

---

### Post by say2sky on 2009-09-28
I have tested the latest version (alpha 6) karmic-desktop-i386.iso but 
it can not boot from usb flash drive.

```

dd if=karmic-desktop-i386.iso of=/dev/sdb

```

---

### Post by mikewhatever on 2009-09-28
Has anyone seem a Miblin iso ever? Miblin images are released as img files, and surely, both can be used to install from USB.

---

### Post by Wim Sturkenboom on 2009-09-28
> **say2sky said:**
> I have tested the latest version (alpha 6) karmic-desktop-i386.iso but 
it can not boot from usb flash drive.

```

dd if=karmic-desktop-i386.iso of=/dev/sdb

```
You need an image file, not an iso. Did you read the link provided by j.bell730

---

### Post by say2sky on 2009-09-28
thanks for help.

I only wonder why moblin can boot from both cd and usb flash drive, I neglect it is a img file. 

Now I see. I can save some cds and save the Earth indirectly, it is all from your info. Thanks again!

---

### Post by say2sky on 2009-09-28
sorry for this question again. 

I have checked moblin live image again.
```

$ file moblin-2.1-preview-20090924-001.img 
moblin-2.1-preview-20090924-001.img: ISO 9660 CD-ROM filesystem data UDF filesystem data (unknown version, id 'NSR01') '2.1-preview-x86_64-200909232140' (bootable)

```

in fact, it's indeed an ISO file.

according to moblin website:
> 
About Live Images
The Moblin live image is a hybrid image that can either be burned onto a CD or written to a USB drive.


moblin live image is one step ahead of ubuntu distribution ISO file. it use same file for both cd and usb drive. no usb creator/script is needed to convert ISO file to another file which is suit for usb drive boot.

---

### Post by pawhtiobo on 2009-09-28
Hi :)
 
You can use this:
 
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
 
see ya...

---

