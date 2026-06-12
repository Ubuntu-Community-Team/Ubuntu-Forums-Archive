---
title: "Unable to boot Windows after installing Ubuntu."
date: 2011-04-03
forum: New to Ubuntu
---

### Post by piyuh91 on 2011-04-03
I just installed Ubuntu 10.10 on my Windows 7 using CD.
I manually made the partitions and now I am not able to run windows 7.
In the Grub menu I dont see Windows 7 option.
Please Help.

---

### Post by piyuh91 on 2011-04-03
I just installed Ubuntu 10.10 on my Windows 7.
I did manual partitions and now I am unable to boot windows.
Windows option is not there in the grub menu.
Please Help!

---

### Post by Quackers on 2011-04-03
Welcome to UF.
Have you run ```
sudo update-grub
``` in the terminal?

---

### Post by The Cog on 2011-04-03
Can you run Ubuntu?

If so, does this fix it? start a command prompt with Applications->Terminal and enter the command
```
sudo update-grub
```and then reboot and try again.

It may also be worth posting the output of the command
```
sudo parted -l
```
to see what partitions there are. I'm hoping the windows partition is still there.

---

### Post by Quackers on 2011-04-03
See your other thread in Absolute Beginner Talk forum.
Please don't ask the same question in two different forums.

---

### Post by piyuh91 on 2011-04-03
Hello,
Yeah I tried sudo update-grub.
But it didnt help.
And I have attached the screenshot of the output of sudo parted -l.
Please check it out and help me.
Thanks a lot.

---

### Post by Quackers on 2011-04-03
No Windows partitions appear in that. Could you have over-written Windows with 10.10?
To confirm, please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by piyuh91 on 2011-04-03
Oh Sorry!
I was confused as to in which section should I post the thread as this is my first thread therefore posted in both sections.

---

### Post by piyuh91 on 2011-04-03
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/grub.
 => No boot loader? is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       976,895       974,848  83 Linux
/dev/sda2             976,896    40,038,399    39,061,504  83 Linux
/dev/sda3          40,038,400    49,803,263     9,764,864  82 Linux swap / Solaris
/dev/sda4          49,805,310    88,864,767    39,059,458   5 Extended
/dev/sda5          49,805,312    88,864,767    39,059,456  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 128 MB, 128974848 bytes
8 heads, 32 sectors/track, 984 cylinders, total 251904 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  32       250,623       250,592   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        20d41fe0-f516-431f-ba16-d00295d0bfc7   ext4                                     
/dev/sda2        dc33aa93-dc74-4158-9893-7d8e1ea2c6d6   ext4                                     
/dev/sda3        3e6c0b08-e38f-4b4f-a58a-6326865bb4dc   swap                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        e94ea4cf-2eb1-4393-a86c-5ef61ce9be4b   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        17E9-242F                              vfat       USB MEMORY                    
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/USB MEMORY        vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


============================= sda1/grub/grub.cfg: =============================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set dc33aa93-dc74-4158-9893-7d8e1ea2c6d6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 20d41fe0-f516-431f-ba16-d00295d0bfc7
set locale_dir=($root)/grub/locale
set lang=en
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 20d41fe0-f516-431f-ba16-d00295d0bfc7
	linux	/vmlinuz-2.6.35-22-generic root=UUID=dc33aa93-dc74-4158-9893-7d8e1ea2c6d6 ro   quiet splash
	initrd	/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 20d41fe0-f516-431f-ba16-d00295d0bfc7
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/vmlinuz-2.6.35-22-generic root=UUID=dc33aa93-dc74-4158-9893-7d8e1ea2c6d6 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 20d41fe0-f516-431f-ba16-d00295d0bfc7
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 20d41fe0-f516-431f-ba16-d00295d0bfc7
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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

