---
title: "Linux for 8 MB laptop?"
date: 2010-03-14
forum: New to Ubuntu
---

### Post by theaveng on 2010-03-14
I found an old laptop with Windows 3.1 and 8 megabytes of RAM (just like I used in college).  Are there any versions of Linux that can squeeze into such a small space, and yet still be as user-friendly as the current Win3.1 install?

---

### Post by kaldor on 2010-03-14
> **theaveng said:**
> I found an old laptop with Windows 3.1 and 8 megabytes of RAM (just like I used in college).  Are there any versions of Linux that can squeeze into such a small space, and yet still be as user-friendly as the current Win3.1 install?

TinyCore maybe?

[http://distrowatch.com/table.php?distribution=tinycore](http://distrowatch.com/table.php?distribution=tinycore)

---

### Post by KIAaze on 2010-03-14
Damn Small Linux: [http://www.damnsmalllinux.org/wiki/index.php/Minimum_Hardware_Requirements](http://www.damnsmalllinux.org/wiki/index.php/Minimum_Hardware_Requirements)

---

### Post by cusinmex on 2010-03-14
Damn Small Linux.  


But I'm assuming your willing to
face the challenges that are included.  xD

---

### Post by undecim on 2010-03-14
Damn small linux would run it, but not with a graphical interface.

If you want a graphical interface, you will need to build a distro from scratch.

---

### Post by dadgetboy on 2010-03-14
> **undecim said:**
> Damn small linux would run it, but not with a graphical interface.

If you want a graphical interface, you will need to build a distro from scratch.

I believe you're mistaken; Damn Small Linux does have a graphical user interface. It may not be as beautiful as Ubuntu's GNOME; however it still works quite well.

---

### Post by undecim on 2010-03-14
> **dadgetboy said:**
> I believe you're mistaken; Damn Small Linux does have a graphical user interface. It may not be as beautiful as Ubuntu's GNOME; however it still works quite well.

DSL comes with a graphical interface, but the graphical interface requires 16mb of ram.

without X11 running, you can do it on 8mb

---

### Post by NightwishFan on 2010-03-14
Could you pull it off in 8 with swapping?

---

### Post by The Real Dave on 2010-03-14
I know the perfect OS, but it's not really Linux. It boots off a floppy, and will fly on 8Mb of RAM. It's called [KolibriOS]("http://www.kolibrios.org/"). Here's quite a [good review]("http://kmandla.wordpress.com/2010/02/08/kolibri-1-44mb-of-cute/"). :) You can install it to the harddrive, as well as run live off a floppy.

If that doesn't tickle your fancy, I'd advise TinyCore, or finding another 8Mb and running the slightly heavier, but nicer DSL. :)

---

### Post by richs-lxh on 2010-03-14
Small Linux will run on 2-3 Mb RAM:
[http://sourceforge.net/projects/smalllinux/](http://sourceforge.net/projects/smalllinux/)

Deli Linux is another option:
[http://www.delilinux.de/#about](http://www.delilinux.de/#about)

Don't be put off by the minimum specs of DSL etc, with some tweaking (disabling services/daemons etc) you could probably squeeze it to run on 8Mb with a graphical desktop, just don't open a load of apps at once.

Ram for that machine must be dirt cheap, can't you get a few more sticks?

---

### Post by undecim on 2010-03-16
> **NightwishFan said:**
> Could you pull it off in 8 with swapping?

Maybe. If you are doing this from the live CD, you would have to set that up manually, but once it's installed to a hard drive, you shouldn't have to worry much about it.

It would probably be kind of slow though. You would want to use only the most lightweight applications possible (no firefox :()

---

### Post by theaveng on 2010-03-17
I did some further research. My laptop appears to be this: [http://www.toshiba-europe.com/bv/computers/products/notebooks/t2000sx/index.shtm](http://www.toshiba-europe.com/bv/computers/products/notebooks/t2000sx/index.shtm)
 
*IF* that page is accurate then it has an 80386sx (32 bit CPU on a 16 bit bus - like a 68000), and the largest expansion RAM advertised by Toshiba is 8 MB. I am under the impression that DSL and TinyCore need a 486 minimum.
 
I would try a Windows 95 install if it had a CD drive, but without that CD drive it's probably hopeless.

---

### Post by theaveng on 2010-03-17
> **The Real Dave said:**
> It boots off a floppy, and will fly on 8Mb of RAM. It's called [KolibriOS]("http://www.kolibrios.org/").    Okay I downloaded the floppy image file.  Now what do I do with that?  I don't seem to have any floppy burning software.  ;-)

---

### Post by theaveng on 2010-03-18
Hello?

---

### Post by canthus13 on 2010-03-18
Well, if it's a .img file, this should work:

[http://ubuntuforums.org/showthread.php?t=452789](http://ubuntuforums.org/showthread.php?t=452789)

--Me

---

### Post by Tikkyca on 2010-03-18
[http://www.damnsmalllinux.org/wiki/index.php/Minimum_Hardware_Requirements](http://www.damnsmalllinux.org/wiki/index.php/Minimum_Hardware_Requirements)

---

### Post by KIAaze on 2010-03-19
> **theaveng said:**
> Okay I downloaded the floppy image file.  Now what do I do with that?  I don't seem to have any floppy burning software.  ;-)

It's a 7zip archive.
First, just extract it. If it doesn't work through the GUI:
```

sudo apt-get install p7zip
mkdir kolibri
cd kolibri
p7zip -d  ~/Downloads/kolibri_0.7.7.0_img_en.7z

```

(For some reasons, this automatically removes the archive after extraction, which is weird.)

Here are the contents of Docs/install.txt from the package:
It tells you to run install.sh to write the image to the floppy. ;)

```
Minimal system requirements for Kolibri 0.7.x.0:                                                                                                                                                                                            
* CPU: Pentium, AMD 5x86 or Cyrix 5x86 without MMX with frequency 100 MHz                                                                                                                                                                   
* RAM: 8 Mb                                                                                                                                                                                                                                 
* Videocard: supporting VGA (640*480*16 mode) or Vesa                                                                                                                                                                                       
* Keyboard: AT                                                                                                                                                                                                                              
* Mouse: COM or PS/2                                                                                                                                                                                                                        

The system can boot from any of following devices:
- Floppy 3.5                                      
- IDE HDD LBA                                     
- CD/DVD                                          
- USB Flash                                       

I. Install to floppy.
  1) Insert clean floppy without bad sectors to drive.
  2) Write to it kolibri.img image with any available methods:
    a) (if you have already loaded Kolibri by any method) run the program
       rdsave and select the variant corresponding to floppy             
    b) (for DOS and Windows) run subjoined install.bat                   
    c) with program WinImage or its analogue (e.g. DiskExplorer)         
    d) (for Linux) set "executable" attribute to subjoined script install.sh
       and run it                                                           
Now you can boot from floppy (keep it in drive, reboot, set in BIOS option  
of floppy booting).                                                         

II. Install to hard disk.
There exists several loaders from hard disk. All are oriented on DOS and
Windows users. Also standard Linux-loader GRUB can be used. All methods work
with file kolibri.img. If you already have old version of Kolibri installed,
simply replace kolibri.img to new. If you have booted from LiveCD, which    
does not contain the file kolibri.img, Kolibri can create it independently, 
to do this, run the program rdsave, enter the file name for saving and select
the corresponding variant. Of course, in this case Kolibri must be able to   
write to file system of selected partitions, currently this means that       
only FAT volumes are ok.                                                     
1) Most of all features has the loader mtldr (author - Diamond) - works with 
   DOS/Win95/98/NT/2k/XP/Vista, supports FAT32 and NTFS, has installator, can
   be installed to any folder on disk.                                       
   To install, simply run file HD_load\mtldr_install.exe and select image file.
   Apropos, by this way you can install several images. There is also          
   variant of install by hand - for those who want to know what installator    
   does: directions in HD_load\mtldr                                           
2) There is also the loader MeOSLoad (author - Trans, expanded by Mario79) -   
   works with DOS/Win95/98, supports FAT32, it is placed with the instruction  
   to the folder HD_load\MeOSLoad.                                             
3) Moreover, there exist a program which allow load Kolibri directly from      
   Windows 95/98/Me (of course, unloading it) - 9x2klbr (author - Diamond),    
   supports FAT32 and NTFS.                                                    
4) Usage of the loader GRUB. The way of using file 'memdisk' to load Kolibri   
   has been described by derPENGUIN on english forum                           
   (http://meos32.7.forumer.com/viewtopic.php?t=110).                          
   The suggested method (described by Alver) is based on that description      
   and was checked on grub-0.97-19mdv2007.0.                                   
   1. Kolibri can write only on FAT filesystem, so if image file is placed not 
      to FAT volume, the system can not save settings. Therefore if you have   
      FAT32 partition, place 'kolibri.img' there.
   2. This method requires the file 'memdisk' from the package 'syslinux'
      (http://syslinux.zytor.com). You may install the whole package or only
      extract the mentioned file. Only the file 'memdisk' is needed. (After
      package install it will be in '/usr/lib/syslinux').
   3. Place the file 'memdisk' to the folder 'boot' or to the partition used
      for Kolibri.
   4. Add to the configuration file 'menu.lst' ('grub.conf') lines as follow:

      title KolibriOS
      kernel (hd[Hard disk number],[partition number])[path]/memdisk
      initrd (hd[Hard disk number],[partition number])[path]/kolibri.img

      (Remember that numeration of partitions in GRUB starts from 0.)
      Example:
      title KolibriOS
      kernel (hd0,0)/boot/memdisk
      initrd (hd0,3)/kolibri/kolibri.img

      The initial variant was:

      label KolibriOS
      root (hd[Hard disk number],[partition number])
      kernel [path]/memdisk
      initrd [path]/kolibri.img

      Here 'memdisk' and 'kolibri.img' must be placed on the same partition.

      Example:
      label KolibriOS
      root (hd0,0)
      kernel /boot/memdisk
      initrd /boot/kolibri.img
      This example is the variant described on english forum, with install to
      Linux boot partition (of course, without FAT partition).

5) The previous method could not work as is in GRUB2 (tested by Apocalypse_dn),
   the commands "linux16" and "initrd16" should be used instead of "kernel"
   and "initrd" (suggested by vkos).

III. Install to USB-Flash-drive.
The special loader for FAT32-volumes has been written, it and its installer
to flash drive can be found in the folder HD_load\USB_Boot.
For not-FAT32 drives you may use article placed in the folder
HD_load\USB_Boot_old.

IV. Install to CD and DVD.
There exists special LiveCD-version of Kolibri, which contains
in addition to standard things some "heavy" (in Kolibri standards) programs:
the ported emulator DosBox, games "Fixed Rate Pig" and "sokoban".
You can also create bootable CD or DVD on the base of kolibri.img, adding
anything what you want, in the mode of floppy emulation.
The appropriate actions are determined by used CD/DVD write program
(focus on words such as "boot floppy emulation").

```

Contents of install.sh:
```
#!/bin/sh
echo "starting..."
dd if=kolibri.img of=/dev/fd0
echo "done. good-bye"

```

So canthus13 was right.

---

