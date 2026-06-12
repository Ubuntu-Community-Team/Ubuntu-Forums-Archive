---
title: "Grub2 - Windows 7 not listed in boot menu"
date: 2010-09-22
forum: New to Ubuntu
---

### Post by vale4674 on 2010-09-22
Hello you all,

yesterday I installed for the first time Ubuntu so I am new here.

My steps were:


[LIST=1]
[*]I  had Windows 7 installed before on ***C: partition***
[*]Then I installed Ubuntu on ***new partition***.
[*]I restarted laptop and choose to boot into Windows 7 and it was OK.
[*]Turned laptop off
[*]Today after I turned it ON I got:
[/LIST]
[INDENT]_*"Unknown file system error, grub error"* _on boot.
[/INDENT]I "googled" and find out that this is probably some problem with Grud.

I fixed that by doing this:
[https://wiki.ubuntu.com/Grub2#Restore%20GRUB2%20-%20Recovering%20from%20a%20Windows%20XP%20/%20Vista%20/%207%20Reinstallation](https://wiki.ubuntu.com/Grub2#Restore%20GRUB2%20-%20Recovering%20from%20a%20Windows%20XP%20/%20Vista%20/%207%20Reinstallation)

After this, when I turn on laptop, on boot menu there is only Ubuntu listed.[INDENT]
[LIST=1]
[*]Ubuntu
[*]Ubuntu (Recovery mode)
[*]Memory..... (something like that)
[*]Memory....
[/LIST]
[/INDENT]So as you see, my problem is that Grud2 does not see Windows 7.

  Then I tried this 
[https://wiki.ubuntu.com/Grub2#Dual-booting](https://wiki.ubuntu.com/Grub2#Dual-booting)

and now I can boot into Ubuntu and into Windows 7 (both Ubuntu and Windows 7 are listed)

[SIZE=4][COLOR=Red]Question[/COLOR][/SIZE]:  
I would like  someone to explain me in short why the first time i could  boot into  Windows and after restart I got that "Unknown file system, grub  error". 
And after installing Grud2 again I could only see Ubuntu in boot menu.  I  would really like to know what is going on in background so I could learn system good.


This is how my partitions look like.
```
sudo fdisk -l 
``````
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x73aa3206

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         249     1998848   82  Linux swap / Solaris
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         249        2628    19108864   83  Linux
/dev/sda3            2629        7727    40957717+   7  HPFS/NTFS
/dev/sda4            7728       14594    55151616    f  W95 Ext'd (LBA)
/dev/sda5            7728       14594    55150592    7  HPFS/NTFS
```[SIZE=4][COLOR=Red]
[/COLOR][/SIZE]

---

### Post by Jesus_Valdez on 2010-09-22
On a terminal:

```
sudo update-grub
```

---

### Post by wilee-nilee on 2010-09-22
Hard to say what happened. The bootscript in my signature though is a good tool for looking at your setup. I also use it if I mess around with partitioning or bootloaders on my own setups. It only shows where and what the setup is now, but if you had a script from the borked set up and one now you would probably have the answer.

I would agree with the update-grub it just may have been as simple as that.;)

---

### Post by Mark Phelps on 2010-09-23
If the installation of GRUB, or re-installation, automatically picked up the other OSs on a PC, then you would never have to run update-grub after installing it after MS Windows -- but you do.

It just appears to be a "glitch" that you have to run update-grub AFTER the install for its prober to find the other OSs.

---

### Post by vale4674 on 2010-09-23
OK.. so my second question is answered, tnx.

How about my first question?
After installing Ubuntu after Windows 7 I could normally see listed Ubuntu and Windows 7 and I booted into Windows 7.

But after first restart i got black screen with 

```
"Unknown file system, grub error
```

Did Windows did something?

---

### Post by Silent Warrior on 2010-09-23
That might depend on how you restarted, or if you did anything to your partitions on the way (maybe). But what COULD cause that is, to my knowledge, faulty fstab-entries, GRUB or initramfs not having been duly updated, a harddrive in need of fsck (hard reboot?), a plain failing harddrive (not likely the case for you right now, I take it)...
Any more causes?

---

### Post by vale4674 on 2010-09-23
> **Silent Warrior said:**
> **That might depend on how you restarted**, or if you did anything to your partitions on the way (maybe). But what COULD cause that is, to my knowledge, faulty fstab-entries, GRUB or initramfs not having been duly updated, a harddrive in need of fsck (hard reboot?), a plain failing harddrive (not likely the case for you right now, I take it)...
Any more causes?

I just turned down laptop and when I turned it on next day that happened (black screen with error).

Waaaaaaait, I remember..... 

While I was in Windows that time. 
I had this partitions:
[LIST=1]
[*]C: 40GB Windows 7
[*]20GB of Ubuntu partition (2GB swap + 18GB Ubuntu) which can't be seen through explorer.

[*]50GB of unallocated space
[/LIST]

then i used Disk Management in Windows 7 to format that 50GB and to make ***D: disk*** from it.

now it looks like this:
Did that formating messed up boot sectors?
 [IMG]http://www.easilysharing.com/images/64958792763350842933.jpg[/IMG]

---

### Post by Mark Phelps on 2010-09-23
> **vale4674 said:**
> Did that formating messed up boot sectors?
 

I would hazard a guess at NO -- for a couple of reasons:
1) I'm presuming you're booting using GRUB, that's also in the MBR, and there's no reason I know why formatting a data partition should cause Win7 to also mess with the MBR
2) I'm also presuming that your first partition is formatted Ext4 and contains your /boot directory.  That being true, Win7 is unable to even READ that filesystem, let alone write to it.

