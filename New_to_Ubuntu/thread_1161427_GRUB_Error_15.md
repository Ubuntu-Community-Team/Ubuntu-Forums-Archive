---
title: "GRUB Error 15"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by RIT_girl on 2009-05-16
I got the infamous grub error. 

After trying 
grub
find /boot/grub/stage1
I get Error 15- File not found

Trying to troubleshoot that with mounting my root partition using 
sudo mkdir /mnt/root
I get cannot creat directory '/mnt/root': File exists. So I moved on to 
sudo mount -t ext3 /dev/sda6 /mnt/root
I got special device /dev/sda6 does not exist. I'm a newbie, and I'm trying to figure out the difference between/what sda6 is...I'm thinking I'm just not pointing it in the right place, so any help would be greatly appreciated. 

On a side note, I really need help just getting information files off my desktop, I'm a TA and all my students grades are on there :( If get GRUB fixed, awesome, if not, I can reload.

---

### Post by goldblattster on 2009-05-16
I found this in another post, this might be the solution for you.

Fixed this by doing a text-based grub install off a live cd. After going through the language settings, hit escape to get to the main menu. Select "install grub" and it will bring up the partitioner. Set the correct mount points in the partitioner, and make sure that the partitions will NOT be formatted. It will then say something about installing a base system, hit escape or no. It should then go to the grub install prompt. Do that, reboot, done.

---

### Post by RIT_girl on 2009-05-16
Is there a walk-through how to do this? I'm not technology-friendly, despite my many attempts :)

