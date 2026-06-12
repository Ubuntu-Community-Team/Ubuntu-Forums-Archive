---
title: "So Close to keeping Ubuntu"
date: 2010-01-21
forum: New to Ubuntu
---

### Post by Xmind2006 on 2010-01-21
I'll try not to rant on how much time I've spent trying to get Ubuntu to install (well rather 95% of that time just trying to get Grub2 to install correctly). Anyway, I now have Ubuntu installed and can use Grub2 to boot into Ubuntu. However, I can not boot into my Windows XP partition from Grub though (errors out with a missing/corrupt hal.dll message). Ironically, my Ultimate Boot CD boots XP just fine.
 
Below is the output of the Boot Info Script.
 
```
============================= Boot Info Summary: ==============================
 
 => Windows is installed in the MBR of /dev/sda
 => Grub 1.97 is installed in the MBR of /dev/sdb and looks for 
    (UUID=75c4b0b8-e6e9-49e0-873d-12507ad3990c)/boot/grub.
 => Grub 1.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #6 for /boot/grub.
sda1: _________________________________________________________________________
 
    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /grub/core.img
 
sdb1: _________________________________________________________________________
 
    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   
 
sdc1: _________________________________________________________________________
 
    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   
 
sdc2: _________________________________________________________________________
 
    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  
 
sdc5: _________________________________________________________________________
 
    File system:       swap
    Boot sector type:  -
    Boot sector info:  
 
sdc6: _________________________________________________________________________
 
    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
 
=========================== Drive/Partition Info: =============================
 
Drive: sda ___________________ _____________________________________________________
 
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd8994d31
 
Partition  Boot         Start           End          Size  Id System
 
/dev/sda1    *             63   156,296,384   156,296,322   7 HPFS/NTFS
 
 
Drive: sdb ___________________ _____________________________________________________
 
Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2e7db42e
 
Partition  Boot         Start           End          Size  Id System
 
/dev/sdb1                  63   488,392,064   488,392,002   7 HPFS/NTFS
 
 
Drive: sdc ___________________ _____________________________________________________
 
Disk /dev/sdc: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders, total 72303840 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xec4cf0e6
 
Partition  Boot         Start           End          Size  Id System
 
/dev/sdc1    *             63    51,536,519    51,536,457   7 HPFS/NTFS
/dev/sdc2          51,536,520    72,292,499    20,755,980   5 Extended
/dev/sdc5          68,099,535    72,292,499     4,192,965  82 Linux swap / Solaris
/dev/sdc6          51,536,646    68,099,534    16,562,889  83 Linux
 
 
blkid -c /dev/null: ____________________________________________________________
 
/dev/sda1: UUID="58C0DEB5C0DE9898" LABEL="New Volume" TYPE="ntfs" 
/dev/sdb1: UUID="305C17A15C176140" LABEL="New Volume" TYPE="ntfs" 
/dev/sdc1: UUID="0C0487C30487AE70" TYPE="ntfs" 
/dev/sdc5: UUID="417c0f8a-db7d-4be5-b983-122efaefa930" TYPE="swap" 
/dev/sdc6: UUID="75c4b0b8-e6e9-49e0-873d-12507ad3990c" TYPE="ext4" 
 
=============================== "mount" output: ===============================
 
/dev/sdc6 on / type ext4 (rw,errors=remount-ro)
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
gvfs-fuse-daemon on /home/issac/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=issac)
 
 
================================ sda1/boot.ini: ================================
 
[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(2)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(2)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
=================== sda1: Location of files loaded by Grub: ===================
 
 
    .0GB: grub/core.img
 
=========================== sdc6/boot/grub/grub.cfg: ===========================
 
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
set root=(hd2,6)
search --no-floppy --fs-uuid --set 75c4b0b8-e6e9-49e0-873d-12507ad3990c
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
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd2,6)
    search --no-floppy --fs-uuid --set 75c4b0b8-e6e9-49e0-873d-12507ad3990c
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=75c4b0b8-e6e9-49e0-873d-12507ad3990c ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd2,6)
    search --no-floppy --fs-uuid --set 75c4b0b8-e6e9-49e0-873d-12507ad3990c
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=75c4b0b8-e6e9-49e0-873d-12507ad3990c ro single 
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd2,6)
    search --no-floppy --fs-uuid --set 75c4b0b8-e6e9-49e0-873d-12507ad3990c
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=75c4b0b8-e6e9-49e0-873d-12507ad3990c ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd2,6)
    search --no-floppy --fs-uuid --set 75c4b0b8-e6e9-49e0-873d-12507ad3990c
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=75c4b0b8-e6e9-49e0-873d-12507ad3990c ro single 
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
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 58c0deb5c0de9898
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###
 
### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
 
=============================== sdc6/etc/fstab: ===============================
 
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/via_dffbcjibfi6 /               ext4    errors=remount-ro 0       1
/dev/mapper/via_dffbcjibfi5 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
 
=================== sdc6: Location of files loaded by Grub: ===================
 
 
  26.3GB: boot/grub/core.img
  26.3GB: boot/grub/grub.cfg
  26.3GB: boot/initrd.img-2.6.31-14-generic
  26.3GB: boot/initrd.img-2.6.31-17-generic
  26.3GB: boot/vmlinuz-2.6.31-14-generic
  26.3GB: boot/vmlinuz-2.6.31-17-generic
  26.3GB: initrd.img
  26.3GB: initrd.img.old
  26.3GB: vmlinuz
  26.3GB: vmlinuz.old
```
 
