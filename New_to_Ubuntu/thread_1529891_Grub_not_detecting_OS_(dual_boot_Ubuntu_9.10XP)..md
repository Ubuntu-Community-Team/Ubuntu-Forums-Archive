---
title: "Grub not detecting OS (dual boot Ubuntu 9.10/XP)."
date: 2010-07-12
forum: New to Ubuntu
---

### Post by sleep furious idea on 2010-07-12
Hi, friendly wizards of tech, I'm a Ubuntu newb with a dire problem.  Here it is:

I cannot boot up a dual boot XP and Ubuntu set up anymore.

Upon boot up GRUB (GNU GRUB 1.97beta4) gives me options of memtest86+ and memtest86+, serial console 115200 BUT no options for Ubuntu 9.10 OR Windows XP.  (I ran the tests and they all passed)

Until last night both XP and Ubuntu were working fine.  I haven't used Ubuntu for a while so I tried to install the updates.  They didn't seem to work.  I couldn't type or move any windows.  Restarted the computer a couple times, then the OSes became ghosts.  Help!  I would quite like to resurrect the OS from the computer grave yard.

Tried following instructions here but to no avail:

[http://ubuntuforums.org/showthread.php?p=9582052#post9582052](http://ubuntuforums.org/showthread.php?p=9582052#post9582052)


Thanks,

Sleep

---

### Post by drs305 on 2010-07-12
For us to see what has happened please boot to the LiveCD desktop and then run the boot info script from this site:
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")
It will provide us with the information we need to provide an informed solution.

Place the contents of the RESULTS.txt between "code" tags in this thread. You can generate the tags by pressing the # icon in the post's menu.

---

### Post by lindsay7 on 2010-07-12
Read thru this info and see if it helps.

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

There needs to be a lot of trouble shooting done to find out what your specific problem is but most times it is an mbr or a grub install problem which can be solved with the steps outlined here.

---

### Post by maizuddin35 on 2010-07-12
have you done sudo update-grub?

---

### Post by sleep furious idea on 2010-07-12
Yes, I tried sudo update-grub but i"m not sure if it worked:)

Took me a while to get it but here is the boot script:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x72845995

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   122,881,184   122,881,122   7 HPFS/NTFS
/dev/sda2         122,881,185   179,189,009    56,307,825   7 HPFS/NTFS
/dev/sda3         179,189,010   234,436,544    55,247,535   5 Extended
/dev/sda5         179,189,073   232,058,924    52,869,852  83 Linux
/dev/sda6         232,058,988   234,436,544     2,377,557  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        18D8D1A2D8D17E86                       ntfs                                     
/dev/sda2        761407101406D353                       ntfs       Log1 sda1                     
/dev/sda2        761407101406D353                       ntfs       Log1 sda1 sda2 sda3 sda5 sda6 
/dev/sda5        80e07a34-30e8-4d4e-b3da-8f3e326add46   ext4                                     
/dev/sda6        dfafdc14-296a-4514-89b7-05164df3d954   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
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
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=80e07a34-30e8-4d4e-b3da-8f3e326add46 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=dfafdc14-296a-4514-89b7-05164df3d954 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  93.2GB: boot/grub/core.img
  92.8GB: boot/grub/grub.cfg
  92.4GB: boot/initrd.img-2.6.31-14-generic
  92.7GB: boot/initrd.img-2.6.31-15-generic
  93.1GB: boot/initrd.img-2.6.31-16-generic
  92.4GB: boot/vmlinuz-2.6.31-14-generic
  92.5GB: boot/vmlinuz-2.6.31-15-generic
  93.1GB: boot/vmlinuz-2.6.31-16-generic
  93.1GB: initrd.img
  92.7GB: initrd.img.old
  93.1GB: vmlinuz
  92.5GB: vmlinuz.old
```

Thanks for your tips!!!

---

### Post by sleep furious idea on 2010-07-12
Results of Grub reinstall:

```
ubuntu@ubuntu:~$ sudo mkdir /media/sda5
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /media/sda5
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/sda5 /dev/sda
Installation finished. No error reported.
This is the contents of the device map /media/sda5/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)	/dev/sda
ubuntu@ubuntu:~$ 

