---
title: "Change 10.04  under wubi into dedicated install"
date: 2010-05-18
forum: New to Ubuntu
---

### Post by vince2678 on 2010-05-18
Is it possible to change a wubi installation of lucid lynx into an install on a dedicated installation on a partition? The most recent version of lvpm is for the hardy installation.
Is there another way of doing this?

---

### Post by ubunterooster on 2010-05-18
try to use [http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/) 

That's my best guess.

---

### Post by drs305 on 2010-05-18
Refer to this wubi guide. Section 8.8 discusses the transition - or is that the script that won't work for you? The first part of the section appears to apply to more than just 8.04.
[https://wiki.ubuntu.com/WubiGuide]("https://wiki.ubuntu.com/WubiGuide")

---

### Post by ubunterooster on 2010-05-18
This part:> How do I migrate to a real partition, and/or get rid of Windows entirely?
Existing Wubi/Lubi installations can be upgraded to an installation on a dedicated partition via LVPM. The main site for LVPM is at [http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html) and the guide and support forum is at [http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591).

As an alternative, the following script can be used with Wubi 8.04.

Download wubi-move-to-partition

Open a terminal and run:

sudo sh wubi-move-to-partition /dev/sda9 /dev/sda10
Replace /dev/sda9 with the partition where you would like to migrate the Wubi installation to, and /dev/sda10 with the appropriate swap partition (you can omit the second argument completely, in which case no swap will be setup). The two partitions must already exist and be empty (you can use any partitioning tool such as gparted to create them in advance). Note that the script will install grub as main bootloader replacing the existing bootloader, and it may not be easy to undo the changes (if things do not work as expected you will have to boot from a Live CD and replace/edit the bootloader manually). Also note that if you have multiple hard-disks, the disk order might have to be adjusted manually.

---

### Post by vince2678 on 2010-05-18
Can I use wubi-move-to-partition with wubi 10.04? Does it work while running ubuntu inside the virtual partitions?

---

### Post by oldfred on 2010-05-18
I am not sure I have seen anyone do this with 10.04, but some used LVPM to convert older but too new to be supported versions and it seemed to copy most everything but then not set up grub correctly.

I would make sure you have at least one Ubuntu liveCD that you know boots and possibly a rescue disk like:
    * SystemRescueCd
    * PartedMagic 
Or you can use USB versions if your computer lets you boot USBs directly. 

You just want to have another way to boot and possibly do commands to repair in case it does not boot correctly.

---

### Post by ubunterooster on 2010-05-18
> **vince2678 said:**
> Can I use wubi-move-to-partition with wubi 10.04? Does it work while running ubuntu inside the virtual partitions?
I believe so.

---

### Post by vince2678 on 2010-06-02
Thanks for the help. Wubi-move-to-partition worked , with a little mods to the file.

---

### Post by Rhsameera on 2010-06-13
> **vince2678 said:**
> Thanks for the help. Wubi-move-to-partition worked , with a little mods to the file.

I'm new to linux.

Can you tell me what is the mod did u do to files?

---

### Post by vince2678 on 2010-06-17
Well, the original file was:

```
#!/bin/sh -e

# Moves a loopinstallation (e.g. Wubi) to a dedicated partition.

# Copyright (C) 2008 Agostino Russo <agostino.russo@gmail.com>

# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2, or (at your option) any
# later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA  02111-1307 USA

dev=$1
swapdev=$2
target=/tmp/wubitarget
swap=/tmp/wubiswap    
usage="
The function should be invokes as follows:
\n
\n\tsudo sh $0 target_partition [swap_partition]
\n
\nFor instance, in order to move to /dev/sda3 use:
\n
\n\tsudo sh $0 /dev/sda3
\n
\nand if you want to have swap on sda5 use:
\n
\n\tsudo sh $0 /dev/sda3 /dev/sda5
\n
"

usage(){
    echo $usage
    exit 1
}

sanity_checks(){
    echo "Sanity checks..."
    if [ -z "$dev" ] || [ ! -b "$dev" ]; then
        echo "First argument (target_partition=$dev) must be a valid partition."
        usage    
    fi
    if [ -n "$swapdev" ] && [ ! -b "$swapdev" ]; then
        echo "Swapdevice=$swapdev is not a block device."            
        usage
    fi
    if [ "$(whoami)" != root ]; then
        echo "Admin rights are required to run this program."
        exit 1
    fi
    mkdir -p $target    
    umount $target 2> /dev/null || true
    if mount -t auto "$dev" $target 2> /dev/null; then
        if [ $(ls -1 $target | wc -l) -gt 1 ] || \
        [ "$(ls -1 $target)" != "lost+found" ]; then    
            echo "Volume $dev is in use. Aborting"
            umount $target || true        
            exit 1
        fi
        umount $target
    fi
}

create_root(){
    mkfs.ext3 $dev
    mount $dev $target
    size=$(df | awk '$5=="/" || $5=="/home" || $5=="/usr" {sum += $3} END {print sum}')
    free_space=$(df $target|tail -n 1|awk '{print $4}')
    if [ $free_space -lt $size ]; then
        echo "Not enough free space ($free_space MB < $size MB), aborting."
        exit 1
    fi
}

migrate_files(){
    echo "Migrating files..."
    rsync -av --exclude=/host --exclude=/mnt/* --exclude=/home/*/.gvfs --exclude=/media/*/* --exclude=/tmp/* --exclude=/proc/* --exclude=/sys/* / $target
}

edit_fstab(){
    echo "Editing fstab..."
    sed -i 's:/.*[\.]disk .*::' $target/etc/fstab
    sed -i 's:/.*/disks/boot .*::' $target/etc/fstab
    echo "UUID=$(vol_id --uuid $dev)    /    ext3    errors=remount-ro    0    1" >> $target/etc/fstab
    if [ -b "$swapdev" ]; then
        echo "UUID=$(vol_id --uuid $swapdev)    none    swap    sw    0    0" >> $target/etc/fstab
    fi
}

target_cmd(){
    mount -o bind /proc $target/proc
    mount -o bind /dev $target/dev
    mount -o bind /sys $target/sys
    chroot $target $*
    umount $target/proc
    umount $target/dev
    umount $target/sys     
}

edit_grub(){
    echo "Editing grub..."    
    sed -i "s:# groot=.*::" $target/boot/grub/menu.lst
    sed -i "s:kopt=.* ro:kopt=root=UUID=$(vol_id --uuid $dev) ro:" $target/boot/grub/menu.lst
    cp /usr/lib/grub/*/*stage* $target/boot/grub/    
    target_cmd update-grub
    disk=${dev%%[0-9]*}
    partn=${dev#$disk}
    disk=${disk##*/}
    gdisk=$(grep -w $disk /boot/grub/device.map|cut -d ')' -f 1)
    gdisk=${gdisk#\(}
    gpartn=$(expr $partn - 1)
    [ -z "$gdisk" ] && gdisk=hd0
    [ -z "$gpartn" ] && gpartn=0    
    echo "
    root ($gdisk,$gpartn)
    setup ($gdisk)
    setup (hd0)
    quit" | grub --batch --device-map=/boot/grub/device.map
}

remove_lupin_support(){
    echo "Removing lupin_support..."    
    target_cmd apt-get -y remove lupin-support
}

create_swap(){
    echo "Creating swap..."
    if [ -b "$swapdev" ]; then
        mkdir -p $swap        
        if mount -t auto "$swapdev" $swap 2> /dev/null; then
            echo "Volume $swapdev is in use. Skipping swap"
            umount $swap || true
        else
            mkswap $swapdev         
        fi
    fi
}

sanity_checks
create_root
create_swap
migrate_files
edit_fstab
remove_lupin_support
edit_grub
umount $dev
echo "\nOperation completed successfully, if all is good feel free to remove the installation from windows."


```

The modified one was:
```
#!/bin/sh -e

# Moves a loopinstallation (e.g. Wubi) to a dedicated partition.

# Copyright (C) 2008 Agostino Russo <agostino.russo@gmail.com>

# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2, or (at your option) any
# later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA  02111-1307 USA

dev=$1
swapdev=$2
target=/tmp/wubitarget
swap=/tmp/wubiswap    
usage="
The function should be invokes as follows:
\n
\n\tsudo sh $0 target_partition [swap_partition]
\n
\nFor instance, in order to move to /dev/sda3 use:
\n
\n\tsudo sh $0 /dev/sda3
\n
\nand if you want to have swap on sda5 use:
\n
\n\tsudo sh $0 /dev/sda3 /dev/sda5
\n
"

usage(){
    echo $usage
    exit 1
}

sanity_checks(){
    echo "Sanity checks..."
    if [ -z "$dev" ] || [ ! -b "$dev" ]; then
        echo "First argument (target_partition=$dev) must be a valid partition."
        usage    
    fi
    if [ -n "$swapdev" ] && [ ! -b "$swapdev" ]; then
        echo "Swapdevice=$swapdev is not a block device."            
        usage
    fi
    if [ "$(whoami)" != root ]; then
        echo "Admin rights are required to run this program."
        exit 1
    fi
    mkdir -p $target    
    umount $target 2> /dev/null || true
    if mount -t auto "$dev" $target 2> /dev/null; then
        if [ $(ls -1 $target | wc -l) -gt 1 ] || \
        [ "$(ls -1 $target)" != "lost+found" ]; then    
            echo "Volume $dev is in use. Aborting"
            umount $target || true        
            exit 1
        fi
        umount $target
    fi
}

create_root(){
    mkfs.ext3 $dev
    mount $dev $target
    size=$(df | awk '$5=="/" || $5=="/home" || $5=="/usr" {sum += $3} END {print sum}')
    free_space=$(df $target|tail -n 1|awk '{print $4}')
    if [ $free_space -lt $size ]; then
        echo "Not enough free space ($free_space MB < $size MB), aborting."
        exit 1
    fi
}

migrate_files(){
    echo "Migrating files..."
    rsync -av --exclude=/host --exclude=/dev/* --exclude=/mnt/* --exclude=/home/*/.gvfs --exclude=/media/*/* --exclude=/tmp/* --exclude=/proc/* --exclude=/sys/* / $target
}

edit_fstab(){
    echo "Editing fstab..."
    sed -i 's:/.*[\.]disk .*::' $target/etc/fstab
    sed -i 's:/.*/disks/boot .*::' $target/etc/fstab
    echo "UUID=$(vol_id --uuid $dev)    /    ext3    errors=remount-ro    0    1" >> $target/etc/fstab
    if [ -b "$swapdev" ]; then
        echo "UUID=$(vol_id --uuid $swapdev)    none    swap    sw    0    0" >> $target/etc/fstab
    fi
}

target_cmd(){
    mount -o bind /proc $target/proc
    mount -o bind /dev $target/dev
    mount -o bind /sys $target/sys
    chroot $target $*
    umount $target/proc
    umount $target/dev
    umount $target/sys     
}

edit_grub(){
    echo "Editing grub..."    
    sed -i "s:# groot=.*::" $target/boot/grub/grub.cfg
    sed -i "s:kopt=.* ro:kopt=root=UUID=$(vol_id --uuid $dev) ro:" $target/boot/grub/grub.cfg
    cp /usr/lib/grub/*/*stage* $target/boot/grub/    
    target_cmd update-grub
    disk=${dev%%[0-9]*}
    partn=${dev#$disk}
    disk=${disk##*/}
    gdisk=$(grep -w $disk /boot/grub/device.map|cut -d ')' -f 1)
    gdisk=${gdisk#\(}
    gpartn=$(expr $partn - 1)
    [ -z "$gdisk" ] && gdisk=hd0
    [ -z "$gpartn" ] && gpartn=0    
    echo "
#    root ($gdisk,$gpartn)
#    setup ($gdisk)
#    setup (hd0)
    quit" | grub --batch --device-map=/boot/grub/device.map
}

remove_lupin_support(){
    echo "Removing lupin_support..."    
    target_cmd apt-get -y remove lupin-support
}

create_swap(){
    echo "Creating swap..."
    if [ -b "$swapdev" ]; then
        mkdir -p $swap        
        if mount -t auto "$swapdev" $swap 2> /dev/null; then
            echo "Volume $swapdev is in use. Skipping swap"
            umount $swap || true
        else
            mkswap $swapdev         
        fi
    fi
}

sanity_checks
create_root
create_swap
migrate_files
edit_fstab
remove_lupin_support
#edit_grub
umount $dev
echo "\nOperation completed successfully, if all is good feel free to remove the installation from windows."


```

Note the difference in the excluded files list (/dev/ is not excluded in the files to be copied since there is no need for it to be copied in recent versions of ubuntu), and the grub installation. The installer uses an outdated version of grub so I stopped grub from running. I have Debian 5.04 'Lenny' running so I don't need it anyway.

---