I assume 'text-based' means through the terminal, which I have been using off a live CD. :( I can't seem to get it to find the existing GRUB to fix.

---

### Post by Didius Falco on 2009-05-16
> **RIT_girl said:**
> I got the infamous grub error. 

After trying 
grub
find /boot/grub/stage1
I get Error 15- File not found

Trying to troubleshoot that with mounting my root partition using 
sudo mkdir /mnt/root
I get cannot creat directory '/mnt/root': File exists. So I moved on to 
sudo mount -t ext3 /dev/sda6 /mnt/root
I got special device /dev/sda6 does not exist. I'm a newbie, and I'm trying to figure out the difference between/what sda6 is...I'm thinking I'm just not pointing it in the right place, so any help would be greatly appreciated. 

On a side note, I really need help just getting information files off my desktop, I'm a TA and all my students grades are on there :( If get GRUB fixed, awesome, if not, I can reload.

Hi,

You can grab the grades files from the hard drive using the Live CD.

Error 15 is one of the better ones to get. FRom the Grub Manual:

> 15 : File not found. This error is returned if the specified file name cannot be found, but everything else (like the disk/partition info) is OK.

Boot the Live Cd, if you aren't already in it, and download this script to your Desktop:

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

Once you have it on your desktop, open a Terminal from **Application/Accessories/Terminal** and type  this command:

```
sudo bash ~/Desktop/boot_info_script*.sh
```The script will gather the relevant information about your drive(s) to help solve this error to a file named RESULTS.txt. Once you have RESULTS.txt, open it up and select it all, then paste it in this thread. Highlight what you just pasted and put code tags around it by clicking the hash (#) on the tool bar.

Then we can get started solving this.

Regards,

Didius

---

### Post by RIT_girl on 2009-05-16
Sorry for the delay...

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 8069 MB, 8069677056 bytes
255 heads, 63 sectors/track, 981 cylinders, total 15761088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x294a294a

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    15,759,764    15,759,702  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 32.2 GB, 32279224320 bytes
255 heads, 63 sectors/track, 3924 cylinders, total 63045360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00040fd0

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    63,039,059    63,038,997  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1006 MB, 1006632960 bytes
65 heads, 32 sectors/track, 945 cylinders, total 1966080 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc3072e18

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             32     1,957,887     1,957,856   6 FAT16


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="fee77d56-01e6-47a4-a45e-2512abd04771" TYPE="swap" 
/dev/sdb1: UUID="d5ff8419-a66c-46dc-971d-fa0a4c17a0c5" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: SEC_TYPE="msdos" LABEL="USB Disk" UUID="C2F8-E4F2" TYPE="vfat" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/sdc1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


I think the attachment makes a lot more sense...and thank you so much for your help!

---

### Post by Didius Falco on 2009-05-16
Can you recheck the RESULTS.txt file and make sure that is all of the output? It should have had copies of your fstab and menu.lst files in it but it doesn't.

If you didn't get all the output, please repost it, otherwise type ```
gksudo gedit 
``` in the Terminal. that will open a text editor that you can use to navigate to **/boot/grub/menu.lst** on your second drive and open the **menu.lst file**. Copy and post the contents here and put code tags around it with the hash (#) button.

Do the same thing with the fstab file, which is located at **/etc/fstab**.

Often that error just means there is a mistake in the configuration of those files, particularly the menu.lst one.

There is also a chance you'll need to repair the possible Bad Superblock, but we'll wait and see if there is a prblem in those two files before we worry about that.

I see you have a USB stick in, so I'm guessing you either already have or are in the process of saving those grade files. <G>

Regards,

Didius

---

### Post by RIT_girl on 2009-05-16
Hi, 

I re-ran the script, but it came out the same. I checked them and didn't see anything about my fstab and menu.lst files. 

When I opened the text and went to my boot menu, there was nothing there for GRUB. I'm actually running eeebuntu, I don't know if that makes a big difference seeing we're dealing with GRUB. My options under the boot menu are
abi-2.6.27-8eeepc
config-2.6.27-8-eeepc
initrd.img-2.6.27-8-eeepc
memtest86+.bin
System.map-2.6.27-8-eeepc
vmlinuz-2.6.27-8-eeepc

I'm running my live disk as a USB :) Silly netbooks don't have a CD drive. I noticed that, and my GRUB was stage2. When I went to the GRUB terminal and tried that find and replacing it with stage2, same error occurred.

---

### Post by Didius Falco on 2009-05-16
You made it to the **boot** directory, but there should a sub-directory of that called **grub**, which contains a file named **menu.lst**. This is all on the second hard drive...

Are you saying you don't have a grub directory or a menu.lst file? How about the fstab file under /etc/fstab? That should be on the second hard drive as well...

I'll keep working on it with you as long as I think I can help, but I'm really hoping someone with more experience with eeebuntu jumps in.

---

### Post by RIT_girl on 2009-05-16
Yea, I found grub.d under the etc  folder under my file system. It contains 20_memtest86+...this is what it says


 #!/bin/bash
set -e

if test -e /boot/memtest86+.bin ; then
  echo "Found memtest86+ image: /boot/memtest86+.bin" >&2
  cat << EOF
menuentry "Memory test (memtest86+)" {
	linux	${GRUB_DRIVE_BOOT}/memtest86+.bin
}
EOF
fi

---

### Post by Didius Falco on 2009-05-16
Okay, lets start from scratch, I think I haven't given you good instructions.

Open the text editor of your choice - then navigate using the "open file" menu to the second hard drive. You are looking for a file named **menu.lst**, which should be two directories down in the file system. The first one you want to find is called **boot**. There should be another directory (or folder, if you prefer) in that one named **grub**. When you open the grub directory, there should be a file named **menu.lst**.

Open that up, copy the entire contents of it and paste it in the thread.

Next, you want to go back up two levels and look for a directory named **etc**. Open that up and scroll down past all the directories until you see a file named **fstab** . Open that one up, copy all the contents and paste them in the thread.

Then I can take a look and see if there is a problem with either of those two files.

Regards,

Didius

---

### Post by RIT_girl on 2009-05-16
Thank goodness for search. I attached what I found...please let me know if I'm getting warmer :) And thank you very much for your help, its beyond appreciated!

---

### Post by RIT_girl on 2009-05-16
Wasn't sure if the files uploaded...

the menu.lst

#
# Sample boot menu configuration file
#

# Boot automatically after 30 secs.
timeout 30

# By default, boot the first entry.
default 0

# Fallback to the second entry.
fallback 1

# For booting GNU (also known as GNU/Hurd)
title  GNU (also known as GNU/Hurd)
root   (hd0,0)
kernel /boot/gnumach.gz root=device:hd0s1
module /hurd/ext2fs.static --multiboot-command-line=${kernel-command-line} --host-priv-port=${host-port} --device-master-port=${device-port} --exec-server-task=${exec-task} -T typed ${root} $(task-create) $(task-resume)
module /lib/ld.so.1 /hurd/exec $(exec-task=task-create)

# For booting GNU/Linux
title  GNU/Linux
root (hd1,0)
kernel /vmlinuz root=/dev/hdb1
#initrd /initrd.img

# For booting GNU/kFreeBSD
title  GNU/kFreeBSD
root   (hd0,2,a)
kernel /boot/loader.gz

# For booting GNU/kNetBSD
title  GNU/kNetBSD
root   (hd0,2,a)
kernel --type=netbsd /boot/knetbsd.gz

# For booting Mach (getting kernel from floppy)
title  Utah Mach4 multiboot
root   (hd0,2)
pause  Insert the diskette now!!
kernel (fd0)/boot/kernel root=hd0s3
module (fd0)/boot/bootstrap

# For booting FreeBSD
title  FreeBSD
root   (hd0,2,a)
kernel /boot/loader

# For booting NetBSD
title  NetBSD
root   (hd0,2,a)
kernel --type=netbsd /netbsd

# For booting OpenBSD
title  OpenBSD
root   (hd0,2,a)
kernel --type=netbsd /bsd

# For booting OS/2
title OS/2
root  (hd0,1)
makeactive
# chainload OS/2 bootloader from the first sector
chainloader +1
# This is similar to "chainload", but loads a specific file
#chainloader /boot/chain.os2

# For booting Windows NT or Windows95
title Windows NT / Windows 95 boot menu
rootnoverify (hd0,0)
makeactive
chainloader  +1
# For loading DOS if Windows NT is installed
# chainload /bootsect.dos

# For installing GRUB into the hard disk
title Install GRUB into the hard disk
root    (hd0,0)
setup   (hd0)

# Change the colors.
title Change the colors
color light-green/brown blink-red/blue



the fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda1 swap swap defaults 0 0

---

### Post by goldblattster on 2009-05-16
The grub folder is in the boot directory. You should have it. Before making the assumption you don't have it, try this...
Type
```
nautilus /boot/grub/
```
into the terminal, and a window will appear. **Do not do anthing in this window except** locate the file *"menu.lst"* and double-click on it. Copy it, close the window, and paste it into the thread.

---

### Post by goldblattster on 2009-05-16
Oh hehe looks like I was a little late. but you got the contents of the file, and that is all that counts!

---

### Post by RIT_girl on 2009-05-16
I went to the GRUB terminal and skipped the find stage 1 step...I assumed based on the menu file it was on hd0,0, and tried 

root(hd0,0)

It gave me Error 27: Unrecognized command. 

I still have my livedisk in, is there anyway to just completely wipe the old GRUB and put a new version on?

---

### Post by goldblattster on 2009-05-16
Well, I do not have a lot of expierence with grub, but I can tell you this. If you are ***_not_*** dual booting windows and ubuntu, you can obtain a gparted live cd, and format the ubuntu partition, then boot from the ubuntu live cd and install ubuntu again. This is dangerous and I am not sure if this will work so you might want someone else's verification before doing this...

---

### Post by RIT_girl on 2009-05-16
I'd be okay with a reboot if I could save my desktop. I'm a TA, and all my students grades are on there...I have a backup, but its a week behind. I don't think they'd like me if I "lost" 2 home work assignments :( 

If someone could walk me through a recovery, I'd be content to let GRUB win this round.

---

### Post by Miljet on 2009-05-16
Your menu.lst file looks nothing like the one should on a regular Ubuntu installation so I am assuming that it is unique to the netbook version of Ubuntu.

It appears that you have two hard drives (sda and sdb). Neither of those drives appear to be partitioned. The entire first hard drive (sda) is used as swap and your Ubuntu operating system appears to be installed on sdb.

The problem is that you have installed GRUB to the Master Boot Record of the first drive, pointing it to files on that disk, which don't exist. The computer is trying to boot from that drive first and cannot find the files it needs to install.

You can try to go into the BIOS setup and change the boot sequence so the computer looks first at the second hard drive. If you need help with that, just ask.

The second possibility is to reinstall GRUB in the MBR of the first drive but have it point to the boot files on the second disk. The commands to do that in the terminal should be:

```
sudo grub
root hd1,1
setup hd0
quit
```

As a final note, you should be able to mount your Ubuntu partition to recover your files by mounting sdb1. You couldn't mount it before because you were attempting to mount sda6 which doesn't exist on your system.

---

### Post by Sir Jasper on 2009-05-17
Hi RIT_girl, Didius and all readers,

I have no idea how to solve your grub problem so I'll confine this to recovering your important student data (and any other vital files).

I think Knoppix may well help because:
* If you, or a friend, can't download it; a CD (or DVD) can be bought cheaply.
* It loads and configures entirely automatically in a few minutes from CD or DVD
* It sees any and all internal and external drives and partitions
* All or any of those drives and partitions can be mounted.
* Vital backup data could be copied to say, a USB stick.

Your time constraints may make this Knoppix solution impracticable but once you have a CD or DVD, and probably just a few words of explanation from us, or elsewhere, to avoid your searching for commands; then, it should be quick.

Alternatively, if you don't have a large external USB drive perhaps you could borrow one from your academy or somewhere and then do a temporary clone.

It might help to say (or restate) the size(s) of your drives and partitions and also to know the type of files you need to backup.

My regards

PS Didius and all friends may shoot down my ideas without mercy since what matters is effective help.

---

### Post by RIT_girl on 2009-05-17
Sorry I took so long to reply, I just had to step away for a bit...I went from Error 15 to Error 17 when I changed my boot order. Does this help/hurt me at all?

PS- I have Grub Stage1.5, or at least that is what its saying is loading.

---

### Post by goldblattster on 2009-05-17
Hello Again, I found this in another post that might solve your problem (Grub error 17):

1. Enter BIOS
2. Make sure all HDD's are detected.

* *Take note of (write down) the current settings just in case you need to set things back later**

3. Search for the HDD that has Ubuntu installed and set its MODE to AUTO (not LBA, large, or normal)
4. Also, if you have this option available, set TYPE to USER, but don't change any of the figures that were automatically detected.
5. And you are done!


Just in case this doesn't work, then:
6. Set all drives to TYPE --> USER and MODE --> AUTO (not LBA, large or normal)

***EDIT:*** Of course, some BIOSes do not offer options to change the hard drive settings.

---

### Post by Miljet on 2009-05-17
GRUB error 17 is usually associated with a corrupt file system. The fix that goldblattster suggested is a good first check for this error.

If that doesn't work, at this point I would concentrate on trying to recover your files. Boot up with a live CD and try mounting partition sdb1. If it mounts you should have access to your files.

Then we can worry about checking your file system for errors.

---

### Post by zeex on 2009-05-17
Hi, 

Use live CD and run fsck on /dev/sdb1

```
$ sudo fsck /dev/sdb1
```

Then reinstall the GRUB. In the terminal

```
$ sudo grub      

grub > find /boot/grub/stage1

```
it'll give you something like hd(X,Y). on your case i think you'll more than one. It could be (hd1,0) that's /dev/sdb1 so .

```
grub > root (hd1,0)
grub > setup (hd1)
grub > quit

```

Although you have installed new grub sometimes menu.lst you 've to manually edit. so you will be able to see OS listing in grub but you 'll again get error 15. From your earlier post you 've very unusual menu.lst file but anyway we need to edit your menu.lst file. 

So please post the output of 
```

$ sudo fdisk -l

$ ls -l /boot

$ cat /boot/grub/device.map

```
and content your /boot/grub/menu.lst file

After this i can tell what to add to your menu.lst file. A wrong entry is mainly the reason for Grub error 15. Also can you describe your system. Is it desktop/laptop/netbook , 32/64 bit etc

---

### Post by egalvan on 2009-05-17
> **RIT_girl said:**
> I went to the GRUB terminal and **skipped the find stage 1 step...**
I assumed based on the menu file it was on hd0,0, and tried 

**[COLOR="Red"]root(hd0,0)[/COLOR]**

It gave me Error 27: [COLOR="Red"]Unrecognized command[/COLOR]. 

I still have my livedisk in, is there anyway to just completely wipe the old GRUB and put a new version on?

the command needs a space after it....
to separate the command from the options...


root (hd0,0)


further, the file "stage1" is not necessarily on the same partition or drive as the file "menu.lst".

further, if you have /boot on a separate partition, the command is

find /grub/stage1

---

### Post by RIT_girl on 2009-05-17
Hi zeex, 

I tried running fsck, and I got some boomerang...any suggestions? 

```


To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fsck /dev/sdb1
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
Superblock has an invalid ext3 journal (inode 8).
Clear<y>? yes

*** ext3 journal has been deleted - filesystem is now ext2 only ***

Superblock doesn't have has_journal flag, but has ext3 journal inode.
Clear<y>? yes

Resize inode not valid.  Recreate<y>? yes

/dev/sdb1 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Inode 1 has EXTENTS_FL flag set on filesystem without extents support.
Clear<y>? yes

Root inode is not a directory.  Clear<y>? yes

Journal inode is not in use, but contains data.  Clear<y>? yes

Inode 17 has EXTENTS_FL flag set on filesystem without extents support.
Clear<y>? yes


Error reading block 3899898 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error<y>? yes

Force rewrite<y>? yes

Error reading block 3899899 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error<y>? yes

Force rewrite<y>? yes

Error reading block 3899900 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error<y>? yes

Force rewrite<y>? yes

Error reading block 3899901 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error<y>? yes

Force rewrite<y>? yes

Error reading block 3899902 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error<y>? yes

Force rewrite<y>? yes

Error reading block 3899903 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error<y>? 


```

I also did the find without looking in boot...and it still says File not found. Interesting it allows me to go to the root, but when I do the setup it gives file not found again :( 

I went through my BIOS and changed their order, but I didn't know how to change their settings...I'm in eeebuntu standards, so I don't know how different things are. 

I have been looking at  something called Super Grub...but of course I'm having trouble implementing that too :(

---

### Post by RIT_girl on 2009-05-17
If someone can help me recover stuff, I tried 

```

mount sdb1

```

and it returned can't find sdb1 in /ect/fstab or /ect/mtab

---

### Post by zeex on 2009-05-17
> **RIT_girl said:**
> Hi zeex, 

I tried running fsck, and I got some boomerang...any suggestions? 


Hi, 

could you post the output i asked for.
```

$ sudo fdisk -l

$ ls -l /boot

$ cat /boot/grub/device.map
```

I'm looking into why you ran into boomrang. Could you also describe your system setup. 

And try 
```

$ sudo fsck -y /dev/sdb1

$ sudo fsck -c -c /dev/sdb1  *<this will take very long time>*


```

---

### Post by zeex on 2009-05-17
> **RIT_girl said:**
> If someone can help me recover stuff, I tried 

```

mount sdb1

```

and it returned can't find sdb1 in /ect/fstab or /ect/mtab

Hi, 

you should 've backed up data earlier. Boot with live CD and try this 

```
$ sudo mkdir /media/disk

$ sudo mount /dev/sdb1 /media/disk
```

then you go to /media/disk and back up data.

---

### Post by RIT_girl on 2009-05-17
Hi, 

It's taking a while to run $ sudo fsck -y /dev/sdb1, but I'm running eeebuntu standard on an ASUS 1000...I don't know much about it, but its single boot.

---

### Post by RIT_girl on 2009-05-17
from fdisk -l

```
Disk /dev/sda: 8069 MB, 8069677056 bytes
255 heads, 63 sectors/track, 981 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x294a294a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         981     7879851   82  Linux swap / Solaris

Disk /dev/sdb: 32.2 GB, 32279224320 bytes
255 heads, 63 sectors/track, 3924 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00040fd0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3924    31519498+  83  Linux

Disk /dev/sdc: 1006 MB, 1006632960 bytes
65 heads, 32 sectors/track, 945 cylinders
Units = cylinders of 2080 * 512 = 1064960 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         942      978928    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(956, 64, 32) logical=(941, 18, 32)

```

from ls -l/boot

```
total 11770
-rw-r--r-- 1 root root  497951 2008-11-16 19:36 abi-2.6.27-8-eeepc
-rw-r--r-- 1 root root   85596 2008-11-16 19:36 config-2.6.27-8-eeepc
-rw-r--r-- 1 root root 8123767 2008-12-11 23:35 initrd.img-2.6.27-8-eeepc
-rw-r--r-- 1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r-- 1 root root 1017725 2008-11-16 19:36 System.map-2.6.27-8-eeepc
-rw-r--r-- 1 root root 2202032 2008-11-16 19:36 vmlinuz-2.6.27-8-eeepc

```

from cat /boot/grub/device.map 

```
ubuntu@ubuntu:~$  cat /boot/grub/device.map
cat: /boot/grub/device.map: No such file or directory
ubuntu@ubuntu:~$ sudo  cat /boot/grub/device.map
cat: /boot/grub/device.map: No such file or directory

```

from sudo fsck -y /dev/sdb1

```

Deleted inode 8237 has zero dtime.  Fix? yes

Deleted inode 8238 has zero dtime.  Fix? yes

Deleted inode 8240 has zero dtime.  Fix? yes

Deleted inode 8241 has zero dtime.  Fix? yes

Deleted inode 8242 has zero dtime.  Fix? yes

Deleted inode 8243 has zero dtime.  Fix? yes

Deleted inode 8244 has zero dtime.  Fix? yes

Deleted inode 8245 has zero dtime.  Fix? yes

Deleted inode 8246 has zero dtime.  Fix? yes

Deleted inode 8248 has zero dtime.  Fix? yes

Deleted inode 8249 has zero dtime.  Fix? yes

Deleted inode 8250 has zero dtime.  Fix? yes

Deleted inode 8251 has zero dtime.  Fix? yes

Deleted inode 8252 has zero dtime.  Fix? yes

Deleted inode 8253 has zero dtime.  Fix? yes

Deleted inode 8254 has zero dtime.  Fix? yes

Deleted inode 8255 has zero dtime.  Fix? yes

Deleted inode 8256 has zero dtime.  Fix? yes

Deleted inode 8257 has zero dtime.  Fix? yes

Deleted inode 8258 has zero dtime.  Fix? yes

Deleted inode 8259 has zero dtime.  Fix? yes

Deleted inode 8260 has zero dtime.  Fix? yes

Deleted inode 8261 has zero dtime.  Fix? yes

Deleted inode 8262 has zero dtime.  Fix? yes

Deleted inode 8263 has zero dtime.  Fix? yes

Deleted inode 8264 has zero dtime.  Fix? yes

Deleted inode 8265 has zero dtime.  Fix? yes

Deleted inode 8266 has zero dtime.  Fix? yes

Deleted inode 8267 has zero dtime.  Fix? yes

Deleted inode 8268 has zero dtime.  Fix? yes

Deleted inode 8269 has zero dtime.  Fix? yes

Deleted inode 8270 has zero dtime.  Fix? yes

Deleted inode 8271 has zero dtime.  Fix? yes

Deleted inode 8272 has zero dtime.  Fix? yes

Deleted inode 8274 has zero dtime.  Fix? yes

Deleted inode 8275 has zero dtime.  Fix? yes

Deleted inode 8276 has zero dtime.  Fix? yes

Deleted inode 8277 has zero dtime.  Fix? yes

Deleted inode 8278 has zero dtime.  Fix? yes

Deleted inode 8279 has zero dtime.  Fix? yes

Deleted inode 8280 has zero dtime.  Fix? yes

Deleted inode 8281 has zero dtime.  Fix? yes

Deleted inode 8282 has zero dtime.  Fix? yes

Deleted inode 8283 has zero dtime.  Fix? yes

Deleted inode 8284 has zero dtime.  Fix? yes

Deleted inode 8285 has zero dtime.  Fix? yes

Deleted inode 8286 has zero dtime.  Fix? yes

Deleted inode 8287 has zero dtime.  Fix? yes

Deleted inode 8288 has zero dtime.  Fix? yes

      
y
Error reading block 3899898 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error? yes

Force rewrite? yes

Error reading block 3899899 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error? yes

Force rewrite? yes

Error reading block 3899900 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error? yes

Force rewrite? yes

Error reading block 3899901 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error? yes

Force rewrite? yes

Error reading block 3899902 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error? yes

Force rewrite? yes

Error reading block 3899903 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error? yes

Force rewrite? yes

Error reading block 3899904 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error? yes

Force rewrite? yes

Recreate journal to make the filesystem ext3 again?
Fix? yes

Creating journal (32768 blocks):  Done.

*** journal has been re-created - filesystem is now ext3 again ***
Restarting e2fsck from the beginning...
Resize inode not valid.  Recreate? yes

/dev/sdb1 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Root inode is not a directory.  Clear? yes

Inode 8, i_blocks is 0, should be 262408.  Fix? yes

Error reading block 3899898 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error? yes

Force rewrite? yes

Error reading block 3899899 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error? yes

Force rewrite? yes

Error reading block 3899900 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error? yes

Force rewrite? yes

Error reading block 3899901 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error? yes

Force rewrite? yes

Error reading block 3899902 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error? yes

Force rewrite? yes

Error reading block 3899903 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error? yes

Force rewrite? yes

Error reading block 3899904 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error? yes

Force rewrite? yes

Error reading block 4456960 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error? yes

Force rewrite? yes

Pass 2: Checking directory structure
Entry '..' in ??? (130817) has deleted/unused inode 2.  Clear? yes

Entry '..' in ??? (196225) has deleted/unused inode 2.  Clear? yes

Entry '..' in ??? (245281) has deleted/unused inode 2.  Clear? yes

Inode 20 (???) has invalid mode (0740).
Clear? yes

Error reading block 1025 (Attempt to read block from filesystem resulted in short read) while reading inode and block bitmaps.  Ignore error? yes

Force rewrite? yes

Error reading block 1026 (Attempt to read block from filesystem resulted in short read) while reading inode and block bitmaps.  Ignore error? yes

Force rewrite? yes

Error reading block 33793 (Attempt to read block from filesystem resulted in short read) while reading inode and block bitmaps.  Ignore error? yes

Force rewrite? yes

Error reading block 33794 (Attempt to read block from filesystem resulted in short read) while reading inode and block bitmaps.  Ignore error? yes

Force rewrite? yes

Entry 'Sink4_15.emf' in ??? (343618) has deleted/unused inode 15.  Clear? yes

Entry '..' in ??? (343393) has deleted/unused inode 2.  Clear? yes

Entry 'Sink.pcb' in .../becky/MSD (384347) has deleted/unused inode 16.  Clear? yes

Entry 'Source.pcb' in .../becky/MSD (384347) has deleted/unused inode 17.  Clear? yes

Entry 'Sink4_15.pcb' in .../becky/MSD (384347) has deleted/unused inode 19.  Clear? yes

Inode 21 (.../becky/MSD/Sink1.sch) has invalid mode (00).
Clear? yes

Entry 'Source4_15.pcb' in .../becky/MSD (384347) has deleted/unused inode 18.  Clear? yes

Entry 'Source4_21.pcb' in .../becky/MSD (384347) has deleted/unused inode 26.  Clear? yes

Entry 'Sink4_23.pcb' in .../becky/MSD (384347) has deleted/unused inode 22.  Clear? yes

Inode 28 (.../becky/MSD/Source_Component.pcb) has invalid mode (0162400).
Clear? yes

Entry 'Source4_28.pcb' in .../becky/MSD (384347) has deleted/unused inode 25.  Clear? yes

Inode 33 (.../becky/MSD/Sink_Component427.pcb) is an illegal block device.
Clear? yes

Inode 32 (.../becky/MSD/Sink4_28.pcb) has invalid mode (0170000).
Clear? yes

Inode 31 (.../becky/MSD/Sink4_28edge.pcb) has invalid mode (0130000).
Clear? yes

Entry 'Sink_Component51.pcb' in .../becky/MSD (384347) has deleted/unused inode 23.  Clear? yes

Entry 'componentboards.ppt' in .../becky/MSD (384347) has deleted/unused inode 30.  Clear? yes

Entry 'Source5_1.pcb' in .../becky/MSD (384347) has deleted/unused inode 27.  Clear? yes

Entry 'Sink4_28jz.pcb' in .../becky/MSD (384347) has deleted/unused inode 34.  Clear? yes

Entry 'Sink5_4.pcb' in .../becky/MSD (384347) has deleted/unused inode 36.  Clear? yes

Inode 29 (.../becky/MSD/Sink_Component51a.pcb) has invalid mode (0170000).
Clear? yes

Entry 'Sink5_10.sch' in .../becky/MSD (384347) has deleted/unused inode 24.  Clear? yes

Entry '..' in ??? (392449) has deleted/unused inode 2.  Clear? yes

Entry '..' in ??? (678609) has deleted/unused inode 2.  Clear? yes

Entry '..' in ??? (833953) has deleted/unused inode 2.  Clear? yes

Entry '..' in ??? (1005649) has deleted/unused inode 2.  Clear? yes

Entry '..' in ??? (1087409) has deleted/unused inode 2.  Clear? yes

Entry '..' in ??? (1120113) has deleted/unused inode 2.  Clear? yes

Entry '..' in ??? (1128289) has deleted/unused inode 2.  Clear? yes

Entry '..' in ??? (1177345) has deleted/unused inode 2.  Clear? yes

Entry '..' in ??? (1250929) has deleted/unused inode 2.  Clear? yes

Entry '..' in ??? (1259105) has deleted/unused inode 2.  Clear? yes

Entry '..' in ??? (1324513) has deleted/unused inode 2.  Clear? yes

Entry '..' in ??? (1627025) has deleted/unused inode 2.  Clear? yes

Entry '..' in ??? (1888657) has deleted/unused inode 2.  Clear? yes

Pass 3: Checking directory connectivity
Root inode not allocated.  Allocate? yes

Unconnected directory inode 130817 (...)
Connect to /lost+found? yes

/lost+found not found.  Create? yes

Unconnected directory inode 196225 (...)
Connect to /lost+found? yes

Unconnected directory inode 245281 (...)
Connect to /lost+found? yes

Unconnected directory inode 343393 (...)
Connect to /lost+found? yes

Unconnected directory inode 392449 (...)
Connect to /lost+found? yes

Unconnected directory inode 678609 (...)
Connect to /lost+found? yes

Unconnected directory inode 833953 (...)
Connect to /lost+found? yes

Unconnected directory inode 1005649 (...)
Connect to /lost+found? yes

Unconnected directory inode 1087409 (...)
Connect to /lost+found? yes

Unconnected directory inode 1120113 (...)
Connect to /lost+found? yes

Unconnected directory inode 1128289 (...)
Connect to /lost+found? yes

Unconnected directory inode 1177345 (...)
Connect to /lost+found? yes

Unconnected directory inode 1250929 (...)
Connect to /lost+found? yes

Unconnected directory inode 1259105 (...)
Connect to /lost+found? yes

Unconnected directory inode 1324513 (...)
Connect to /lost+found? yes

Unconnected directory inode 1627025 (...)
Connect to /lost+found? yes

Unconnected directory inode 1888657 (...)
Connect to /lost+found? yes

Pass 4: Checking reference counts
Inode 35 (...) has invalid mode (0403).
Clear? yes

Inode 49 (...) has invalid mode (02230).
Clear? yes

Inode 52 (...) has invalid mode (00).
Clear? yes

Inode 55 (...) has invalid mode (037166).
Clear? yes

Inode 56 (...) has invalid mode (074656).
Clear? yes

Inode 58 (...) is an illegal block device.
Clear? yes

Inode 59 (...) has invalid mode (0173371).
Clear? yes

Inode 60 (...) has invalid mode (0114310).
Clear? yes

i_faddr for inode 62 (...) is 4288112546, should be zero.
Clear? yes

Extended attribute block for inode 62 (...) is invalid (4220875932).
Clear? yes

Unattached inode 62
Connect to /lost+found? yes

Inode 62 ref count is 65479, should be 1.  Fix? yes

Inode 63 (...) has invalid mode (074255).
Clear? yes

Inode 97 (...) has invalid mode (00).
Clear? yes

Inode 98 (...) has invalid mode (01).
Clear? yes

i_faddr for inode 99 (...) is 201326592, should be zero.
Clear? yes

Extended attribute block for inode 99 (...) is invalid (100663296).
Clear? yes

Unattached inode 99
Connect to /lost+found? yes

Inode 99 ref count is 1537, should be 1.  Fix? yes

Inode 102 (...) has invalid mode (01).
Clear? yes

i_faddr for inode 106 (...) is 393216, should be zero.
Clear? yes

Unattached inode 106
Connect to /lost+found? yes

Inode 106 ref count is 7, should be 1.  Fix? yes

Inode 108 (...) has invalid mode (01).
Clear? yes

Inode 117 (...) has invalid mode (0211).
Clear? yes

Inode 130817 ref count is 3, should be 2.  Fix? yes

Inode 196225 ref count is 10, should be 9.  Fix? yes

Inode 245281 ref count is 4, should be 3.  Fix? yes

Inode 343393 ref count is 7, should be 6.  Fix? yes

Inode 392449 ref count is 12, should be 11.  Fix? yes

Inode 678609 ref count is 15, should be 14.  Fix? yes

Inode 833953 ref count is 3, should be 2.  Fix? yes

Inode 1005649 ref count is 3, should be 2.  Fix? yes

Inode 1087409 ref count is 3, should be 2.  Fix? yes

Inode 1120113 ref count is 3, should be 2.  Fix? yes

Inode 1128289 ref count is 3, should be 2.  Fix? yes

Inode 1177345 ref count is 138, should be 137.  Fix? yes

Inode 1250929 ref count is 4, should be 3.  Fix? yes

Inode 1259105 ref count is 5, should be 4.  Fix? yes

Inode 1324513 ref count is 11, should be 10.  Fix? yes

Inode 1627025 ref count is 3, should be 2.  Fix? yes

Inode 1888657 ref count is 15, should be 14.  Fix? yes

Pass 5: Checking group summary information
Block bitmap differences:  +(0--1538) +(32768--34305) +(491520--491871) -(3899905--3932159) -(3932673--3933218)
Fix? yes

Free blocks count wrong for group #0 (30973, counted=31227).
Fix? yes

Free blocks count wrong for group #119 (0, counted=32255).
Fix? yes

Free blocks count wrong for group #120 (0, counted=546).
Fix? yes

Free blocks count wrong (4767038, counted=4800093).
Fix? yes

Inode bitmap differences:  +1 +(3--10) +62 +99 +106
Fix? yes

Free inodes count wrong for group #0 (8161, counted=8162).
Fix? yes

Directories count wrong for group #0 (3, counted=2).
Fix? yes

Free inodes count wrong (1852383, counted=1852384).
Fix? yes


/dev/sdb1: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sdb1: 118032/1970416 files (1.2% non-contiguous), 3079781/7879874 blocks
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ y
bash: y: command not found
ubuntu@ubuntu:~$ sudo fsck -c -c /dev/sdb1
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
fsck.ext3: Attempt to read block from filesystem resulted in short read while checking ext3 journal for /dev/sdb1


```

---

### Post by RIT_girl on 2009-05-17
Okay, trying to back up..

```
ubuntu@ubuntu:~$ sudo mkdir /media/disk
ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /media/disk
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

I tried this with a USB in, and taken out. 

And thanks for your help! I really do appreciate it!

---

### Post by zeex on 2009-05-18
> **RIT_girl said:**
> Okay, trying to back up..

```
ubuntu@ubuntu:~$ sudo mkdir /media/disk
ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /media/disk
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

I tried this with a USB in, and taken out. 

And thanks for your help! I really do appreciate it!

Hi, 

A lot of people here trying to help you out with your problem assumes you have a standard desktop or laptop. It's always helpful if you mention up front that you 've special system like ASUS 1000. I'm telling you this because debugging differs system to system.

Anyway, back to your problem. I'm describing your system as i understand it. You 've 2 drives

/dev/sda1 = Linux swap (8 GB)
/dev/sdb1 = Linux root (32 GB)

You 've a 1 GB live USB drive which show up as /dev/sdc1. This probably the live usb drive.

You 'll need a blank USB drive for backing up your data. After booting up with live usb drive plug in the blank usb and run 

```
$ sudo fdisk -l
```

The new drive should show up as /dev/sdd1 . Check in menu Places -> Removable media if it's already mounted then you only need to mount /dev/sdb1. I'm assuming it's not mounted so you do this 
```

$ sudo mkdir /media/backup
$ sudo mount /dev/sdd1 /media/backup


$ sudo mkdir /media/disk 
$ sudo mount -t ext3 /dev/sdb1 /media/disk
```

I hope this helps. Make a copy of all the data you need. If your backup is more in size than your backup usb drive then unmount USB drive copy data somewhere else and mount again.

***_There are files missing in your system like you don't 've the directory /boot/grub and your /etc/fstab seems incomplete_***

**Do this step by step **

1) boot from live USB drive you have.
2) make a directory grub in /boot
```
$ sudo mkdir /boot/grub
```
3) make a file device.map in /boot/grub
```
$ sudo gedit /boot/grub/device.map
```
Add these lines in /boot/grub/device.map
```
(hd0) /dev/sda
(hd1) /dev/sdb
```
4) make a backup of fstab
```
$ sudo cp /etc/fstab /etc/fstab.backup
```
5) open /etc/fstab
```
$ sudo gedit /etc/fstab
```
Add these to /etc/fstab (delete it's content and just copy and paste this )
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sdb1	/               ext3    errors=remount-ro 0       1
/dev/sda1	none            swap    sw              0       0

```
6) now you 'll be installing grub 
```
$ sudo grub
grub > root (hd1,0)
grub > setup (hd1)
grub > quit
```
7) Now you need to edit your menu.lst file
```
$ sudo gedit /boot/grub/menu.lst
```
Add these lines to /boot/grub/menu.lst

