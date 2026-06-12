---
title: "I Need Help with 10.04 install - restoring dual boot"
date: 2011-06-13
forum: New to Ubuntu
---

### Post by pstefanini on 2011-06-13
I upgraded from Karmic Koala to 10.04 (fresh install) and lost my dual boot option.  

I had one hard drive booting Windows 7 and a separate drive with Ubuntu (now 10.04).  I am fine with hitting F11 and changing hard drives to get either operating system. 

Somehow, the boot loader on the Windows drive was either overwritten or corrupted.  I get a GRUB error on a blank screen.  The Ubuntu loader shows the Windows 7 option but it doesn't work.

Does anyone have a solution or know the best way to correct this problem?    Thank you for any assistance!

---

### Post by oldfred on 2011-06-13
Best to see what is where first:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by pstefanini on 2011-06-13
Sorry Oldfred... I'm not good at this.  I can't seem to get the terminal command working.....  what is the insert in <output file>?

---

### Post by Quackers on 2011-06-13
Where did you download the file to? It will be a zip file - probably in your home folder or Downloads.

---

### Post by oldfred on 2011-06-13
If it downloads like mine, it will be in Downloads. I use Nautilus and double click on the .zip file and it opens, I then click on extract and boot_info_script.sh is saved in /Downloads.

I then open terminal, Applications, Accessories, Terminal 
I change to Downloads. And the results are in Downloads as results.txt (mine is long as I have 3 drives and it is results2.txt as I have run it before). Open results.txt and copy & paste the contents in a new post. Then highlight and click on the # in the edit panel to put into code tags.

```
fred@fred-MavericDT:~$ cd Downloads
fred@fred-MavericDT:~/Downloads$ sudo bash boot_info_script.sh 
[sudo] password for fred: 

boot_info_script version: 0.60        [17 May 2011]

Identifying MBRs...
Computing Partition Table of /dev/sda...
Computing Partition Table of /dev/sdb...
Computing Partition Table of /dev/sdc...
Computing Partition Table of /dev/sdd...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda4 for information... 
Searching sdb1 for information... 
Searching sdb2 for information... 
Searching sdb3 for information... 
Searching sdb4 for information... 
Searching sdc1 for information... 
Searching sdc2 for information... 
Searching sdc3 for information... 
Searching sdc5 for information... 
Searching sdc6 for information... 
Searching sdc7 for information... 
Searching sdc8 for information... 
Searching sdc9 for information... 
Searching sdc10 for information... 
Searching sdc11 for information... 
Searching sdc12 for information... 
Searching sdc13 for information... 
Searching sdc14 for information... 
Searching sdc15 for information... 
Searching sdd1 for information... 

Finished. The results are in the file "RESULTS2.txt"
located in "/mnt/data/Downloads/".


```

---

### Post by pstefanini on 2011-06-15
OldFred... I hope you are still there.  It took me some time to do this (work sometimes gets in the way).  Anyway here is the output file:
                 Boot Info Script 0.60    from 17 May 2011

```

============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sdb1 and looks at sector 272575 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /NTDETECT.COM

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   964,702,207   964,700,160  83 Linux
/dev/sda2         964,704,254   976,773,119    12,068,866   5 Extended
/dev/sda5         964,704,256   976,773,119    12,068,864  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   268,414,019   268,413,957   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        c386697b-38e3-4214-9898-9b91a5e0384b   ext4       
/dev/sda5        ca88e1f9-1ee3-4bff-a8d0-0b80d8e6f8e4   swap       
/dev/sdb1        8E7407067406F12F                       ntfs       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set c386697b-38e3-4214-9898-9b91a5e0384b
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set c386697b-38e3-4214-9898-9b91a5e0384b
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
menuentry 'Ubuntu, with Linux 2.6.32-32-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c386697b-38e3-4214-9898-9b91a5e0384b
	linux	/boot/vmlinuz-2.6.32-32-generic root=UUID=c386697b-38e3-4214-9898-9b91a5e0384b ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-32-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c386697b-38e3-4214-9898-9b91a5e0384b
	echo	'Loading Linux 2.6.32-32-generic ...'
	linux	/boot/vmlinuz-2.6.32-32-generic root=UUID=c386697b-38e3-4214-9898-9b91a5e0384b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-32-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c386697b-38e3-4214-9898-9b91a5e0384b
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c386697b-38e3-4214-9898-9b91a5e0384b
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
	insmod ntfs
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 8e7407067406f12f
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=c386697b-38e3-4214-9898-9b91a5e0384b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ca88e1f9-1ee3-4bff-a8d0-0b80d8e6f8e4 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 378.129829407 = 406.013812736  boot/grub/core.img                             1
  24.239933014 = 26.027429888   boot/grub/grub.cfg                             1
 378.258407593 = 406.151872512  boot/initrd.img-2.6.32-32-generic              1
 378.141132355 = 406.025949184  boot/vmlinuz-2.6.32-32-generic                 1
 378.258407593 = 406.151872512  initrd.img                                     1
 378.141132355 = 406.025949184  vmlinuz                                        1

```
```

```

---

### Post by oldfred on 2011-06-16
You have grub in the windows boot sector. Windows has to have its code in the partition boot sector. 

```
sdb1: _________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   [COLOR=Red]Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sdb1 and looks at sector 272575 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.[/COLOR]
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /NTDETECT.COM

```

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

