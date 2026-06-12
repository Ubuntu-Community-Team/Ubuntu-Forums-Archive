---
title: "Downloaded Ubuntu 11.04 and lost ability to boot Windows 7"
date: 2011-05-17
forum: New to Ubuntu
---

### Post by Need Help Please on 2011-05-17
Downloaded Ubuntu 11.04 and lost ability to boot Windows 7
 

 

 Walp, I kept hearing how great Ubuntu was so after I had an issue with Windows I decided to give it a try so I could use it to get online in case of another  problem. I tried it from disc a few times and after viewing a few tutorials on Youtube I figured I'd install a dual boot option, Windows7 and Ubuntu 11.04.  
 

 It went fine until I tried to restart the computer and boot back into Windows. Instead of  getting a screen asking me which operating system I wanted to use like I was getting when I was using Ubuntu from the disk** I now have a small window with the words “Input not supported” that slowly moves diagonally around the screen for about 30 seconds before Ubuntu would  load and start**. I never get a screen asking which operating system I want to boot and have been unable to launch Windows 7 since. I've tried a dozen times over the last few days. I haven't seen this particular issue listed and when people add their problems to already posted threads members say to start a new thread as the problems may not be the same.  
 

 I used the search feature here and tried updating GRUB but nothing changed. It seems to still see Windows which I can only assume is a good sign.  
 

 

 michael@michael-*******:~$ sudo update-grub  
 Generating grub.cfg ...  
 Found linux image: /boot/vmlinuz-2.6.38-8-generic  
 Found initrd image: /boot/initrd.img-2.6.38-8-generic  
 Found memtest86+ image: /boot/memtest86+.bin  
 Found Windows Recovery Environment (loader) on /dev/sda1  
 Found Windows 7 (loader) on /dev/sda2  
 done  
 michael@michael-*******:~$  
 

 My skill set is minimal, my only experience with computers has been when I purchased a windows machine a few years ago so I could learn since it seemed they were more than just a fad and computer skills were a necessity in todays world. You have to literally explain all the steps for me. It seems all the instructions I find includes me spending a few hours on Google trying to figure out what the terms mean and how to access them. Example: One page said to launch a terminal but didn't say how to do that or what exactly a Terminal was. Yes, I'm really that naive and it seems all the instructions I find are meant for Power Users. 
 

 My computer is a little over a year old, is running Windows 7 64 bit, AMD64 dual core 2.7 and a single 800g hard drive (from memory) and was running fine before installing Ubuntu.  I run Windows Defender, AVG, Avast and Malwarebytes along with noscript and Adblocker.   
 

 Any help will be greatly appreciated. :(

*I did enter something into the Terminal that updated Ubuntu to the latest updates.

---

### Post by Hedgehog1 on 2011-05-17
Lets figure out what went wrong and get you running again (dual-boot style).

We need to get a look at what shape your install is in.

Please boot off the LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the [noparse]```
 & 
```[/noparse] tags.

***The Hedge***

:KS

p.s. If you had not already realized it yet, you can use the internet and visit the Ubuntu Forums from the LiveCD/LiveUSB. :D

---

### Post by Need Help Please on 2011-05-17
Is this right?



```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /BOOT/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe /wubildr 
                       /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    31,459,327    31,457,280  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     31,459,328    31,664,127       204,800   7 NTFS / exFAT / HPFS
/dev/sda3          31,664,128   975,812,520   944,148,393   7 NTFS / exFAT / HPFS
/dev/sda4         975,812,606 1,465,147,391   489,334,786   5 Extended
/dev/sda5         975,812,608 1,453,090,815   477,278,208  83 Linux
/dev/sda6       1,453,092,864 1,465,147,391    12,054,528  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        90661B56661B3C82                       ntfs       PQSERVICE
/dev/sda2        F86A1C246A1BDE66                       ntfs       SYSTEM RESERVED
/dev/sda3        3A001D86001D4A71                       ntfs       eMachines
/dev/sda5        aade7d59-69e4-4129-9d19-7b6f5ee2eb24   ext4       
/dev/sda6        7512f4e4-3bca-484e-9b8e-0e653febe7c4   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root aade7d59-69e4-4129-9d19-7b6f5ee2eb24
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root aade7d59-69e4-4129-9d19-7b6f5ee2eb24
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root aade7d59-69e4-4129-9d19-7b6f5ee2eb24
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=aade7d59-69e4-4129-9d19-7b6f5ee2eb24 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root aade7d59-69e4-4129-9d19-7b6f5ee2eb24
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=aade7d59-69e4-4129-9d19-7b6f5ee2eb24 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root aade7d59-69e4-4129-9d19-7b6f5ee2eb24
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root aade7d59-69e4-4129-9d19-7b6f5ee2eb24
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 90661B56661B3C82
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root F86A1C246A1BDE66
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=aade7d59-69e4-4129-9d19-7b6f5ee2eb24 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=7512f4e4-3bca-484e-9b8e-0e653febe7c4 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 663.438247681 = 712.361394176  boot/grub/core.img                             1
 629.549804688 = 675.973955584  boot/grub/grub.cfg                             1
 629.811992645 = 676.255477760  boot/initrd.img-2.6.38-8-generic               2
 663.436527252 = 712.359546880  boot/vmlinuz-2.6.38-8-generic                  1
 629.811992645 = 676.255477760  initrd.img                                     2
 663.436527252 = 712.359546880  vmlinuz                                        1

========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde sdf sdg 

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```*Added When I posted the code into the Terminal I also got this. Not sure if it's relevant.


```

ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot_info_script*.sh 

boot_info_script version: 0.60        [17 May 2011]


"gawk" could not be found, using "busybox awk" instead.
This may lead to unreliable results.

Identifying MBRs...
Computing Partition Table of /dev/sda...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda3 for information... 
Searching sda4 for information... 
Searching sda5 for information... 
Searching sda6 for information... 

Finished. The results are in the file "RESULTS.txt"
located in "/home/ubuntu/Desktop/".

ubuntu@ubuntu:~$ 


```

---

### Post by Need Help Please on 2011-05-17
> **Hedgehog1 said:**
> 

p.s. If you had not already realized it yet, you can use the internet and visit the Ubuntu Forums from the LiveCD/LiveUSB. :D


I was aware of that but it seemed to have limited functionality aka I couldn't watch youtube videos and it couldn't download the needed plug-ins. 

The reason I downloaded it to my hard drive was there seems to be a lot of cool stuff in the Ubuntu Software Center that I would like to try.

P.S. Do I need to download any Anti-Virus software for the Ubuntu partition? I've read both yes and no.

---

### Post by NormanFLinux on 2011-05-17
You don't need anti-virus in Linux. I've never had it on any Unix-like system I run. All I need is to enable the firewall.

---

### Post by Need Help Please on 2011-05-17
> **NormanFLinux said:**
> You don't need anti-virus in Linux. I've never had it on any Unix-like system I run.** All I need is to enable the firewall**.


How do I enable the Firewall? :redface:

---

### Post by williejones on 2011-05-17
> michael@michael-*******:~$ sudo update-grub  
 Generating grub.cfg ...  
 Found linux image: /boot/vmlinuz-2.6.38-8-generic  
 Found initrd image: /boot/initrd.img-2.6.38-8-generic  
 Found memtest86+ image: /boot/memtest86+.bin  
 Found Windows Recovery Environment (loader) on /dev/sda1  
 **Found Windows 7 (loader) on /dev/sda2  **
 done  
 michael@michael-*******:~$ Your Windows 7 is still there. There has to be some issue not allowing your computer not starting grub.  What graphics card is in your computer?

---

### Post by Need Help Please on 2011-05-17
> **williejones said:**
> Your Windows 7 is still there. There has to be some issue not allowing your computer not starting grub.  What graphics card is in your computer?


According to the product description I found online it has an integrated Nvidia GeForce 6150 SE .

---

### Post by williejones on 2011-05-17
I am not familiar with your graphics card, perhaps this will help

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by Hedgehog1 on 2011-05-18
Need Help Please,

This is my first chance to have a look at your system.

Do you have both a WUBI install and a dual-boot install?

```
sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe [B]/wubildr 
                       /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr[/B]

...  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        **/boot/grub/grub.cfg **/etc/fstab /boot/grub/core.img
```

It looks like you also use/have used EasyBCD:

```
sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        **/BOOTMGR /BOOT/BCD**
```

And this is not something I have seen before:

>  I now have a small window with the words “Input not supported” that slowly moves diagonally around the screen for about 30 seconds before Ubuntu would load and start. 


As I see it, you have two options:

(1) Change your PC to boot from Windows again and then clean out and reinstall Ubuntu  in a controlled way.

(2) Attempt to fix this install.  

I am asking an EasyBCD expert to have a look at this thread in hopes of he might see some obvious solution I have completely missed.

***The Hedge***

:KS

---

### Post by suzypeppercorn on 2011-05-18
I am going to take a wild guess and say that GRUB is displaying a resolution that is not supported by your monitor.


Some of your responses are not clear to me so let me double check a few things. Ubuntu DOES boot correctly after 30 seconds when you start your computer, correct? Ubuntu functions correctly after booting?

To test my theory, when you see the "image not supported" message at startup, hold the down arrow key for 3 seconds. This should select Windows from the GRUB list. Then hit the Enter key. Does this start your computer in Windows?

---

### Post by Hedgehog1 on 2011-05-18
> **suzypeppercorn said:**
> I am going to take a wild guess and say that GRUB is displaying a resolution that is not supported by your monitor.

**I think you are on to something here.**  That scrolling message  is the monitor complaining about the scan rate! :redface:

**Need Help Please** After you boot into Ubuntu, please do this:

```
gksudo gedit /etc/default/grub
```

[COLOR="Red"]and change this line:[/COLOR]

#GRUB_GFXMODE=640x480

[COLOR="red"]to this:[/COLOR]

GRUB_GFXMODE=640x480

[COLOR="red"]Then save and exit the document.[/COLOR]


Then do:

```
sudo update-grub
```


***The Hedge***

:KS

---

### Post by garvinrick4 on 2011-05-18
OP still has wubildr in Windows boot BCD, had or installed WUBI before and has left over
in boot manager in windows.
Can reinstall Windows boot and the check in 
command line windows:
```
bcdedit
```As administrator.
See if any entry with wubildr in it if so delete:
```
bcdedit delete {indentifier number in here with these}
```will remove entry if there. Make sure it is one with wubildr in it.

#Maybe when uses this link to get 7 booting again will overwrite the wubildr entry and
will not need to go throught the wubildr delete process.
#Also after booting into windows 7 check in ADD and REMOVE programs and make sure no
Ubuntu in there if is Uninstall it that will get rid of wubildr in BCD of Windows also,
#Here is link to get windows booting below: Only two commands:
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708") 

#After windows boots put in install Cd for Ubuntu and choose Try Ubuntu and open a terminal:
copy and paste these:
```
sudo mount /dev/sda5 /mnt
``````
sudo grub-install --recheck --root-directory=/mnt /dev/sda
``````
sudo umount /mnt
``````
sudo reboot
```Boot into Ubuntu and open a terminal and
```
sudo update-grub
```That will put windows in grub-config and menu entry in grub.

## We just have to get rid of wubildr entrys in Windows and reinstall windows boot(installing windows boot from recovery cd might just do that) then install grub2 from Ubuntu. Should take about 5 minutes. Have you got it any questions ask?

---

### Post by Need Help Please on 2011-05-18
> **Hedgehog1 said:**
> Need Help Please,

This is my first chance to have a look at your system.

Do you have both a WUBI install and a dual-boot install?

And this is not something I have seen before:




As I see it, you have two options:

(1) Change your PC to boot from Windows again and then clean out and reinstall Ubuntu  in a controlled way.

(2) Attempt to fix this install.  

I am asking an EasyBCD expert to have a look at this thread in hopes of he might see some obvious solution I have completely missed.

***The Hedge***

:KS
I downloaded from the Ubuntu page the 64bit version to my Desktop, then burned that to DVD. I ran Ubuntu from that DVD a handful of times before deciding to download it to my hard drive along side Windows7 with a dual boot option. 

I have no idea how to get my PC to boot from windows again. lol

---

### Post by Need Help Please on 2011-05-18
> **suzypeppercorn said:**
> I am going to take a wild guess and say that GRUB is displaying a resolution that is not supported by your monitor.
[COLOR=Red]**The thing is I don't think there is a resolution my monitor doesn't support as far as I know. **[/COLOR]

Some of your responses are not clear to me so let me double check a few things. Ubuntu DOES boot correctly after 30 seconds when you start your computer, correct? Ubuntu functions correctly after booting?
[COLOR=Red]**Yes, Ubuntu does boot correctly after 30 seconds and funtion correctly. I'm making all my posts from the computer in question. **[/COLOR]


To test my theory, when you see the "image not supported" message at startup, hold the down arrow key for 3 seconds. This should select Windows from the GRUB list. Then hit the Enter key. Does this start your computer in Windows?

I actually tried that. I tried pushing it once, twice, then three times and held it down for a few seconds thinking the selection screen was still there but I couldn't see it. The only thing that happened was the "Input not Supported" box stayed until I pressed Control/Alt/Delete then it booted into Ubuntu.

---

### Post by Need Help Please on 2011-05-18
> **Hedgehog1 said:**
> **I think you are on to something here.**  That scrolling message  is the monitor complaining about the scan rate! :redface:

**Need Help Please** After you boot into Ubuntu, please do this:

```
gksudo gedit /etc/default/grub
```[COLOR=Red]and change this line:[/COLOR]

#GRUB_GFXMODE=640x480

[COLOR=red]to this:[/COLOR]

GRUB_GFXMODE=640x480

[COLOR=red]Then save and exit the document.[/COLOR]


Then do:

```
sudo update-grub
```***The Hedge***

:KS
OK. Hopefully I changed the right code. This is from the terminal:


```
michael@michael-*******:~$ gksudo gedit /etc/default/grub

michael@michael-*******:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Recovery Environment (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
done
michael@michael-*******:~$ 

```

---

### Post by smcrossman on 2011-05-18
Hey!  I had the same issue....got a NVidia graphics by chance?  Regarless, I posted in launchpad....the offical tech support and got the answer straight off.  It had put a default screen resolution onto the login menu and I wasn't seeing it at all.  U can use an app called startup manager to alter the boot file safely....change the resolution size to something your monitor supports, change the time out  (I increased it to 25 sec so I have plenty of time to change op sys loading) and choose the default system you want to load.  Try that out and see if it works.  You can find the app in Ubuntu Software Center.  There is documentation in the community support stuff as well.  Search under topics of Grub, Grub2, Startup Manager, etc.

---

### Post by Need Help Please on 2011-05-18
> **garvinrick4 said:**
> OP still has wubildr in Windows boot BCD, had or installed WUBI before and has left over
in boot manager in windows.
Can reinstall Windows boot and the check in 
command line windows:
```
bcdedit
```As administrator.
See if any entry with wubildr in it if so delete:
```
bcdedit delete {indentifier number in here with these}
```will remove entry if there. Make sure it is one with wubildr in it.

#Maybe when uses this link to get 7 booting again will overwrite the wubildr entry and
will not need to go throught the wubildr delete process.
#Also after booting into windows 7 check in ADD and REMOVE programs and make sure no
Ubuntu in there if is Uninstall it that will get rid of wubildr in BCD of Windows also,
#Here is link to get windows booting below: Only two commands:
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708") 

#After windows boots put in install Cd for Ubuntu and choose Try Ubuntu and open a terminal:
copy and paste these:
```
sudo mount /dev/sda5 /mnt
``````
sudo grub-install --recheck --root-directory=/mnt /dev/sda
``````
sudo umount /mnt
``````
sudo reboot
```Boot into Ubuntu and open a terminal and
```
sudo update-grub
```That will put windows in grub-config and menu entry in grub.

## We just have to get rid of wubildr entrys in Windows and reinstall windows boot(installing windows boot from recovery cd might just do that) then install grub2 from Ubuntu. Should take about 5 minutes. Have you got it any questions ask?

OK, I'm attempting to do the things listed here:

```
How to restore the Windows Vista or 7 bootloader

To restore the Windows Vista/7 bootloader, you must first boot off your Windows Vista/7 installation DVD.
If you have one of the many OEM computers that didnt come with a Vista/7  installation disk, you can get the same effect with a Vista recovery  disk, which you can download for [Vista]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download") or [Win 7]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/").
When you get to the Regional settings, select your Location/Keyboard  setting then click next. On the next page you must click on "Repair your  computer."

On the next page, if it finds your Windows Vista/7 installation, make sure it is UNSELECTED before clicking next.
Then click on "Command prompt". From there, type in the folowing:

     Code:
     bootrec.exe /fixboot 
     Code:
     bootrec.exe /fixmbr 
Now close the two windows and click "Restart."

Take out your Vista/7 DVD and hopefully, you will be left with your Windows Vista/7 Bootloader.
```But the author fails to grasp my level of incompetence. I was smart enough to make a (Actually 3) recovery discs when I first got the computer. Problem is when I put in Recovery Disc 1 it displays in a window with the files contained on the disc but that's it. I put in all 3 discs but didn't see any files named Regional Settings. I right click > open but it just shows me more files. Using the directions contained in the link garvinrick supplied the directions state **"When you get to the Regional settings, select your Location/Keyboard setting then click next" **I don't see any filesnamed **Regional Settings**. Was the disc supposed to autorun? Here's a screencap of what I see:

[ATTACH]192564[/ATTACH]


I have no idea what my next step should be. :confused:

---

### Post by Need Help Please on 2011-05-18
> **smcrossman said:**
> Hey!  I had the same issue....got a NVidia graphics by chance?  Regarless, I posted in launchpad....the offical tech support and got the answer straight off.  It had put a default screen resolution onto the login menu and I wasn't seeing it at all.  U can use an app called startup manager to alter the boot file safely....change the resolution size to something your monitor supports, change the time out  (I increased it to 25 sec so I have plenty of time to change op sys loading) and choose the default system you want to load.  Try that out and see if it works.  You can find the app in Ubuntu Software Center.  There is documentation in the community support stuff as well.  Search under topics of Grub, Grub2, Startup Manager, etc.


While I'm waiting for an answer to my other question I'll try and pursue this fix attempt since I do have an integrated Nvidia GeForce 6150 SE .

---

### Post by Need Help Please on 2011-05-18
> **smcrossman said:**
> Hey!  I had the same issue....got a NVidia graphics by chance?  Regarless, I posted in launchpad....the offical tech support and got the answer straight off.  It had put a default screen resolution onto the login menu and I wasn't seeing it at all.  U can use an app called startup manager to alter the boot file safely....change the resolution size to something your monitor supports, change the time out  (I increased it to 25 sec so I have plenty of time to change op sys loading) and choose the default system you want to load.  Try that out and see if it works.  You can find the app in Ubuntu Software Center.  There is documentation in the community support stuff as well.  Search under topics of Grub, Grub2, Startup Manager, etc.

> **Need Help Please said:**
> While I'm waiting for an answer to my other question I'll try and pursue this fix attempt since I do have an integrated Nvidia GeForce 6150 SE .


I found and downloaded the app but how do I launch/use it? I can't find it under my installed apps. :confused:

---

### Post by Need Help Please on 2011-05-18
> **Need Help Please said:**
> I found and downloaded the app but how do I launch/use it? I can't find it under my installed apps. :confused:
Nevermind :oops:   For some reason it took 10 minutes to show up in the installed apps folder.

I'm attempting to shut down to see if I can see the boot screen after changing the resolution.

---

### Post by Need Help Please on 2011-05-18
[SIZE=4]**IT'S FIXED!!!**[/SIZE]

I downloaded the startup-manager recommended by [B]smcrossman, changed the resulution from 640x480 to 800x600, shut down the computer then restarted and I got the GNU   GRUB screen. I selected Windows 7 (loader) hit enter and it took me to the Black and White select Ubuntu or Windows7 screen. I chose Windows7 hit enter and Windows booted.

Thanks to everyone that assisted me in troubleshooting this problem! I am grateful. It's actually somewhat strange that there are so many people willing to take the time to help people figure out and fix their problems. 

And now I begin my Ubuntu journey.[B] :D




[/B][/B]

---

### Post by garvinrick4 on 2011-05-18
> But the author fails to grasp my level of incompetence. I was smart  enough to make a (Actually 3) recovery discs when I first got the  computer. Problem is when I put in Recovery Disc 1 it displays in a  window with the files contained on the disc but that's it. I put in all 3  discs but didn't see any files named Regional Settings. I right click  > open but it just shows me more files. Using the directions  contained in the link garvinrick supplied the directions state **"When you get to the Regional settings, select your Location/Keyboard setting then click next" **I don't see any filesnamed **Regional Settings**. Was the disc supposed to autorun? Here's a screencap of what I see:You have to put them in cd tray and boot from them. Put them in cd try and reboot. Machine
should be set to boot CD before Hard Drive. Then run the two commands.

## When you got computer you can make all the recovery CD's you want. Thats good it is in your appications forget where.
You can make one set of 3 disks that is your complete Windows 7 operating System.

---

### Post by Need Help Please on 2011-05-18
> **garvinrick4 said:**
> You have to put them in cd tray and boot from them. Put them in cd try and reboot. Machine
should be set to boot CD before Hard Drive. Then run the two commands.

## When you got computer you can make all the recovery CD's you want. Thats good it is in your appications forget where.
You can make one set of 3 disks that is your complete Windows 7 operating System.


lol  It makes perfect sense that I would have to restart and boot from them. :lolflag::oops:

One final question, when I walk away from the computer for a few minutes there's always a box asking me to input my password when I return. Can I stop this from happening?

---

### Post by garvinrick4 on 2011-05-18
> One final question, when I walk away from the computer for a few minutes  there's always a box asking me to input my password when I return. Can I  stop this from happening?
Start up your screensaver application and uncheck the box that tells it to lock.
Make all your changes to settings while there.

---

### Post by fidamehran on 2011-05-18
> **Need Help Please said:**
> [SIZE=4]**IT'S FIXED!!!**[/SIZE]

I downloaded the startup-manager recommended by [B]smcrossman, changed the resulution from 640x480 to 800x600, shut down the computer then restarted and I got the GNU   GRUB screen. I selected Windows 7 (loader) hit enter and it took me to the Black and White select Ubuntu or Windows7 screen. I chose Windows7 hit enter and Windows booted.

Thanks to everyone that assisted me in troubleshooting this problem! I am grateful. It's actually somewhat strange that there are so many people willing to take the time to help people figure out and fix their problems. 

And now I begin my Ubuntu journey.[B] :D




[/B][/B]

Something tells me the Windows boot entry still has the Wubi entry in it. Or am I mistaken? Does the black and white menu selection screen comes even after GRUB?

---

### Post by garvinrick4 on 2011-05-18
> Something tells me the Windows boot entry still has the Wubi entry in  it. Or am I mistaken? Does the black and white menu selection screen  comes even after GRUB?     I would say that is about 100% it would have to be physically removed, I have been there
done that a while back. OP is just so happy to be booting and no reason to bother with it now.
I imagine one day OP will see it in a bootscript or when looking in BCD and want to fix it up.
OP seems to be one happy camper now. It's all good and has a great attitude it seems should
enjoy linux.

---

### Post by Need Help Please on 2011-05-19
> **garvinrick4 said:**
> Start up your screensaver application and uncheck the box that tells it to lock.
Make all your changes to settings while there.

Thanks again!


> **fidamehran said:**
> Something tells me the Windows boot entry  still has the Wubi entry in it. Or am I mistaken?** Does the black and  white menu selection screen comes even after GRUB?**

Yes it does. 


> **garvinrick4 said:**
> I would say that is about 100% it would have to be physically removed, I have been there
done that a while back. OP is just so happy to be booting and no reason to bother with it now.
I imagine one day OP will see it in a bootscript or when looking in BCD and want to fix it up.
OP seems to be one happy camper now. It's all good and has a great attitude it seems should
enjoy linux.

I never installed Ubuntu in windows so I don't know how Wubi would have been installed. The only thing I can think of is when I went to make the Ubuntu download into a disc it asked me if I wanted it to make changes so the disc would be sure to run. I figured it was just making sure the DVD player came before the hard drive in the boot sequence. Maybe it installed Wubi at that time.

I'll probably live with it as is for a little while then follow the instructions to remove it. I've already had enough frustration for this month and another computer clusterfark might put me over the edge. ](*,) As stated, I'm just happy to be dual booting! :D

