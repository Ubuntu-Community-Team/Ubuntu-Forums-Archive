---
title: "Grub loading Error: No Such Device"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by Tholley on 2009-11-10
I have an old pc that formally had Win2000 on it. I installed Ubuntu 9.04 on it with no problems, then when 9.10 came out, I wanted to do a fresh install instead of upgrade since I had several issues on this other machine and fresh install fixed all.

But on this recent install, (I've tried it 3 different times) it seems to install just fine, but when I reboot, I get a black screen with:

Grub Loading
Error: No Such Device XXXXX... alot of letter and numbers, which are each different on every install attempt.

A couple times it showed the boot menu, but highlighting any line caused it to flash and clicking on it would just go back to the Grub loading error.

I have tried installing manually with select ext3, format, mount point /, and also letting the Live CD do it automatically, with the same results.

I have read a couple threads concerning the same or similar problem but not a solution yet. 

Any ideas out there?

---

### Post by philinux on 2009-11-10
> **Tholley said:**
> I have an old pc that formally had Win2000 on it. I installed Ubuntu 9.04 on it with no problems, then when 9.10 came out, I wanted to do a fresh install instead of upgrade since I had several issues on this other machine and fresh install fixed all.

But on this recent install, (I've tried it 3 different times) it seems to install just fine, but when I reboot, I get a black screen with:

Grub Loading
Error: No Such Device XXXXX... alot of letter and numbers, which are each different on every install attempt.

A couple times it showed the boot menu, but highlighting any line caused it to flash and clicking on it would just go back to the Grub loading error.

I have tried installing manually with select ext3, format, mount point /, and also letting the Live CD do it automatically, with the same results.

I have read a couple threads concerning the same or similar problem but not a solution yet. 

Any ideas out there?

From what you say the live cd runs ok. Did you run "check cd for defects" before you installed.

---

### Post by ranch hand on 2009-11-10
Did you check the md5sum?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Tholley on 2009-11-10
> From what you say the live cd runs ok. Did you run "check cd for defects" before you installed.

Yep... I guess I could again tho, but it installed 9.10 on another pc just fine.

I am running off the Live CD right now.

---

### Post by Tholley on 2009-11-10
> **ranch hand said:**
> Did you check the md5sum?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

```
**MD5SUM on Linux**

 Most Linux distributions come with the md5sum utility so installation is usually unnecessary. We are going to use the Ubuntu 8.10 LiveCD for the following example: 
 
**Check the iso file**

  
**Manual method**

 First open a terminal and go to the correct directory to check a downloaded iso file: 
cd download_directory
```I got this:

```
ubuntu@ubuntu:~$ cd download_directory
bash: cd: download_directory: No such file or directory
ubuntu@ubuntu:~$ 
```


Should I not be running in Live CD?

---

### Post by ranch hand on 2009-11-10
If you download to the Desktop like I do you need to;
[code]
cd /home/<your user name>/Desktop

---

### Post by Tholley on 2009-11-10
> **ranch hand said:**
> If you download to the Desktop like I do you need to;
[code]
cd /home/<your user name>/Desktop

I must be doing something wrong... everything I do says No such file or directory.

I quit running off the Live CD on the other computer and have it in my good one now even.

---

### Post by kansasnoob on 2009-11-10
To check md5sum of a disc:

[https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20CD](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20CD)

But much easier to do this (I've even had the prior fail to "print" an md5sum when the disc is fine):

[https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck)

If the disc integrity check passes OK it would probably be best to see the results of the Boot Info Script performed from the live CD on your non-booting machine as described here;

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by Tholley on 2009-11-10
> To check md5sum of a disc:

[https://help.ubuntu.com/community/Ho...5SUM%20on%20CD]("https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20CD")

I got nothing?


```
terrell@terrell-bedroom:~$ cd /cdrom
terrell@terrell-bedroom:/cdrom$ md5sum -c md5sum.txt | grep -vi 'OK$'
terrell@terrell-bedroom:/cdrom$ 
```

I'll try the next one.

---

### Post by Tholley on 2009-11-10
Integrity check was ok

Here are the results from the Boot Info Script...

```
============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfa0cfa0c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    77,304,779    77,304,717  83 Linux
/dev/sda2          77,304,780    80,292,869     2,988,090   5 Extended
/dev/sda5          77,304,843    80,292,869     2,988,027  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="415e5ecb-e9b3-45a5-b049-baad4589e4bb" TYPE="ext4" 
/dev/sda5: UUID="33f5b6f6-ce40-492a-b94b-df19c140d281" TYPE="swap" 
/dev/ramzswap0: TYPE="swap" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root=(hd0,1)
search --no-floppy --fs-uuid --set 415e5ecb-e9b3-45a5-b049-baad4589e4bb
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
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 415e5ecb-e9b3-45a5-b049-baad4589e4bb
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=415e5ecb-e9b3-45a5-b049-baad4589e4bb ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 415e5ecb-e9b3-45a5-b049-baad4589e4bb
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=415e5ecb-e9b3-45a5-b049-baad4589e4bb ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=415e5ecb-e9b3-45a5-b049-baad4589e4bb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=33f5b6f6-ce40-492a-b94b-df19c140d281 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: initrd.img
    .0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sda

00000000  eb 63 90 d0 bc 00 7c fb  50 07 50 1f fc be 1b 7c  |.c....|.P.P....||
00000010  bf 1b 06 50 57 b9 e5 01  f3 a4 cb bd be 07 b1 04  |...PW...........|
00000020  38 6e 00 7c 09 75 13 83  c5 10 e2 f4 cd 18 8b f5  |8n.|.u..........|
00000030  83 c6 10 49 74 19 38 2c  74 f6 a0 b5 07 b4 03 02  |...It.8,t.......|
00000040  ff 00 00 20 01 00 00 00  00 02 fa 90 90 f6 c2 80  |... ............|
00000050  75 02 b2 80 ea 59 7c 00  00 31 00 80 01 00 00 00  |u....Y|..1......|
00000060  00 00 00 00 ff fa eb 07  f6 c2 80 75 02 b2 80 ea  |...........u....|
00000070  74 7c 00 00 31 c0 8e d8  8e d0 bc 00 20 fb a0 64  |t|..1....... ..d|
00000080  7c 3c ff 74 02 88 c2 52  be 88 7d e8 24 01 be 05  ||<.t...R..}.$...|
00000090  7c f6 c2 80 74 48 b4 41  bb aa 55 cd 13 5a 52 72  ||...tH.A..U..ZRr|
000000a0  3d 81 fb 55 aa 75 37 83  e1 01 74 32 31 c0 89 44  |=..U.u7...t21..D|
000000b0  04 40 88 44 ff 89 44 02  c7 04 10 00 66 8b 1e 5c  |.@.D..D.....f..\|
000000c0  7c 66 89 5c 08 66 8b 1e  60 7c 66 89 5c 0c c7 44  ||f.\.f..`|f.\..D|
000000d0  06 00 70 b4 42 cd 13 72  05 bb 00 70 eb 73 b4 08  |..p.B..r...p.s..|
000000e0  cd 13 73 0a f6 c2 80 0f  84 d8 00 e9 82 00 66 0f  |..s...........f.|
000000f0  b6 c6 88 64 ff 40 66 89  44 04 0f b6 d1 c1 e2 02  |...d.@f.D.......|
00000100  88 e8 88 f4 40 89 44 08  0f b6 c2 c0 e8 02 66 89  |....@.D.......f.|
00000110  04 66 a1 60 7c 66 09 c0  75 4e 66 a1 5c 7c 66 31  |.f.`|f..uNf.\|f1|
00000120  d2 66 f7 34 88 d1 31 d2  66 f7 74 04 3b 44 08 7d  |.f.4..1.f.t.;D.}|
00000130  37 fe c1 88 c5 30 c0 c1  e8 02 08 c1 88 d0 5a 88  |7....0........Z.|
00000140  c6 bb 00 70 8e c3 31 db  b8 01 02 cd 13 72 29 8c  |...p..1......r).|
00000150  c3 60 1e b9 00 01 8e db  31 f6 bf 00 80 8e c6 fc  |.`......1.......|
00000160  f3 a5 1f 61 ff 26 5a 7c  be 8e 7d e8 44 00 eb 0e  |...a.&Z|..}.D...|
00000170  be 93 7d e8 3c 00 eb 06  be 9d 7d e8 34 00 be a2  |..}.<.....}.4...|
00000180  7d e8 2e 00 cd 18 eb fe  47 52 55 42 20 00 47 65  |}.......GRUB .Ge|
00000190  6f 6d 00 48 61 72 64 20  44 69 73 6b 00 52 65 61  |om.Hard Disk.Rea|
000001a0  64 00 20 45 72 72 6f 72  0d 0a 00 bb 01 00 b4 0e  |d. Error........|
000001b0  cd 10 ac 3c 00 75 f4 c3  0c fa 0c fa 00 00 80 01  |...<.u..........|
000001c0  01 00 83 fe ff ff 3f 00  00 00 8d 93 9b 04 00 fe  |......?.........|
000001d0  ff ff 05 fe ff ff cc 93  9b 04 3a 98 2d 00 00 00  |..........:.-...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```Is that first part what I think it means? "No known boot loader..."

---

### Post by Tholley on 2009-11-10
I'm downloading another copy of 9.10-desktop-i386.iso, and will burn another CD, then see if I have any better luck.

Unless anybody has some ideas about the above boot file.

---

### Post by kansasnoob on 2009-11-10
> **Tholley said:**
> I'm downloading another copy of 9.10-desktop-i386.iso, and will burn another CD, then see if I have any better luck.

Unless anybody has some ideas about the above boot file.

Just got a chance to look at it.

Give me a little bit to parse all the info.

---

### Post by kansasnoob on 2009-11-10
I have an idea that may or may not work. It's fairly simple though and I feel worth a try.

Just give me about 15 minutes to get everything typed right and double check myself for errors.

Go ahead and boot the Live CD if it's not already as we'll be working from the Live Desktop.

---

### Post by mr_steve on 2009-11-10
This is very likely bug #[lpbug]403408[/lpbug]. There are some comments there which have a way to fix this. I don't know why this hasn't been fixed yet, as it seems to be biting a lot of people with fresh installations.

---

### Post by kansasnoob on 2009-11-10
From the Live Desktop we're going to mount and chroot sda1:

```
sudo mount /dev/sda1 /mnt
```

```
sudo mount --bind /dev /mnt/dev
```

```
sudo mount --bind /proc /mnt/proc
```

```
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
```

```
sudo chroot /mnt
```

Here you'll see the terminal prompt change to a # so we don't need to use sudo while we're chroot:

```
apt-get update
```

```
apt-get dist-upgrade
```

```
mv /boot/grub /boot/grub_old
```

```
mkdir /boot/grub
```

```
apt-get install --reinstall grub-pc grub-common os-prober
```

```
update-grub
```

```
grub-install /dev/sda
```

```
exit
```

Here you'll see we're back in a normal terminal prompt (ubuntu@ubuntu) so we need to sudo again:

```
sudo umount /mnt/dev
```

```
sudo umount /mnt/proc
```

```
sudo umount /mnt
```

```
sudo reboot
```

Hopefully that works. If there are any errors during that process post them here though. I'll keep watching.

---

### Post by kansasnoob on 2009-11-10
**[COLOR="Red"]After reading that bug report I'm adding two commands to my prior post![/COLOR]**

---

### Post by Tholley on 2009-11-10
> **kansasnoob said:**
> I have an idea that may or may not work. It's fairly simple though and I feel worth a try.

Just give me about 15 minutes to get everything typed right and double check myself for errors.

Go ahead and boot the Live CD if it's not already as we'll be working from the Live Desktop.

Ok, in Live CD and opening Terminal and will start copying and pasting the commands.

---

### Post by Tholley on 2009-11-10
> **kansasnoob said:**
> **[COLOR=Red]After reading that bug report I'm adding two commands to my prior post![/COLOR]**

Ok so post #15 is good to go?

---

### Post by kansasnoob on 2009-11-10
> **Tholley said:**
> Ok so post #15 is good to go?

Yes. Done editing. Added update and upgrade.

---

### Post by kansasnoob on 2009-11-10
> **mr_steve said:**
> This is very likely bug #[lpbug]403408[/lpbug]. There are some comments there which have a way to fix this. I don't know why this hasn't been fixed yet, as it seems to be biting a lot of people with fresh installations.

Many thanks! Hopefully this will work.

---

### Post by Tholley on 2009-11-10
> Code:
 	apt-get install --reinstall grub-pc grub-common os-prober 
 	Code:
 	update-grub


not done yet but at the bottome of these 2, 
"Cannot find list of partitions!
done"

any concerns?

I'm continuing...

---

### Post by Tholley on 2009-11-10
> sudo umount /mnt/devHere it says:
umount: /mnt/dev: device is busy



Do I continue?

---

### Post by kansasnoob on 2009-11-10
> **Tholley said:**
> Here it says:
umount: /mnt/dev: device is busy



Do I continue?

That indicates that something is still running in sda1 which is your root partition.

But yes continue. I'm more concerned about update-grub saying what it did.

Did you give each command time to complete? It would be indicated by the # coming back up.

---

### Post by Tholley on 2009-11-10
> **kansasnoob said:**
> That indicates that something is still running in sda1 which is your root partition.

But yes continue. I'm more concerned about update-grub saying what it did.

Did you give each command time to complete? It would be indicated by the # coming back up.

yes I waited for the # each time.

Also on the next one 

sudo umount /mnt/proc

same thing.

there were a couple of other during upgrade and reinstall I saw "Cannot write log", and something openpty, but everything seemed to load ok.

---

### Post by Tholley on 2009-11-10
all 3 sudos before reboot say device is busy.

Go ahead and reboot?

---

### Post by kansasnoob on 2009-11-10
When you ran apt-get dist-upgrade were there a bunch of updates available? Did you say yes (y)?

---

### Post by kansasnoob on 2009-11-10
Would you please run though that all again and post the full output of the terminal here?

---

### Post by Tholley on 2009-11-10
> **kansasnoob said:**
> When you ran apt-get dist-upgrade were there a bunch of updates available? Did you say yes (y)?

Yes...

---

### Post by Tholley on 2009-11-10
> **kansasnoob said:**
> Would you please run though that all again and post the full output of the terminal here?

Would you like me to copy everything from the terminal and post it?

---

### Post by kansasnoob on 2009-11-10
> **Tholley said:**
> Would you like me to copy everything from the terminal and post it?

Yes please. I'm a bit puzzled as to what may still be running.

---

### Post by Tholley on 2009-11-10
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Can not write log, openpty() failed (/dev/pts not mounted?)
Setting up python2.6-minimal (2.6.4-0ubuntu2) ...

Can not write log, openpty() failed (/dev/pts not mounted?)
(Reading database ... 114040 files and directories currently installed.)
Preparing to replace python 2.6.4~rc1-0ubuntu1 (using .../python_2.6.4-0ubuntu1_all.deb) ...
Unpacking replacement python ...
Preparing to replace python-minimal 2.6.4~rc1-0ubuntu1 (using .../python-minimal_2.6.4-0ubuntu1_all.deb) ...
Unpacking replacement python-minimal ...
Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 25 changed doc-base file(s)...
Registering documents with scrollkeeper...
Can not write log, openpty() failed (/dev/pts not mounted?)
Setting up python-minimal (2.6.4-0ubuntu1) ...
Can not write log, openpty() failed (/dev/pts not mounted?)
(Reading database ... 114040 files and directories currently installed.)
Preparing to replace libudev0 147~-6 (using .../libudev0_147~-6.1_i386.deb) ...
Unpacking replacement libudev0 ...
Can not write log, openpty() failed (/dev/pts not mounted?)
Setting up libudev0 (147~-6.1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Can not write log, openpty() failed (/dev/pts not mounted?)
(Reading database ... 114040 files and directories currently installed.)
Preparing to replace udev 147~-6 (using .../udev_147~-6.1_i386.deb) ...
Adding `local diversion of /sbin/udevadm to /sbin/udevadm.upgrade'
Unpacking replacement udev ...
Preparing to replace apparmor 2.3.1+1403-0ubuntu27 (using .../apparmor_2.3.1+1403-0ubuntu27.1_i386.deb) ...
Unpacking replacement apparmor ...
Preparing to replace libapparmor1 2.3.1+1403-0ubuntu27 (using .../libapparmor1_2.3.1+1403-0ubuntu27.1_i386.deb) ...
Unpacking replacement libapparmor1 ...
Preparing to replace libapparmor-perl 2.3.1+1403-0ubuntu27 (using .../libapparmor-perl_2.3.1+1403-0ubuntu27.1_i386.deb) ...
Unpacking replacement libapparmor-perl ...
Preparing to replace apparmor-utils 2.3.1+1403-0ubuntu27 (using .../apparmor-utils_2.3.1+1403-0ubuntu27.1_i386.deb) ...
Unpacking replacement apparmor-utils ...
Preparing to replace update-manager 1:0.126.6 (using .../update-manager_1%3a0.126.9_all.deb) ...
Unpacking replacement update-manager ...
Preparing to replace update-manager-core 1:0.126.6 (using .../update-manager-core_1%3a0.126.9_i386.deb) ...
Unpacking replacement update-manager-core ...
Preparing to replace python-problem-report 1.9.3-0ubuntu4 (using .../python-problem-report_1.9.3-0ubuntu4.1_all.deb) ...
Unpacking replacement python-problem-report ...
Preparing to replace python-apport 1.9.3-0ubuntu4 (using .../python-apport_1.9.3-0ubuntu4.1_all.deb) ...
Unpacking replacement python-apport ...
Preparing to replace apport 1.9.3-0ubuntu4 (using .../apport_1.9.3-0ubuntu4.1_all.deb) ...
apport stop/waiting
Unpacking replacement apport ...
Preparing to replace apport-gtk 1.9.3-0ubuntu4 (using .../apport-gtk_1.9.3-0ubuntu4.1_all.deb) ...
Unpacking replacement apport-gtk ...
Preparing to replace binutils 2.20-0ubuntu1 (using .../binutils_2.20-0ubuntu2_i386.deb) ...
Unpacking replacement binutils ...
Preparing to replace libnautilus-extension1 1:2.28.1-0ubuntu1 (using .../libnautilus-extension1_1%3a2.28.1-0ubuntu2_i386.deb) ...
Unpacking replacement libnautilus-extension1 ...
Preparing to replace libbrasero-media0 2.28.1-0ubuntu1 (using .../libbrasero-media0_2.28.2-0ubuntu1_i386.deb) ...
Unpacking replacement libbrasero-media0 ...
Preparing to replace brasero 2.28.1-0ubuntu1 (using .../brasero_2.28.2-0ubuntu1_i386.deb) ...
Unpacking replacement brasero ...
Preparing to replace checkbox-gtk 0.8.5 (using .../checkbox-gtk_0.8.6_all.deb) ...
Unpacking replacement checkbox-gtk ...
Preparing to replace checkbox 0.8.5 (using .../checkbox_0.8.6_all.deb) ...
Unpacking replacement checkbox ...
Preparing to replace libcups2 1.4.1-5ubuntu2 (using .../libcups2_1.4.1-5ubuntu2.1_i386.deb) ...
Unpacking replacement libcups2 ...
Preparing to replace libcupscgi1 1.4.1-5ubuntu2 (using .../libcupscgi1_1.4.1-5ubuntu2.1_i386.deb) ...
Unpacking replacement libcupscgi1 ...
Preparing to replace libcupsdriver1 1.4.1-5ubuntu2 (using .../libcupsdriver1_1.4.1-5ubuntu2.1_i386.deb) ...
Unpacking replacement libcupsdriver1 ...
Preparing to replace libcupsimage2 1.4.1-5ubuntu2 (using .../libcupsimage2_1.4.1-5ubuntu2.1_i386.deb) ...
Unpacking replacement libcupsimage2 ...
Preparing to replace libcupsmime1 1.4.1-5ubuntu2 (using .../libcupsmime1_1.4.1-5ubuntu2.1_i386.deb) ...
Unpacking replacement libcupsmime1 ...
Preparing to replace libcupsppdc1 1.4.1-5ubuntu2 (using .../libcupsppdc1_1.4.1-5ubuntu2.1_i386.deb) ...
Unpacking replacement libcupsppdc1 ...
Preparing to replace libpoppler5 0.12.0-0ubuntu2 (using .../libpoppler5_0.12.0-0ubuntu2.1_i386.deb) ...
Unpacking replacement libpoppler5 ...
Preparing to replace poppler-utils 0.12.0-0ubuntu2 (using .../poppler-utils_0.12.0-0ubuntu2.1_i386.deb) ...
Unpacking replacement poppler-utils ...
Preparing to replace cups-common 1.4.1-5ubuntu2 (using .../cups-common_1.4.1-5ubuntu2.1_all.deb) ...
Unpacking replacement cups-common ...
Preparing to replace cups-bsd 1.4.1-5ubuntu2 (using .../cups-bsd_1.4.1-5ubuntu2.1_i386.deb) ...
Unpacking replacement cups-bsd ...
Preparing to replace cups-client 1.4.1-5ubuntu2 (using .../cups-client_1.4.1-5ubuntu2.1_i386.deb) ...
Unpacking replacement cups-client ...
Preparing to replace cups 1.4.1-5ubuntu2 (using .../cups_1.4.1-5ubuntu2.1_i386.deb) ...
 * Stopping Common Unix Printing System: cupsd                           [ OK ] 