=================== sda1: Location of files loaded by Grub: ===================


    .1GB: grub/core.img
    .1GB: grub/grub.cfg
    .0GB: initrd.img-2.6.35-22-generic
    .0GB: vmlinuz-2.6.35-22-generic

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda2       /               ext4    errors=remount-ro 0       1
/dev/sda1       /boot           ext4    defaults        0       2
# /home was on /dev/sda5 during installation
UUID=e94ea4cf-2eb1-4393-a86c-5ef61ce9be4b /home           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=3e6c0b08-e38f-4b4f-a58a-6326865bb4dc none            swap    sw              0       0
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000060  00 00 00 00 00 00 00 00  ca 30 43 30 00 00 00 88  |.........0C0....|
00000070  ff 81 9f 9e 1c 43 72 42  a2 75 22 eb 86 5a b7 ba  |.....CrB.u"..Z..|
00000080  00 03 00 00 01 00 01 00  2f 00 00 00 48 70 5a 00  |......../...HpZ.|
00000090  ff ff ff ff 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000a0  00 00 00 00 a5 1a 49 77  f0 8f 57 00 02 00 00 00  |......Iw..W.....|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000140  ef 30 43 30 00 00 00 88  ff 81 9f 9e 1c 43 72 42  |.0C0.........CrB|
00000150  a2 75 22 eb 86 5a b7 ba  04 03 00 00 01 00 01 00  |.u"..Z..........|
00000160  30 00 00 00 70 70 5a 00  ff ff ff ff 00 00 00 00  |0...ppZ.........|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 a5 1a 49 77  |..............Iw|
00000180  50 90 57 00 02 00 00 00  00 00 00 00 00 00 00 00  |P.W.............|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 fe  |................|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 00 54 02 00 00  |............T...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

I have done the same steps and here are the contents of that file.
Thanks a Lot.

---

### Post by Quackers on 2011-04-03
Thanks for the script output.
Unfortunately it confirms that there are no Windows partitions or operating system on your machine. It seems that you have over-written Windows with Ubuntu.
The new partitions that you made wiped out Windows. Also, if you had a recovery partition originally (for Windows) it has been over-written too.
Do you have a Windows installation disc, or a set of recovery dvd's?

---

### Post by piyuh91 on 2011-04-03
OH ****!
I am so dead.
Yeah I do have all the recovery disks.
But is there anyway that I can recover my data?


Thanks.

---

### Post by Quackers on 2011-04-03
It may be possible to recover data, but it is likely to be a long process. If that is your intention you should stop using Ubuntu now and use only the live cd desktop. If you continue writing to the hard drive by using the system you will over-write any data that is still left.
You should take a look at testdisk and have a read through this guide
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)

