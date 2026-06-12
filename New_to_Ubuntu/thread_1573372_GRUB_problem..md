---
title: "GRUB problem."
date: 2010-09-12
forum: New to Ubuntu
---

### Post by Baelfael on 2010-09-12
So I had split my hard-drive in half a good long time ago: one partition for Windows, one for Ubuntu. I found myself not using Ubuntu, so I figured I'd turn that partition into a separate storage space for Windows. So the Ubuntu side became an empty NTFS storage space.

A few days later, I turned on my computer to get a GRUB error message:

GRUB loading.
error: unknown filesystem
grub rescue>

What do I do? I know the problem is simply GETTING to my operating system, not the operating system itself, since GRUB is the bootloader and I obviously confused it by deleting Ubuntu. But how can I boot into Windows and get rid of this problem? I can't afford to start Windows fresh, either.

---

### Post by oldfred on 2010-09-12
If you still have a Ubuntu liveCD you can do this:

Restore basic windows style boot loader - universe enabled from Ubuntu or liveCD
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

If you have a windows CD you have to run fixMBR or BootRec.exe /fixmbr depending on version and run from the repair console.

---

### Post by coffeecat on 2010-09-12
Another alternative is to use [Supergrubdisk]("http://www.supergrubdisk.org/"). Since this is just to repair the Windows mbr, get the Super Grub Disk version, not Super Grub2 Disk. I know the legacy version will repair the Windows mbr, but I've never used Super Grub2 Disk.

When you boot from it, there are two entries in the rather user-hostile menu for Windows. One to boot into Windows, the other to fix mbr and boot into Windows.

The reason you lost your grub menu is because the grub menu configuration file and grub stage 2 are in the Ubuntu root partition. It's a common error to make.

---

### Post by Baelfael on 2010-09-12
Thanks guys, ran a FixMBR and I'm good to go.

---

