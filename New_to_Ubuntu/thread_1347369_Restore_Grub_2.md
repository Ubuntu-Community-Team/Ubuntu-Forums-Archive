---
title: "Restore Grub 2"
date: 2009-12-06
forum: New to Ubuntu
---

### Post by donescamillo on 2009-12-06
Hi,
 
I had dual-boot-Ubuntu (KK) and WinXP. Grub 2 let me select whichever one I wanted to boot into. But I had to reinstall WinXP, which promptly overwrote the boot sector so now I have a partition with Ubuntu KK installed but cant use it, but no boot manager anymore. Is it possible to restore Grub 2  somehow from the Live CD so as to avoid reinstalling the whole Ubuntu?
 
regards,
donescamillo

---

### Post by candtalan on 2009-12-06
Hi there
I did this recently by using a 9.10 (kk) live CD to run the system, then install grub2 from the live system onto its correct place.

If you look down the page here
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)
until you find
Recover Grub 2 via LiveCD
then follow the steps. See what you think?

---

### Post by Paul T. on 2009-12-06
I too have lost grub2 on my notebook and have been trying restore it via the link above. However I don't understand the part about seperate boot partition that needs to be mounted, is this referring to the Windows ntfs boot partition?

---

### Post by Paul T. on 2009-12-06
Now just get a partial grub menu "minimal bash...."
and the prompt 'sh:grub>' nothing else, no option for windows either, help.

---

### Post by putu.sundika on 2009-12-06
Couple weeks ago, my Grub was error too.
I don't know if my error exactly same with yours, but i knew that my GRUB was broken. 

Here what i've done :
1.Run LiveCD Ubuntu (cant live without it(yet))
2.Run Terminal
3.Type $>sudo grub
4.Will be grub>
5.Type grub>find /boot/grub/stage1
6.It let me know where Linux is --> (hd0,7)
7.Type grub>root (hd0,7) 
  grub>setup (hd0)
  grub>quit
8.Rebooting computer

My GRUB back to normal.
I'm using WinXP (original) and UBUNTU 9.04

---

### Post by ranch hand on 2009-12-06
> **putu.sundika said:**
> Couple weeks ago, my Grub was error too.
I don't know if my error exactly same with yours, but i knew that my GRUB was broken. 

Here what i've done :
1.Run LiveCD Ubuntu (cant live without it(yet))
2.Run Terminal
3.Type $>sudo grub
4.Will be grub>
5.Type grub>find /boot/grub/stage1
6.It let me know where Linux is --> (hd0,7)
7.Type grub>root (hd0,7) 
  grub>setup (hd0)
  grub>quit
8.Rebooting computer

My GRUB back to normal.

I'm using WinXP (original) and UBUNTU 9.04
You are also using grub-legacy not grub2.  This will not in anyway work with grub2.

---

### Post by ranch hand on 2009-12-06
When using the directions;

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

Ignore the instructions about editing the file, not needed.  What you do need is the "update-grub" and "grub-install /dev/<your drive designation>.

The instructions for a separate boot partition are only there for cases where folks set up there box in that manner.

Grub2 should restore just fine.  Remember to breath and take your time.  Have FUN

---

### Post by Paul T. on 2009-12-06
> **ranch hand said:**
> When using the directions;

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

Ignore the instructions about editing the file, not needed.  What you do need is the "update-grub" and "grub-install /dev/<your drive designation>.

The instructions for a separate boot partition are only there for cases where folks set up there box in that manner.

Grub2 should restore just fine.  Remember to breath and take your time.  Have FUN