```

---

### Post by sleep furious idea on 2010-07-12
> **sleep furious idea said:**
> Results of Grub reinstall:

```
ubuntu@ubuntu:~$ sudo mkdir /media/sda5
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /media/sda5
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/sda5 /dev/sda
Installation finished. No error reported.
This is the contents of the device map /media/sda5/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)	/dev/sda
ubuntu@ubuntu:~$ 

```


Just rebooted and the problem persists - no OS options...

I have GRU GRUB 1.97beta4.  Should I or could I update to GRUB2?

If so, how?

---

### Post by lindsay7 on 2010-07-12
did you run   sudo update-grub

---

### Post by sleep furious idea on 2010-07-12
> **lindsay7 said:**
> did you run   sudo update-grub

I tried again but I get:


root@ubuntu:~# sudo update-grub
grub-probe: error: cannot find a device for /.


Did I do something wrong or is it another problem? Thanks...

---

### Post by lindsay7 on 2010-07-12
did you run these commands? from  this site [http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html](http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html)


a) Firstly, you need to find out on which partition your Linux system is installed:

sudo fdisk -l

(in my case, it's "sda1")

b) Now, we must mount this partition:

sudo mount /dev/sda1 /mnt

Where "sda1" is the partition where you installed Ubuntu (or any other Linux distro). It could be "sda5", "sda6", etc. for you.

c) Install grub to the partition you've mounted:

sudo grub-install --root-directory=/mnt/ /dev/sda

Important:  Please notice that it's "/dev/sda", not "/dev/sda1". "sda" is the hard disk on which your Linux distribution is installed!

d) Restart your computer. As previous Grub2 entries are removed, run the following command to restore them:

sudo update-grub

---

### Post by sleep furious idea on 2010-07-12
Grub 1.97beta4 is GRUB2 is it not?
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

### Post by lindsay7 on 2010-07-12
Right now I think there is a problem with a mount point for /. Take a look at the exact code to put in per the web site.

---

### Post by Kirkland14 on 2010-07-12
I just had this same problem.  Lindsay gave me sound advice that worked. Thanks again Lindsay7

---

### Post by sleep furious idea on 2010-07-12
Hi Lindsay7,

I followed your instructions and got this same error again:

> **sleep furious idea said:**
> 

root@ubuntu:~# sudo update-grub
grub-probe: error: cannot find a device for /.



---

### Post by john newbuntu on 2010-07-12
Yes you have grub2.  Do you want to try and boot from the CLI?  When you boot and get to the grub screen, press C  This will get you a prompt like:
grub>

At this prompt, type these commands one after the other:

set root=(hd0,5)
linux /vmlinuz root=/dev/sda5 ro quiet splash
initrd /initrd.img
boot

If these set of commands boot you in, immediately run this from a terminal (application->accessories->terminal):
sudo update-grub

---

### Post by sleep furious idea on 2010-07-12
> **john newbuntu said:**
> Yes you have grub2.  Do you want to try and boot from the CLI?  When you boot and get to the grub screen, press C  This will get you a prompt like:
grub>

At this prompt, type these commands one after the other:

set root=(hd0,5)
linux /vmlinuz root=/dev/sda5 ro quiet splash
initrd /initrd.img
boot

If these set of commands boot you in, immediately run this from a terminal (application->accessories->terminal):
sudo update-grub

Well, I followed these instructions and got a blank screen:(

I'll keep trying and reading other posts in the mean time...

---

### Post by oldfred on 2010-07-12
I have never seen the script duplicate a partition like this:

/dev/sda2        761407101406D353                       ntfs       Log1 sda1                     
/dev/sda2        761407101406D353                       ntfs       Log1 sda1 sda2 sda3 sda5 sda6 

I do not know if it is the script but since the prober is also having trouble I worry that something is wrong with partitions. fdisk looked ok.

Please rerun just the command to see if it still shows a double entry:
```
blkid -c /dev/null
```

---

### Post by sleep furious idea on 2010-07-12
I will try that...

BTW, I tried the XP disk and I can't get to recovery or repair.  After a minute it goes to this message:

```
A problem has been detected and windows has been shut down to prevent damage to your computer.

If this is the first time...blah blah blah...

