---
title: "installing from .iso file"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by Billybob97060 on 2008-12-05
I have a .iso dvd image of Ultimate edition 2.0 and i can't burn it to a cd because it just says "wrong media format" i have only been able to burn dvd images in vista, which i fortunately don't have. lol. but i want to know if there is a way i can install it from the .iso image instead of finding a vista computer to burn the image with.. is there any way to just have the iso on my windows partition and go from there?

Edit: i meant i can't burn the image to a dvd because of the issue, not a cd lol.

---

### Post by binbash on 2008-12-05
did you try to burn your iso with this command ? 

cdrecord -v -dao dev=1,0,0 speed=8 file.iso

---

### Post by crjackson on 2008-12-05
I just read your edit. Did you try with K3b and a fresh DVD - Not the one that you had problems with being reported as wrong media type.

---

### Post by Billybob97060 on 2008-12-05
i just tried that and here is the output

joey@joey-desktop:/media/LACIE/Ultimate Edition 2.0 Reformat$ cdrecord -v -dao dev=1,0,0 speed=8 Ultimate-edition-2.0-gamers.iso
TOC Type: 1 = CD-ROM
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '1,0,0'
scsibus: 1 target: 0 lun: 0
WARNING: the deprecated pseudo SCSI syntax found as device specification.
Support for that may cease in the future versions of wodim. For now,
the device will be mapped to a block device file where possible.
Run "wodim --devices" for details.
Linux sg driver version: 3.5.27
wodim: No such file or directory. 
Cannot open SCSI driver!
For possible targets try 'wodim --devices' or 'wodim -scanbus'.
For possible transport specifiers try 'wodim dev=help'.
For IDE/ATAPI devices configuration, see the file README.ATAPI.setup from
the wodim documentation.

Update: I Didn't word my first post very well but I am using a DVD-R disc in a DVD-RW drive it just won't work...

---

### Post by halitech on 2008-12-05
if you don't want to.can't burn it, try unetbootin ( [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) ) it will do an install from an iso you select

---

### Post by Therion on 2008-12-05
...

---

### Post by crjackson on 2008-12-05
> **Therion said:**
> ...

Funny how one edit from the OP caused a domino effect  ):P

---

### Post by Billybob97060 on 2008-12-05
I have tried everything i can to burn it to a dvd, but everytime it just says wrong media format, but when i do on my buddies vista laptop, it works just fine with the same blank dvd everytime..

---

