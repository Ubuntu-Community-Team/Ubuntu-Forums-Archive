---
title: "Please help make my menu.lst"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by G_Alexander on 2009-11-06
I have no menu.lst file, my laptop boots Ubuntu and there is a Windows 7 partition on the drive as well. I'd like to be able to choose which OS to boot on startup.

Can someone please advise what I should type ina  menu.lst file?

My partitions according to gparted are:

```

Partition             File System   Label          Flags
*********             ***********   ***********    **********
/dev/sda1             fat16         DellUtility    boot
/dev/sda2             ntfs          Recovery
unallocated    
/dev/sda4             extended                     lba
    /dev/sda6         ext4   /      
    /dev/sda7         linux-swap
    /dev/sda5         unknown 
unallocated

```

The windows partition is sda5 (linux is sda6). In disk utilty I checked 'bootable' for this partition now the file system for this partition has changed from NTFS to unknown... so now I'm also worried Windows 7 and the data on that partition is gone forever :(


Hope you guys can help! 

Many thanks
Grant

---

### Post by Byrd740 on 2009-11-06
Have you tried
```
sudo update-grub
```?

---

### Post by G_Alexander on 2009-11-06
Hi,

Yes tried that one (found that off google and hoped it would work but no joy).

Have also tried booting in to windows by  typing stuff (in to /boot/grub/menu.lst) I've found online like:

```

title Windows 7
rootnoverify (hd0,3)
savedefault
chainloader +1

```

But it doesn't seem to make any different whatsoever.

Thanks
Glen

---

### Post by enyoj on 2009-11-06
When you boot your laptop does it boot automatically into windows?  If so try restoring grub, it will create a valid menu.lst for you. Try:
```
sudo grub
find /boot/grub/stage1
```
see what it returns and replace the question mark in following code:
```
root (hd0,?)
setup (hd0)
quit
```
now reboot

Hope it helps

---

### Post by Byrd740 on 2009-11-06
> **G_Alexander said:**
> The windows partition is sda5 (linux is sda6). In disk utilty I checked 'bootable' for this partition now the file system for this partition has changed from NTFS to unknown... so now I'm also worried Windows 7 and the data on that partition is gone forever :(
If I am not mistaken, if Windoze is sda5 than it should not be included in the extended partition with Linux.  You need to separate it.  But, if it is not recognized as ntfs, than it might be corrupt.

---

### Post by screaminfakah on 2009-11-06
From what you posted the only NTFS partition is labeled Recovery.  That doesn't look good. I doubt the Windows partition would be labeled Recovery.  
Did you just install Ubuntu? Have you ever been able to dual boot?

---

### Post by G_Alexander on 2009-11-06
enjoy - I installed grub using apt-get so I could do that command. Within grub in the console, the find command doesn't find anything so can't complete that.

Byrd740 - I'm not sure how to go about doing that, I've attached a screenshot of gparted showing my partitions, could you suggest how to move windows out of the extended partition if you think that will help? thanks

screaminfakah - The partition with label RECOVERY will be Dell's windows vista recovery partition. The unknown is Windows 7 - I think it started saying unknown after I tried checking 'Bootable' in Disk Utility. Though now that I have unchecked 'Bootable' since it didn't work, Disk Utility sees the partition as an NTFS one.


Many thanks

---

### Post by screaminfakah on 2009-11-06
Not sure how that would have happened.
In the past I have used Super Grub Disc to fix my grub but in your case I dont know if that would help or make things worse.

---

### Post by kansasnoob on 2009-11-06
First of all Windows commonly does not like booting from a logical partition. Some history on how it got there would be nice.

I'd imagine since you're running Win 7 but have a Vista recovery partition you installed it that way? Has Win 7 ever been boot-able?

It all gets downright scary from there. You start off saying you have no menu.lst which would be correct if you have grub2, then later you say you installed grub using apt-get. If you started with grub2 (aka: grub-pc) and then ran the command apt-get install grub you'll likely soon find you can't boot anything.

So, lets begin by seeing the output of these commands:

```
cat /etc/issue
```

```
grub-install -v
```

```
ls /boot/grub
```

---

### Post by G_Alexander on 2009-11-06
Hi, thanks for your reply. Well, before I installed Ubuntu yesterday I had a Vista Partition and a Windows 7 partition, which used windows boot manager. I decided I wanted to ditch vista and keep Windows 7 whilst trying out Ubuntu. 

The vista partition was huge and the windows 7 one small, so I shrunk the vista one and grew the windows 7 one so they were both equal in size. Then I used gparted to delete the vista partition and in the ubuntu installer I used the 'use biggest free space' when asked what partition to use.

Up until now I have been able to access my windows 7 files from within ubuntu. But since checking 'bootable' and clicking apply in Disk Utility out of curiosity, I can no longer see the Windows drive in ubuntu, and gparted and disk utility see the old windows partition as an unknown file system.

