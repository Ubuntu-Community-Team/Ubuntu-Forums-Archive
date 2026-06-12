---
title: "no kernel exists"
date: 2010-09-20
forum: New to Ubuntu
---

### Post by orangesoda22 on 2010-09-20
ok, im just about tired of all these problems.

getting this thing installed and running has been a real bitch and a half.


but heres whats going on.

i got ubuntu installed. everything was running fine. i got my files moved from windows into it, and then i rebooted into into vista to back up my bookmarks from firefox so i could import them. as i was rebooting into vista, the computer ran a ntfs disk checker thing of some kind. im not sure what it was because it wasnt on screen very long. it seemed sort of like a disk defragger. well i thought nothing of and went into vista to do my business.

finished that and attempted to reboot back into ubuntu and all i get is a command line like thing that says 

grub>

at the very top of the screen it says GNU grub version 1.98-1ubuntu6

i tried typing boot but it said there was no kernel.

so im lost. what do i do?

i cant reinstall, because all my files were moved into the ubuntu partition and if i install itll wipe them all out..........right?

HELP

---

### Post by Rubi1200 on 2010-09-20
Do you have the Ubuntu CD?

If yes, boot the computer choosing to try Ubuntu in live mode.

Then, post the results of the bootscript linked to at the bottom of my post.

Thanks.

---

### Post by wilee-nilee on 2010-09-20
> **Rubi1200 said:**
> Do you have the Ubuntu CD?

If yes, boot the computer choosing to try Ubuntu in live mode.

Then, post the results of the bootscript linked to at the bottom of my post.

Thanks.
+1 OP what you saw was probably a chkdsk never interrupt that, who is your computers manufacturer?

Windows will run a auto chkdsk if you resize the partition, if it is not done in a on board wind virtual like the disk manager in Vista and Windows 7.

---

### Post by orangesoda22 on 2010-09-20
its not working.

the script is definetely on the desktop but all im getting is this