Unpacking replacement cups ...
Preparing to replace libempathy30 2.28.1-1ubuntu1 (using .../libempathy30_2.28.1.1-0ubuntu1_i386.deb) ...
Unpacking replacement libempathy30 ...
Preparing to replace libempathy-common 2.28.1-1ubuntu1 (using .../libempathy-common_2.28.1.1-0ubuntu1_all.deb) ...
Unpacking replacement libempathy-common ...
Preparing to replace libenchant1c2a 1.5.0-0ubuntu2 (using .../libenchant1c2a_1.5.0-0ubuntu3_i386.deb) ...
Unpacking replacement libenchant1c2a ...
Preparing to replace libempathy-gtk28 2.28.1-1ubuntu1 (using .../libempathy-gtk28_2.28.1.1-0ubuntu1_i386.deb) ...
Unpacking replacement libempathy-gtk28 ...
Preparing to replace libempathy-gtk-common 2.28.1-1ubuntu1 (using .../libempathy-gtk-common_2.28.1.1-0ubuntu1_all.deb) ...
Unpacking replacement libempathy-gtk-common ...
Preparing to replace empathy 2.28.1-1ubuntu1 (using .../empathy_2.28.1.1-0ubuntu1_i386.deb) ...
Unpacking replacement empathy ...
Preparing to replace empathy-doc 2.28.1-1ubuntu1 (using .../empathy-doc_2.28.1.1-0ubuntu1_all.deb) ...
Unpacking replacement empathy-doc ...
Preparing to replace libevdocument1 2.28.1-0ubuntu1 (using .../libevdocument1_2.28.1-0ubuntu1.1_i386.deb) ...
Unpacking replacement libevdocument1 ...
Preparing to replace libevview1 2.28.1-0ubuntu1 (using .../libevview1_2.28.1-0ubuntu1.1_i386.deb) ...
Unpacking replacement libevview1 ...
Preparing to replace libpoppler-glib4 0.12.0-0ubuntu2 (using .../libpoppler-glib4_0.12.0-0ubuntu2.1_i386.deb) ...
Unpacking replacement libpoppler-glib4 ...
Preparing to replace evince 2.28.1-0ubuntu1 (using .../evince_2.28.1-0ubuntu1.1_i386.deb) ...
Unpacking replacement evince ...
Preparing to replace libgnome-desktop-2-11 1:2.28.1-0ubuntu2 (using .../libgnome-desktop-2-11_1%3a2.28.1-0ubuntu3_i386.deb) ...
Unpacking replacement libgnome-desktop-2-11 ...
Preparing to replace evolution 2.28.1-0ubuntu1 (using .../evolution_2.28.1-0ubuntu2_i386.deb) ...
Unpacking replacement evolution ...
Preparing to replace evolution-common 2.28.1-0ubuntu1 (using .../evolution-common_2.28.1-0ubuntu2_all.deb) ...
Unpacking replacement evolution-common ...
Preparing to replace evolution-plugins 2.28.1-0ubuntu1 (using .../evolution-plugins_2.28.1-0ubuntu2_i386.deb) ...
Unpacking replacement evolution-plugins ...
Preparing to replace f-spot 0.6.1.3-2 (using .../f-spot_0.6.1.4-0ubuntu1_i386.deb) ...
Unpacking replacement f-spot ...
Preparing to replace xulrunner-1.9.1-gnome-support 1.9.1.3+build1+nobinonly-0ubuntu6 (using .../xulrunner-1.9.1-gnome-support_1.9.1.4+nobinonly-0ubuntu0.9.10.1_i386.deb) ...
Unpacking replacement xulrunner-1.9.1-gnome-support ...
Preparing to replace xulrunner-1.9.1 1.9.1.3+build1+nobinonly-0ubuntu6 (using .../xulrunner-1.9.1_1.9.1.4+nobinonly-0ubuntu0.9.10.1_i386.deb) ...
Removing obsolete conffile /etc/gre.d/1.9.1.3.system.conf ...
Unpacking replacement xulrunner-1.9.1 ...
Preparing to replace firefox-3.5-gnome-support 3.5.3+build1+nobinonly-0ubuntu6 (using .../firefox-3.5-gnome-support_3.5.4+nobinonly-0ubuntu0.9.10.1_i386.deb) ...
Unpacking replacement firefox-3.5-gnome-support ...
Preparing to replace firefox-3.5-branding 3.5.3+build1+nobinonly-0ubuntu6 (using .../firefox-3.5-branding_3.5.4+nobinonly-0ubuntu0.9.10.1_i386.deb) ...
Unpacking replacement firefox-3.5-branding ...
Preparing to replace firefox-3.5 3.5.3+build1+nobinonly-0ubuntu6 (using .../firefox-3.5_3.5.4+nobinonly-0ubuntu0.9.10.1_i386.deb) ...
Unpacking replacement firefox-3.5 ...
Preparing to replace firefox 3.5.3+build1+nobinonly-0ubuntu6 (using .../firefox_3.5.4+nobinonly-0ubuntu0.9.10.1_all.deb) ...
Unpacking replacement firefox ...
Preparing to replace firefox-gnome-support 3.5.3+build1+nobinonly-0ubuntu6 (using .../firefox-gnome-support_3.5.4+nobinonly-0ubuntu0.9.10.1_all.deb) ...
Unpacking replacement firefox-gnome-support ...
Preparing to replace gnome-about 1:2.28.1-0ubuntu2 (using .../gnome-about_1%3a2.28.1-0ubuntu3_all.deb) ...
Unpacking replacement gnome-about ...
Preparing to replace gnome-desktop-data 1:2.28.1-0ubuntu2 (using .../gnome-desktop-data_1%3a2.28.1-0ubuntu3_all.deb) ...
Unpacking replacement gnome-desktop-data ...
Preparing to replace grub-pc 1.97~beta4-1ubuntu3 (using .../grub-pc_1.97~beta4-1ubuntu4_i386.deb) ...
Unpacking replacement grub-pc ...
Preparing to replace grub-common 1.97~beta4-1ubuntu3 (using .../grub-common_1.97~beta4-1ubuntu4_i386.deb) ...
Unpacking replacement grub-common ...
Preparing to replace gtk2-engines 1:2.18.4-1ubuntu1 (using .../gtk2-engines_1%3a2.18.4-1ubuntu2_i386.deb) ...
Unpacking replacement gtk2-engines ...
Preparing to replace gtk2-engines-murrine 0.90.3-1ubuntu1 (using .../gtk2-engines-murrine_0.90.3-1ubuntu2_i386.deb) ...
Unpacking replacement gtk2-engines-murrine ...
Preparing to replace kerneloops-daemon 0.12+git20090217-1ubuntu4 (using .../kerneloops-daemon_0.12+git20090217-1ubuntu4.1_i386.deb) ...
 * Stopping Kernel Oops catching service kerneloops                      [ OK ] 