Tried your advice above, but same result, just ended up with 'sh:grub>' command prompt :(

Reading down the web link I came across the dual booting workaround using

 'sudo apt-get install --reinstall libdebian-installer4'

followed this, then re-did your above advice and success!! Grub menu back up, dual boot option etc.

Many thanks for your advice, and appreciate your encouragment Ranch Hand \\:D/

---

### Post by ranch hand on 2009-12-06
WOW, I have seen that set of instructions but have never known of anyone, before, that need to use them.

Kind of hard to "grub-install" without the lib.

Good job.

---

### Post by gkh73 on 2009-12-06
Ok... can you guys help me next?  :D
I am dual-booting XP & KK9.10 and I lost grub after having to do some repairs to XP.
I am dual-drive dual-booting though, so I'm a little confused as to where I need to work.

Here's my info:

> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60800   488375968+   7  HPFS/NTFS

Disk /dev/sdb: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfdbbfdbb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       11661    93666951   83  Linux
/dev/sdb2           11662       12161     4016250    5  Extended
/dev/sdb5           11662       12161     4016218+  82  Linux swap / Solaris
BTW - My HDD setup is XP is installed on main drive, 9.10 is installed on slave drive.

Thanks guys!!

---

### Post by ranch hand on 2009-12-06
What is it you did to Win JerryLewis Pro that screwed grub?

Are you sure that you are using grub2?  If you upgraded from9.04 you should still be using grub-legacy.  If you are not sure run and post the results here of;
```

grub-install -v

```
That is  assuming you can get into your 9.10 system.  If not we will worry about it later.

Was this setup working, booting through grub, before what ever it was you did in MS?

What works now?

I think  with the answers to these questions we can get started.

---

### Post by gkh73 on 2009-12-06
Ok... this is what I got:

> [FONT=monospace]grub-install (GNU GRUB 1.97~beta4)[/FONT]

Truth be told... I was previously running 8.04 on the slave drive, then decided to do a clean install of 9.10.  I repartitioned the entire drive since I didn't have any crucial docs on 8.04.

Right after that ... a few days I believe... I started getting the "Error 15 no drive found" or whatever it is precisely... and couldn't boot into any OS.  So I ran my Live CD and tried to reinstall grub... didn't work.  So I resorted to the XP install disc, used the disc check utility and did a "fixmbr" ... which reinstalled MS loader.
XP boots up fine now ... system seems to be stable again... but I  can't get back to Ubuntu.

---

### Post by ranch hand on 2009-12-06
OK, now we know what we are working with.

A couple of interesting things here.  Right now, in the 10.04testing forum, there is a person having trouble booting from the slave drive on a IDE system.  Grub2 has a history of some problems booting to more than one drive.

This is not appearently your problem because it was working for several days.

Just to save time later when this turns out to be more complex than it seems now, how about running this script;

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

and posting the results here.

We will then have all the info on your system we need.  You should hang on to that script, it comes in handy for diagnosing boot problems and you never  know when you may run into one.

---

### Post by gkh73 on 2009-12-06
Ah, very handy indeed!
Here are my results:

> ============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

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

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   976,751,999   976,751,937   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfdbbfdbb

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   187,333,964   187,333,902  83 Linux
/dev/sdb2         187,333,965   195,366,464     8,032,500   5 Extended
/dev/sdb5         187,334,028   195,366,464     8,032,437  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 2029 MB, 2029805568 bytes
64 heads, 63 sectors/track, 983 cylinders, total 3964464 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63     3,963,455     3,963,393   6 FAT16


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="8EB44B8FB44B792B" LABEL="Hasser" TYPE="ntfs" 
/dev/sdb1: UUID="dd27535a-24d9-456f-8048-c93e2006fea0" TYPE="ext4" 
/dev/sdb5: UUID="4c1600e1-93a1-4e04-b2bd-23c8d186f907" TYPE="swap" 
/dev/sdc1: SEC_TYPE="msdos" UUID="4C9E-6634" TYPE="vfat" 

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


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 

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
search --no-floppy --fs-uuid --set dd27535a-24d9-456f-8048-c93e2006fea0
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
menuentry "Ubuntu, Linux 2.6.31-14-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set dd27535a-24d9-456f-8048-c93e2006fea0
    linux    /boot/vmlinuz-2.6.31-14-generic-pae root=UUID=dd27535a-24d9-456f-8048-c93e2006fea0 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-14-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set dd27535a-24d9-456f-8048-c93e2006fea0
    linux    /boot/vmlinuz-2.6.31-14-generic-pae root=UUID=dd27535a-24d9-456f-8048-c93e2006fea0 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic-pae
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
    search --no-floppy --fs-uuid --set 8eb44b8fb44b792b
    drivemap -s (hd0) ${root}
    chainloader +1
}
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
UUID=dd27535a-24d9-456f-8048-c93e2006fea0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=4c1600e1-93a1-4e04-b2bd-23c8d186f907 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic-pae
    .0GB: boot/vmlinuz-2.6.31-14-generic-pae
    .0GB: initrd.img
    .0GB: vmlinuz


I am booting IDE drives as well... not SATA.

---

### Post by ranch hand on 2009-12-07
I knew you were using an IDE system as you have a slave drive.  It came as a shock to me when we bought this new box with SATA, no such thing here.  No big clunky cables to mess with your air flow either.  I really like it.