* I tried to go to the original post so I could change it to SOLVED but I don't think I can. Does a Moderator have to do that?

---

### Post by quickk on 2011-05-19
To mark the thread as "solved" all you have to do is click on the "thread tools" drop down box (right below the top page number indicator).   It should be the last option if I remember correctly.

---

### Post by jtarin on 2011-05-19
> **Need Help Please said:**
> 
One final question, when I walk away from the computer for a few minutes there's always a box asking me to input my password when I return. Can I stop this from happening?Yes wear dark glasses and a slouchy hat and your computer will become tired of asking you as it will not recognize you and will assume you can't be fooled second time.

---

### Post by quickk on 2011-05-19
To stop the password prompt, you have to open up the screensaver preferences and untick a box:

[http://www.liberiangeek.net/2010/06/how-to-disableremove-password-prompts-in-ubuntu-10-04-lucid-lynx-during-sleep-mode/]("http://www.liberiangeek.net/2010/06/how-to-disableremove-password-prompts-in-ubuntu-10-04-lucid-lynx-during-sleep-mode/")

For Ubuntu 11.04:

[http://www.liberiangeek.net/2011/04/how-to-disable-screensaver-lock-in-ubuntu-11-04-natty-narwhal/]("http://www.liberiangeek.net/2011/04/how-to-disable-screensaver-lock-in-ubuntu-11-04-natty-narwhal/")

---

### Post by smcrossman on 2011-05-19
> **quickk said:**
> To stop the password prompt, you have to open up the screensaver preferences and untick a box:

[http://www.liberiangeek.net/2010/06/how-to-disableremove-password-prompts-in-ubuntu-10-04-lucid-lynx-during-sleep-mode/](http://www.liberiangeek.net/2010/06/how-to-disableremove-password-prompts-in-ubuntu-10-04-lucid-lynx-during-sleep-mode/)

For Ubuntu 11.04:

[http://www.liberiangeek.net/2011/04/how-to-disable-screensaver-lock-in-ubuntu-11-04-natty-narwhal/](http://www.liberiangeek.net/2011/04/how-to-disable-screensaver-lock-in-ubuntu-11-04-natty-narwhal/)

Thank you for this! I probably would have never gotten around to looking for it....the password thing wasn't bothering me, but the short time was!  I'm still trying to figure out the Unity desktop so that small thing was buried! Now I can answer the phone and not have to log back in when I turn around!:D

---

### Post by JerryC on 2011-05-19
> **smcrossman said:**
> Hey!  I had the same issue....got a NVidia graphics by chance?  Regarless, I posted in launchpad....the offical tech support and got the answer straight off.  It had put a default screen resolution onto the login menu and I wasn't seeing it at all.  U can use an app called startup manager to alter the boot file safely....change the resolution size to something your monitor supports, change the time out  (I increased it to 25 sec so I have plenty of time to change op sys loading) and choose the default system you want to load.  Try that out and see if it works.  You can find the app in Ubuntu Software Center.  There is documentation in the community support stuff as well.  Search under topics of Grub, Grub2, Startup Manager, etc.

My problem is a bit different, but I think the above might be the answer. When I attempt to boot 11.04 from a wubi install, I get the same "monitor going to sleep" type response after selecting Ubuntu from the menu.  Is there a way to apply some form of the above fix in this situation?  I too am a very new user to Ubuntu.

JC

---

### Post by matey3 on 2011-05-19
Can wubi mess up your windows install?

Have you guys ever used [Wubi]("https://help.ubuntu.com/community/Wubi")? It is a very small program like 1.4 megs and runs in Windows, sets up latest version of Ubuntu where you tell it to (Like your D: drive ,I have not tried to use it on any USB drives yet so I donno if it would work on a removable disk, I dont see why not?),

Only thing which I didnt like about Wubi is that you have a limit in disk space usage (I think it only goes up to 100 GB and its menu driven so you cannot change that :()?
but the good thing about wubi is that it wont mess up your boot sector , delete or replace anything and it places itself 2nd to windows where the pc automatically boots into windows every time,  after the setup not unless you manually change that.
But despite all that can it ruin your windows setup?

---