My Windows XP's boot.ini file located on the boot drive:
```
[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(2)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(2)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
```
 
Layout of disks in XP's Disk Management:
[[IMG]http://www.freeimagehosting.net/uploads/th.99c3c8e04d.jpg[/IMG]]("http://www.freeimagehosting.net/image.php?99c3c8e04d.jpg")
 
In case the above isn't enough info my XP partition is on SDC1, Linux Swap on SDC5, and Ubuntu on SDC6. SDC is currently my only SATA drive and my motherboard always treats SDA, my 80 gig EIDE drive as the boot drive. SDA does have all the XP boot info.
 
I've read a boat load of forum posts and tried adding different boot combinations to the Grub.cfg (in the grub.d directory) based on examples I've found, but to no avail getting grub to load XP correctly. I've read other people being told to reinstall the MBR for XP, then Grub's MBR again, but I am extremely hesitant to do that at the moment because it is fresh in my mind on how long it has taken me to get Grub installed and booting at least 1 OS correctly.
 
Sorry for the wall of text, but it just seems like there is some very simple thing I am missing that is preventing me from having a cleaned up system....errr...boot menu anyway.
 
Thanks in advance for any assistance as I am looking forward to migrating from XP to Ubuntu.....cause I really don't care for Windows 7 at all. :P

---

### Post by cariboo on 2010-01-21
A corrupt/missing hal.dll is a pretty common problem. Have a look at this [this ]("http://support.microsoft.com/kb/314477")page, there a 4 different methods of fixing the problem.

You shouldn't have to reinstall grub2 if you follow the guide.

---

### Post by Xmind2006 on 2010-01-25
[EMAIL="*&^@#$*%$*@^#$@$"]*&^@#$*%$*@^#$@$[/EMAIL]!
 
Well after following the MS link, it replaced my Grub2 boot, so I had to re-install GRUB2 via the liveCD.  Many hours and a bit of a learning curve for me I finally got Grub2 to boot Ubuntu 9.10 and now XP without a boot disk....finally!
 
Takes a little bit to get used to, but so far Ubuntu looks good and runs fairly smoothly...just need to read more about installing stuff properly now....like WoW! :D

---

### Post by Xmind2006 on 2010-01-30
RAWR!  
 
So Grub booted XP once, and now I'm back again with the whole missing/corrupt hal.dll issue.  I am having a hard time believing that Windows and/or it's boot info is corrupt or missing as any boot disk I use can boot into XP without a problem.  I know it is reading the boot.ini correctly because I get the option of which XP to boot (there are 2 entries because of following the previous responders link re-creates the XP entries and I haven't deleted the duplicate one).
 
I did not update grub2 after it worked and I have not done anything regarding the boot files; strictly booted into XP, restarted booted into Ubuntu, restarted and then couldn't boot into XP again without a boot disk.
 
Just to recap that I suspect Grub2 is having problems with the XP boot info on the SDA drive, but the Windows root is on SDC.  
 
Anyone have any suggestions on what my Grub.cfg should be?  I've used a lot of other versions, but they didn't work.

---

### Post by oldfred on 2010-01-30
I think grub is telling windows it is the first drive which is often the case, but windows still thinks it is rdisk([COLOR=DarkRed]2[/COLOR]).

multi(0)disk(0)rdisk([COLOR=DarkRed]2[/COLOR])partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

This is my entry but on this computer I only have one drive.
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect

Be careful about editing windows files from Ubuntu as the line endings are different.
If editing windows files like boot.ini
(Using nano instead of gedit, it's better for dos-style linebreaks)


Did you remove drives while installing? that often mixes things up.

Also how did you get a grub file in the window XP partition?
 sda1
Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM [COLOR=DarkRed]/grub/core.img[/COLOR]

---

### Post by meierfra. on 2010-01-30
> This is my entry but on this computer I only have one drive.
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windo ws XP Media Center Edition" /noexecute=optin /fastdetect


The "drivemap" command turns /dev/sda into "rdisk(0)".   So the windows  drive /dev/sdc will be either "rdisk(1)" or "rdisk(2)" . Since "rdisk(2)" gives the "hal.dll" error, I would guess that "rdisk(1)" would be the correct entry.  


But I suggest to move the  Windows boot files to the Window partition,  update  grub.cfg and edit boot.ini

```
cd /mnt
sudo mkdir a c
sudo mount /dev/sda1 a
sudo mount /dev/sdc1 c
cd a
sudo cp boot.ini ntldr NTDETECT.COM  /mnt/c
sudo update-grub
sudo nano /mnt/c/boot.ini
```

Now that the boot files are on /dev/sdc1 you have to use "rdisk(0)". So change both "rdisk(2)" in boot.ini to "rdisk(0)". Follow the instruction on the bottom of the screen to save the file. "^" means the "ctrl" key.

Hopefully that will cure the "hal.dll" problem.

> /grub/core.img
It seems you once installed Grub with /dev/sda1 mounted at /boot.  That should not cause any problems, but I still suggest to deleted the grub folder on /dev/sda1.

---

### Post by louieb on 2010-01-30
> **meierfra. said:**
> ...

But I suggest to move the  Windows boot files to the Window partition,  update  grub.cfg and edit boot.ini

[CODE]...
sudo [COLOR=Red]**cp**[/COLOR] boot.ini,ntldr,NTDETECT.COM  /mnt/c
...


Hello meierfra, think you might have missed something.:D Computers can be so pickkey.

---

### Post by meierfra. on 2010-01-30
> Hello meierfra, think you might have missed something
Thanks, I fixed it. But you did not catch all my typos. The ","'s don't belong in there :)

---

### Post by Xmind2006 on 2010-01-30
> **meierfra. said:**
> 
 
But I suggest to move the Windows boot files to the Window partition, update grub.cfg and edit boot.ini
 
```
cd /mnt
sudo mkdir a c
sudo mount /dev/sda1 a
sudo mount /dev/sdc1 c
cd a
sudo cp boot.ini ntldr NTDETECT.COM  /mnt/c
sudo update-grub
sudo nano /mnt/c/boot.ini
```
 
Now that the boot files are on /dev/sdc1 you have to use "rdisk(0)". So change both "rdisk(2)" in boot.ini to "rdisk(0)". Follow the instruction on the bottom of the screen to save the file. "^" means the "ctrl" key.
 
Hopefully that will cure the "hal.dll" problem.
 
 
It seems you once installed Grub with /dev/sda1 mounted at /boot. That should not cause any problems, but I still suggest to deleted the grub folder on /dev/sda1.
 
Woot! Thanks a bunch Meierfra!  Grub2 now works as intended so that I no longer need a boot disk to get into XP.
 
I am very impressed the amount of support that there is on these forums considering the volume of new posts on these forums.  Keep up the great work on helping the "converts" ;)

---

### Post by meierfra. on 2010-01-30
> these forums considering the volume of new posts on these forums. 
Luckily as the number of posts increased, the number of people  helping out  also has increased.


> Grub2 now works as intended so
Great. 

> Thanks a bunch Meierfra!
You are welcome. And thanks again to louieb for  catching  my  typo.

---

### Post by capitalfear on 2010-01-30
i would like to take a moment to thank God that i am not the only one that has a problem with grub...sigh...

---

### Post by meierfra. on 2010-01-30
> grub...sigh...
Can't blame this  one on  Grub.  It  was a  plain Windows problem:  a faulty "boot.ini".

---

### Post by Xmind2006 on 2010-01-31
Well, I wouldn't blame Windows on this one, it was an interaction/configuration with GRUB and the Windows boot files.  The boot.ini file is unchanged from when I only had XP installed.  In fact any boot disk was able to boot XP just fine with the XP boot files, including reading the boot.ini file.
 
The difference appears that grub does not like having XP's boot information in a seperate drive/partition than the other system files.  However, my setup was a little unique with the boot drive not being my system drive.

---

### Post by meierfra. on 2010-01-31
> The difference appears that grub does not like having XP's boot information in a seperate drive/partition than the other system files
No.   The problem was caused by the change in the boot order in the bios and the fact that the boot.ini refers to  hard disks by  the position in the bios  rather than uuids (like Grub does) or disk signature (like Vista/Win 7) does.

Grub has  no problems with that configuration.  I only asked you to move the boot files, since it simplifies  your setup, and avoids running into similar problems in the future.  

There would have been two different  ways to leave the boot files on /dev/sda1 and still boot Windows:

1)  Change "rdisk(2)" in boot.ini on /dev/sda1  to "rdisk(1)"

