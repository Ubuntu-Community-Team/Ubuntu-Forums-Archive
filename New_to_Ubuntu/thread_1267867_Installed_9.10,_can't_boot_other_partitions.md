---
title: "Installed 9.10, can't boot other partitions"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by Falc7 on 2009-09-16
Hi
I installed Kubuntu 9.10 from a cd and it seems to have changed grub to 1.97. And in doing so deleted all my other boot options, such as windows 7, and ubuntu 9.04.
How do i get these back?

---

### Post by halitech on 2009-09-16
can you open a terminal and post the output of
```
sudo fdisk -l
```

---

### Post by Falc7 on 2009-09-16
Here it is:

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa88cb8cc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       25394   203977273+  83  Linux
/dev/sda2   *       29324       38159    70975170    7  HPFS/NTFS
/dev/sda3           38160       38913     6056505    5  Extended
/dev/sda4           25395       29155    30210232+  83  Linux
/dev/sda5           38160       38913     6056473+  82  Linux swap / Solaris

Partition table entries are not in disk order
jamie@jamie-laptop:~$


```

---

### Post by ubongo2008 on 2009-09-16
i think you should have a look at /boot/grub/menu.lst and maybe add an entry for windows if it is that what you are missing.  or maybe press ESC when booting if you can't see the possible options what to boot.

---

### Post by drs305 on 2009-09-16
Grub2 no longer uses menu.lst  It is a major remake of the way the bootloader menu is created and altered. Take a look at these guides for Grub 2. They explain the new files in Grub 2. The os_prober script should find your other OS. The guide shows what the Windows entries normally look like and how to edit files to change the Grub menu.

[Grub 2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275")

[https://wiki.ubuntu.com/Grub2]("https://wiki.ubuntu.com/Grub2")

---

### Post by Nburnes on 2009-09-16
In Terminal
```
sudo update-grub
```

It should automagically add you other Oses to the boot menu.

---

### Post by AndyCee on 2009-09-16
I did something similar when ext4 first came out.

I'm not sure about how grub 1.7 works, but as a temporary measure you could boot into a 9.04 liveCD and follow [these]("http://ubuntuforums.org/showthread.php?t=224351") instructions. That should be fine, but might not recognise your new 9.10 partition which might be formatted ext4.

EDIT: The above post suggests this step won't work.
Alternatively, if grub 1.7 uses the same commands as 0.97, you could simply log in to 9.10, mount the 9.04 partition and copy the command lines from your old boot menu into the 9.10 boot menu (/boot/grub/menu.lst).

Does that make sense? Let us know if you can get it to work.

---

### Post by Falc7 on 2009-09-16
> **Nburnes said:**
> In Terminal
```
sudo update-grub
```

It should automagically add you other Oses to the boot menu.

This one worked, thanks very much!

---