Unpacking replacement kerneloops-daemon ...
Preparing to replace libclutter-gtk-0.10-0 0.10.2-0ubuntu1 (using .../libclutter-gtk-0.10-0_0.10.2-0ubuntu2_i386.deb) ...
Unpacking replacement libclutter-gtk-0.10-0 ...
Preparing to replace libgd2-xpm 2.0.36~rc1~dfsg-3ubuntu1 (using .../libgd2-xpm_2.0.36~rc1~dfsg-3ubuntu1.9.10.1_i386.deb) ...
Unpacking replacement libgd2-xpm ...
Preparing to replace libgudev-1.0-0 1:147~-6 (using .../libgudev-1.0-0_1%3a147~-6.1_i386.deb) ...
Unpacking replacement libgudev-1.0-0 ...
Preparing to replace libhtml-parser-perl 3.61-1 (using .../libhtml-parser-perl_3.61-1ubuntu0.1_i386.deb) ...
Unpacking replacement libhtml-parser-perl ...
Preparing to replace nautilus-data 1:2.28.1-0ubuntu1 (using .../nautilus-data_1%3a2.28.1-0ubuntu2_all.deb) ...
Unpacking replacement nautilus-data ...
Preparing to replace nautilus 1:2.28.1-0ubuntu1 (using .../nautilus_1%3a2.28.1-0ubuntu2_i386.deb) ...
Unpacking replacement nautilus ...
Preparing to replace nvidia-common 0.2.15 (using .../nvidia-common_0.2.15.1_i386.deb) ...
Unpacking replacement nvidia-common ...
Preparing to replace ubuntuone-client-gnome 1.0.2-0ubuntu1 (using .../ubuntuone-client-gnome_1.0.2-0ubuntu2_i386.deb) ...
Unpacking replacement ubuntuone-client-gnome ...
Preparing to replace ubuntuone-client 1.0.2-0ubuntu1 (using .../ubuntuone-client_1.0.2-0ubuntu2_all.deb) ...
Unpacking replacement ubuntuone-client ...
Preparing to replace python-ubuntuone-client 1.0.2-0ubuntu1 (using .../python-ubuntuone-client_1.0.2-0ubuntu2_all.deb) ...
Unpacking replacement python-ubuntuone-client ...
Preparing to replace rhythmbox 0.12.5-0ubuntu4 (using .../rhythmbox_0.12.5-0ubuntu5_i386.deb) ...
Unpacking replacement rhythmbox ...
Preparing to replace ubuntu-xsplash-artwork 0.8.4-0ubuntu1 (using .../ubuntu-xsplash-artwork_0.8.5-0ubuntu1_i386.deb) ...
Unpacking replacement ubuntu-xsplash-artwork ...
Preparing to replace xsplash 0.8.4-0ubuntu1 (using .../xsplash_0.8.5-0ubuntu1_i386.deb) ...
Unpacking replacement xsplash ...
Preparing to replace evolution-documentation-en 2.28.1-0ubuntu1 (using .../evolution-documentation-en_2.28.1-0ubuntu2_all.deb) ...
Unpacking replacement evolution-documentation-en ...
Processing triggers for sreadahead ...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for shared-mime-info ...
Processing triggers for ufw ...
Processing triggers for doc-base ...
Processing 1 changed doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for install-info ...
Can not write log, openpty() failed (/dev/pts not mounted?)
Setting up python2.6 (2.6.4-0ubuntu2) ...