2)  Do not edit the boot.ini on /dev/sda1. Instead create a custom entry for Windows XP 
```
gksudo gedit /etc/grub.d/40_custom
``` 

add this to the end of the file

menuentry "XP Test"{
set  root=(hd1,1)
drivemap (hd1) (hd0)
drivemap (hd0) (hd2)
chainloader +1
}



PS:  Due to the confusion caused by my typos, my instruction ended up coping the boot files from /dev/sda1 to /dev/sdc1. (I originally wanted to move them).  So you should have two entries for Windows XP on your Grub menu. If you delete the boot files on /dev/sda1 and run "update-grub" the extra entry  will disappear.

---

### Post by Xmind2006 on 2010-01-31
Yeah, I realised that copying them would cause duplicate entries when doing an update-grub, so I copied and archived the files.

I didn't remove any disks from the system at any time during this process and I never changed the drive/system location in the boot.ini file.

I guess we can agree to disagree on what/who was at fault.  I agree using the UUIDs or the disk sigs is a better disk identifier method, but IMO, GRUB should be able to understand or prompt the user during the install/setup (in an advanced option) with regards to XP.  Unfortunately GRUB has to be the one to accommodate XP's inferior boot method, not make the user learn about the different disk reading/booting/priority methods between operating systems.  Not that I'm complaining myself as I am glad to learn this information, but for someone that isn't computer savvy just looking to install Ubuntu, this is/will be a huge deterrent.  just my $0.02 cents as I couldn't imaging many non-tech people spending as much time as I have just to install Ubuntu correctly....errr Grub rather, but then again they probably would have just installed inside XP, so I guess I know just enough to make things difficult.  :D


