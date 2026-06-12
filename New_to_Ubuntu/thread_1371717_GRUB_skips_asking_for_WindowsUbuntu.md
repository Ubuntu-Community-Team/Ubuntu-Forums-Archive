---
title: "GRUB skips asking for Windows/Ubuntu"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by natpagle on 2010-01-03
I started off today getting a new HDD. Installed as Single Drive on separate IDE from Windows. I wanted to dual boot Ubuntu and Windows. 

I started the installer and set up Ubuntu 9.10 on /dev/sdb, whereas Windows XP is on /dev/sda. I used the option that wiped the drive and set up Ubuntu.

Now, when I reboot my computer it says starting GRUB, then just boots directly into Ubuntu. I'd like it to ask me if I want to boot into one or the other.

Thanks in advance.

---

### Post by drs305 on 2010-01-03
Booting directly into Ubuntu is the default action if Grub 2 isn't aware of another OS. Often "sudo update-grub" must be run after an install to make sure that G2 finds the Window install. Once G2 knows of Windows, that may solve the "no menu" issue as well.

You can also check the display settings in /etc/grub.d/default. Make sure that "GRUB_TIMEOUT=" is some positive integer. If you want it to display until you hit ENTER, make the value "-1"
```
gksu gedit /etc/default/grub
```
Save the file, then "sudo update-grub" 

Try that. If it still boots directly to an OS, you can hold down the shift key during boot to display the menu.

---

### Post by Zoot7 on 2010-01-03
Give this a shot:

```
sudo apt-get install os-prober
sudo os-prober
sudo update-grub
```

Then run:
```
gksudo gedit /etc/default/grub
```

Find then line starting with **GRUB_TIMEOUT** and change it to 
**GRUB_TIMEOUT=10** or any other value you would like.
Save, close and then reboot to see if it worked.

EDIT: drs305 beat me to it! :)

---

### Post by natpagle on 2010-01-03
Thanks for both of your suggestions, here are my results.

```
sudo apt-get install os-prober
sudo os-prober
sudo update-grub
```

Done

```
gksudo gedit /etc/default/grub
```

Changed to -1, was at 10 before.

Done

Saved and updated both times.

Still says Loading GRUB, goes to a black screen with a cursor, then boots to Ubuntu.

---

### Post by herbertportillo on 2010-01-03
> **natpagle said:**
> I used the option that wiped the drive and set up Ubuntu.

Does that mean that you formatted the drive? If that's the case, then there isn't a Windows partition on your system anymore.

---

### Post by natpagle on 2010-01-03
> **herbertportillo said:**
> Does that mean that you formatted the drive? If that's the case, then there isn't a Windows partition on your system anymore.
No, I selected the blank drive.

```
Disk /dev/sda: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41e941e8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9963    80027766    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002965c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9327    74919096   83  Linux
/dev/sdb2            9328        9729     3229065    5  Extended
/dev/sdb5            9328        9729     3229033+  82  Linux swap / Solaris
```

The results of: 
```
fdisk -l
```

---

### Post by Zoot7 on 2010-01-03
Is there a line **GRUB_HIDDEN_TIMEOUT=0** in /etc/default/grub? If there is put a # in front of it, so it's **#GRUB_HIDDEN_TIMEOUT=0**.

---

### Post by happyhamster on 2010-01-03
- Take a look at the contents of your /etc/default/grub file:

cat /etc/default/grub

- There should be a line that says

grub_hidden_timeout=0

- or perhaps it has some other value. If so, turn that line into a comment, by putting a # character in front of it:

gksudo gedit /etc/default/grub

- and change that line into:

# grub_hidden_timeout=0

- Save, and exit the editor. Then update grub:

sudo update-grub

---

### Post by natpagle on 2010-01-03
That worked! WOO! However, my Windows is not there. I just have Linux, Linux Recovery, Memtest and 1 other Memtest. 
I know I still have Windows installed, as I didn't write over that drive, right? 


