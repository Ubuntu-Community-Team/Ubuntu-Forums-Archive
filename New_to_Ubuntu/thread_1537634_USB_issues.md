---
title: "USB issues"
date: 2010-07-23
forum: New to Ubuntu
---

### Post by uscelwyn on 2010-07-23
Hi,
I have an Imation drive and have partitioned it using ImationLock v224. Is there any way that I can operate this with Ubuntu?
Thanks,
Uri
(newbie to Ubuntu and loving it)

---

### Post by ubunterooster on 2010-07-23
You will have to reformat the drive using DiskUtility first I assume

According to 
[http://gadgets.softpedia.com/gadgets/Computer-Peripherals/The-Imation-Pocket-Flash-Drive-Series-of-Portable-Storage-Solutions-2725.html](http://gadgets.softpedia.com/gadgets/Computer-Peripherals/The-Imation-Pocket-Flash-Drive-Series-of-Portable-Storage-Solutions-2725.html)

> The drives from the Pocket Flash Drive series don't offer any  partitioning functions, but they do come packed with Imation's Lock  password protection software, which will protect the files against any  unauthorized access. However, as in the case of all the other Imation  flash drives, this software suite is only compatible with Windows-based  OS systems (no Mac OS or Linux)

---

### Post by uscelwyn on 2010-07-23
The drive works fine. It's just when I try to run 'ImationLock.exe' which gives me access to the encrypted partition on the drive, I get an error from 'Archive Manager' (I do note that it does recognise the correct option that this is an executable file):

Archive:  /media/ABFD-D6C1/ImationLOCKv224.exe
[/media/ABFD-D6C1/ImationLOCKv224.exe]
  End-of-central-directory signature not found.  Either this file is not a zipfile, or it constitutes one disk of a multi-part archive.  In the latter case the central directory and zipfile comment will be found on the last disk(s) of this archive.
note:  /media/ABFD-D6C1/ImationLOCKv224.exe may be a plain executable, not an archive.
zipinfo:  cannot find zipfile directory in one of /media/ABFD-D6C1/ImationLOCKv224.exe or
          /media/ABFD-D6C1/ImationLOCKv224.exe.zip, and cannot find /media/ABFD-D6C1/ImationLOCKv224.exe.ZIP, period.

---

### Post by ubunterooster on 2010-07-23
Go to system>administration>synaptic: use this to get ```
wine
```

---

### Post by sandyd on 2010-07-23
> **uscelwyn said:**
> The drive works fine. It's just when I try to run 'ImationLock.exe' which gives me access to the encrypted partition on the drive, I get an error from 'Archive Manager' (I do note that it does recognise the correct option that this is an executable file):

Archive:  /media/ABFD-D6C1/ImationLOCKv224.exe
[/media/ABFD-D6C1/ImationLOCKv224.exe]
  End-of-central-directory signature not found.  Either this file is not a zipfile, or it constitutes one disk of a multi-part archive.  In the latter case the central directory and zipfile comment will be found on the last disk(s) of this archive.
note:  /media/ABFD-D6C1/ImationLOCKv224.exe may be a plain executable, not an archive.
zipinfo:  cannot find zipfile directory in one of /media/ABFD-D6C1/ImationLOCKv224.exe or
          /media/ABFD-D6C1/ImationLOCKv224.exe.zip, and cannot find /media/ABFD-D6C1/ImationLOCKv224.exe.ZIP, period.

> **ubunterooster said:**
> You will have to reformat the drive using DiskUtility first I assume

According to 
[http://gadgets.softpedia.com/gadgets/Computer-Peripherals/The-Imation-Pocket-Flash-Drive-Series-of-Portable-Storage-Solutions-2725.html](http://gadgets.softpedia.com/gadgets/Computer-Peripherals/The-Imation-Pocket-Flash-Drive-Series-of-Portable-Storage-Solutions-2725.html)
you can't see the encrypted contents with linux ubunterooster means

---

### Post by anewguy on 2010-07-23
If you already have this drive partitioned and formatted, and you have data encrypted that you want to access (that's what it sounds like to me) you need to understand that the ImationLOCKv224.exe is a Windows executable, and it won't execute in Linux.  Someone has recommended installing Wine - this would give you the ability to execute a Windows program, but I don't know if it will let you access the drive.  Wine (at least the last time I checked) doesn't support USB devices, and if the drive is a USB device, I don't think running the executable in Wine will solve anything since the drive probably won't be seen by Wine.

Dave ;)

---