> menuentry "XP Test"{
set  root=(hd1,1)
drivemap (hd1) (hd0)
drivemap (hd0) (hd2)
chainloader +1
}


This was the example I was looking for.  I tried many iterations of this, but never did the drivemap hd1, hd0/hd0, hd2 as all the examples I seen used the same 2 drives in each drivemap, just swapped.

---

### Post by meierfra. on 2010-01-31
> I didn't remove any disks from the system at any time during this process and I never changed the drive/system location in the boot.ini file.
You changed to boot order. You used to boot from /dev/sda and now you are booting from /dev/sdc (or maybe from /dev/sdb)  Its the boot order which matters for boot.ini, not the  physical order.

---

### Post by meierfra. on 2010-01-31
> but IMO, GRUB should be able to understand or prompt the user during the install/setup (in an advanced option) with regards to XP.
Actually that is very difficult to do. To get the settings correct, the Grub  installer would have the know the boot order in the BIOS. But  the operating system has no knowledge of the boot order in the bios. This problem has plagued Grub for a long time, even when  Windows is not involved.   Using UUID's overcame this problem, but has  let to longer boot up times.


IMO Grub2   does a very  good job setting up Windows correctly. But Grub2 is currently not able to automatically compensate  for a faulty boot.ini. Your case is pretty rare, in fact its is the first time I have seen a case where a faulty boot.ini can be corrected by a clever use of "drivemap".  Usually it requires to edit boot.ini.

---