Now, what in flinderation do you have MS boot on both sda and sdb for?  I will never understand the MS "we must control all" crap.

Other than that, everything looks pretty good.  I think that I would try just running these instructions;

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

ignoring the instructions about file editing as it should not be needed if we can get this installed as your grub.cfg file looks fine.

Install the bugger on the master drive as that should be where grub2 looks for the MBR.  If that doesn't work do it again but install on the slave and then on the master.  That should not be needed as any boot loader should be looking at the master drive MBR, this is why the MS crap on the slave bothers me.

Lets not borrow trouble.  Let's just try this and see if it works.  If not we will go on to something else.

---

### Post by apesa on 2009-12-07
I am following this thread while trying to fix my grub error 22 that just came up. I have booted from LiveCD, but I have the SATA controller set up as RAID1. Therefore my drives show up as 500Gb singles as opposed to a single drive. I know it is because I don't have the RAID support under Ubuntu loaded. With 9.10 I did not have to load RAID driver(s) during install, the RAID1 drives showed up as a single during partitioning.

I have a fresh install of ubuntu 9.10 64bit with Grub 1.97 beta.

Any insight or advice is appreciated.

---

### Post by gkh73 on 2009-12-07
Ok... I admit I'm not too confident in a terminal window.
I tried to install grub on the master and this is what happened... along with my second attempt....

> ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
fuse: mount failed: Device or resource busy
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
fuse: mount failed: Device or resource busy
ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /mnt
ubuntu@ubuntu:~$ update-grub
/usr/sbin/grub-mkconfig: You must run this as root
ubuntu@ubuntu:~$ sudo update-grub
grub-probe: error: cannot find a device for /.

ubuntu@ubuntu:~$ sudo mount /dev/sdb1
mount: /dev/sdb1 already mounted or /mnt busy
mount: according to mtab, /dev/sdb1 is already mounted on /mnt
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic-pae
Found initrd image: /boot/initrd.img-2.6.31-14-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
grep: /proc/mounts: No such file or directory
Cannot find list of partitions!
done


Then I tried this:
> 
root@ubuntu:/# grub-install /dev/sda
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda
(hd1)    /dev/sdb


Should I be good to go?  I'm afraid to exit the LiveCD... hahahahaha!  :)

---

### Post by gkh73 on 2009-12-07
Ok... well I got anxious and decided to give it a whirl...
So I restarted the computer... 
Good news...   Grub2 is back!
Bad news... XP is not in the boot menu... hahahaha.

Any suggestions?

---

### Post by ranch hand on 2009-12-07
I am not sure.  I would not worry about the CD you can always get back into it.

Reboot and see.  If that doesn't work, there is a slightly easier way to chroot into things and we can set you up for that.

I am not going to be on here too much longer tonight.  Hour max.  Lets try it and find out what happens.  That way if it doesn't work we can both loose sleep over it.

---

### Post by gkh73 on 2009-12-07
Yeah, I rebooted a couple times to make sure, grub loads beautifully.
But it only gives me an option of booting up "Ubuntu, Linux 2.6.31-14-generic-pae"

I guess I could fix mbr in XP again, then install grub on the slave drive and see what happens?

---

### Post by ranch hand on 2009-12-07
No, let's not do that.

Lets try one more thing tonight and then my brain is going to shut down (I am a grumpy geezer - I need some sleep).

While booted in to Ubuntu run:
```

sudo update-grub

```
A lot of times os-prober miss' MS when you do your Ubuntu install.  Running that will pick it up abot 90% of the time.  If it doesn't we will get back to this tomorrow and get it working when I have a working head.

---

### Post by gkh73 on 2009-12-07
And viola!   You sir are a genius!

Grub is running wonderfully, and XP is back on the menu list!

Thank you very much for all your help!   I hope you can sleep easy now, as will I!  

:popcorn:

---

### Post by ranch hand on 2009-12-07
You have no idea how happy I am about that.

If you read the link in my sig you will know a lot more about how grub2 works.  The first 3 links at the bottom of my post are, besides the community docs, the best there is as far as in depth info on grub2.

Have FUN.

---

### Post by TironN on 2009-12-07
> **Paul T. said:**
> Now just get a partial grub menu "minimal bash...."
and the prompt 'sh:grub>' nothing else, no option for windows either, help.

Your running legacy not GRUB2

---

