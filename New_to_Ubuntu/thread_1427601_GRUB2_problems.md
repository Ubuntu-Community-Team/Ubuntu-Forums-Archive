---
title: "GRUB2 problems"
date: 2010-03-11
forum: New to Ubuntu
---

### Post by alekoarch on 2010-03-11
I have a dual boot on three computers-no problems till yesterday.
I had to reinstall Windows 7 then Linux on one of them. 
Although on the other 2 computers GRUB finds the other OS, it didn't find it on this one.
I looked at the Grub2#Reinstalling GRUB 2 guide, as well as others, but so far the only thing accomplished was to reinstall for the second time Linux and configure GRUB to show up on start-up, but I do not see the other OS listed. Also tried
sudo grub-install /dev/sda

Could someone help me?

with fdisk -l I get:

aleko@aleko ~ $ sudo fdisk -l
[sudo] password for aleko: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   *          13        5230    41899206+   7  HPFS/NTFS
/dev/sda3            5231       14593    75208297+   5  Extended
/dev/sda5            5231       14206    72099688+  83  Linux
/dev/sda6           14207       14593     3108546   82  Linux swap / Solaris
aleko@aleko ~ $

Thank you in advance;)

---

### Post by audiomick on 2010-03-11
have you tried
```
sudo update-grub
```

---

### Post by alekoarch on 2010-03-11
yes, I tried that several times
thanks

---

### Post by Locke_99GS on 2010-03-11
Are you running the latest grub from backports? (or proposed, or wherever it is) Early GRUB2 didn't always detect some Windows installs. It is far better now.

Otherwise, manually add your Windows entry to the end of */etc/grub.d/40_custom*

---

### Post by alekoarch on 2010-03-11
well Locke_99GS, I'm a little lost on what you are writing. 
How do I find out what version Grub do I have? What are backports?
Otherwise, manually add your Windows entry to the end of */etc/grub.d/40_custom- HOW?*

thanks

---

### Post by alekoarch on 2010-03-11
OK, I think I found out what version I have-
aleko@aleko ~ $ grub-install -v
grub-install (GNU GRUB 1.97~beta4)
aleko@aleko ~ $ 

i believe it's the latest-no?

---

### Post by Locke_99GS on 2010-03-11
Try ```
dpkg -s grub-pc |grep Ver
``` to see what version of GRUB you have installed. I am using 1.98~20100128 (from git) for instance.

Backports and Proposed are optional repo's maintained by Ubuntu and it's community. They can be enabled by uncommenting their deb lines in */etc/apt/sources.list* . I think there is a GUI called Software Sources in the administration menu where you can enable/disable these.

Then if you want to manually add the entry, something like this:
```

menuentry "Windows" {
	insmod ntfs
	set root=(hd0,1)
	drivemap -s (hd0) ${root}
	chainloader +1
}
```

added to your 40_custom (use *sudo gedit /etc/grub.d/40_custom*) to add the entry, ought to work. Then run *sudo update-grub* again.

---

### Post by alekoarch on 2010-03-11
sorry for being such a noob, but I don't think this is working. Did I miss something, or a character?

---

### Post by Locke_99GS on 2010-03-11
Ahh, the sources.list is where the repo list is kept on your local system. You don't add it as a repo.

You're using Mint, and I know they change quite a few things. I'm unsure if Mint has any of their own similar repo's, or if it would be safe to manually add the ubuntu repo's. 

Probably best to wait for somebody esle to chime in.

---

### Post by alekoarch on 2010-03-11
well thanks Locke_99GS for everything so far. I'll keep trying as well.
Hopefully I won't mess it up any more. 3 reinstalls in 2 days is a little ridiculous.

---