Thus, it's unlikely that Win7 messed up your Linux boot.

But then ... nothing is "impossible" where MS Windows is concerned ...

---

### Post by Rubi1200 on 2010-09-23
Please post the results of the bootscript posted above by wilee-nilee.

It will give us a better idea of what is going on and make offering solutions easier.

Thanks.

---

### Post by vale4674 on 2010-09-24
> **Mark Phelps said:**
> I would hazard a guess at NO -- for a couple of reasons:
1) I'm presuming you're booting using GRUB, that's also in the MBR, and there's no reason I know why formatting a data partition should cause Win7 to also mess with the MBR
2) I'm also presuming that your first partition is formatted Ext4 and contains your /boot directory.  That being true, Win7 is unable to even READ that filesystem, let alone write to it.

Thus, it's unlikely that Win7 messed up your Linux boot.

But then ... nothing is "impossible" where MS Windows is concerned ...




1) yes, I am booting using Grub (Grub2) ... I really think so too... as  you can see my picture above with partitions, D is on the end.

2) you can see on image above:

[LIST=1]
[*]first 2GB is swap
[*]next 18GB is ext4 for linux
[/LIST]
 
> **Rubi1200 said:**
> Please post the results of the bootscript posted above by wilee-nilee.

It will give us a better idea of what is going on and make offering solutions easier.

Thanks. 

Here is the result of bootscript:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 37911608 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     3,999,743     3,997,696  82 Linux swap / Solaris
/dev/sda2    *      3,999,744    42,217,471    38,217,728  83 Linux
/dev/sda3          42,218,820   124,134,254    81,915,435   7 HPFS/NTFS
/dev/sda4         124,135,424   234,438,655   110,303,232   f W95 Ext d (LBA)
/dev/sda5         124,137,472   234,438,655   110,301,184   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        2bac5d6c-f875-4134-a88c-8de7b68921ee   swap                                     
/dev/sda2        f17d6230-df75-4273-8a75-1a0a2d3cc9c0   ext4                                     
/dev/sda3        483E5F9A3E5F803C                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        F8286E7C286E39B0                       ntfs       Data                          
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro)
/dev/sda3        /media/483E5F9A3E5F803C  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda2/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,2)'
search --no-floppy --fs-uuid --set f17d6230-df75-4273-8a75-1a0a2d3cc9c0
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,2)'
search --no-floppy --fs-uuid --set f17d6230-df75-4273-8a75-1a0a2d3cc9c0
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set f17d6230-df75-4273-8a75-1a0a2d3cc9c0
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=f17d6230-df75-4273-8a75-1a0a2d3cc9c0 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set f17d6230-df75-4273-8a75-1a0a2d3cc9c0
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=f17d6230-df75-4273-8a75-1a0a2d3cc9c0 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set f17d6230-df75-4273-8a75-1a0a2d3cc9c0
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set f17d6230-df75-4273-8a75-1a0a2d3cc9c0
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda3)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 483e5f9a3e5f803c
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=f17d6230-df75-4273-8a75-1a0a2d3cc9c0 /               ext4    errors=remount-ro 0       1
/dev/sda1       none            swap    sw              0       0