I have tried the super grub CD as suggested above, and that only seems to see the linux operating system. I have tried using a vista CD (can't find my windows 7 one) and clicking 'repair', which said it has found and repaired a 'windows lornhorn' partition. That made me excited, but as far as I can see it hasn't actually done anything and when I try again the vista repair program can't find wrong anymore...

Hope this is still fixable, but if it definitely past the point of repair please let me know and I'll have to reluctantly reinstall windows and restore windows and a backup.

Many thanks

As requested:
```

grant@grant-laptop:~$ cat /etc/issue
Ubuntu 9.10 \n \l

grant@grant-laptop:~$ grub-install -v
grub-install (GNU GRUB 0.97)
grant@grant-laptop:~$ ls /boot/grub
915resolution.mod  gptsync.mod                     parttool.lst
acpi.mod           grub.cfg                        parttool.mod
affs.mod           grubenv                         password.mod
afs_be.mod         gzio.mod                        pci.mod
afs.mod            halt.mod                        play.mod
aout.mod           handler.lst                     png.mod
ata.mod            handler.mod                     probe.mod
ata_pthru.mod      hdparm.mod                      pxeboot.img
at_keyboard.mod    hello.mod                       pxecmd.mod
befs_be.mod        help.mod                        pxe.mod
befs.mod           hexdump.mod                     raid5rec.mod
biosdisk.mod       hfs.mod                         raid6rec.mod
bitmap.mod         hfsplus.mod                     raid.mod
blocklist.mod      iso9660.mod                     read.mod
boot.img           jfs.mod                         reboot.mod
boot.mod           jpeg.mod                        reiserfs.mod
bsd.mod            kernel.img                      scsi.mod
bufio.mod          keystatus.mod                   search.mod
cat.mod            linux16.mod                     serial.mod
cdboot.img         linux.mod                       setjmp.mod
chain.mod          lnxboot.img                     sfs.mod
cmp.mod            loadenv.mod                     sh.mod
command.lst        loopback.mod                    sleep.mod
configfile.mod     lsmmap.mod                      tar.mod
core.img           ls.mod                          terminfo.mod
cpio.mod           lspci.mod                       test.mod
cpuid.mod          lvm.mod                         tga.mod
crc.mod            mdraid.mod                      true.mod
datehook.mod       memdisk.mod                     udf.mod
date.mod           memrw.mod                       ufs1.mod
datetime.mod       menu.lst                        ufs2.mod
default            menu.lst~                       uhci.mod
device.map         menu.lst_backup_by_grub2_prerm  usb_keyboard.mod
diskboot.img       minicmd.mod                     usb.mod
dm_nv.mod          minix.mod                       usbms.mod
drivemap.mod       mmap.mod                        usbtest.mod
echo.mod           moddep.lst                      vbeinfo.mod
efiemu32.o         msdospart.mod                   vbe.mod
efiemu64.o         multiboot.mod                   vbetest.mod
efiemu.mod         normal.mod                      vga.mod
elf.mod            ntfscomp.mod                    vga_text.mod
ext2.mod           ntfs.mod                        video_fb.mod
extcmd.mod         ohci.mod                        video.mod
fat.mod            part_acorn.mod                  videotest.mod
font.mod           part_amiga.mod                  xfs.mod
fs_file.mod        part_apple.mod                  xnu.mod
fshelp.mod         part_gpt.mod                    xnu_uuid.mod
fs.lst             partmap.lst                     zfsinfo.mod
fs_uuid.mod        part_msdos.mod                  zfs.mod
gfxterm.mod        part_sun.mod

```

---

### Post by Paqman on 2009-11-06
What version of Ubuntu are you running? 

If it's the latest (9.10 "Karmic Koala") then your bootloader doesn't use the menu.lst file any more. The new version of Grub has a new way of doing things, so we'd need to give you different instructions.

---

### Post by G_Alexander on 2009-11-06
> **Paqman said:**
> What version of Ubuntu are you running? 

If it's the latest (9.10 "Karmic Koala") then your bootloader doesn't use the menu.lst file any more. The new version of Grub has a new way of doing things, so we'd need to give you different instructions.

Hi Paqman, yes it's 9.10. Thanks

---

### Post by oldfred on 2009-11-06
When you booted into windows before it then gave you a choice for Vista and Win7. When you installed Win7 it combined its boot with the Vista boot. That in fact is the only way to boot windows from an extended partition since it is really booting from the primary Vista partition. I do not think even the repair Win7 disk will fix this since it is in the extended partition. If Win7 was in a primary you could run the repair and reinstall all the boot files that are missing.

I do not know if it can be repaired but someone else may have gone thru the process if it is possible.

---

### Post by mbc2000 on 2009-11-06
Have you tried "sudo os-prober" followed by "sudo update-grub2"?  That worked for me when my Windows partition didn't show up after installing a Karmic alpha.

---

### Post by G_Alexander on 2009-11-06
> **mbc2000 said:**
> Have you tried "sudo os-prober" followed by "sudo update-grub2"?  That worked for me when my Windows partition didn't show up after installing a Karmic alpha.

Thanks, but didn't do anything (and update-grub2 wasn't found so I used update-grub).

