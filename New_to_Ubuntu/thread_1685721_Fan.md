---
title: "Fan"
date: 2011-02-11
forum: New to Ubuntu
---

### Post by akmal710 on 2011-02-11
I have Aspire 1810Tz the battery life is 8 hours, but after browsing i found that i need to reduce the speed of fan, for which i need to install Windows 7, It was previously installed and I removed and installed ubuntu. 
Now i want to know if i can modify the code and can regain 8 hours battery life or do i need to install Windows & and partition my drive to boot, but it would be no use as I don't use Windows.

---

### Post by mikewhatever on 2011-02-11
Modify what code? Can you be more specific.

---

### Post by akmal710 on 2011-02-11
[http://www.linlap.com/wiki/acer+aspire+1410](http://www.linlap.com/wiki/acer+aspire+1410)

Then above site requires to download the updated BIOS from the Acer homepage and install it in Windows 7 as I dont have Windows 7 installed do I need to install it, or to proceed with _[U]_[/U]the Fan Control instructions on the same page. 
I am afraid about loss of data in update in Windows 7 as the site focuses on ruin the entire data or the notebook.

---

### Post by Mark Phelps on 2011-02-11
> **akmal710 said:**
> ... 
I am afraid about loss of data in update in Windows 7 as the site focuses on ruin the entire data or the notebook.

But, in your first post, you said you removed Win7.

So, which is it:
1) Win7 is still present
2) Win7 has been removed

---

### Post by eriktheblu on 2011-02-11
Many times while the BIOS update procedure is focused on Windows, the binary that does it is actually DOS based. This means you can often employ a FreeDOS session from CD or USB boot.

While not specific to your model, [this guide](http://www.netbooktech.com/tag/acer-aspire-one-bios-update-instructions/) may help.

---

### Post by mikewhatever on 2011-02-11
I'd suggest checking the BIOS version you have with **sudo lshw | head -n 10**. In my case, the output is as follows, and the BIOS version is A4.
```
description: Portable Computer
    product: Inspiron 1010
    vendor: Dell Inc.
    version: A04

```

It could be that your current BIOS version is newer then v1.3314 and doesn't need updating.

---

### Post by akmal710 on 2011-02-11
win 7 is removed

---

### Post by akmal710 on 2011-02-11
I got this output. Do i need to update the BIOS. as i dont know which is the latest BIOS for my notebook.

akmal@akmal-Aspire-1810TZ:~$ sudo lshw | head -n 10
[sudo] password for akmal: 
akmal-aspire-1810tz       
    description: Computer
    product: Aspire 1810TZ
    vendor: Acer
    version: v0.3119
    serial: LXPM50200394216BC92500
    width: 32 bits
    capabilities: smbios-2.6 dmi-2.6
    configuration: boot=normal uuid=21F6E958-FA04-4213-96BD-DBC521097934
  *-core

---

### Post by akmal710 on 2011-02-11
i have got Acer Aspire 1810tz...

---

### Post by mikewhatever on 2011-02-11
It looks like you'll need to install Windows and update the BIOS.

Edit: The zip archive with the latest bios Acer provides for your laptop contains both dos and Windows versions, which means you can use freedos from a cd/usb.

---

### Post by akmal710 on 2011-02-11
can u define what freedos is and provide  a link with description

can i begin by backing up data to an external HD and partition my HD using Gparted  and then install win 7

---

### Post by eriktheblu on 2011-02-23
Sorry for the late reply
[http://www.freedos.org/]("http://www.freedos.org/")
FreeDOS is an operating system designed for compatibility with MS-DOS programs. It is free.

MS-DOS is a family of command line operating systems that were the predecessor to the MS Windows operating systems (early versions of Windows in fact ran in DOS).

---