Check fo rviruses...remove any newly installed hard drive controllers.  Check hard drive configuration....Run CHKDSK /F and restart....
```

In Ubuntu live I can still access partitioned XP files though...

---

### Post by john newbuntu on 2010-07-12
I was gonna say, run "chkdsk /r" from the recovery console. But now that I read your message, at least make sure the Ubuntu partition is clean, from an ubuntu liveCD/USB, run the following:
sudo e2fsck -C0 -p -f -v /dev/sda5

If this gives any errors, then run:
sudo e2fsck -f -y -v /dev/sda5

---

### Post by sleep furious idea on 2010-07-13
> **oldfred said:**
> I have never seen the script duplicate a partition like this:

/dev/sda2        761407101406D353                       ntfs       Log1 sda1                     
/dev/sda2        761407101406D353                       ntfs       Log1 sda1 sda2 sda3 sda5 sda6 

I do not know if it is the script but since the prober is also having trouble I worry that something is wrong with partitions. fdisk looked ok.

Please rerun just the command to see if it still shows a double entry:
```
blkid -c /dev/null
```

```
ubuntu@ubuntu:~$ blkid -c /dev/null
ubuntu@ubuntu:~$ sudo blkid -c /dev/null
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="18D8D1A2D8D17E86" TYPE="ntfs" 
/dev/sda2: UUID="761407101406D353" LABEL="????" TYPE="ntfs" 
/dev/sda5: UUID="80e07a34-30e8-4d4e-b3da-8f3e326add46" TYPE="ext4" 
/dev/sda6: UUID="dfafdc14-296a-4514-89b7-05164df3d954" TYPE="swap" 
ubuntu@ubuntu:~$ 


```

Here are the results. Doesn't appear to be duplicates to me...

---

### Post by sleep furious idea on 2010-07-13
> **john newbuntu said:**
> I was gonna say, run "chkdsk /r" from the recovery console. But now that I read your message, at least make sure the Ubuntu partition is clean, from an ubuntu liveCD/USB, run the following:
sudo e2fsck -C0 -p -f -v /dev/sda5

If this gives any errors, then run:
sudo e2fsck -f -y -v /dev/sda5

Here are the results:

```
ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f /dev/sda5
/dev/sda5: 186243/1654784 files (0.1% non-contiguous), 1192976/6608731 blocks  
ubuntu@ubuntu:~$ sudo e2fsck -f -y -v /dev/sda5
e2fsck 1.41.9 (22-Aug-2009)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

  186243 inodes used (11.25%)
     151 non-contiguous files (0.1%)
     117 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 162831/29
 1192976 blocks used (18.05%)
       0 bad blocks
       1 large file

  133483 regular files
   23132 directories
      68 character device files
      26 block device files
       0 fifos
     387 links
   29518 symbolic links (23272 fast symbolic links)
       7 sockets
--------
  186621 files


```

---

### Post by sleep furious idea on 2010-07-13
> **lindsay7 said:**
> Right now I think there is a problem with a mount point for /. 

Could you (or someone) explain what this means?

---

### Post by lindsay7 on 2010-07-13
I can not see anything that is incorrect but Linux can not find a device or partition that is mounted as / or the root directory where the grub files and startup instructions should be even though your info shows they are there.  At least that is what I think.  John and Oldfred are trying to see why this is so. Did you you the checkdisk commands.

---

### Post by sleep furious idea on 2010-07-13
Are 'check disk' window commands, as in chkdsk  /f?

If so I can't do them right now as when I put in the XP disk I get this notice:

> **sleep furious idea said:**
> I will try that...

BTW, I tried the XP disk and I can't get to recovery or repair.  After a minute it goes to this message:

```
A problem has been detected and windows has been shut down to prevent damage to your computer.

If this is the first time...blah blah blah...

