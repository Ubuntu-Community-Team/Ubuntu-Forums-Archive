---
title: "Unable to repair grub using Ubuntu 9.10 (Karmic) Live-CD."
date: 2010-03-29
forum: New to Ubuntu
---

### Post by scrypt on 2010-03-29
Hey all.

I am having an issue repairing grub on my Dell laptop.

I did have Windows 7 and Ubuntu 9.10 (Karmic). On A dual boot system with grub controlling my OS choice and boot process.
Until I had to reinstalled Windows 7. Now I can only boot into Windows 7. 
I still have my Ubuntu on the partition it was originally installed. just NO option to choose between my Two Operating Systems. Since the Windows 7 re-installation has wiped grub and the option to boot into Ubuntu from my system.

I have Dual booted for quite some time now and I always found grub really easy to repair by just popping in my Ubuntu Live-CD and following these instructions ::

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)  

(Thank's Catlett for your great concisive post)

But. Since Ubuntu has upgraded to 9.10 Karmic I am finding it difficult to repair grub easily using the Ubuntu live-CD. and the above Ubuntu thread's instructions.

What has changed about grub since the last Ubuntu Upgrade. From Ubuntu 9.08 to Ubuntu 9.10 ?

Also. How can I easily repair grub on my Dell laptop. Using the Ubuntu 9.10 Karmic installation Live-CD.
 So I can once again choose between Windows 7 and Ubuntu using grub as my bootloader ?

Thank's in advance for any help

---

### Post by sisco311 on 2010-03-29
[uhelp]community/Grub2#Reinstalling%20from%20LiveCD[/uhelp]

---

### Post by scrypt on 2010-03-30
thnaks for your reply

I have tried using the instructions from your link but i am unable to repair grub2 using this because when i run the ::

ubuntu@ubuntu:~$ sudo mount /dev/sda3 /mnt 
command it gives me this output:

mount: you must specify the filesystem type

I do not know what file type i should choose. or how to write the right command.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x18000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       31081   249553920    7  HPFS/NTFS
/dev/sda3           31082       38913    62910540    5  Extended
/dev/sda5           31082       38588    60299946   83  Linux

Disk /dev/sdb: 1999 MB, 1999568384 bytes
255 heads, 63 sectors/track, 243 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00013ec3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         243     1951866    6  FAT16

ubuntu@ubuntu:~$ sudo mount /dev/sda3 /mnt
mount: you must specify the filesystem type

my windows7 partition is on my largest partition and I am unsure which partition I should use to repair grub2.

Can you help me with this ?

---

### Post by sisco311 on 2010-03-30
/dev/sda3 is the extended partition, Ubuntu's root partition is /dev/sda5:
```
sudo mount /dev/sda5 /mnt
```

---

### Post by scrypt on 2010-03-30
hey

I have tried using

sudo mount /dev/sda5 /mnt 

this seems to mount it successfuly

but when i run 

sudo grub-install --root-directory=/mnt/ /dev/sda5

I get these errors ::

---

### Post by sisco311 on 2010-03-30
You have to install grub to the MBR, the second command is:
```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

---

### Post by scrypt on 2010-03-30
okay that worked successfuly after running the two commands i now get this output ::

ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
mount: /dev/sda5 already mounted or /mnt busy
mount: according to mtab, /dev/sda5 is already mounted on /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sda
Installation finished. No error reported.
This is the contents of the device map /mnt//boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)	/dev/sda

---

### Post by sisco311 on 2010-03-30
Looks good, reboot to see if it worked.

---

### Post by scrypt on 2010-03-31
Hey 

Im still having trouble with this.

I ran the above commands and they seemed to work fine.

When I reboot I do enter grub as my bootloader.

But when I choose Ubuntu I am met with karmic splash screen then I am met with this error :

One or more of the mounts listed in /etc/fstab
cannot yet be mounted: swap: waiting for UUID=24a39a90-c6e1-42a8-a437-37564625b082
press esc to enter a recovery shell.

I then press escape and I am met with my Ubuntu logon screen.
I enter my password and then boot into a normal Ubuntu desktop.

I also cannot boot into my windows OS either.
it is on my grub bootloader screen. but if I select it. grub just then reloads.

any more help wold be appreciated

---

### Post by sisco311 on 2010-03-31
Please post the output of:
```
cat /etc/fstab
sudo blkid
sudo cat /boot/grub/grub.cfg
```

---

### Post by scrypt on 2010-03-31
-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=4fbbe068-d073-4a87-a668-3743b50ac715 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=24a39a90-c6e1-42a8-a437-37564625b082 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
-laptop:~$ sudo blkid
[sudo] password for : 
/dev/sda1: UUID="B82686812686407C" LABEL="System Reserved" TYPE="ntfs" 
/dev/sda2: UUID="B0FE8A1BFE89D9CC" TYPE="ntfs" 
/dev/sda5: UUID="4fbbe068-d073-4a87-a668-3743b50ac715" TYPE="ext4" 
laptop:~$


I also just rebooted and the option to choose to boot into windows is NO longer on my grub boot screen.

---

### Post by sisco311 on 2010-03-31
The swap partition (sda6) doesn't exist. Did you reformat it?

please post the output of:
```
sudo fdisk -l
``` 

```

sudo cat /boot/grub/grub.cfg

```

---

### Post by scrypt on 2010-03-31
No i have not reformatted anything.

laptop:~$ sudo fdisk -l
[sudo] password for mark: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x18000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       31081   249553920    7  HPFS/NTFS
/dev/sda3           31082       38913    62910540    5  Extended
/dev/sda5           31082       38588    60299946   83  Linux


laptop:~$ sudo cat /boot/grub/grub.cfg
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
set root=(hd0,5)
search --no-floppy --fs-uuid --set 4fbbe068-d073-4a87-a668-3743b50ac715
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
menuentry "Ubuntu, Linux 2.6.31-21-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 4fbbe068-d073-4a87-a668-3743b50ac715
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=4fbbe068-d073-4a87-a668-3743b50ac715 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 4fbbe068-d073-4a87-a668-3743b50ac715
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=4fbbe068-d073-4a87-a668-3743b50ac715 ro single 
	initrd	/boot/initrd.img-2.6.31-21-generic
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
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
-laptop:~$

---

### Post by sisco311 on 2010-03-31
Edit:

Comment out the swap partition's entry in the fstab:
```
gksu gedit /etc/fstab
```

```
...
# / was on /dev/sda5 during installation
UUID=4fbbe068-d073-4a87-a668-3743b50ac715 / ext4 errors=remount-ro 0 1
# swap was on /dev/sda6 during installation
**#**UUID=24a39a90-c6e1-42a8-a437-37564625b082 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
..
```

I don't know what happened to the partition, but it no longer exists.

---

### Post by sisco311 on 2010-03-31
Try to upgrade your system:
```
sudo apt-get update
sudo apt-get upgrade
```

and see if Windows is detected by grub:
```
sudo update-grub
```

---

### Post by scrypt on 2010-03-31
okay here is  gksu gedit /etc/fstab output :


# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=4fbbe068-d073-4a87-a668-3743b50ac715 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=24a39a90-c6e1-42a8-a437-37564625b082 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

appologies but im am unsure how to correctly use your last command.
to comment out.

Can you clarify for me ?

---

### Post by sisco311 on 2010-03-31
type a # symbol at the beginning of the *UUID=24a39a90-c6e1-42a8-a437-37564625b082 none swap sw 0 0* line.

---

### Post by scrypt on 2010-03-31
okay thank-you for that.

here is gksu gedit /etc/fstab ::

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=4fbbe068-d073-4a87-a668-3743b50ac715 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
#UUID=24a39a90-c6e1-42a8-a437-37564625b082 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


I have saved this change. should i now reboot ??

---

### Post by sisco311 on 2010-03-31
Before you reboot update the system & run update-grub (see post #15), hopefully grub will detect Windows, if not, then you will have to create a custom entry manually for it. But for now just hope it's detected...

---

### Post by scrypt on 2010-03-31
Okay i just rebooted and i logged into Ubuntu fine this time. no problems here.

But the option to choose to log into Windows is still unavailable. not showing on grub screen.

here is my udo update-grub

-laptop:~$ sudo update-grub
[sudo] password for mark: 
Sorry, try again.
[sudo] password for: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-21-generic
Found initrd image: /boot/initrd.img-2.6.31-21-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory
done

if this helps

---

### Post by scrypt on 2010-03-31
Hey sisco

I updated grub

and rebooted. But still no option to choose to boot into windows 7

Do you have any idea why this would have disappeared ?

---

### Post by sisco311 on 2010-03-31
> **scrypt said:**
> Hey sisco

I updated grub

and rebooted. But still no option to choose to boot into windows 7

Do you have any idea why this would have disappeared ?

Yep: [thread]8708802[/thread]

*You have a "Boot" and "boot" folder on /dev/sda1. This leads to confusion since "ntfs" partitions are case insensitive. See this link for the details:*

[https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows](https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows)

---

### Post by scrypt on 2010-03-31
sisco

no thread appears when i visit [http://ubuntuforums.org/showthread.php?t=8708802](http://ubuntuforums.org/showthread.php?t=8708802)

and can you help me to fix this ?

---

### Post by sisco311 on 2010-03-31
> **scrypt said:**
> sisco

no thread appears when i visit [http://ubuntuforums.org/showthread.php?t=8708802](http://ubuntuforums.org/showthread.php?t=8708802)

and can you help me to fix this ?

Sorry. [http://ohioloco.ubuntuforums.org/showthread.php?p=8708802](http://ohioloco.ubuntuforums.org/showthread.php?p=8708802)

You have to mount the /dev/sda1 partition & rename the boot directory. 

```
sudo mount /dev/sda1 /mnt
sudo mv /mnt/boot /mnt/old-boot
sudo umount /mnt
sudo update-grub
```

---

### Post by scrypt on 2010-03-31
okay great.

do i need to do this with live-cd ?

---

### Post by sisco311 on 2010-03-31
Nope, just open a terminal in Ubuntu.

---

### Post by scrypt on 2010-03-31
Okay I thought so. just wanted to make sure :)

I ran your commands from your last post.

laptop:~$ sudo mount /dev/sda1 /mnt
[sudo] password for mark: 
laptop:~$ sudo mv /mnt/boot /mnt/old-boot
laptop:~$ sudo umount /mnt
laptop:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-21-generic
Found initrd image: /boot/initrd.img-2.6.31-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done

And all seems to be okay.

I will reboot shortly and see if the win7 boot option is back on my grub2 .
I will also post back as soon as I find out.

Thank-you for all you clear, concise instruction.

---

### Post by scrypt on 2010-03-31
Hello Sisco311

My issue is completely fixed.

I can now boot-up and once again choose between Ubuntu(Karmic)
and Windows7.

Thank's again for all your help and assistance.

Scrypt

---

### Post by sisco311 on 2010-03-31
> **scrypt said:**
> Hello Sisco311

My issue is completely fixed.

I can now boot-up and once again choose between Ubuntu(Karmic)
and Windows7.

Thank's again for all your help and assistance.

Scrypt

You're welcome!

---

