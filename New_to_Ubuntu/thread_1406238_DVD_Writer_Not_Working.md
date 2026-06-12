---
title: "DVD Writer Not Working"
date: 2010-02-13
forum: New to Ubuntu
---

### Post by acreech on 2010-02-13
I have a combo DVD/CD Writer internal drive. I have found that the DVD writer has worked in the past. Now it seems that I can no longer write to a DVD. I can write to a CD still though. The error that I got from K3B is "OPC Failed. Probably the writer does -like the medium."

I am not sure if this is a software issue or a hardware issue. Can anyone give me some hints on how to determine if I am dealing with a software issue or a hardware issue. 

Thanks

acreech

---

### Post by acreech on 2010-02-14
I ran the code

```
 sudo lshw | less
```

This is the hardware on my computer. 

> acreech-laptop
    description: Notebook
    product: Aspire 7520
    vendor: Acer
    version: V1.21
    serial: 
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall64 vsyscall32
    configuration: boot=normal chassis=notebook uuid=66303861-3538-6239-6635-001B38C81CD2


 *-cdrom
             description: DVD-RAM writer
             product: DVD-RW DVRKD08RS
             vendor: PIONEER
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: 1.02
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc



My firm ware on the drive is 1.02. I wondered if I could try to update the firmware for the drive, but I have not been able to find the place to download the firmware. 

Thanks for any help with this. 


acreech

---

### Post by acreech on 2010-02-14
bump

---

### Post by acreech on 2010-02-14
Let me throw a kink into the works. 

I was trying to burn to a regular sized TDK DVD-R 1-16X 4.7 GB DVDR

I found that I could burn to a small Ridata DVD-R 4X 1.46 GB DVDR

Why can I burn a mini disk and not a full size disk. Firmware?

---

### Post by mwcrowley on 2010-02-14
Don't update the firmware yet.
Are you running karmic and was it working before the upgrade to karmic?
[http://art.ubuntuforums.org/showthread.php?p=8809940](http://art.ubuntuforums.org/showthread.php?p=8809940)

---

### Post by acreech on 2010-02-14
> **mwcrowley said:**
> Don't update the firmware yet.
Are you running karmic and was it working before the upgrade to karmic?
[http://art.ubuntuforums.org/showthread.php?p=8809940](http://art.ubuntuforums.org/showthread.php?p=8809940)

I am running karmic. I have not experienced this problem while using hardy heron, Intrepid Ibex, or Jackalope Jaunty. I burnt DVD's before switching to karmic to backup some data. 

I also have not done anything to change the hardware in my system. So the system is the same one. 

My system recognizes the blank DVD when you put it in, but it errors out when you try to write to it. 

My brother had some issues with writing to a DVD when he switched to Karmic, but he solved it by installing K3B. I attempted to use K3B and that did not solve my issue. 


acreech

---

### Post by phillw on 2010-02-14
Hi,

If brassero and K3B are giving you grief, can I suggest cleaning the drive with a cd-drive cleaner, it's possible that there's some old-fashioned muck on your write LED.



Regards,

Phill.

---

### Post by acreech on 2010-02-14
> **phillw said:**
> Hi,

If brassero and K3B are giving you grief, can I suggest cleaning the drive with a cd-drive cleaner, it's possible that there's some old-fashioned muck on your write LED.



Regards,

Phill.

Thanks for such a simple suggestion. I had not thought of that because it was still reading and writing to some degree, but after I cleaned the laser, it appears to be working just fine.

---