=================== sda2: Location of files loaded by Grub: ===================


  19.4GB: boot/grub/core.img
   4.8GB: boot/grub/grub.cfg
  19.4GB: boot/initrd.img-2.6.32-24-generic
  19.4GB: boot/vmlinuz-2.6.32-24-generic
  19.4GB: initrd.img
  19.4GB: vmlinuz
```

---

### Post by Rubi1200 on 2010-09-24
There seem to be a couple of issues going on here:

Fstab is not correct:
> # / was on /dev/[COLOR=Red]sda3[/COLOR] during installation UUID=f17d6230-df75-4273-8a75-1a0a2d3cc9c0 /               ext4    errors=remount-ro 0       1[COLOR=Red] /dev/sda1       none            swap[/COLOR]    sw              0       0 

The Ubuntu install is on sda2 not 3 and swap is missing its UUID.

My recommendation is to reinstall GRUB and to correct the errors in fstab.

Reinstall GRUB from the LiveCD:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Fstab:
use the LiveCD and GParted to get the correct UUID (right-click > Information) and then edit the file and enter the correct values.

---

### Post by vale4674 on 2010-09-24
> **Rubi1200 said:**
> There seem to be a couple of issues going on here:

Fstab is not correct:


The Ubuntu install is on sda2 not 3 and swap is missing its UUID.

My recommendation is to reinstall GRUB and to correct the errors in fstab.

Reinstall GRUB from the LiveCD:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Fstab:
use the LiveCD and GParted to get the correct UUID (right-click > Information) and then edit the file and enter the correct values.

I'm not sure if I understand. I can boot into W7 and into Ubuntu. Why do I need to reinstall GRUB then?
Can you tell my what is my problem in detail (for dummy :)?

---

### Post by Rubi1200 on 2010-09-24
Hmm, I am getting old! 

I understood that you were unable to boot into Ubuntu because of the GRUB error.

Nonetheless, the results of the bootscript indicate there might be a problem with your fstab file.

So, next time you boot into Ubuntu go to the terminal and post the output of ```
cat /etc/fstab
```Maybe there was just a glitch in the system for some reason.

And if you can boot into Ubuntu, then there is obviously no need to reinstall GRUB again; my apologies.

---

### Post by vale4674 on 2010-09-24
> **Rubi1200 said:**
> Hmm, I am getting old! 

I understood that you were unable to boot into Ubuntu because of the GRUB error.

Nonetheless, the results of the bootscript indicate there might be a problem with your fstab file.

So, next time you boot into Ubuntu go to the terminal and post the output of ```
cat /etc/fstab
```Maybe there was just a glitch in the system for some reason.

And if you can boot into Ubuntu, then there is obviously no need to reinstall GRUB again; my apologies.

No need for apologies, you are being very kind with your help :)

here is the output:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=f17d6230-df75-4273-8a75-1a0a2d3cc9c0 /               ext4    errors=remount-ro 0       1
/dev/sda1       none            swap    sw              0       0

```

---

### Post by Rubi1200 on 2010-09-24
Well, I am not sure what is going on because, in many cases, a faulty fstab file is likely to result in the types of errors you encountered or even leave the file-system unbootable.

Again, take a look at your fstab and compare it with the bootscript:

You have the swap partition on sda1 and Ubuntu on sda2.

Fstab says this:
> # / was on /dev/[COLOR=Red]sda3[/COLOR] during installation UUID=f17d6230-df75-4273-8a75-1a0a2d3cc9c0 /               ext4    errors=remount-ro 0Also the line for swap should read > # swap was on /dev/sda1 followed by the UUID (as above for the Ubuntu partition, but here the UUID is missing.

Was Ubuntu originally on sda3 before you made the partition changes in Windows?

And, one more thing, what does the output of ```
free -m
``` show?

---

### Post by john newbuntu on 2010-09-24
Just a few suggestions:
1. Change your boot flag from /dev/sda2 to /dev/sda3.
2. The /grldr located on your sda3 indicates that at some point you used grub4dos for booting or some other bootloader, which might confuse grub (not sure though). Move that out of the way(dont delete it).
3. Run chkdsk on your NTFS partitions from your win CD.
4. Try booting to ubuntu and and run "sudo update grub" and see if win shows up.
5. If at all you are able to get into Ubuntu in step4, run "sudo grub-install /dev/sda". Reboot and see if things look ok (boot to win)

---