Setting up libpython2.6 (2.6.4-0ubuntu2) ...

Setting up python (2.6.4-0ubuntu1) ...

Setting up udev (147~-6.1) ...
udev start/running, process 5282
Removing `local diversion of /sbin/udevadm to /sbin/udevadm.upgrade'
update-initramfs: deferring update (trigger activated)

Setting up apparmor (2.3.1+1403-0ubuntu27.1) ...
Installing new version of config file /etc/apparmor.d/abstractions/gnome ...
Installing new version of config file /etc/apparmor.d/abstractions/kde ...
Installing new version of config file /etc/apparmor.d/abstractions/ubuntu-browsers ...

Setting up libapparmor1 (2.3.1+1403-0ubuntu27.1) ...

Setting up libapparmor-perl (2.3.1+1403-0ubuntu27.1) ...
Setting up update-manager-core (1:0.126.9) ...

Setting up update-manager (1:0.126.9) ...

Setting up python-problem-report (1.9.3-0ubuntu4.1) ...

Setting up python-apport (1.9.3-0ubuntu4.1) ...

Setting up apport (1.9.3-0ubuntu4.1) ...
apport start/running

Setting up apport-gtk (1.9.3-0ubuntu4.1) ...
Setting up binutils (2.20-0ubuntu2) ...

Setting up libnautilus-extension1 (1:2.28.1-0ubuntu2) ...

Setting up libbrasero-media0 (2.28.2-0ubuntu1) ...

Setting up brasero (2.28.2-0ubuntu1) ...

Setting up checkbox (0.8.6) ...

Setting up checkbox-gtk (0.8.6) ...

Setting up libcups2 (1.4.1-5ubuntu2.1) ...

Setting up libcupscgi1 (1.4.1-5ubuntu2.1) ...

Setting up libcupsdriver1 (1.4.1-5ubuntu2.1) ...

Setting up libcupsimage2 (1.4.1-5ubuntu2.1) ...

Setting up libcupsmime1 (1.4.1-5ubuntu2.1) ...

Setting up libcupsppdc1 (1.4.1-5ubuntu2.1) ...

Setting up libpoppler5 (0.12.0-0ubuntu2.1) ...

Setting up poppler-utils (0.12.0-0ubuntu2.1) ...
Setting up cups-common (1.4.1-5ubuntu2.1) ...
Setting up cups-client (1.4.1-5ubuntu2.1) ...

Setting up cups-bsd (1.4.1-5ubuntu2.1) ...

Setting up cups (1.4.1-5ubuntu2.1) ...
 * Starting Common Unix Printing System: cupsd                           [ OK ] 

Setting up libempathy-common (2.28.1.1-0ubuntu1) ...
Setting up libempathy30 (2.28.1.1-0ubuntu1) ...

Setting up libenchant1c2a (1.5.0-0ubuntu3) ...

Setting up libempathy-gtk-common (2.28.1.1-0ubuntu1) ...

Setting up libempathy-gtk28 (2.28.1.1-0ubuntu1) ...

Setting up empathy-doc (2.28.1.1-0ubuntu1) ...
Setting up empathy (2.28.1.1-0ubuntu1) ...
Setting up libevdocument1 (2.28.1-0ubuntu1.1) ...

Setting up libevview1 (2.28.1-0ubuntu1.1) ...

Setting up libpoppler-glib4 (0.12.0-0ubuntu2.1) ...

Setting up evince (2.28.1-0ubuntu1.1) ...
Installing new version of config file /etc/apparmor.d/abstractions/evince ...
Installing new version of config file /etc/apparmor.d/usr.bin.evince ...

Setting up libgnome-desktop-2-11 (1:2.28.1-0ubuntu3) ...

Setting up evolution-common (2.28.1-0ubuntu2) ...
Setting up evolution (2.28.1-0ubuntu2) ...

Setting up evolution-plugins (2.28.1-0ubuntu2) ...
Setting up f-spot (0.6.1.4-0ubuntu1) ...

Setting up xulrunner-1.9.1 (1.9.1.4+nobinonly-0ubuntu0.9.10.1) ...
update-alternatives: using /usr/bin/xulrunner-1.9.1 to provide /usr/bin/xulrunner (xulrunner) in auto mode.

Setting up xulrunner-1.9.1-gnome-support (1.9.1.4+nobinonly-0ubuntu0.9.10.1) ...

Setting up gnome-desktop-data (1:2.28.1-0ubuntu3) ...
Setting up gnome-about (1:2.28.1-0ubuntu3) ...
Setting up grub-common (1.97~beta4-1ubuntu4) ...
Installing new version of config file /etc/grub.d/30_os-prober ...

Setting up grub-pc (1.97~beta4-1ubuntu4) ...
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Cannot find list of partitions!
done

Setting up gtk2-engines (1:2.18.4-1ubuntu2) ...
Setting up gtk2-engines-murrine (0.90.3-1ubuntu2) ...
Setting up kerneloops-daemon (0.12+git20090217-1ubuntu4.1) ...
Installing new version of config file /etc/init.d/kerneloops ...
update-rc.d: warning: kerneloops stop runlevel arguments (0 1 6) do not match LSB Default-Stop values (1)

Setting up libclutter-gtk-0.10-0 (0.10.2-0ubuntu2) ...

Setting up libgd2-xpm (2.0.36~rc1~dfsg-3ubuntu1.9.10.1) ...

Setting up libgudev-1.0-0 (1:147~-6.1) ...

Setting up libhtml-parser-perl (3.61-1ubuntu0.1) ...
Setting up nautilus-data (1:2.28.1-0ubuntu2) ...

Setting up nautilus (1:2.28.1-0ubuntu2) ...

Setting up nvidia-common (0.2.15.1) ...

Setting up python-ubuntuone-client (1.0.2-0ubuntu2) ...

Setting up ubuntuone-client (1.0.2-0ubuntu2) ...
Setting up ubuntuone-client-gnome (1.0.2-0ubuntu2) ...
Setting up rhythmbox (0.12.5-0ubuntu5) ...

Setting up ubuntu-xsplash-artwork (0.8.5-0ubuntu1) ...
Setting up xsplash (0.8.5-0ubuntu1) ...
Setting up evolution-documentation-en (2.28.1-0ubuntu2) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.31-14-generic
Setting up apparmor-utils (2.3.1+1403-0ubuntu27.1) ...
Setting up firefox-3.5-branding (3.5.4+nobinonly-0ubuntu0.9.10.1) ...
Setting up firefox-3.5 (3.5.4+nobinonly-0ubuntu0.9.10.1) ...
Please restart all running instances of firefox-3.5, or you will experience problems.

Setting up firefox-3.5-gnome-support (3.5.4+nobinonly-0ubuntu0.9.10.1) ...

Setting up firefox (3.5.4+nobinonly-0ubuntu0.9.10.1) ...
Setting up firefox-gnome-support (3.5.4+nobinonly-0ubuntu0.9.10.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
root@ubuntu:/# mv /boot/grub /boot/grub_old
root@ubuntu:/# mkdir /boot/grub
root@ubuntu:/# apt-get install --reinstall grub-pc grub-common os-prober
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 3 reinstalled, 0 to remove and 0 not upgraded.
Need to get 22.1kB/1,450kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main os-prober 1.35 [22.1kB]
Fetched 22.1kB in 0s (29.3kB/s)  
Preconfiguring packages ...
Can not write log, openpty() failed (/dev/pts not mounted?)
(Reading database ... 114036 files and directories currently installed.)
Preparing to replace grub-common 1.97~beta4-1ubuntu4 (using .../grub-common_1.97~beta4-1ubuntu4_i386.deb) ...
Unpacking replacement grub-common ...
Preparing to replace grub-pc 1.97~beta4-1ubuntu4 (using .../grub-pc_1.97~beta4-1ubuntu4_i386.deb) ...
Unpacking replacement grub-pc ...
Preparing to replace os-prober 1.35 (using .../os-prober_1.35_i386.deb) ...
Unpacking replacement os-prober ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Processing triggers for sreadahead ...
Can not write log, openpty() failed (/dev/pts not mounted?)
Setting up grub-common (1.97~beta4-1ubuntu4) ...

Setting up grub-pc (1.97~beta4-1ubuntu4) ...
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Cannot find list of partitions!
done

Setting up os-prober (1.35) ...
root@ubuntu:/# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Cannot find list of partitions!
done
root@ubuntu:/# grub-install /dev/sda
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda
root@ubuntu:/# exit
exit
ubuntu@ubuntu:~$ sudo umount /mnt/dev
umount: /mnt/dev: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
ubuntu@ubuntu:~$ !!
sudo umount /mnt/dev
umount: /mnt/dev: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
ubuntu@ubuntu:~$ sudo umount /mnt/proc
umount: /mnt/proc: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
ubuntu@ubuntu:~$ !!
sudo umount /mnt/proc
umount: /mnt/proc: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
ubuntu@ubuntu:~$ sudo umount /mnt
umount: /mnt: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
ubuntu@ubuntu:~$

---

### Post by kansasnoob on 2009-11-10
There were a lot of errors there. Since that didn't unmount see what happens when you just run the command:

```
sudo chroot /mnt
```

If it appears to mount run the command:

```
top
```

Maybe we can see what's running.

---

### Post by Tholley on 2009-11-10
> **kansasnoob said:**
> There were a lot of errors there. Since that didn't unmount see what happens when you just run the command:

```
sudo chroot /mnt
```If it appears to mount run the command:

```
top
```Maybe we can see what's running.

it did but won't let me copy...

---

### Post by Tholley on 2009-11-10
It is constantly changing, what do I need to look for?

Tasks: 139 total, 1 running, 138 sleeping, ?

PIDS & USER keeps changing/fluctuating.

---

### Post by kansasnoob on 2009-11-10
> **Tholley said:**
> It is constantly changing, what do I need to look for?

Tasks: 139 total, 1 running, 138 sleeping, ?

PIDS & USER keeps changing/fluctuating.

Type k.

It should then ask what process to kill by PID.

Start killing. Kill everything but gnome-terminal.

---

### Post by kansasnoob on 2009-11-10
Oh, and kill top last.

Then try to run:

```
dpkg --configure -a
```

---

### Post by Tholley on 2009-11-10
> Type k.

It should then ask what process to kill by PID.

Start killing. Kill everything but gnome-terminal.

I did, typed in 2182 whch showed to be Xorg, it said something, not sure if it was asking me to kill, I pressed enter and it shut me down.

I still have set to boot from CD, but am now at a Log In screen and everything is frozen.

---

### Post by kansasnoob on 2009-11-10
Well, you'll probably just have to do a hard reboot.

I've never seen that happen before. Never!

---

### Post by kansasnoob on 2009-11-10
I was in hopes that reinstalling grub2 would fix this:

> =========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sda

00000000  eb 63 90 d0 bc 00 7c fb  50 07 50 1f fc be 1b 7c  |.c....|.P.P....||
00000010  bf 1b 06 50 57 b9 e5 01  f3 a4 cb bd be 07 b1 04  |...PW...........|
00000020  38 6e 00 7c 09 75 13 83  c5 10 e2 f4 cd 18 8b f5  |8n.|.u..........|
00000030  83 c6 10 49 74 19 38 2c  74 f6 a0 b5 07 b4 03 02  |...It.8,t.......|
00000040  ff 00 00 20 01 00 00 00  00 02 fa 90 90 f6 c2 80  |... ............|
00000050  75 02 b2 80 ea 59 7c 00  00 31 00 80 01 00 00 00  |u....Y|..1......|
00000060  00 00 00 00 ff fa eb 07  f6 c2 80 75 02 b2 80 ea  |...........u....|
00000070  74 7c 00 00 31 c0 8e d8  8e d0 bc 00 20 fb a0 64  |t|..1....... ..d|
00000080  7c 3c ff 74 02 88 c2 52  be 88 7d e8 24 01 be 05  ||<.t...R..}.$...|
00000090  7c f6 c2 80 74 48 b4 41  bb aa 55 cd 13 5a 52 72  ||...tH.A..U..ZRr|
000000a0  3d 81 fb 55 aa 75 37 83  e1 01 74 32 31 c0 89 44  |=..U.u7...t21..D|
000000b0  04 40 88 44 ff 89 44 02  c7 04 10 00 66 8b 1e 5c  |.@.D..D.....f..\|
000000c0  7c 66 89 5c 08 66 8b 1e  60 7c 66 89 5c 0c c7 44  ||f.\.f..`|f.\..D|
000000d0  06 00 70 b4 42 cd 13 72  05 bb 00 70 eb 73 b4 08  |..p.B..r...p.s..|
000000e0  cd 13 73 0a f6 c2 80 0f  84 d8 00 e9 82 00 66 0f  |..s...........f.|
000000f0  b6 c6 88 64 ff 40 66 89  44 04 0f b6 d1 c1 e2 02  |...d.@f.D.......|
00000100  88 e8 88 f4 40 89 44 08  0f b6 c2 c0 e8 02 66 89  |....@.D.......f.|
00000110  04 66 a1 60 7c 66 09 c0  75 4e 66 a1 5c 7c 66 31  |.f.`|f..uNf.\|f1|
00000120  d2 66 f7 34 88 d1 31 d2  66 f7 74 04 3b 44 08 7d  |.f.4..1.f.t.;D.}|
00000130  37 fe c1 88 c5 30 c0 c1  e8 02 08 c1 88 d0 5a 88  |7....0........Z.|
00000140  c6 bb 00 70 8e c3 31 db  b8 01 02 cd 13 72 29 8c  |...p..1......r).|
00000150  c3 60 1e b9 00 01 8e db  31 f6 bf 00 80 8e c6 fc  |.`......1.......|
00000160  f3 a5 1f 61 ff 26 5a 7c  be 8e 7d e8 44 00 eb 0e  |...a.&Z|..}.D...|
00000170  be 93 7d e8 3c 00 eb 06  be 9d 7d e8 34 00 be a2  |..}.<.....}.4...|
00000180  7d e8 2e 00 cd 18 eb fe  47 52 55 42 20 00 47 65  |}.......GRUB .Ge|
00000190  6f 6d 00 48 61 72 64 20  44 69 73 6b 00 52 65 61  |om.Hard Disk.Rea|
000001a0  64 00 20 45 72 72 6f 72  0d 0a 00 bb 01 00 b4 0e  |d. Error........|
000001b0  cd 10 ac 3c 00 75 f4 c3  0c fa 0c fa 00 00 80 01  |...<.u..........|
000001c0  01 00 83 fe ff ff 3f 00  00 00 8d 93 9b 04 00 fe  |......?.........|
000001d0  ff ff 05 fe ff ff cc 93  9b 04 3a 98 2d 00 00 00  |..........:.-...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Now I'm just not sure.