### Post by ranch hand on 2009-12-07
> **apesa said:**
> I am following this thread while trying to fix my grub error 22 that just came up. I have booted from LiveCD, but I have the SATA controller set up as RAID1. Therefore my drives show up as 500Gb singles as opposed to a single drive. I know it is because I don't have the RAID support under Ubuntu loaded. With 9.10 I did not have to load RAID driver(s) during install, the RAID1 drives showed up as a single during partitioning.

I have a fresh install of ubuntu 9.10 64bit with Grub 1.97 beta.

Any insight or advice is appreciated.
Are you still having this problem?

What grub are you using?  I am pretty sure that  "error 22" is a grub-legacy error.

Run;
```

grub-install -v

```
Then we will know what your box thinks it is using.

Was this a clean install or an update to 9.10?

---

### Post by apesa on 2009-12-07
> **ranch hand said:**
> Are you still having this problem?

What grub are you using?  I am pretty sure that  "error 22" is a grub-legacy error.

Run;
```

grub-install -v

```Then we will know what your box thinks it is using.

Was this a clean install or an update to 9.10?

Yes, still struggling through getting Grub back. This was a clean install about 1 week old. Here is the output of grub-install -v
```
ubuntu@ubuntu:/$ grub-install -v
grub-install (GNU GRUB 1.97~beta4)
ubuntu@ubuntu:/$ 
```My current  problem is getting my BIOS enabled RAID1 mounted. I opened another post under that description. I have determined what I want to mount "/dev/mapper/pdc_hdbgeifbd" that is the correct RAID set (2x500gb hdds) but mount is asking for the fstype. I am stuck here. I tried ext4 (What I chose when in the partitioning screen during install) I have also read dmsg looking for any info on what fstype it may have seen during startup on LiveCD.

So I am here:
Booted under LiveCD in hopes of getting Grub back.
tried to mount /dev/mapper/pdc_hdbgeifbd
need to find out what fstype to pass to -t in mount

here is my mount statement
```
ubuntu@ubuntu:/$ sudo mount -t ext4 /dev/mapper/pdc_hdbgeifbd /mnt
mount: wrong fs type, bad option, bad superblock on /dev/mapper/pdc_hdbgeifbd,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:/$ 
```I really appreciate any help here. I woudl rather work through this than re-install.

Pat

---

### Post by ranch hand on 2009-12-07
Well,  iam not sure that I am the guy to help with this.  Yes, I have  SATA box.  No, I do not run RAID.  Just don't like the concept.  Assume it is a personality fault.

There is, however, no problem with ext4.  You had this running, I think, with ext4.  I have used ext4 sense a week before 9.04 final was released.  There are 2 9.04 installations on this box, both ext4, that have never given me any trouble.  This does not count 3 versions of 9.10 and 3 of 10.04testing all running ext4, some on internal HDDs and some on an external enclosure.

In the link in my sig you will find more links.  I would recommend checking the 2nd one and maybe doing a thread search for "raid" after reading the original post.

Other wise hope for something on your other thread.

More than one thread per subject, by the way is highly frowned upon in these forums.  Just for your future posting informatition.  You are certainly not the only one to do it.

---

### Post by apesa on 2009-12-07
Thanks Ranch Hand. I understand the 2 threads per subject and adhere. It's just that my current problem was with DMRAID and not Grub plus the posts get buried in minutes around here, quite amazingly fast.

I did read your Grub2 Introduction. Thanks, I am now well ready to get into fixing things once I can get the corrrect mount to work on. PS I do like ext4 and I don't think it is the problem. I do think I could / should have used LVM to create the RAID1 mirror in ubuntu instead of using the mobo bios supplied stuff.

Anyhow, Thanks much for your time.. BTW, Montana is where I want to retire, after my kids college is paid for.

pat

---

### Post by ranch hand on 2009-12-07
Make sure you check out drs305's grub basics How To, 2nd link in my post.  A whole bunch of us started with grub2 on Karmic-testing-alpha2 when it was added.  he has done a whole lot of experimenting with his own and other folks ideas and really done a super job of writing it all up.  That thread has many posts and it would not surprise me if raid is not in there somewhere and fixed.

LVM is another thing I have not fooled with bu I understand that is has its own quirks with grub2.

Montana is a nice place.  Right now I am in the county seat of Powder River county (Broadus pop=500).  I prefer to be on a ranch but my last boss up and died on me.  At least here in the big city I get DSL.  On the ranch it was dial up @ 4.4Kb/sec.

My son is 37.

---