### Post by vale4674 on 2010-09-25
> **Rubi1200 said:**
> Well, I am not sure what is going on because, in many cases, a faulty fstab file is likely to result in the types of errors you encountered or even leave the file-system unbootable.

Again, take a look at your fstab and compare it with the bootscript:

You have the swap partition on sda1 and Ubuntu on sda2.

Fstab says this:
Also the line for swap should read  followed by the UUID (as above for the Ubuntu partition, but here the UUID is missing.

**Was Ubuntu originally on sda3 before you made the partition changes in Windows?**

And, one more thing, what does the output of ```
free -m
``` show?

This was my procedure of installing Ubuntu:


[LIST=1]
[*]Insert Ubutnu CD
[*]In disk management deleted all partitions except C: where Windows are.
[*]Now disk looks like this: 20GB unallocated - 40GB Windows - 50GB unallocated
[*]From first 20GB made 2GB swap + 18GB Ubuntu partitions
[*]Installed Ubuntu
[*]Boot into Windows
[*]In disk management in Windows 7 formated last 50GB of unallocated space and made D: disk from it
[/LIST]
then my problems started after first restart which I explained above.

free -m:

```
             total       used       free     shared    buffers     cached
Mem:          2011        560       1451          0        122        231
-/+ buffers/cache:        206       1805
Swap:         1951          0       1951

```As I can boot into W7 and Ubuntu I don't realize what is my problem.. because you say that I have problem (according to result od bootscript)

---

### Post by Rubi1200 on 2010-09-25
I also do not understand what is going on; you can boot into both operating systems and yet the fstab file seems (from my understanding) to indicate something is not quite right.

But, the results of ```
free -m
``` show that the swap partition is recognized and in use.

If everything is working, leave it and sleep easy at night.

As they say, if it ain't broke don't fix it.

:)

---

### Post by vale4674 on 2010-09-26
> **Rubi1200 said:**
> I also do not understand what is going on; you can boot into both operating systems and yet the fstab file seems (from my understanding) to indicate something is not quite right.

But, the results of ```
free -m
``` show that the swap partition is recognized and in use.

If everything is working, leave it and sleep easy at night.

As they say, if it ain't broke don't fix it.

:)

I think I'll do that.. just gonna leave it that way.
Although I think that you are right about that something is not quite right (this sounds odd :S)

For example, if I turn ON my laptop with external USB HD (WD Passport) I got a black screen with message (MBR is missing).. which was not the case while I had only Windows. But if I turn it ON without external USB HD I got GRUB menu with ubuntu and w7.

So I also think that something is not quite good in all those files.

---

### Post by QLee on 2010-09-26
[QUOTE=vale4674]...
For example, if I turn ON my laptop with external USB HD (WD Passport) I got a black screen with message (MBR is missing).. which was not the case while I had only Windows. But if I turn it ON without external USB HD I got GRUB menu with ubuntu and w7
....[/QUOTE]
I'll give you one possible scenario which could result in those symptoms. If your BIOS is set to boot from USB first, then it could do that, but it wouldn't be a problem if the USB drive wasn't connected at boot time.

---

### Post by vale4674 on 2010-09-26
> **QLee said:**
> I'll give you one possible scenario which could result in those symptoms. If your BIOS is set to boot from USB first, then it could do that, but it wouldn't be a problem if the USB drive wasn't connected at boot time.

you are right... I put USB first in BIOS menu when I was trying to install grub from USB.... I forgot about that... tnx...

man.. this transition to Ubuntu is cool... always some problems :)

---

### Post by QLee on 2010-09-26
[QUOTE=vale4674]...
man.. this transition to Ubuntu is cool... always some problems :)[/QUOTE]
Problems? No, not problems, opportunities to learn, there will be no problems after you have learned enough, that is, except for the ones you will be able to create for yourself.;-)

Best of luck!

---

### Post by vale4674 on 2010-09-26
> **QLee said:**
> Problems? No, not problems, opportunities to learn, there will be no problems after you have learned enough, that is, except for the ones you will be able to create for yourself.;-)

Best of luck!

heh.. tnx U all for helping :)

---

### Post by jtarin on 2010-09-26
Another possiblity not mentioned is when you decided to format the unallocated space after all installations you modified the partition record which moved things from where they were during the intitial setup.

---

### Post by vale4674 on 2010-09-26
> **jtarin said:**
> Another possiblity not mentioned is when you decided to format the unallocated space after all installations you modified the partition record which moved things from where they were during the intitial setup.