Check fo rviruses...remove any newly installed hard drive controllers.  Check hard drive configuration....Run CHKDSK /F and restart....
```

In Ubuntu live I can still access partitioned XP files though...

---

### Post by john newbuntu on 2010-07-13
Your linux file system looks good to me and so does boot info script (other than the duplicate label that oldfred mentioned).  You have re-installed grub but your grub.cfg is not complete because of what lindsay7 has explained.  Perhaps a previous update-grub failed when your system was up and running.

The one thing I am not sure of is if all the grub files exist.  So I think if we are out of ideas and if re-installation is not an option, you might want to re-install grub2 using method2 or 3 per the following documents:

[https://help.ubuntu.com/community/Grub2#METHOD%202%20-%20Copy%20GRUB%202%20Files%20from%20the%20Installed%20Partition]("https://help.ubuntu.com/community/Grub2#METHOD%202%20-%20Copy%20GRUB%202%20Files%20from%20the%20Installed%20Partition")
OR
[https://help.ubuntu.com/community/Grub2#METHOD%203%20-%20CHROOT](https://help.ubuntu.com/community/Grub2#METHOD%203%20-%20CHROOT)

I am hoping this will give you a workable grub.cfg.  Also follow this up with the post-restoration commands.  I would also wait on oldfred and lindsay7 for their opinions.

A strong suggestion is to back up any information you can from the liveCD if you have not already done so.

---

### Post by lindsay7 on 2010-07-13
I agree with John.  You could start up with the Ubuntu live cd and run gparted.  You can find a disc check utility under the partition button.  Run check on each partition.  I am puzzled as to why you can not start up the windows xp repair disc an nothing we have done should have changed anything on the windows partition.  If you can get window repair going you could do the mbr reinstall and that would at least get windows working again, You can find this here  [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)  under the xp fix boot portions.

---

### Post by sleep furious idea on 2010-07-13
Thanks guys for all your help.  I was quite stunned for a while. 

I will follow your last instructions, then back up some files and re-install.  Hopefully that will solve it.

I'll post the results later to follow up.

---

### Post by sleep furious idea on 2010-07-13
> **lindsay7 said:**
> I agree with John.  You could start up with the Ubuntu live cd and run gparted.  You can find a disc check utility under the partition button.  Run check on each partition.  I am puzzled as to why you can not start up the windows xp repair disc an nothing we have done should have changed anything on the windows partition.  If you can get window repair going you could do the mbr reinstall and that would at least get windows working again, You can find this here  [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)  under the xp fix boot portions.

In Gparted:

I have a waring in  /dev/sda1

The information shows a series of Accounting cluster failures.

Ex:

Cluster accounting faied at 395163 (0x6097b): extra cluster in $Bitmap

...it goes on for aobut 10 lines like this all with different numbers...

Might this be where the problem lies????

---

### Post by sleep furious idea on 2010-07-13
See above post ------in GParted it says,


Check and repair file system (ntfs) on /dev/sda1

Not sure what to do here.  Have some time today and hope to get it fixed or else see if I can break the record for 19th floor laptop balcony slingshot.

---

### Post by sleep furious idea on 2010-07-13
> **sleep furious idea said:**
> See above post ------in GParted it says,


Check and repair file system (ntfs) on /dev/sda1

Not sure what to do here.  Have some time today and hope to get it fixed or else see if I can break the record for 19th floor laptop balcony slingshot.

Here is the error methinks (actually I have no idea)

in dev/sda - GParted

Applying pending operations

There is a waring

ntfsresize -P -i -f /dev/sda1


Any chance to fix this yet?

---

### Post by sleep furious idea on 2010-07-13
> **john newbuntu said:**
> Your linux file system looks good to me and so does boot info script (other than the duplicate label that oldfred mentioned).  You have re-installed grub but your grub.cfg is not complete because of what lindsay7 has explained.  Perhaps a previous update-grub failed when your system was up and running.

The one thing I am not sure of is if all the grub files exist.  So I think if we are out of ideas and if re-installation is not an option, you might want to re-install grub2 using method2 or 3 per the following documents:

[https://help.ubuntu.com/community/Grub2#METHOD%202%20-%20Copy%20GRUB%202%20Files%20from%20the%20Installed%20Partition]("https://help.ubuntu.com/community/Grub2#METHOD%202%20-%20Copy%20GRUB%202%20Files%20from%20the%20Installed%20Partition")
OR
[https://help.ubuntu.com/community/Grub2#METHOD%203%20-%20CHROOT](https://help.ubuntu.com/community/Grub2#METHOD%203%20-%20CHROOT)

I am hoping this will give you a workable grub.cfg.  Also follow this up with the post-restoration commands.  I would also wait on oldfred and lindsay7 for their opinions.

A strong suggestion is to back up any information you can from the liveCD if you have not already done so.


Okay, here is where I am at.  I reinstalled grub. Following the method 3 above. (I was missing a step as my boot partition sda1 not where linux is (sda5)

Now, I rebooted and the opening screen is:

sh:grub>

Where can I go from here?  (Other than a meditation center while munching some *****.)

---

### Post by sleep furious idea on 2010-07-13
I'd like to thank everyone again for their help.

Couldn't fix the problem in the end so I reinstalled everything.

So it goes...

---

