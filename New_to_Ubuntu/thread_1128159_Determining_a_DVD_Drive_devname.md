---
title: "Determining a DVD Drive /dev/name?"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by jondgls on 2009-04-17
Liniux Experience = 2 weeks. (Raised on Windows (Feel free to express pity))

Just need to know what the /dev/name is of one of my DVD drives. Is there a terminal command or daemon that can list my drive names? I know this is probably really basic and I'm sorry but new OS's are always a challenge.

Thanks in advance,

JonDgls

---

### Post by mc4man on 2009-04-17
In a terminal
```
sudo lshw -C disk
```

---

### Post by Bachstelze on 2009-04-17
A bit less verbose:

```
dmesg | grep -i dvd
```

---

### Post by jondgls on 2009-04-17
Thank you mc4man. The output reads:


  *-cdrom
       description: DVD-RAM writer
       product: DVD-RW  DVR-216
       vendor: PIONEER
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrw1
       logical name: /dev/dvd1
       logical name: /dev/dvdrw1
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: 1.06
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready

Can I use any of the logical names listed?

JonDgls

---

### Post by Bachstelze on 2009-04-17
> **jondgls said:**
> Thank you mc4man. The output reads:


  *-cdrom
       description: DVD-RAM writer
       product: DVD-RW  DVR-216
       vendor: PIONEER
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrw1
       logical name: /dev/dvd1
       logical name: /dev/dvdrw1
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: 1.06
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready

Can I use any of the logical names listed?

JonDgls

Yes, they are probably all just symlinks to [font="monospace"]/dev/sr1[/font].

---

### Post by egalvan on 2009-04-17
> **jondgls said:**
> Linux Experience = 2 weeks. (Raised on Windows (Feel free to express pity))

need to know what the /dev/name is of DVD drives.
 Is there a terminal command or daemon that can list my drive names?
[B] I know this is probably really basic and I'm sorry but new OS's are always a challenge.
[/B]
JonDgls

Since this is the **Absolute Beginner Talk** section, there is no need to apologize for being an Absolute Beginner...
We were all beginners at one time :)

Welcome to the Linux world, and to this forum.
May your journey be fascinating...
and the challenges interesting.

ErnestG

---

### Post by jondgls on 2009-04-17
Thank you all for your speedy and informative replies. =D>

I am now burning a DVD in the command line using growisofs. After changing the directory to the location of the .ISO I used the following command:

```
growisofs -use-the-force-luke=dao -use-the-force-luke=break:1913760 -dvd-compat -speed=2 -Z /dev/dvdrw1=isoNAME.iso
```

Its the first process I have ever run in command line and it's a real trip! :P

Thanks again,
JonDgls

---

