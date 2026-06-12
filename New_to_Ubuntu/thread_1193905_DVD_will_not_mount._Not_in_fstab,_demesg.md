---
title: "DVD will not mount. Not in fstab, demesg"
date: 2009-06-22
forum: New to Ubuntu
---

### Post by MatMan on 2009-06-22
CDs mount automatically after some griding (the disc is continually accessed even if I am not doing anything), **but DVDs will not mount**.

fstab doesn't mention cd or dvd, as I have seen in other people's fstab outputs (see below). When I put in a DVD it doesn't get mentioned in dmesg (see dmesg output below).

when I put in a CD, I get error messages in dmesg, but it mounts and I can play the CD (see CD dmesg below also).

There are a lot of outputs down there, sorry about that. If it helps, I installed jaunty (clean install) from a USB stick, and my computer is 

HP pavilion dv2700
running jaunty 32bit


**if you can help, you're rad.**



**the output from gedit /etc/fstab is**

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=f5a79412-2e21-4be4-a819-ca86058a5683 /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=8ebc5c06-a923-4c38-8e86-7ccfbb9325d1 /home           ext3    relatime        0       2
# swap was on /dev/sda5 during installation
UUID=726d4b5e-1de2-4bca-96df-2a9c8c459df8 none            swap    sw              0       0



[B]
the output from dmesg after inserting a dvd is[/B]

[ 9418.523185] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[11698.474420] usb 2-1: USB disconnect, address 6
[12419.660033] usb 2-1: new high speed USB device using ehci_hcd and address 7
[12419.795387] usb 2-1: configuration #1 chosen from 1 choice
[12419.908024] scsi7 : SCSI emulation for USB Mass Storage devices
[12419.932049] usb-storage: device found at 7
[12419.932053] usb-storage: waiting for device to settle before scanning
[12424.960060] usb-storage: device scan complete
[12424.960923] scsi 7:0:0:0: Direct-Access     FUJITSU  MHZ2320BH G2     0009 PQ: 0 ANSI: 2 CCS
[12424.962873] sd 7:0:0:0: [sdb] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[12424.963615] sd 7:0:0:0: [sdb] Write Protect is off
[12424.963621] sd 7:0:0:0: [sdb] Mode Sense: 00 38 00 00
[12424.963626] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[12424.966624] sd 7:0:0:0: [sdb] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[12424.967363] sd 7:0:0:0: [sdb] Write Protect is off
[12424.967369] sd 7:0:0:0: [sdb] Mode Sense: 00 38 00 00
[12424.967374] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[12424.967382]  sdb: sdb1
[12424.995452] sd 7:0:0:0: [sdb] Attached SCSI disk
[12424.995596] sd 7:0:0:0: Attached scsi generic sg2 type 0

**end of output from dmesg after inserting a CD**

[12424.967363] sd 7:0:0:0: [sdb] Write Protect is off
[12424.967369] sd 7:0:0:0: [sdb] Mode Sense: 00 38 00 00
[12424.967374] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[12424.967382]  sdb: sdb1
[12424.995452] sd 7:0:0:0: [sdb] Attached SCSI disk
[12424.995596] sd 7:0:0:0: Attached scsi generic sg2 type 0
[27954.004479] end_request: I/O error, dev sr0, sector 0
[27954.004490] __ratelimit: 33 callbacks suppressed
[27954.004496] Buffer I/O error on device sr0, logical block 0
[27954.004511] Buffer I/O error on device sr0, logical block 1
[27954.004517] Buffer I/O error on device sr0, logical block 2
[27954.004523] Buffer I/O error on device sr0, logical block 3
[27954.058537] end_request: I/O error, dev sr0, sector 0
[27954.058548] Buffer I/O error on device sr0, logical block 0

---

### Post by tarps87 on 2009-06-22
Can you try mounting it manualy
```
sudo mount /dev/cdrom /media/cdrom
```
or
```
sudo mount /dev/dvd /media/cdrom
```

Can you post any error messages here please

---

### Post by MatMan on 2009-06-23
Hi tarps87

I tried and get

