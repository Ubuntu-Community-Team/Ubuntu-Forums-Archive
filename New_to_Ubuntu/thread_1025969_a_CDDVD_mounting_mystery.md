---
title: "a CD/DVD mounting mystery"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by minsf on 2008-12-30
my cd/dvd drive mounts only 1 in (about) 5 boots of ubuntu.
how to mount the CD after a "bad" boot?

**_here's some analysis:_**
1) after a "good" boot, i get the following output from lshw:
```
           *-cdrom
                description: DVD reader
                [COLOR="Red"]product: CDRW/DVD SN-324B
                vendor: SAMSUNG[/COLOR]
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /media/cdrom0
                [COLOR="Red"]version: U101[/COLOR]
                capabilities: [COLOR="Red"]removable[/COLOR] audio cd-r cd-rw dvd
                [COLOR="Green"]configuration: ansiversion=5 status=nodisc[/COLOR]
```

2) after a "bad" boot, i get the same output, but without the red parts, and the last green line changes to [COLOR="Green"]configuration: status=open[/COLOR] (even though the CD tray is closed).

3) after a "bad" boot, i CANNOT mount the cd manually. for instance, when i try "sudo mount -t iso9660 /dev/cdrom /media/cdrom0", 
i get the error "mount: No medium found". similarly, if i try "sudo mount -t iso9660 /dev/scd0 /media/cdrom0", i get the error
"mount: special device /dev/scd does not exist"

4) after a good boot, when i insert a cd, it mounts automatically, and the green line changes to:
```
                [COLOR="Green"]configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,utf8 state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /media/cdrom0
                   configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,utf8 state=mounted[/COLOR]
```

5) the file /etc/fstab is the same after "good" and "bad" boots.

6) after a "bad" boot, i tried to refresh the hardware detection by "sudo /etc/init.d/hal restart" with no success. (same lshw output, without the red parts).

any idea why "bad" boots happen?
Your help will be greatly appreciated :)

Edit: ubuntu 8.10

---

### Post by linux_tech on 2008-12-30
One suggestion is to try this next time you boot.  

When grub begins, press the Esc key, select the kernel line, and then press the [e] key. Then add:  noapic acpi=off to the end of that line. Press [Enter] and then the [b] key to boot

---

