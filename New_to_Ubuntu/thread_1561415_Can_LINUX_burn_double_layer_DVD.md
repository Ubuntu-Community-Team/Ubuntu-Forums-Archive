---
title: "Can LINUX burn double layer DVD ?"
date: 2010-08-26
forum: New to Ubuntu
---

### Post by honeybear on 2010-08-26
Hello,

I will buy a new dvd burner, high-tech. Is it supported by LINUX to burn double layer DVD ?

---

### Post by jonnywombat on 2010-08-26
As long as your burner can burn dual layer then yes

---

### Post by scrooge_74 on 2010-08-26
Classic thinking: "is linux advance as Windows?"

:D

---

### Post by migs73 on 2010-08-26
Classic thinking?? Maybe not. My drive will read DL DVD-R in windows but not linux. Not to much of a problem as I don't use them much, but there can be differences.:(

---

### Post by khelben1979 on 2010-08-26
> **migs73 said:**
> Classic thinking?? Maybe not. My drive will read DL DVD-R in windows but not linux.(

I wonder.. What brand is it?

---

### Post by migs73 on 2010-08-26
Khelben

hwinfo reports;

45: SCSI 00.0: 10602 CD-ROM (DVD)
  [Created at block.247]
  UDI: /org/freedesktop/Hal/devices/storage_model_DVD__RW_DS_8W1P
  Unique ID: KD9E.5HVF9Wxspm1
  Parent ID: Eu86.+LtHlOt8nWF
  SysFS ID: /class/block/sr0
  SysFS BusID: 0:0:0:0
  SysFS Device Link: /devices/pci0000:00/0000:00:14.1/host0/target0:0:0/0:0:0:0
  Hardware Class: cdrom
  Model: "PBDS DVD+-RW DS-8W1P"
  Vendor: "PBDS"
  Device: "DVD+-RW DS-8W1P"
  Revision: "BD1B"
  Driver: "pata_atiixp", "sr"
  Driver Modules: "pata_atiixp"
  Device File: /dev/sr0 (/dev/sg0)
  Device Files: /dev/sr0, /dev/block/11:0, /dev/scd0, /dev/disk/by-path/pci-0000:00:14.1-scsi-0:0:0:0, /dev/cdrom, /dev/cdrw, /dev/dvd, /dev/dvdrw
  Device Number: block 11:0 (char 21:0)
  Features: CD-R, CD-RW, DVD, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+DL
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #22 (IDE interface)
  Drive Speed: 24

It mounts the media, can see its name but cannot see any data on it.

EDIT BTW it is the built in drive on my Dell Inspiron 1501.

---

### Post by ezsit on 2010-08-26
> It mounts the media, can see its name but cannot see any data on it.

Maybe you need to install UDF tools, I think that's what it is called. Anyhow, search for UDF in synaptic and there should be some programs for dealing with UDF discs.

---

### Post by migs73 on 2010-08-27
ezsit,

no joy after the UDF install. See screen shot. This a DL DVD+R full of .avi's. Even my DVD player can see the files, as can the laptop I am using if in Windows.

Edit: Also attached is the same properties from a Standard DL DVD, showing 6.9Gb of info on the disc.

---

### Post by kelvin spratt on 2010-08-27
I burn Dl DVD in linux with no problems at all

---

### Post by ezsit on 2010-08-27
> no joy after the UDF install.

Sorry. I only remembered half the story. You will need the package libudf0 as well as the udftools. The library is what provides the reading capability for UDF filesystems. As you can see from your own screenshot in the lower right hand corner of the disc properly read, the filesystem type is UDF.

---

### Post by migs73 on 2010-08-30
Ezsit

My libudfs0 is already installed. It must be that isofs filesystem that is the problem. I never noticed it before, I'll give it a google. Thanks anyway.

---

### Post by khelben1979 on 2010-09-09
Did you find the solution to this problem?

---