mat@vickers:~$ sudo mount /dev/cdrom /media/cdrom
[sudo] password for mat: 
mount: /dev/sr0: unknown device
mat@vickers:~$ sudo mount /dev/dvd /media/cdrom
mount: /dev/sr0: unknown device
mat@vickers:~$

---

### Post by LewRockwell on 2009-06-23
is that dv2700 a laptop that is 64 bit capable?

did you just install ubuntu or have you been using it awhile?

how much other stuff do you have plugged into this machine?

are you certain all your BIOS settings are correct?

is your optical device clean and debris-free?

have you tried these operations with another operating system?

if the machine were in front of me the first thing I would do is live-run Puppy Linux on it to see what it does(you should be able to remove the Puppy disk after it's all loaded up)

---

### Post by MatMan on 2009-06-24
Hi Lew,
actually, I don't know if it is 64 bit capable.. I am running 32 bit though.

I ran Intrepid before Jaunty. I am pretty lousy at deep troubleshooting though

Other stuff plugged in is a USB external HDD

the bios is OK. or at least seems ok. I will try and check that out.

don't know about debris. Seems like an obvious one to check in hindsight. Nothing visibly wrong/obstructions with the drive though.

I have tried to open a CD with puppy and also tried to boot from a CD, neither of which work...

thanks Lew,

mat.

---

### Post by ACupOfCoffee on 2009-06-24
I'd bet money the DVD laser in your drive has failed but the CD laser hasn't. I have a drive where the exact opposite happened.

---

### Post by tarps87 on 2009-06-24
> **MatMan said:**
> Hi tarps87

I tried and get

mat@vickers:~$ sudo mount /dev/cdrom /media/cdrom
[sudo] password for mat: 
mount: /dev/sr0: unknown device
mat@vickers:~$ sudo mount /dev/dvd /media/cdrom
mount: /dev/sr0: unknown device
mat@vickers:~$

Was this with the a cd or dvd in? Probably should have mentioned this before.

Either way it is trying to use the correct device do you can now use /dev/sr0 instead of both /dev/cdrom and /dev/dvd
Is you bios set to boot from the cd drive? If it is it sound like you drive may be dyeing as booting from a cd is controlled by the bios before any OS's boot.

As LewRockwell suggests it may just be a dirty lens, for this I usually use meths and a tissue, but there are proper cleaning kits out there. Using chemicals on a disk drive should really be done as a last resort as there is a risk the in cleaning the lens it will get damaged

---

### Post by MatMan on 2009-06-24
Tarps

I did it with both CD and DVD, and got the same response for all. I also just tried it using /dev/sr0 and the same again.

thanks,
mat

---

### Post by tarps87 on 2009-06-24
It should be able to mount a cd without it being in the fstab file, when it mounts a cd can you view the contents of it?

Also you can try adding it to the fstab
```
sudo gedit /etc/fstab
```
(asumming you are using gnome)
or
```
sudo nano /etc/fstab
```

Not add the line
```
/dev/scd0  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8  0  0
```

(/dev/scd0 and /dev/sr0 should be the same thing but the Ubuntu default install uses /dev/scd0 so probably best to use this one in the fstab file)

---

### Post by MatMan on 2009-06-24
Hi tarps,

It has stopped mounting CDs now too. But when it did mount them, I could see the contents. I am starting to think it is the drive. I added the fstab line and no change.

---

### Post by tarps87 on 2009-06-25
> **MatMan said:**
> Hi tarps,

It has stopped mounting CDs now too. But when it did mount them, I could see the contents. I am starting to think it is the drive. I added the fstab line and no change.

So am I, can you see any visible damage to the lens.
Just had a thought, if you go into the bios it usually lists the internal devices like cd drives and hard drives. It is usually on the first screen but may vary. If you can find this list and the cd/dvd drive is not listed it may be a faulty connection which may be solved by reseating the connection. This may involve taking your laptop apart which will void any warranty you have, I believe drives are coved under most warranties.

---

### Post by MatMan on 2009-06-25
I took the drive out and tested it. It is dead. Time for a new one. thanks for your help, mate.

cheers
mat.

---

### Post by tarps87 on 2009-06-26
No problem

---

