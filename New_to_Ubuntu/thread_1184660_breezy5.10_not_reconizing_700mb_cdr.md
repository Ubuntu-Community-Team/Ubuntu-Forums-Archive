---
title: "breezy5.10 not reconizing 700mb cdr"
date: 2009-06-11
forum: New to Ubuntu
---

### Post by munbuntu on 2009-06-11
breezy badger 5.10 (my local library version) I know -old -unsupported etc...will not recognize a 700MB cd-r. I have been able to d/l an iso image to the desktop that md5sum hash matches....however i cannot get the write to disk to recognize the cd-r as having enough space ubuntu-desktop-9.04.iso...was hopeing that i need to fix sumpthin in the cdr driver ...any help please. this started since this box had a NT 4.0 that i couldn't get to hash latest ver Ubuntu. so i installed old ver via library copy now need to upgrade would step by step upgrade be a strategy or 'alternate' install and get packages via internet...Newbie here any strategies would be helpful,danks

---

### Post by jonobr on 2009-06-11
Stupid question for you when,

When you say you are trying to write to a CDR, is the CD R or RW,
As in Write also?

It may be just a reader and does not burn cds?

---

### Post by 73ckn797 on 2009-06-11
What burner program are you using?

I assume you have been able to burn previous to this?

Gnomebaker has options for CD capacity. I ran into that a couple of times before realizing I needed to set it for the rated capacity of the blank disk.

---

### Post by H2SO_four on 2009-06-11
It sounds like this isn't your computer, so you won't have root acess to change or install anything, so hopefully the machine already has what you need.  I would verify that the drive is a burner, also that it can recognize another blank cd.

---

### Post by mcduck on 2009-06-11
> **jonobr said:**
> Stupid question for you when,

When you say you are trying to write to a CDR, is the CD R or RW,
As in Write also?

It may be just a reader and does not burn cds?

Both CD-R and CD-RW are writable. All CD's are, of course, readable so there's no need to add any letters to the name to tell that. :)

CD-R = Compact Disc-Recordable
CD-RW = Compact Disc-ReWritable

Anyway, for the original poster's problem, installing 5.10 and upgrading from there really isn't an option as many of the in-between versions are out of support as well.

When trying to write the disk make sure you are burning it as image, and not just trying to add the .iso file to the disk like you would add normal file to a data-CD. Also, the latest Ubuntu versions have a tool that allows creating a bootable USB drive so if you can't get the disk to burn but have a thumbdrive or something around that could be an option.

---

### Post by jonobr on 2009-06-11
Now, you learn something new everyday!!

---

### Post by Ptero-4 on 2009-06-11
You might try to see if you got syslinux installed. If you got it installed and you have a pendrive try mounting the iso to a folder created inside your home folder (type this: )
```

cd ~ 
mount -t iso9660 -o loop ubuntu-desktop-9.04.iso *folder*

```
then copy everything from the folder you mounted the iso into to your pendrive,
```

cp -a * /media/*yourpendrive*

```
finally install syslinux in the pendrive
```

syslinux /dev/sdX

```
and modify the bootloader config to boot off the pendrive 
```

cd /media/*yourpendrive*
mv isolinux.cfg syslinux.cfg

```
After that you can boot off your pendrive and install 9.04 off it.

---

### Post by zvacet on 2009-06-12
@ **munbuntu**

Download latest Ubuntu version with torrent.After that read [this.]("https://help.ubuntu.com/community/BurningIsoHowto")

---

