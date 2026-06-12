---
title: "Is there a fix yet for vista live file systems?"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by medic8ted on 2009-03-06
I'm using Intrepid with kernel 2.6.27-11 and I can't read a vista burned cd.  When trying to mount /dev/sdc0 I get this
```
matt@desktop:~$ sudo mount /dev/scd0 /media/cdrom0 -t udf
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


matt@desktop:~$ dmesg | tail
[47876.448455] end_request: I/O error, dev sr0, sector 16964
[47879.595569] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[47879.595579] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[47879.595584] sr 0:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[47879.595589] end_request: I/O error, dev sr0, sector 16960
[47880.550957] end_request: I/O error, dev sr0, sector 16968
[47880.550988] udf: udf_read_inode(ino 4242) failed !bh
[47881.181431] end_request: I/O error, dev sr0, sector 16968
[47881.181463] udf: udf_read_inode(ino 4242) failed !bh
[47881.181473] UDF-fs: No partition found (1)

```
I thought this was supposed to be fixed in Intrepid?  I fixed it in Hardy with a patch I found here on the forums, but I don't see anything for this kernel.

---

### Post by jimreynold2nd on 2009-03-07
Well, it is a Vista's problem. You should ask on Vista forums =P.
But really, you made me curious. I have never seen this error before with CDs burned from Vista. What disk burner are you using? Do you have multisessions option on? is that a DVD-RAM or a CD/DVD-RW formatted with MountRainier?

---

### Post by medic8ted on 2009-03-09
Its a cd-r burned with whatever default settings vista uses, a friend burned it and he's technologically challenged so whatever comes up when you click "burn" is what he uses.  He burned one for me when I used Hardy and I got it working using the patch on these forums, but that was an older kernel and I'm afraid to patch it now cuz I don't want to break my kernel and re-install (again).  Unless someone knows how to "unpatch" a kernel?

---

### Post by Mark Phelps on 2009-03-09
I use both Vista and Intrepid and swap CDs and DVDs burned with both all the time. 

All I have to do is insert the media in the drive and then an icon appears on my desktop and a Nautilus page is opened for the drive.  I don't have to manually mount anything.

I notice that you're mounting the media as UDF -- is that because there are files larger than 3GB on it? I'm not sure that Intrepid can mount such a file, haven't tried it.

---

### Post by Victormd on 2009-03-09
I would look into "why is the CD not auto-mounting" because there shouldn't be any issues between these. Do you have to manually mount every CD or is it just this one (or vista-burned CDs)?

Your error msg is also saying that it may be related to wrong file type:
> mount: **wrong fs type**, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
So you may want to try to mount with the "auto" option:
```
sudo mount /dev/scd0 /media/cdrom0 -t auto
```

---

### Post by LowSky on 2009-03-09
[http://ubuntuforums.org/showthread.php?t=512782](http://ubuntuforums.org/showthread.php?t=512782)
this link shows the issue but its a error reading UDF created by VISTA (doesn't MS have a history of creating formats that other PC can not use....hmmmm), which can be fixed it seems quite easily. tell your friend to use a better ROM burning tool, like Nero (at least it works)

you need an application called udftools
[http://ubuntuforums.org/showthread.php?t=424245](http://ubuntuforums.org/showthread.php?t=424245)
command for it should be
```
sudo apt-get install udftools
```
if not check synaptic for the correct package.

---