Also bear in mind that Windows cannot be installed to a logical partition. It must be installed to a primary partition (which you don't have one spare), or at least its boot files do.

---

### Post by piyuh91 on 2011-04-03
Ohk thanks a lot for your support.
I ll do exactly the same and hope that i get back my data.
Thanks a lot.

---

### Post by Darth Penguin on 2011-04-03
Download and burn the Windows 7 recovery disc. You said you have recovery discs but I mention it so other people can fix this problem if they don't have a recovery disc.

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

Boot from that disk and choose the command line option.

Type in **bootrec.exe /FixMbr** then press Enter.

Type in **bootrec.exe /FixBoot** then press Enter.

Restart the computer.

Once you log on to Windows, download [EasyBCD](http://neosmart.net/dl.php?id=1) and add an entry for Ubuntu. Select **Grub 2** when you create an entry for Ubuntu, then save settings. You can then dual boot both operating systems.

---

### Post by Quackers on 2011-04-03
Erm, there's no Windows left to repair.

Good luck with testdisk piyuh91. I'm not sure whether testdisk is available on the live cd, you may need to install it through synaptic package manager first.

---

### Post by The Cog on 2011-04-03
I merged the thread from General Help with this one. Looking at the messy result, maybe that was a mistake. 

Quackers suggestion of testdisk is probably your best bet now. With any luck Ubuntu will have mostly overwritten XP and your data files will still mostly be there. I've never tried to use testdisk, but I think it might let you recover the files to a USB drive, after which you can start again with the internal drive.

---

### Post by JamesBartlett on 2011-04-03
I hate to be the bearer of bad news, but I had a PC with MS Windows 7 and installed Ubuntu to play around with. I was hoping, like you, to set-up a partition with Ubuntu on one, and Windows on the other, and the option to choose when I booted the computer. However like you, Ubuntu seems to have replaced Windows on my Hard Drive, Windows neither appears in any diagnostic, or in BIOS. However, I have a 320gb hard drive, yet Ubuntu is only detecting 270gb, and I know my Windows OS plus my data and programs amounted to approximately 50gb. Check the same thing. How much space is UBuntu detecting on your hard drive compared to what you know to be the total capacity? If you're not sure of the capacity, turn your machine off and unplug it, open the back and have a look at the hard drive. If you're not sure what it looks like, ITs normally located (but not always) at the front of the casing if you have a desktop, its a silver box about 3.5 inches long, 2(ish) wide, and only about a centimetre deep. It will have a cable with a shitload of wires going to it. Unscrew it (carefully) and it should tell you the capacity somewhere on the label. Its much easier than it sounds! Just dont lose the screws and remember where the hard drive went. ;)

I don't know of any solutions yet based on this, but hopefully someone else might... Good luck!

---

### Post by Quackers on 2011-04-03
JamesBartlett, please start your own thread.
It would also be useful to include the output of the bootscript.
Please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by piyuh91 on 2011-04-04
Guys I am unable to install testdisk.
Please help me out!

---

### Post by Quackers on 2011-04-04
Why is that?
In a terminal from the live cd desktop run```
sudo apt-get install testdisk
``` once you have an internet connection.
Or first just check that it isn't installed please. System > Admin > Synaptic package manager and enter testdisk in the search box. When testdisk appears in the main window of synaptic it will have a green box to its left, if it is already installed.
There is no GUI for testdisk, it is run from the terminal.

---

### Post by piyuh91 on 2011-04-04
Should I do this in the "Try Ubuntu" when I put the CD or the ubuntu installed in my hard drive?

---

### Post by Quackers on 2011-04-04
Yes. You don't really want to be using your normal Ubuntu installation if you want to recover data from the system.

---

### Post by piyuh91 on 2011-04-04
Oh.
That was the mistake I was making.
I was trying to run testdisk from the ubuntu installed on my hard drive and not from the try ubuntu from the disk.
But now when I try "sudo apt-get install testdisk" 
it says "Unable to locate package testdisk"
Please Help
Thanks

---

### Post by piyuh91 on 2011-04-04
I have tried sudo apt-get update install also.
Still it gives that error only.
And its not there in synaptic package manager also.

---

### Post by coffeecat on 2011-04-04
> **piyuh91 said:**
> Oh.
That was the mistake I was making.
I was trying to run testdisk from the ubuntu installed on my hard drive and not from the try ubuntu from the disk.
But now when I try "sudo apt-get install testdisk" 
it says "Unable to locate package testdisk"
Please Help
Thanks

> **piyuh91 said:**
> I have tried sudo apt-get update install also.
Still it gives that error only.
And its not there in synaptic package manager also.

Hi, I haven't read through all the thread yet, but I noticed this.

It's an irritation with the live CD. Testdisk is in the Universe repository and although the Universe repository is enabled in a default permanent installation, it isn't in the live CD session. I don't know why.

Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing testdisk with Synaptic.

Good luck!

---

### Post by Quackers on 2011-04-04
Sorry piyuh91, I forgot about the repository!
Thanks coffeecat :-)

---

### Post by piyuh91 on 2011-04-04
Hey,
Thanks a lot!
It worked.

---

### Post by Quackers on 2011-04-04
Good :-)
If you follow Herman's advice, in the link that I posted earlier and take your time, you may be able to recover your Windows partition. This is likely to over-write your Ubuntu, but that can be replaced, if necessary.
Good luck.

---