I'm beginning to see the situtaion as... a fix for this isn't likely so the best options would be to shrink the linux partition in the extended partition, which I guess would allow me to increase the size of the primary partition uncllocated space and install windows in there which would allow me to try and recover my files. Plan b) count my losses and just delete the win7 partition in the extended parition, increase the primary partitiona and install win7 in there...

Either way, I'm glad I have a backup of the important stuff on a seperate system otherwise I'd be insane by now haha

Thanks

---

### Post by screaminfakah on 2009-11-06
[http://ubuntuforums.org/showthread.php?t=1192147](http://ubuntuforums.org/showthread.php?t=1192147)
Check this post.  User had same issue.

---

### Post by philinux on 2009-11-06
> **G_Alexander said:**
> I have no menu.lst file, my laptop boots Ubuntu and there is a Windows 7 partition on the drive as well. I'd like to be able to choose which OS to boot on startup.


Can you post back the output of this.

```
cat /boot/grub/grub.cfg
```

Remember to wrap code tags around it.

---

### Post by G_Alexander on 2009-11-06
> **screaminfakah said:**
> [http://ubuntuforums.org/showthread.php?t=1192147](http://ubuntuforums.org/showthread.php?t=1192147)
Check this post.  User had same issue.

Thanks v much, look promising, will read through tonight. After some wine I think anything will be possible.


Cheers philinux

```

grant@grant-laptop:~$ cat /boot/grub/grub.cfg
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,6)
search --no-floppy --fs-uuid --set 716985a6-63a8-4b59-93d2-c22754e2380a
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 716985a6-63a8-4b59-93d2-c22754e2380a
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=716985a6-63a8-4b59-93d2-c22754e2380a ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 716985a6-63a8-4b59-93d2-c22754e2380a
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=716985a6-63a8-4b59-93d2-c22754e2380a ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
grant@grant-laptop:~$ 


```

---

### Post by kansasnoob on 2009-11-06
Your "ls /boot/grub" shows that you did partially install legacy grub as does the output of "grub-install -v".

Your /boot/grub folder has both legacy grub abd grub2 files in it now. I doubt very much that you'll even be able to boot Ubuntu now.

When you install the package "grub" it automatically removes the package "grub-pc" which is grub2. So you need to figure out which grub you want to use.

The main text of the following HowTo describes how to install and set up legacy grub, whereas Appendix #2 describes very briefly how to reinstall and setup grub2:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

I have serious doubts that you can get the Win 7 partition to boot regardless, at least i don't know how, especially since you played with "disk utility".

---

### Post by philinux on 2009-11-06
Looks like the os-prober is failing to find the win7 partition. Maybe its because it's unknown. Maybe it's lost its partition boot record.

It should look something like this.
```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    set root=(hd0,1)
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###
```

Example in here [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

You could create a custom entry by adding your 40_custom file.

gksudo gedit /etc/grub.d/40_custom

And adding something similar but edited to your machine

```
menuentry "Whatever" {

      set root=(hd1,1)

      chainloader +1

      }
```

Dont forget hd0 is disk 1 and ,1 is the first partition.

then sudo update-grub

---

### Post by G_Alexander on 2009-11-06
> **kansasnoob said:**
> Your "ls /boot/grub" shows that you did partially install legacy grub as does the output of "grub-install -v".

Your /boot/grub folder has both legacy grub abd grub2 files in it now. I doubt very much that you'll even be able to boot Ubuntu now.

When you install the package "grub" it automatically removes the package "grub-pc" which is grub2. So you need to figure out which grub you want to use.

The main text of the following HowTo describes how to install and set up legacy grub, whereas Appendix #2 describes very briefly how to reinstall and setup grub2:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

I have serious doubts that you can get the Win 7 partition to boot regardless, at least i don't know how, especially since you played with "disk utility".

I can definitely still boot ubuntu. The disk utility is "palimpsest disk utility". I'll look through the other thread suggested tonight and if there's nothing there I fancy trying, I'll just delete all the partitions and start again. Thanks

---

### Post by G_Alexander on 2009-11-06
> **philinux said:**
> Looks like the os-prober is failing to find the win7 partition. Maybe its because it's unknown. Maybe it's lost its partition boot record.

Does that mean the partition cannot be recovered?

---

### Post by philinux on 2009-11-06
> **G_Alexander said:**
> Does that mean the partition cannot be recovered?

See post #20 I was busy editing it. lol

---

### Post by G_Alexander on 2009-11-06
Hi hi,

I ran TestDisk to try and repair things, which seemed to repair the Windows partition and damage the Ubuntu one.

In the end, I've deleted all partitions then installed Windows 7 then Ubuntu all over again (using the 'install alongside' option)... so I have a much cleaner partition table and a functioning dual boot system, hoorah!

Looking forward to trying to settle with Ubuntu now (whilst still relying on windows for the iphone). So thanks everyone for your help today, I'm sure I'll be back here again soon :)


Cheers
Grant

---

