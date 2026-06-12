---
title: "[SOLVED] Adding a second hard drive for file server"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by pshootr on 2008-12-12
Hello. I finally got my 8.10 server updated and Samba installed. Thanks to the community here!!! Now I want to add a second drive to hold my shared files. Using and old machine with IDE. I plan on using a 40gig drive. Was wondering if there is a good tut on doing this. I used seaerch on this forum, but didn't have any luck. Thanks

---

### Post by Peter09 on 2008-12-12
Here are some threads to help

[http://www.tuxfiles.org/linuxhelp/mounting.html](http://www.tuxfiles.org/linuxhelp/mounting.html)

[http://www.smorgasbord.net/how-to-in...-ubuntu-linux/](http://www.smorgasbord.net/how-to-in...-ubuntu-linux/)

[http://ubuntuforums.org/showthread.php?t=403650](http://ubuntuforums.org/showthread.php?t=403650)
__________________
PC

---

### Post by pshootr on 2008-12-12
Thank you Peter. I will check it out.

---

### Post by pshootr on 2008-12-12
I think I udertand the mounting part. I am unsure of how I am going to figure out what device name will be givin to the new drive. For me to use during the mount.

---

### Post by Peter09 on 2008-12-12
Try

```
lshw -C storage
```

or 
```
df -h
```

These should show the devices on your system

---

### Post by pshootr on 2008-12-12
> **Peter09 said:**
> Try

```
lshw -C storage
```

or 
```
df -h
```

These should show the devices on your system

Ok cool. Thank you very much Peter.

---

### Post by Frogbarf on 2008-12-12
That seems to be the biggest single stumbling block when you add another hard drive.

But aha! don't ask me how to do it! I only know it's a problem, not how to do it!

---

### Post by pshootr on 2008-12-13
> **Peter09 said:**
> Try

```
lshw -C storage
```

or 
```
df -h
```

These should show the devices on your system

I entered "lshw -C storage" and got this. Does not seem to show added drives. How come?      

product: 82371AB/EB/MB PIIX4 IDE
       vendor: Intel Corporation
       physical id: 7.1
       bus info: pci@0000:00:07.1
       logical name: scsi2
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: ide bus_master emulated
       configuration: driver=ata_piix latency=64 module=ata_piix
  *-storage
       description: Mass storage controller
       product: PDC20262 (FastTrak66/Ultra66)
       vendor: Promise Technology, Inc.
       physical id: 10
       bus info: pci@0000:00:10.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: storage bus_master
       configuration: driver=pata_pdc202xx_old latency=64 module=pata_pdc202xx_old

And using this "df -h"  gave me this.

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             3.8G  723M  2.9G  20% /
tmpfs                 156M     0  156M   0% /lib/init/rw
varrun                156M  272K  156M   1% /var/run
varlock               156M     0  156M   0% /var/lock
udev                  156M  2.7M  154M   2% /dev
tmpfs                 156M     0  156M   0% /dev/shm

This only displays my existing drive.

---

### Post by JohnFH on 2008-12-13
> **pshootr said:**
> I entered "lshw -C storage" and got this. Does not seem to show added drives. How come?      


To get information on drives:
```
lshw -C disk
```
and if you also want to display the drive volumes:
```
lshw -C disk -C volume
```

The df command only displays the mounted file systems.  To add a new mounted filesystem, edit /etc/fstab file or use th mount command directly.

---