```
title		EEEbuntu, kernel 2.6.27-8-eeepc
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-8-eeepc root=/dev/sdb1 ro 
initrd		/boot/initrd.img-2.6.27-8-eeepc

title		EEEbuntu, kernel 2.6.27-8-eeepc (single-user mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-8-eeepc root=/dev/sdb1 ro single
initrd		/boot/initrd.img-2.6.27-8-eeepc
```


8:: Reboot the system remove the live USB drive.
9:: Go to BIOS and make your 32 GB drive the primary boot device. (I hope you know how to do this)
10:: save setting and boot.

Let me know if this works. 

Good luck :)

---

### Post by Sir Jasper on 2009-05-18
Hi zeex,

I'm not in the least critical as I'm impressed and in awe of your expertise though I think you meant to type "blank" rather than "black".

Purely out of interest, do you think using a Knoppix CD (or any other bootable Linux CD) together with the USB stick could have backed up the vital files in this case?

My regards

Addendum:

Hi again, and thank you for your explanation immediately below.

---

### Post by zeex on 2009-05-18
> **Sir Jasper said:**
> Hi zeex,

I'm not in the least critical as I'm impressed and in awe of your expertise though I think you meant to type "blank" rather than "black".

Purely out of interest, do you think using a Knoppix CD (or any other bootable Linux CD) together with the USB stick could have backed up the vital files in this case?

My regards

Hello!

Thank you for the correction. I knew i wrote black when i was typing but just forgot to correct it :P

Yes you can use any debian (like knoppix) or ubuntu based live CD and a USB drive to backup important files. It's always the same, we need a bootable OS and a backup drive. If you 've Fedora or Suse or any other flavour of Linux installed you need a live CD of that flavour. The commands are more or less the same.

In this particular case the system is ASUS 1000. It's a Netbook it doesn't have CD/DVD drive. So instead of a live CD a live USB drive is required.

:)

:: *using the same flavour of live cd I personally recommend but i think if you know what you are doin' you can use any linux CD you want*

---

### Post by RIT_girl on 2009-05-22
Hello Everyone, 

Thank you for your help, but it was too little too late, I needed a working computer and just reinstalled. I really do appreciate it!

---

### Post by Sir Jasper on 2009-05-22
Hi RIT_girl,

Pleased to hear of your success but hope you managed to keep all your students' data.

My regards

---

