---
title: "I killed Kubuntu (I think)"
date: 2010-03-24
forum: New to Ubuntu
---

### Post by sixthwheel on 2010-03-24
After using Ubuntu for a month now, and may I say that I'm thrilled with it, I decided to install Kubuntu.

Everything went fine, got it set up , then went looking for Synaptic.

I found the repository, and downloaded a bunch of stuff.
It downloaded fine, however after I restarted the system,  logged in, the Plasma thingie stopped working.

No desktop...Just total blackness.
A pop up window came up , something about the plasma thing  was messed up.

I tried to copy the message, but copy didn't work.
I restarted it a few times, even in recovery mode, told it to fix the little bugs, then restarted it, and the same problem.

BTW..What is this plasma thing?

---

### Post by sixthwheel on 2010-03-24
I ran fsck, and this is the output.
It's showing 50 Gigs in the Disk Utility


```
peter@peter-laptop:~$ sudo fsck /dev/sda2
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda2
Could this be a zero-length partition?
peter@peter-laptop:~$ 

```

---

### Post by lykwydchykyn on 2010-03-24
plasma is the part of KDE that draws your desktop, panels, widgets, etc.

For some reason, it's crashing on you.

When you log in to KDE, can you hit alt-f2 and bring up the krunner dialog?  If so, it would be helpful from a trouble shooting perspective if you did this:
 - launch konsole
 - run the command "plasma-desktop"
 - copy and paste the output here

---

### Post by sixthwheel on 2010-03-24
Now I ran Fdisk, and its showing my kubuntu partition as extended..Did it get wiped off the face of the Earth?

```
peter@peter-laptop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13731372

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3701    29728251    7  HPFS/NTFS
/dev/sda2            3702        9729    48419910    5  Extended
/dev/sda5            5713        9558    30892963+  83  Linux
/dev/sda6            9559        9729     1373526   82  Linux swap / Solaris
/dev/sda7            3702        5622    15430369+  83  Linux
/dev/sda8            5623        5712      722893+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

---

### Post by lykwydchykyn on 2010-03-24
I don't think /dev/sda2 is your KDE partition.  When you create extended partitions, one partition name is designated to represent the whole extended partition, and subsequent names are used to represent partitions within the extended partition.

That probably makes no sense, but if you look at the start and end values for your partitions it might be more apparent where things are located.

try typing the "mount" command to show what is where.

---

### Post by sixthwheel on 2010-03-24
p```
eter@peter-laptop:~$ mount
/dev/sda5 on / type ext4 (rw,errors=remount-ro)
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
gvfs-fuse-daemon on /home/peter/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=peter)