---

### Post by Tholley on 2009-11-10
I downloaded a new 9.10 CD and burned a new copy, should I maybe just try to do another fresh install?

Or do you think I would have the same problem?

Would a video card have anything to do with it?

Reason asking is, before I tried to install 9.10 the first time, I replaced the video card with a little bit better/newer nvidia card. I thought that was the prob, so put the old one back in and it still was asking me to apply the nvidia restricted drivers in the Live CD.

just a thought...

---

### Post by Tholley on 2009-11-10
oh... back in CD now

---

### Post by kansasnoob on 2009-11-10
Since you're back in the Live Desktop I'd try to repeat that, but instead of "apt-get update" & "apt-get dist-upgrade" try:

```
dpkg --configure -a
```

If either that or "update-grub" return errors I think you'll have to reinstall. Can't hurt to just try and reboot though.

I don't think this is due to your graphics card.

Just btw I checked my /usr/lib/grub/grub-mkconfig_lib and it's correct without editing so updates must have fixed it. Referring to this:

[http://ubuntuforums.org/showpost.php?p=8170878&postcount=6](http://ubuntuforums.org/showpost.php?p=8170878&postcount=6)

---

### Post by Tholley on 2009-11-10
> **kansasnoob said:**
> Since you're back in the Live Desktop I'd try to repeat that, but instead of "apt-get update" & "apt-get dist-upgrade" try:

```
dpkg --configure -a
```If either that or "update-grub" return errors I think you'll have to reinstall. Can't hurt to just try and reboot though.

I don't think this is due to your graphics card.

Just btw I checked my /usr/lib/grub/grub-mkconfig_lib and it's correct without editing so updates must have fixed it. Referring to this:

[http://ubuntuforums.org/showpost.php?p=8170878&postcount=6](http://ubuntuforums.org/showpost.php?p=8170878&postcount=6)

So go ahead and do all of what we did earlier, but don't do the 2 above, instead do the dpkg --- ?

---

### Post by kansasnoob on 2009-11-10
> **Tholley said:**
> So go ahead and do all of what we did earlier, but don't do the 2 above, instead do the dpkg --- ?

Yes.

I've just never seen a mount/chroot stay mounted like that. Or soooooooo many failures.

Then again I've never seen errors like you had in that Boot Info script.

---

### Post by Tholley on 2009-11-10
are the "cannot write log, openpty() failed (/dev/pts not mounted?) a concern?

or the Cannot find list of partitions! ?

---

### Post by Tholley on 2009-11-10
rebooting now!

---

### Post by Tholley on 2009-11-10
nope... :sad:

error: no such device: 415e5ecb-e9b3-45a5-b049-baad4589e4bb
 Failed to boot default entries.
Press any key to continue...

---

### Post by ranch hand on 2009-11-10
I have been lurking and pulling for this.  A my foather used to say "OH THE DEVIL AND ALL HIS HELPERS".

---

### Post by Tholley on 2009-11-10
Thanks...

I'm trying another fresh install now with the new CD...

wish me luck!

---

### Post by Tholley on 2009-11-10
Still didn't work... I give up!

So I'm gonna try to re-install 9.04. If that works, maybe I'll try the upgrade (or just leave the heck alone).

Now if 9.04 won't re-install, then I'll know it is a hardware problem.

Good thing this was just a spare computer I was gonna give to either my daughter or a coworker.

If this would have been on one of my main computers, I'd be raving mad about now.

---

### Post by ranch hand on 2009-11-10
Upgrades are a little tougher than a clean install.  If you get 9.04 back on there, I would leave well enough alone.

---

### Post by kansasnoob on 2009-11-10
> **ranch hand said:**
> Upgrades are a little tougher than a clean install.  If you get 9.04 back on there, I would leave well enough alone.

Ditto that!

I've seen problems in the past few weeks that I've never seen before.

---

### Post by Tholley on 2009-11-10
> **ranch hand said:**
> Upgrades are a little tougher than a clean install.  If you get 9.04 back on there, I would leave well enough alone.

Yeah... I know what you mean... I did an upgrade on my other machine first and had all kinds of issues! After spending a couple days troubleshooting like today, I ended up doing a clean install after all. 

That one went well tho! 

So yes... I will probably leave as is.

As long it installs... we'll see in a few minutes.

---

### Post by Tholley on 2009-11-10
oh yeah... Thanks everybody, especially kansasnoob for all the help!

---

### Post by Tholley on 2009-11-10
Well... 9.04 installed again just fine.

So must be a compatibility issue with 9.10 and this dinosaur computer.

Thanks again for all your help kansasnoob!


I would not not consider this "Solved" tho, by any means.

---

### Post by not me on 2009-11-10
(this is the quote from the post I've just created [http://ubuntuforums.org/showthread.php?t=1322223](http://ubuntuforums.org/showthread.php?t=1322223) )

> Hi.

I've just finished installing Ubuntu 9.1 Desktop 386.

When the instalation finishes, the CD ejects, I take it out, close the tray, and the notebook reboots.

When the BIOS presentation ends, I get this

---------------------------------------------------

GRUB Loading
Error: no such device: 83d79e62-2763-473f-9ef7-51ee8b2d49df

----------------------------------------------------

for one half of a second and then my screen goes blank

Just to be certain, I installed it twice, with the same result

This notebook use to have 6, hours ago, Fedora 11 and worked fine

The hardware info is Compaq EVO N610c
1.5 GB
160 GB IDE Disk

Please guide me to detect the failure.

Thanks


---

I've checked HDD integrity with Live CD and it's OK, so is the Ram
Fedora worked fine

It is not a hardware problem.

Please tell me the status of this bug.

---

### Post by kansasnoob on 2009-11-10
> **Tholley said:**
> Well... 9.04 installed again just fine.

So must be a compatibility issue with 9.10 and this dinosaur computer.

Thanks again for all your help kansasnoob!


I would not not consider this "Solved" tho, by any means.

I'm sorry we couldn't work things out for you.

---

### Post by rexh on 2009-11-10
I had the same error message when I installed 9.10 on a new hard drive in an old laptop.
 I found out that if hit "shift" as the computer was booting I could get to the grub menu.  Once in the grub2 menu I typed "e" and was able to do a one time edit of the boot menu and when I erased the entire line that starts with the word "search" and then typed Control "x" the computer boots.

---

### Post by not me on 2009-11-10
Where can I download 9.04 from?

---

### Post by Lord_Chewbakka on 2009-11-11
I've been following this thread intensely since I am on a IBM Thinkpad R40 and got the same error message. The hardrive is the default fujitsu drive. 

I've also tried Xubuntu to see if that one would work, which it didn't.

I can however confirm that post #58 did work, but only to get me in to Ubuntu. The "search" line is added by default if I restart again.

Since I am quite the noob I´m going to see if I can find this text and edit it with sudo instead, to make the change permanent. Anyone got any ideas which file that holds the text?

---

### Post by Lord_Chewbakka on 2009-11-11
Okay, I have an update.

I tried changing the grub config which held the line search --no-floppy etc.. which didn't help since it was generated again upon reboot.

However, I followed the guide: [https://help.ubuntu.com/community/Grub2#Reverting%20to%20GRUB%20Legacy](https://help.ubuntu.com/community/Grub2#Reverting%20to%20GRUB%20Legacy) and reverted from Grub 2, and now I can boot.

Just wanted to let you guys know of this temporary fix.__[URL="https://help.ubuntu.com/community/Grub2#Reverting%20to%20GRUB%20Legacy"]
[/URL]

---

### Post by rexh on 2009-11-11
Here is a more permanant temporary solution, It was sent to me by drs305. If you do this you can boot your computer until you update Grub2, then you have to do it again. drs305 sent me some other options as well but I have not found the time to try them yet. I am and a newbie and have no real knowledge of the Grub code. Anyway here is the code:
 
sudo chmod +w /boot/grub/grub.cfg # makes writable
sudo cp /boot/grub/grub.cfg /boot/grub/grub.cfg.old
gksu gedit /boot/grub/grub.cfg
 
Place a comment in front of the "search" lines.
 
Save the file, then:
sudo update-grub
 
 
 
I have found that it works without doing the "sudo update-grub" step.

---

### Post by Lord_Chewbakka on 2009-11-11
Tried your solution and it didn't work. I basically did the same thing as you did before, and made sure that my changes were set with sudo vim ... but the changes I did were reverted by the system during the reboot.
Why did you do an update at the end where? Seems to defeat  the purpose of editing the config.

Anyways, my solution still works, if you can live with using Grub instead of Grub 2.

---

### Post by rexh on 2009-11-11
When I have edited the grub2 menu, I have not been doing the "sudo-update" at the end of that sequence.  Reverting to an earlier Grub version until this is all worked out is probably the best option anyway.  The edit I have been using only works until Grub is updated, then it reverts back and the menu has to be edited again.

---

### Post by Tholley on 2009-11-11
> **not me said:**
> Where can I download 9.04 from?
 
You can download the 9.04 torrent file here, best bet is to make sure you have something like Deluge as a BitTorrent client. Works like a champ!
 
[http://www.torrentz.com/60d5d82328b4547511fdeac9bf4d0112daa0ce00](http://www.torrentz.com/60d5d82328b4547511fdeac9bf4d0112daa0ce00)
 
and personal experience, use any (I like PirateBay) except the "sponsered" site

---

### Post by Jakint on 2009-11-16
> **Lord_Chewbakka said:**
> Tried your solution and it didn't work. I basically did the same thing as you did before, and made sure that my changes were set with sudo vim ... but the changes I did were reverted by the system during the reboot.
Why did you do an update at the end where? Seems to defeat  the purpose of editing the config.

Anyways, my solution still works, if you can live with using Grub instead of Grub 2.

There are a few solution that don't seem to work for getting rid of that "search" line.
Changing grub.cfg gets overwritten after the next update-grub.
Changing grub-mkconfig_lib is overwritten at some point too (if the package is updated I think).
Here's how I did it, it seem to work for now:

[LIST=1]
[*]Open a terminal (in Applications -> Accessories)
[*]cd /etc/grub.d/ #change folder
[*]sudo cp 10_linux 07_custom #we use a copy to keep the flags on the file
[*]sudo gedit 07_custom
[*]remove content and paste the content of the file attached to this reply (07_custom.txt) and save and close gedit
[*]sudo gedit /etc/default/grub
[*]uncomment the line GRUB_DISABLE_LINUX_UUID=true and save and close gedit
[*]sudo update-grub #updates grub.cfg with our changes
[/LIST]
This should create two new entries in grub.cfg with exactly the same title as before preceeded with custom and no search line in the entry. The path /dev/sda* will be used instead of the UUID too.

If it doesn't work, you can still choose the old entries with search line in the grub menu at boot. Remove the 07_custom file and re-comment to undo.

As this is the proper way to configure, this won't be erased by future updates and this should update itself if the kernel version changes.

Hope this helps,
Jakint
[Edit: change upgrade to update on line 8]

---

### Post by zwat on 2009-11-17
I just followed jakint's guide. now it boots up, but with an "no such device error" and it skips the grub selection window. I'm too new to ubuntu and linux to know if that is a problem :D


also change point 8 *from upgrade to update for a working command.

---

### Post by Jakint on 2009-11-17
We could do something about that message too but I got lazy and was happy enough it just starts.
Updated with your comment cheers.

---

### Post by hwscell on 2009-11-18
Jakint, Thanks for your terrific work on this.

I had exactly the same problem, only I had no way to boot at all, when I held down shift, I did not get a GRUB menu, it perniciously went to the grub rescue> prompt
when I did a LS, I could see the devices, but trying to ls the files only got me "Cannot get C/H/S or some such error.

I tried booting off a cd, but then I only had Read only access to the partition, so again, couldn't make the changes once to even boot, and couldn't make the semi-permanent changes you recommended. 

I figured I had 3 options - 
1 fall back to 9.04 
2 load GRUB1 or LILO
3 pray to Jah and sacrifice a goat

fortunately for the goat, I decided to play around with my system BIOS /CMOS settings first.

I had a setting to turn off the on-chip FDD (floppy disk) controlller, and an option mysteriously called "Report FDD not available to OS?" which I turned ON.

Voila, GRUB2 works like a charm.

I still can't use shift to break into the menu, I suspect I have a weird keyboard controller or keyboard issue.

So, as you work towards a solution for GRUB 2, my guess is that the configurations it is tested for have BIOS for machines that don't even have FDD controllers.  But for older machines and laptops, the FDD controller is sometimes hidden but not used in the main board or onboard chip. (or in my case an on-chip controller)

For other users with the same problem, dig deep into your BIOS settings and try disabling anything related to the Floppy drive or FDD, might make GIMP2 work for ya without resorting to editing it.

peace, h

---

### Post by tyrannosaur on 2009-11-18
I had exactly the same problems with my Compaq Presario 2500. I downloaded UE 2.4, wiped the disk, formatted to XFS, installed, and received "cannot find hardware". I did this 3 times. I downloaded again, same error. I then tried to load 2.4 with only the defaults, same error. I used both UE 2.3 and Windows XP to burn the ISO, same problem. I partitioned the drive, I loaded/installed 2.4 and then 2.3. 2.3 (that is 9.04) loaded perfectly, 2.4 would not load, grub showed "generic linux version". When you tried the 2.4 it would go into a dead zone in which nothing would work. I then reversed the process, loaded 2.3 then 2.4. This time grub reported "error". I then used pure Ubuntu 9.10 and 9.04 in exactly the same procedure with exactly the same results. I am not sure what is going on here but something appears out of wack with the new grub and 9.10.

---

### Post by Tholley on 2009-11-18
It's good to see this topic is still up and going. :smile:
 As I had mentioned before, I reverted back to 9.04 and has been working perfect.
 
I would still like to put 9.10 on it someday, (just 'cause I like to have the lastest-greatest) but am not going to attempt it again until there is a sure fire fix. 
 
It looks like alot of great stuff, but what works for one, doesn't work for everbody, and still leaves some bugs behind. 
 
So Y'all keep this thread alive and sooner or later there will be a complete solution!
 
ta ta for now... and good luck to everybody!
 
(I just wish I could this kind of response for my cdrom0 thread!)

---

### Post by Tavathlon on 2009-11-30
Hi guys, and thank you unknowingly helping me!  =D

Thanks to Jakint's guide on page 7, I managed to get on the right track, even though that fix didn't do it for me. You see, eliminating the 'search'-line never helped for me at all, although the symptoms otherwise were similar - sometimes, at least. My problems have not been 100% reproducible, but have rather been quite random. Anyway, I think the problem is solved no.

Instead of deleting/uncommenting the 'search' line, I managed to boot of I added "acpi=off" after the line that ends with "quiet splash". Consequently, Jakint's guide literally would not help me, since it only fixes the 'search' line. What I did instead is that I sudo gedited the /etc/default/grub file, and replaced this line:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

with this:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off"

(or rather, just added acpi=off)

Since the problem was kinda random to begin with, by randomly messing up boot also from Live CD (while it sometimes worked without this fix), I cannot be 100% sure yet whether it's gonna work in the long run. It works so far anyway, so I am happy for now.  =P

Once more, thank you! And I hope my addition might help someone else with the same problem.  =)

---

### Post by Harix on 2010-03-23
Many thanks, Yakint, after problems with loading grub, your solution worked fine for my (old) PC, ASUS CUSL2 1000 MHZ, Intel 815E chipset, with new 320 gb harddrive. Have ubuntu 9.10 installed now and running perfectly!!
Thanks again!

---

