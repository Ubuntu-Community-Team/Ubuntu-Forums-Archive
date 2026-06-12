---
title: "grub problem after first install"
date: 2011-01-02
forum: New to Ubuntu
---

### Post by chrismax2 on 2011-01-02
Hi,

I just installed Ubuntu onto the 2nd Hard Drive I was informed the installation was successful (after many attempts, my old CD Drive was at fault) However it gave me a error message when it tried to restart, now Windows Vista boots up with no grub.  Even if I press shift it wont work.  I checked the Partition on the second Drive and it appears Ubuntu is installed.  I tried following the help guide into reinstalled Grub 2.0 but I am not understanding exactly the command to make sure I know where my boot sector is located.  I tried the location I thought it was and got a warning that I should not install this at that location.

Any help would make my day thanks and regards

Chris

---

### Post by drs305 on 2011-01-02
The error was probably because you were trying to install Grub2 to a partition (sdXY) rather than the drive (sdX). Under most circumstances you want to install G2 only to the drive. You will probably end up installing G2 on sdb and then changing the boot order in your BIOS so it boots that drive first.

If you will boot the LiveCD and download/run the boot info script and post the contents of the RESULTS.txt we can probably find out where the problem is.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by chrismax2 on 2011-01-02
thanks for the quick reply
this is what I got

```


 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  


```

---

### Post by drs305 on 2011-01-02
We didn't get the full content of RESULTS.txt, but it appears all you need to do is change the BIOS to boot your Ubuntu/sdb drive first. This will allow G2 to boot either Ubuntu and Windows. 

If you don't see Windows listed in the menu, run "sudo update-grub" after booting into Ubuntu.

With this setup, the Windows bootloader will still be installed on the current sda drive, so if you ever have problems with Ubuntu you can change the BIOS boot order to boot directly into Windows (like your current situation).

---

### Post by chrismax2 on 2011-01-02
Yeah, that's done it thanks, thats my problem always looking for the harder fix rather than the easier fix.  Sounds not working but I will worry about that tomorrow on another post.

Thanks again :p

Got to work out how to put solve on this post now lol.

---

### Post by drs305 on 2011-01-02
> **chrismax2 said:**
> Got to work out how to put solve on this post now lol.

At the top right above the first post, click 'Thread Tools', then 'Mark this thread as solved'.

Happy Ubuntu-ing!

---