If you want you can also install a windows boot loader to the MBR of sdb. I like to have each drive boot independently. Or so each drive could be removed and still work.

Restore basic windows boot loader - universe enabled
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing testdisk with Synaptic.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

If windows then boots ok from one time boot key or BIOS to select sdb, then boot sda and run this to find the windows install. Set BIOS to boot sda and you have a choice from the grub menu.

sudo update-grub

You can also use a windows repair disk for repairs. But the neosmart download site does not have it "checking for copyright issues" or MS must be giving issues.  If you can make a windows repair CD from your recovery partition you should.
BootRec.exe /FixBoot  #updates PBR partition boot sector

---

### Post by pstefanini on 2011-06-16
OldFred:  I just got home and couldn't wait to see if you or anyone responded.   Man, you are good!  I'm going to do this now and let you know.  You are in Chicago Suburbs I see.  Are you a Little Walter/Chicago Blues fan... I am, even though I'm from Boston... anyway, I digress though I am very grateful for your expertise and thorough analysis of a difficult problem (for me anyway)... I will take it step at a time and let you know how I manage.  Regardless the outcome... thank you in advance for your time, super help and willingness to stick with me!!!  Phil

---

### Post by oldfred on 2011-06-16
I just notice I posted installing lilo's boot loader to sda. Teach me just to copy & paste. Most windows are on sda. You should set BIOS to boot sdb and then install the lilo boot loader to sdb. I am not sure if BIOS is booting sda it may not work. I know lilo boots windows when it is on the same drive, not sure about different drives.

---

### Post by pstefanini on 2011-06-16
I ignored the warning so I was too hasty myself.  Unfortunately no boot from startup or from either drive once BIOS...  indicating:

>grub rescue 

OldFred... I'm not sure what to do at this point.  I'm using my work laptop...your help appreciated.  I still want to thank you for your help. 

If worse comes to worse, I can start over though I will loose some files on the Windows side.  Phil

---

### Post by pstefanini on 2011-06-16
The warning i got during lilo install was to run LILO configuration before completing 'the process'.  I didn't get whaat it meant but it may have been what locked everything up.  Phil

---

### Post by pstefanini on 2011-06-16
I'm "Ready to (Re-)Install" 10.04 on my 500G drive.   I'm at the menu that asks me to confirm indicated settings:

Among things like location and keyboard... it lists:

Windows 7(loader)(/dev/sdb1):

This menu also liss 'advanced options' that let me check off "Install boot loader" and drop down menu of devices for boot loader installation.  The drop down menu indicates the following choices:

/dev/sda       ATA ST 500GB HD that has Ubuntu 10.04 now)
/dev/sda1      Ubuntu 10.04.2 LTS (10.04) 
/dev/sdb       ATA WDC 160GB HD that has Win7 on it
/dev/sdb1      Windows 7 (loader)
/dev/sdb-1     

What do suggest I do at this point?

Thank you!  Phil

---

### Post by pstefanini on 2011-06-16
Well... for better or worse... I stuck with the default, hit the 'install' key.  

BTW Ubuntu 10.04 is really excellent.  Everything I have worked first time, no problems.

---

### Post by s3a on 2011-06-16
I don't feel like reading everything above. Are you still having a problem? If so, can you summarize it?

---

### Post by pstefanini on 2011-06-16
Yes.  I will try.  

I lost my dual boot option on Window7 when I upgraded to Ubuntu 10.04, I have two hard drives; one runs windows7 and the other Ubuntu 10.04.  OldFred helped me download my hard drive boot config.  Then he suggested several options and I tried to restore using a "LILO Installation" program but got that wrong and ended up losing the ability to boot Ubuntu as well.

I reinstalled Ubuntu 10.04 about an hour ago and I'm back to the original problem.  The computer wont' boot at startup unless I go into Bios and choose the Ubuntu drive... but I'm back up with 10.04 at least.

What is the best way to restore a Windows7 dual boot.  I'm very happy allowing Windows 7 as the default and hitting F11 to choose my Ubuntu hard drive.

Thank you.  Phil

---

### Post by oldfred on 2011-06-16
Just to make sure we are installing to the correct drive, and you have reinstalled, please post a new copy of boot info script.

I think if I had you install Lilo to sdb, it would have booted windows from sdb. The error is lilo is a full boot loader and wants its code installed. We do not want its code just its boot loader as its boot loader works like windows in jumping to the partition boot sector to continue to boot.

When you installed lilo to sda, it overwrote grub2's boot loader in sda. You should not have had to reinstall Ubuntu but just reload grub2's boot loader to sda.

If you boot Ubuntu using sda, and run this does it now add windows to the menu?
sudo update-grub

---

### Post by s3a on 2011-06-17
Click System=>Administration=>Gparted (or partition editor or whatever it's called) to find out which what your drives are "called".

I am guessing your Ubuntu 10.04 is /dev/sda. What's your Windows hard drive?

If oldfred's sudo update-grub doesn't do it (it should), then do sudo grub-install /dev/sda and sudo grub-install WTV where "WTV" (without the quotes) is replaced by what your Windows hard drive is "called" (determined from Gparted).

_If none of these work, then do_:
sudo rm -rf /boot/grub/grub.cfg
followed by the sudo grub-install /dev/sda and sudo grub-install WTV commands.

If I am unclear somewhere, just tell me.

---