hmmm I don't know.. 
it's really strange why that happened.. and as I see no one of us can say exactly what happened :(

---

### Post by drs305 on 2010-09-26
As far as the fstab entry regarding the comment 
> # / was on /dev/sda3 during installation

While it correctly states where the installation was originally placed, it *never* changes unless you do another install. This means that the comment is of very little value when troubleshooting. Even though it says "sdXY", this value may no longer be accurate if partitions have subsequently been added or deleted. In truth, you can't even be positive which device was "sdX" unless you only have one drive since this value can change depending on the order the devices were recognized during boot. 

To find out where the system is currently installed, if running Ubuntu, use the command *mount*, open Gparted or check System, Administration, Disk Utility (look at the mount points). See where **/** is mounted.

And of course you can use "sudo blkid" to compare the UUIDs to the ones in fstab. If the partitions have recently changed, you might want to run the command as below to make sure you aren't getting cached results. I've never seen that happen, but apparently it can.
```
sudo blkid -c /dev/null
```

---

### Post by vale4674 on 2010-09-28
> **drs305 said:**
> As far as the fstab entry regarding the comment 


While it correctly states where the installation was originally placed, it *never* changes unless you do another install. This means that the comment is of very little value when troubleshooting. Even though it says "sdXY", this value may no longer be accurate if partitions have subsequently been added or deleted. In truth, you can't even be positive which device was "sdX" unless you only have one drive since this value can change depending on the order the devices were recognized during boot. 

To find out where the system is currently installed, if running Ubuntu, use the command *mount*, open Gparted or check System, Administration, Disk Utility (look at the mount points). See where **/** is mounted.

And of course you can use "sudo blkid" to compare the UUIDs to the ones in fstab. If the partitions have recently changed, you might want to run the command as below to make sure you aren't getting cached results. I've never seen that happen, but apparently it can.
```
sudo blkid -c /dev/null
```

fstab:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=f17d6230-df75-4273-8a75-1a0a2d3cc9c0 /               ext4    errors=remount-ro 0       1
/dev/sda1       none            swap    sw              0       0

```sudo blkid:
```
/dev/sda1: UUID="2bac5d6c-f875-4134-a88c-8de7b68921ee" TYPE="swap" 
/dev/sda2: UUID="f17d6230-df75-4273-8a75-1a0a2d3cc9c0" TYPE="ext4" 
/dev/sda3: UUID="483E5F9A3E5F803C" TYPE="ntfs" 
/dev/sda5: LABEL="Data" UUID="F8286E7C286E39B0" TYPE="ntfs" 
```Gparted:
[IMG]http://www.easilysharing.com/images/63375933642417404781.png[/IMG]


So why as you can see, gparted reports different thing than blkid. 
Shouldn't they report same?

---

### Post by drs305 on 2010-09-28
> **vale4674 said:**
> fstab:
So why as you can see, gparted reports different thing than blkid. 
Shouldn't they report same?

Sorry, I either don't see it or don't understand your question. 

If you mean that blkid doesn't show the unallocated space - it locates block devices (such as partitions) but not unallocated space such as is shown in gparted.

---

### Post by jtarin on 2010-09-28
I'm feeling queasy looking at that GParted shot.:shock:

---

### Post by jtarin on 2010-09-28
The problem has to be syntax:> I "googled" and find out that this is probably some problem with **Grud**.
So as you see, my problem is that **Grud2** does not see Windows 7.
And after installing **Grud2** again I could only see Ubuntu in boot menu.But seriously if it's Grud enough for you it's Grud enough for me.

---

### Post by vale4674 on 2010-09-28
> **drs305 said:**
> Sorry, I either don't see it or don't understand your question. 

If you mean that blkid doesn't show the unallocated space - it locates block devices (such as partitions) but not unallocated space such as is shown in gparted.

Ok, blkid is cleared now for me.

It just looks ugly to me that Gparted shows that hierarchy in ext4 partition (unallocated + sda5) when I clearly formated all of the remaining unallocated space in Windows for D: partition. It would be logical that it says: sda1 swap, sda2 ext4, sda3 ntfs, sda4 ntfs and just that.

> **jtarin said:**
> I'm feeling queasy looking at that GParted shot.:shock:

looks ugly right? :(

> **jtarin said:**
> But seriously if it's Grud enough for you it's Grud enough for me.

don't understand this one.. hmm
if yout think that I was messing with different versions of Grub then NO.. because I only used that one from 10.04 CD.

---