### Post by piyuh91 on 2011-04-04
Yeah thanks.
But I am getting little confused at 1 step.
After I selected my hard drive and put it into "Analyse" 
I get this screen.
And I dont know what to do next.
Can you please help me here also.

```
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 320 GB / 298 GiB - CHS 38914 255 63
     Partition               Start        End    Size in sectors
* FAT32                    0   1  1     9 254 63     160587 [NO NAME]
P FAT32 LBA               10   0  1  4187 254 63   67119570 [ Unlabeled]
P Linux                 6279 130 60  7272 185 17   15955968
L HPFS - NTFS           9132 176  5 38913  70  5  478425088








Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
NTFS, 244 GB / 228 GiB


```

---

### Post by Quackers on 2011-04-04
fadimoh, please start your own thread giving full details of what has happened and what you now see at boot, thanks.

piyuh91,
I have not used testdisk, but having looked at the guide, I would say use the down arrow to highlight the last entry (HPFS) then press the left or right arrow until a * appears to its left (instead of the L) then press enter to proceed.

---

### Post by piyuh91 on 2011-04-04
Ohk I did that.
And now it says "Invalid Partition Structure"
:(

---

### Post by coffeecat on 2011-04-04
@piyuh91, this isn't of immediate help but I'm posting this link for the record.

[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

It might be worth your looking through that.

The other thing you might need to consider is that if you can't manage to restore the lost Windows partition with testdisk, you may be able to recover personal files with photorec which comes with testdisk. There are instructions for photorec on that link.

---

### Post by Quackers on 2011-04-04
Here is another link which gives explanations. Sorry if I'm not much use now - I'm a bit out of my depth here!
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by coffeecat on 2011-04-04
> **piyuh91 said:**
> Ohk I did that.
And now it says "Invalid Partition Structure"
:sad:

When you get to this screen:

> **piyuh91 said:**
> ```
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 320 GB / 298 GiB - CHS 38914 255 63
     Partition               Start        End    Size in sectors
* FAT32                    0   1  1     9 254 63     160587 [NO NAME]
P FAT32 LBA               10   0  1  4187 254 63   67119570 [ Unlabeled]
P Linux                 6279 130 60  7272 185 17   15955968
L HPFS - NTFS           9132 176  5 38913  70  5  478425088








Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
NTFS, 244 GB / 228 GiB


```If you highlight the first partition and press enter, you should get the choice to do a deep scan. This will take some time.

---

### Post by piyuh91 on 2011-04-04
Ohk I did that.
And here is the result that appeared.
please tell me what to do next.
```
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 320 GB / 298 GiB - CHS 38914 255 63
     Partition               Start        End    Size in sectors
D FAT32                    0   1  1     9 254 63     160587 [NO NAME]
D Linux                    0  32 31    60 206 16     974848
D Linux                    0  32 33    60 206 18     974848
D FAT32 LBA               10   0  1  4187 254 63   67119570 [ Unlabeled]
D HPFS - NTFS             10  18  9  1299 238 27   20721664 [RECOVERY]
D Linux                   60 206 19  2492  37 41   39059456
D Linux                 1128 120 17  3559 206 39   39059456
D Linux                 1131 167 61  3562 254 20   39059456
D Linux                 1133 178  6  3565   9 28   39059456
D HPFS - NTFS           1299 238 27  2589 203 45   20721664
D HPFS - NTFS           1299 238 28  9132 111  3  125829120
D HPFS - NTFS           1299 238 28  9132 143 35  125831168
D Linux Swap            2492  70 11  3100  27 47    9764848
D Linux                 3100  60 33  5531 146 55   39059456
D Linux                 6279 130 60  7272 185 17   15955968
D Linux                 6291 224 14  7285  23 34   15955968
D Linux                 6292  34 15  7285  88 35   15955968
D Linux                 6321 246  6  7315  45 26   15955968
D HPFS - NTFS           9132 143 35 16965  48 42  125831168
D HPFS - NTFS           9132 143 36 38913  37 36  478425088
D HPFS - NTFS           9132 176  5 38913  70  5  478425088






Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
FAT32, 82 MB / 78 MiB


```

---

### Post by Quackers on 2011-04-04
How are you doing? Any further or are you still at the above point?
The answer to your question is I don't know :-(
I can see a recovery partition which was doubtless on your pc before you installed Ubuntu.
I can also see 6 other NTFS entries, but I'm not sure about which of those you should try to recover. Some of them appear to be duplicated. 

We need somebody with some testdisk experience to come along.

At least this post will bump the thread back to the top again :wink:

---

### Post by piyuh91 on 2011-04-04
Yeah I have got struck on the last code that I have posted.
The problem is now I dont know which partition to make bootable or primary.
There are no files in FAT32.
In FAT32 LBA there are quite a number of files.
In HPFS-NTFS there are two files but dont have any name or anything and with everything in numeric columns as 0.
The last HPFS-NTFS partition has all my D-drive data.
I can see all my D-drive folders in there.
And in all the other HPFS-NTFS partitions there is nothing.

So If anyone can figure out some solution using the data I have provided please let me know ASAP.

Thanks.

---

### Post by Quackers on 2011-04-04
Try to get back to the screen you posted in post 29.

From your recent comments it seems that the C: partition may have been badly damaged, so we may have nothing to lose, apart from Ubuntu, which can be re-installed easily enough.
At that screen (from post 29) where it lists 4 partitions with the last one having a "L" to its left - what happens if you press enter?

---

### Post by piyuh91 on 2011-04-06
Ohk I managed to recover back my D-drive using testdisk.
And i can see that no windows boot file is there and C-drive also has got corrupted so i can' t boot my windows 7 and since i recoverd my D-drive ubuntu also is not there so i am left with option of using live cd only.
I tried using wondows recovery disc but it wont boot ,I dont know why.
It gives me an error
"Error;Unknown Filesystem
Grub Rescue>"
Someone please help me and tell me how to get rid of this error so that my windows 7 recovery disk can boot.

Thanks.

---

### Post by Quackers on 2011-04-06
Use the live cd desktop to backup any files you need from the D: partition.

What recovery disc are you using to try to recover Windows? In my experience there is more than one and they are dvd's - though some systems may be different.
At the time you recovered the D: partition, did you also recover the Recovery partition mentioned by testdisk?

---

### Post by piyuh91 on 2011-04-06
How do I backup files using live cd?
And yeah there are 2 dvd.
they are "Dell recovery disks" but for some reason they are not working.
they do boot but during recovery just freezes at some point.
Then I have windows 7 recovery disk which I burnt using the link given by Coffeecat in my thread on 2nd page which obviously is not even booting and that pathetic error is coming.

---

### Post by piyuh91 on 2011-04-06
Sorry the link was given by "Darth Penguin" and not "Coffeecat'.
Just got confused.

---

### Post by Quackers on 2011-04-06
Does the D: partition appear in the Places menu of the live desktop? If so, just copy the files needed to a cd or usb stick.
You need to use the Dell Recovery discs to recover the system. The Win 7 disc is almost certainly a "repair" disc - which has no operating system on it.
It may be worthwhile to use gparted from the live desktop to delete all current partitions (once you have backed up what you need) and reformat the disc as one NTFS partition - though it shouldn't need that afaik.

Also try wiping the discs carefully first. And make sure you are using disc 1 first!
If they still won't run, contact Dell and tell them the discs won't run. See what they say.

---

### Post by piyuh91 on 2011-04-06
OH ****!
I am one hell of an IDIOT!
Yeah the files do appear in Places.
It was just so silly of me to not even try and see whats there in places.
Thanks a lot.
After backing up my data I might i even consider doing a fresh installation.
Yeah but before that i ll have to delete my partitions using gparted.

Thanks.

---

### Post by Quackers on 2011-04-06
No problem. Good luck.

---

### Post by piyuh91 on 2011-04-06
Thanks.
You are truly awesome!

---

