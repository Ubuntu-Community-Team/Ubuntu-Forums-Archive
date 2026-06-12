---
title: "Where to install grub?"
date: 2010-02-15
forum: New to Ubuntu
---

### Post by Redmage913 on 2010-02-15
Hey there,

I'm about to install Xubuntu 9.10 on my Dell Mini 9, that currently has Win7 Pro on it.  I need to keep the Win7 installation, so I'm installing Xubuntu on an SDHC card.  What I need to know is, where should I put grub?

FYI, My partition information for the main hard drive is:
/dev/sda (14.35 GB)
[INDENT]1.00 MiB: Unallocated.
/dev/sda1: NTFS. Label: System Reserved. Size: 100.00 MiB, 33.59 MiB used, 66.41 MiB unused, Flags: boot
/dev/sda2: NTFS. Label: <none> Size: 14.25 GiB, 9.84 GiB used, 4.41 GiB unused. Flags: <none>

[/INDENT]Where do I go from here?

--Red

---

### Post by ubunterooster on 2010-02-15
By default, the MBR is written to the main disk: devsda. Don't stick it on the SD unless card is bootable (hardly likely)

---

### Post by snowpine on 2010-02-16
Dell Mini 9 can't boot from SDHC as far as I know. You'll need to install GRUB to the internal SSD (/dev/sda), overwriting the Windows boot manager.

---