# To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo bash [/home/ubuntu/Downloads/boot_info_script*.sh
bash: [/home/ubuntu/Downloads/boot_info_script*.sh: No such file or directory
ubuntu@ubuntu:~$ sudo bash [/home/ubuntu/Downloads/boot_info_script055.sh
bash: [/home/ubuntu/Downloads/boot_info_script055.sh: No such file or directory
ubuntu@ubuntu:~$ sudo bash [/home/ubuntu/desktop/boot_info_script055.sh
bash: [/home/ubuntu/desktop/boot_info_script055.sh: No such file or directory
ubuntu@ubuntu:~$ sudo bash /home/ubuntu/desktop/boot_info_script055.sh
bash: /home/ubuntu/desktop/boot_info_script055.sh: No such file or directory
ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot_info_script055.ssh
bash: /home/ubuntu/Desktop/boot_info_script055.ssh: No such file or directory
ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot/info/script_055.sh
bash: /home/ubuntu/Desktop/boot/info/script_055.sh: No such file or directory
ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot/info/script_055.sh
bash: /home/ubuntu/Desktop/boot/info/script_055.sh: No such file or directory
ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot/info/script_055.sh
bash: /home/ubuntu/Desktop/boot/info/script_055.sh: No such file or directory
ubuntu@ubuntu:~$ sudo bash ~/Desktop_boot/info_script_055.sh
bash: /home/ubuntu/Desktop_boot/info_script_055.sh: No such file or directory
ubuntu@ubuntu:~$ 


as you can see i tried moving it and typing it different was none of it worked.


btw i didnt interrupt the process and im on a compaq

---

### Post by drs305 on 2010-09-20
On Desktop:
```
sudo bash /home/ubuntu/Desktop/boot_info_script055.sh
```

In Downloads:
```
sudo bash ~/Desktop/boot_info_script055.sh
```

---

### Post by orangesoda22 on 2010-09-20
never mind that. i moved the file back into the download folder and  tried it again and it worked. not sure how or why but oh well. here is what the results file said```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => HP/Gateway is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/swap.disk

sda1/Wubi: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   292,984,831   292,984,769   7 HPFS/NTFS
/dev/sda2         292,984,832   312,573,951    19,589,120   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        303AF1454CC3C3B6                       ntfs                                     
/dev/sda2        A0DCF5CCDCF59CAA                       ntfs       PRESARIO_RP                   
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1/Wubi



```

---

### Post by Calash on 2010-09-20
Looks like a Wubi install.  Wubi installs Ubuntu as a file instead of a partition on the drive.  Most people feel it is more for testing and getting a feel for the operating system than an actual full setup.

There is some information here on how to recover files from the virtual drive.  It may be of some use.

[https://wiki.ubuntu.com/WubiGuide#How can I access the Wubi files from Windows?](https://wiki.ubuntu.com/WubiGuide#How can I access the Wubi files from Windows?)

---

### Post by Rubi1200 on 2010-09-20
Unfortunately, it also looks as if whatever you did may have failed:
> sda1/Wubi: _________________________________________________________________________      File system:            Boot sector type:  Unknown     Boot sector info:       Mounting failed: mount: unknown filesystem type '' 

I am not sure if using a LiveCD will help you rescue the files, but it may be worthwhile trying that as well.

---

### Post by orangesoda22 on 2010-09-20
well, i installed ext2 and am looking for the files but im not sure where to look.

is there something specific i should try to look for to get into the partitioned section of my HDD?

---

### Post by wilee-nilee on 2010-09-20
I would boot the live Ubuntu cd and open gparted and look at the ntfs partition for a yellow triangle. If you see one right click and look at the information. It may be that the moving of the files to the wubi setup just triggered a auto chkdsk that needs to be run to get back in order, and this may be why the script doesn't show the Ubuntu correct as far as boot files go.

The line Rubi1200 is referencing should look like this,

Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

Also I am not sure about the mbr as well.

HP/Gateway is installed in the MBR of /dev/sda

Never seen a manufacturers name in this area before it would generally be the Windows 7 bootloader.

In the end I think you may not understand wubi, moving your files to it was not a good idea as when and if you remove windows wubi is gone unless you move it to a partition. The moving of the files from Windows to Ubuntu, if combined with deleting them from windows from Ubuntu is not safe.

---

### Post by Calash on 2010-09-20
Your drive is not partitioned.  Wubi puts all the disk information in a file.  In windows it would be /Ubuntu/winboot/

You will need to mount this using the Live CD and then ether extract your data to your windows drive or try to fix the install.

Fixing it is a bit beyond what I know but the Wiki I liked to may be of some help.

---

### Post by orangesoda22 on 2010-09-20
mounted it and looked in the directory. not seeing any files in it at all. im guessing this means theyre gone?

---

### Post by wilee-nilee on 2010-09-20
> **orangesoda22 said:**
> mounted it and looked in the directory. not seeing any files in it at all. im guessing this means theyre gone?

Look at gparted while your in the live cd environment for the yellow triangle in the partition header in the far left column.

---

### Post by orangesoda22 on 2010-09-20
> **wilee-nilee said:**
> Look at gparted while your in the live cd environment for the yellow triangle in the partition header in the far left column.



no yellow triangles. this is all im seeing.
[IMG]http://i53.tinypic.com/wa3rj7.jpg[/IMG]

---

### Post by wilee-nilee on 2010-09-20
Bump for that member who I know knows this stuff.;)

---

### Post by bcbc on 2010-09-21
according to the bootinfoscript, the root.disk is gone. It should be listed here:> Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/swap.disk


This can happen if windows thinks it is corrupted. Look in c:\FOUND.000 and hopefully it is sitting there (FOUND.000 is a hidden folder so you might have to adjust your settings in explorer to see it).

If you find it just copy it back to c:\ubuntu\disks\ and try booting.

Without the root.disk file there is no wubi. If you've put all your important data on this, then you need to back it up, or at least back up all the data stored within it.

---