Contents of GRUB:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"
```

---

### Post by danastasio on 2010-01-03
I could be wrong, but judging on what fdisk says, either you dont have the other drive plugged in (and im not sure about multi-drive boots in GRUB2) or you formatted the wrong disk.

---

### Post by kansasnoob on 2010-01-03
I see Windows right where the OP said it would be:

> Disk /dev/sda: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41e941e8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9963    80027766    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002965c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9327    74919096   83  Linux
/dev/sdb2            9328        9729     3229065    5  Extended
/dev/sdb5            9328        9729     3229033+  82  Linux swap / Solaris

Once again try running:

```
sudo update-grub
```

Be sure and wait until it says "done".

If it still fails to find Windows post the output of the Boot Info Script as described here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by @B6Mwu8fN9M on 2010-01-03
> **kansasnoob said:**
> I see Windows right where the OP said it would be:



What @danastasio is saying is that he may have installed to the wrong drive. The new drive might've had an NTFS partition on it when it was bought.

Just to check if @danastasio is right:

Can you mount NTFS partition? It should appear in  your Places menu. Or if not you can mount with: 
```
mount /dev/sda1 /media/windows
```

If you can, then the drive is plugged in. @danastasio might be right about you formatting the wrong drive. To check if you did, just mount the NTFS partition and look at the folders inside. If they are folders normally in the C: drive, then you installed to the right drive.

---

### Post by garyed on 2010-01-03
For some reason the os-prober is not finding Windows.
I hope your boot files are still there. 
If all else fails you could make a custom entry for windows.
Paste the contents below into a text file & name it " 72_custom " 
```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.
# Be careful not to change the 'exec tail' line above.
menuentry "Microsoft Windows" {
insmod ntfs
set root=(hd0,1)
drivemap -s (hd0) ${root}
chainloader +1
}
```
Go to the terminal & to the folder where 72_custom is & do:
```
sudo cp 72_custom /etc/grub.d/ 
```
then do:
```
sudo chmod 755 /etc/grub.d/72_custom
```
then do:
```
sudo update-grub
```
When you reboot Windows should be on the bottom of your grub menu & hopefully will boot it also.

---

### Post by natpagle on 2010-01-03
> **kansasnoob said:**
> I see Windows right where the OP said it would be:



Once again try running:

```
sudo update-grub
```

Be sure and wait until it says "done".

If it still fails to find Windows post the output of the Boot Info Script as described here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
Going to reply to each one of these as I try them.

Done.

Results:
```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks for 
    (UUID=9fcf5900-d845-4fc3-8903-774b631f11a6)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
$MFTMirr does not match $MFT (record 1).
Failed to mount '/dev/sda1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
$MFTMirr does not match $MFT (record 1).
Failed to mount '/dev/sda1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x41e941e8

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   160,055,594   160,055,532   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0002965c

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   149,838,254   149,838,192  83 Linux
/dev/sdb2         149,838,255   156,296,384     6,458,130   5 Extended
/dev/sdb5         149,838,318   156,296,384     6,458,067  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

sda1: UUID="7EE44FFAE44FB2E7" TYPE="ntfs" 
sdb1: UUID="9fcf5900-d845-4fc3-8903-774b631f11a6" TYPE="ext4" 
sdb5: UUID="e3008e6e-1389-4dc0-8ae6-aba18d92dca6" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ryan/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ryan)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root=(hd1,1)
search --no-floppy --fs-uuid --set 9fcf5900-d845-4fc3-8903-774b631f11a6
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
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 9fcf5900-d845-4fc3-8903-774b631f11a6
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=9fcf5900-d845-4fc3-8903-774b631f11a6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 9fcf5900-d845-4fc3-8903-774b631f11a6
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=9fcf5900-d845-4fc3-8903-774b631f11a6 ro single 
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
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=9fcf5900-d845-4fc3-8903-774b631f11a6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=e3008e6e-1389-4dc0-8ae6-aba18d92dca6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/core.img
    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: initrd.img
    .0GB: vmlinuz
```

---

### Post by natpagle on 2010-01-03
> **vlad003 said:**
> What @danastasio is saying is that he may have installed to the wrong drive. The new drive might've had an NTFS partition on it when it was bought.

The drive was an Windows drive that had been wiped and used as an OS X drive that I got from work. 


> Just to check if @danastasio is right:

Can you mount NTFS partition? It should appear in  your Places menu. Or if not you can mount with: 
```
mount /dev/sda1 /media/windows
```

If you can, then the drive is plugged in. @danastasio might be right about you formatting the wrong drive. To check if you did, just mount the NTFS partition and look at the folders inside. If they are folders normally in the C: drive, then you installed to the right drive.

I tried to mount it, got this:
> $MFTMirr does not match $MFT (record 1).
Failed to mount '/dev/sda1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

---

### Post by natpagle on 2010-01-03
> **garyed said:**
> For some reason the os-prober is not finding Windows.
I hope your boot files are still there. 
If all else fails you could make a custom entry for windows.
Paste the contents below into a text file & name it " 72_custom " 
```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.
# Be careful not to change the 'exec tail' line above.
menuentry "Microsoft Windows" {
insmod ntfs
set root=(hd0,1)
drivemap -s (hd0) ${root}
chainloader +1
}
```
Go to the terminal & to the folder where 72_custom is & do:
```
sudo cp 72_custom /etc/grub.d/ 
```
then do:
```
sudo chmod 755 /etc/grub.d/72_custom
```
then do:
```
sudo update-grub
```
When you reboot Windows should be on the bottom of your grub menu & hopefully will boot it also.

After doing this one, Microsoft Windows showed up at the bottom of the list and when I selected it, it booted XP and ran a Check Disk on itself. Rebooted again, now I'm replying from within XP!

Thank you sooo sooooooo much guys for all of your help!

---

### Post by danastasio on 2010-01-03
oh i see it now!

I completley missed that second chunk of text >.<

sorry about that! My statement still stands though (even though it was wrong :P)

---

