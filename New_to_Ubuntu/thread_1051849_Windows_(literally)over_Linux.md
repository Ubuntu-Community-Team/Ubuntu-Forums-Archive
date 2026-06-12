---
title: "Windows (literally)over Linux"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by pinsky on 2009-01-27
Hello there!

I know that this question is more windows based, but i wold like to know if someone perhaps found a solution for it.

So I have Linux installed on one hard, and am planing to install win on the other one. Linux hard is primary master, windows hard will be primary slave.

Last time i wanted to set ap a dual-boot in this order (linux over windows) windows completly messed up grub, and I coudn't (didn't knoe how) to boot to linux any more. Windows just booted as they were the only OS.

I'm in the same sitoation now, so does anybody know how to prevent this from hapening, or how to make grub functional again after the installation of windows?


Tnx

---

### Post by talsemgeest on 2009-01-27
Take a look [here.](http://ubuntuforums.org/showthread.php?t=224351) It should tell you how to reinstall the grub.

---

### Post by rafaelsousa on 2009-01-27
Unfortunatelly, you cannot prevent windows from overwrite boot sector... But let it to do so, you can recover your grub again. The steps are as follow:

1. Boot your live cd again
2. Access an text based terminal with ctrl+alt[0..6]
3. Mount your / partition, of installed linux system you want recover.
4. Type:

```
chroot <mounted-root-system>
```

5. Type:
```
grub-install <path-to-first-disk-with-mbr>
```

In path to first device could be something like /dev/sda, for sata disks or
/dev/hda for ide disks.

---

### Post by talsemgeest on 2009-01-27
> **rafaelsousa said:**
> Unfortunatelly, you cannot prevent windows from overwrite boot sector... But let it to do so, you can recover your grub again. The steps are as follow:

1. Boot your live cd again
2. Access an text based terminal with ctrl+alt[0..6]
3. Mount your / partition, of installed linux system you want recover.
4. Type:

```
chroot <mounted-root-system>
```

5. Type:
```
grub-install <path-to-first-disk-with-mbr>
```

In path to first device could be something like /dev/sda, for sata disks or
/dev/hda for ide disks.
The link I posted is easier and safer than this.

---

### Post by Nostalos on 2009-01-27
How about just: 
 
1. disconnect the Ubuntu Drive.  
2. Install Windows to 2nd drive.   
3. Reconnect Ubuntu Drive.  
4. Modify Grub to Boot Windows from 2nd Drive.

Windows can't write to a drive that isn't there ;)

---

### Post by TheLions on 2009-01-27
> **Nostalos said:**
> How about just: 
 
1. disconnect the Ubuntu Drive.  
2. Install Windows to 2nd drive.   
3. Reconnect Ubuntu Drive.  
4. Modify Grub to Boot Windows from 2nd Drive.

Windows can't write to a drive that isn't there ;)

maybe better disable it in BIOS but if this is a laptop you can't disconect the drive

---

### Post by Ben Page on 2009-01-27
I would, in this case, install one OS to 1st drive, and other to 2nd drive, and then boot from bios. In bios, your MB supports an option to select the 1st boot drive, so when you want to boot the 1st drive OS, set your boot options in bios to boot the 1st drive 1st. And for 2nd OS set it to boot 2nd drive 1st. Only drawback is that you'll have to enter bios each time you want to boot the other OS, but this way you will have full integrity in both OSes, and the wont be able to mess with each other.

---

### Post by talsemgeest on 2009-01-27
> **Ben Page said:**
> I would, in this case, install one OS to 1st drive, and other to 2nd drive, and then boot from bios. In bios, your MB supports an option to select the 1st boot drive, so when you want to boot the 1st drive OS, set your boot options in bios to boot the 1st drive 1st. And for 2nd OS set it to boot 2nd drive 1st. Only drawback is that you'll have to enter bios each time you want to boot the other OS, but this way you will have full integrity in both OSes, and the wont be able to mess with each other.
Instead of messing around with the bios, and having to change the default boot drive every time, he could just install windows, reinstall grub as per the link I gave, then add windows to the bootloader. There is no need to complicate things. :)

---