```

---

### Post by sixthwheel on 2010-03-24
partition 1 is Windows, and 5 is Ubuntu....7 does not show in grub.
When I select partition2  the kubuntu logo comes on, then nothing, but blackness

---

### Post by lykwydchykyn on 2010-03-24
Looks like your Kubuntu is on /dev/sda5, if that's what you're currently booted to there.

That would explain your fsck output.

It doesn't explain why plasma is crashing, but if you can paste that output I mentioned above, that might put us in the right direction.

---

### Post by lykwydchykyn on 2010-03-24
> **sixthwheel said:**
> partition 1 is Windows, and 5 is Ubuntu....7 does not show in grub.
When I select partition2  the kubuntu logo comes on, then nothing, but blackness
Ah, so Ubuntu is not on /dev/sda5.  Do you know what IS on /dev/sda7?  Most likely that's your Kubuntu.

---

### Post by sixthwheel on 2010-03-24
> if that's what you're currently booted to there.
Cant boot to Kubuntu...BTW a fellow Tennesseean...

---

### Post by The Cog on 2010-03-24
Agreed. Your kubuntu partition is either sda5 or sda7. An "extended" partition is just a container partition that is dedicated to holding a set of inner partitions.

If you need to reinstall, remember that kubuntu doesn't use synaptic. It uses somethig called kpackagekit instead.

---

### Post by sixthwheel on 2010-03-24
I have no idea whats on 7..it does not show in grub

---

### Post by lykwydchykyn on 2010-03-24
> **The Cog said:**
> Agreed. Your kubuntu partition is either sda5 or sda7. An "extended" partition is just a container partition that is dedicated to holding a set of inner partitions.

If you need to reinstall, remember that kubuntu doesn't use synaptic. It uses somethig called kpackagekit instead.
Synaptic should work just fine in Kubuntu (though it won't be installed by default).  Personally I'd recommend it if that's what you're used to.

> **sixthwheel said:**
> I have no idea whats on 7..it does not show in grub

Can you post the contents of /boot/grub/grub.cfg ?  Are you using 9.10 for both Ubuntu and Kubuntu, and is your Ubuntu a clean 9.10 install or upgraded from previous versions (what I'm getting at is, are you using grub1 or grub2 on these installs)?

BTW, if you don't mind me asking, what part of TN you from?

---

### Post by sixthwheel on 2010-03-24
is there anyway to screenshot grub?

If not..I have 2 instances of Linux without a number, then I have one instance of Windows, then 3 instances of Linux again.
The first instance is Kubuntu..I know that, because when I selected,the Kubuntu logo comes on, then everything goes to black.

It's no big deal, I just installed Kubuntu to play with it, so if I lose it no biggie

---

### Post by sixthwheel on 2010-03-24
> Can you post the contents of /boot/grub/grub.cfg ? Are you using 9.10 for both Ubuntu and Kubuntu, and is your Ubuntu a clean 9.10 install or upgraded from previous versions (what I'm getting at is, are you using grub1 or grub2 on these installs)?

BTW, if you don't mind me asking, what part of TN you from? 	


Ubuntu clean install. I would imagine is Grub 2 Both Ubuntu and Kubuntu is 9.10

Chattanooga


```
peter@peter-laptop:~$ /boot/grub/grub.cfg 
bash: /boot/grub/grub.cfg: Permission denied
peter@peter-laptop:~$ 

```

---

### Post by Pbethe on 2010-03-24
> **sixthwheel said:**
> Ubuntu clean install. I would imagine is Grub 2 Both Ubuntu and Kubuntu is 9.10

Chattanooga


```
peter@peter-laptop:~$ /boot/grub/grub.cfg 
bash: /boot/grub/grub.cfg: Permission denied
peter@peter-laptop:~$ 

```

I think you want to enter this:

cat /boot/grub/grub.cfg

Paul

---

### Post by sixthwheel on 2010-03-24
> **Pbethe said:**
> I think you want to enter this:

cat /boot/grub/grub.cfg

Paul

```
peter@peter-laptop:~$ cat /boot/grub/grub.cfg
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
search --no-floppy --fs-uuid --set 3f19da88-2d9c-449d-86bc-252f2ea8ea15
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
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 3f19da88-2d9c-449d-86bc-252f2ea8ea15
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=3f19da88-2d9c-449d-86bc-252f2ea8ea15 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 3f19da88-2d9c-449d-86bc-252f2ea8ea15
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=3f19da88-2d9c-449d-86bc-252f2ea8ea15 ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 3f19da88-2d9c-449d-86bc-252f2ea8ea15
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=3f19da88-2d9c-449d-86bc-252f2ea8ea15 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 3f19da88-2d9c-449d-86bc-252f2ea8ea15
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=3f19da88-2d9c-449d-86bc-252f2ea8ea15 ro single 
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
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 4cb4bdbab4bda73c
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
peter@peter-laptop:~$ 


```

---

### Post by lykwydchykyn on 2010-03-24
Hmmm... Looks like there's no entry there for anything but your /dev/sda5 install (notice all the boot entries have root=(hd0,5)).

I'm guessing the Kubuntu install has its own /boot directory on /dev/sda7, but I haven't tried dual-booting with grub2 yet so I'm not sure how to proceed there.

You could try re-running
```

sudo update-grub

```
to see if it picks up your Kubuntu partition automatically.

---

