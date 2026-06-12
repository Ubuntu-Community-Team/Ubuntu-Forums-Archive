---
title: "Acer and grub rescue&gt;"
date: 2011-08-30
forum: New to Ubuntu
---

### Post by Roland07 on 2011-08-30
So yesterday my Windows 7 installation stopped working properly. (It would hang on the login's "loading" screen indefinitely after selecting a user.) So after trying safe mode, and a couple other things, I picked "Windows 7 recovery environment(loader)" from my GRUB menu, on a guess. Turns out it was Acer's pre-installed "recovery partition," and the only option I had was to reset the whole computer to factory defaults or exit, so I just exited and rebooted.

Now, my computer gets past the BIOS, and goes straight to

error: no such partition.
grub rescue>

I've fished around a few threads and tutorials, but all of their suggestions result in "Unknown command." Any help for a Linux dabbler?

---

### Post by jtarin on 2011-08-30
Is this a WUBI installation of Ubuntu?

---

### Post by gnometorule on 2011-08-31
This happened out of the blue? Please describe any changes you, or the system (eg, Windows Update) made.

What version of Ubuntu have you been running? There are apparently many threads about Acer + intel graphics cards + upgrading to 11.04 on this forum.

---

### Post by waynefoutz on 2011-08-31
That Acer recovery program, it's hard to tell what it destroyed before you aborted it. From that error, it looks like it re-partitioned your drive and formatted, or at least partially formatted it.  If your Windows install was broken, unfortunately the only way to get it back is to run that program, or use recovery dvds that the Acer Erecovery created. Try hitting alt f10 as it boots and see if it launches again. 
if not,hopefully, you burned the DVDs before you installed Ubuntu. If not, you can buy them from Acer. It took about a week when I ordered mine. Companies like Acer should be punished, in my opinion, for not giving us real Windows install disks. If you want Windows back, you're going to have to run that recovery program. It's 4 dvds. You boot from the first and follow the directions. Or you could install straight Ubuntu. 

In the future, if you get Windows and Ubuntu dual booting again, install Grub Customizer from the Software Center and edit out that recovery partition option so you don't accidentally hit it again,that way if you ever need to access the recovery partition, you can just reinstall grub from a live Ubuntu cd, then select it.

---

### Post by coffeecat on 2011-08-31
@Roland07, boot up from an Ubuntu live CD or live USB and choose "try Ubuntu" to get to the desktop. You need to be connected to the internet. Go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script following the instructions there. Post the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags for readability. This will give us an overview of your system, including what may have happened to your Ubuntu root partition. The "error: no such partition" is probably referring to your Ubuntu partition.

---

### Post by waynefoutz on 2011-08-31
> **coffeecat said:**
> @Roland07, boot up from an Ubuntu live CD or live USB and choose "try Ubuntu" to get to the desktop. You need to be connected to the internet. Go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script following the instructions there. Post the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags for readability. This will give us an overview of your system, including what may have happened to your Ubuntu root partition. The "error: no such partition" is probably referring to your Ubuntu partition.

Yeah, that'd be helpful, but he's probably halfway through the Acer recovery process. Selecting that in the GRUB menu destroys things pretty fast. That's why I edited it out of mine.

---

### Post by coffeecat on 2011-09-01
> **waynefoutz said:**
> Yeah, that'd be helpful, but he's probably halfway through the Acer recovery process. Selecting that in the GRUB menu destroys things pretty fast. That's why I edited it out of mine.

Yes, that's why it would be helpful to see the boot script output - to see what the recovery process may have done.

I have an Acer laptop. I did once boot into the recovery partition to see what's what and I'm 99% sure that there was a way of getting out of it before it did anything. Nevertheless, I agree that it looks as though the recovery process may have done something destructive.

---

### Post by Mattheu on 2011-09-02
Sorry I've no solutions, but I'm a fellow sufferer. I think earlier I accidentally selected the wrong partition - Windows 7 recovery instead of Windows 7 and now I get the[INDENT]error: no such partition
grub rescue>
[/INDENT]message. So I can't get to any of the partitions. I have an Acer too, as it happens.

Bah!

Help!

I will try to boot from the live USB tomorrow, etc.

---

### Post by Mattheu on 2011-09-02
In the meantime, if it's any help, when I type "set", the response is

[INDENT]```
prefix=(hd0,msdos7)/boot/grub
root=hd0,msdos7
```[/INDENT]
and typing "ls", gives

[INDENT]```
(hd0) (hd0,msdos6) (hd0,msdos5) (hd0,msdos3) (hd0,msdos2) (hd0, msdos1)
```[/INDENT]

---

### Post by coffeecat on 2011-09-03
> **Mattheu said:**
> In the meantime, if it's any help, when I type "set", the response is

[INDENT]```
prefix=(hd0,msdos7)/boot/grub
root=hd0,msdos7
```[/INDENT]
and typing "ls", gives

[INDENT]```
(hd0) (hd0,msdos6) (hd0,msdos5) (hd0,msdos3) (hd0,msdos2) (hd0, msdos1)
```[/INDENT]

It looks as though your root partition was (hd0,7) but it's no longer there. If you post the output of the boot info script that I link to in post #5, we can see the full details.

---

### Post by YesWeCan on 2011-09-03
Here's how to boot from the rescue prompt: [https://help.ubuntu.com/community/Grub2#Rescue_Mode_.28.27.27grub_rescue.3E.27.27.29_Booting](https://help.ubuntu.com/community/Grub2#Rescue_Mode_.28.27.27grub_rescue.3E.27.27.29_Booting)

Your root partition is probably hd0,5.

---

### Post by Mattheu on 2011-09-05
Thank you both for your help.

I attempted to boot Ubuntu 11.04 from a Live USB and it worked briefly, before starting to give "program error" messages. I was therefore unable to run the boot info script, as requested in reply #5.

Now Ubuntu 11.04 will not boot from the Live USB - I get "program error" messages before the desktop appears.

I did manage to salvage data from some partitions, even without Ubuntu 11.04 running (how?), but other partitions were unfortunately not accessible.

I tried the grub rescue procedure, as recommended in reply #11. But the response to the "linux" and "initrd" commands is "Unknown command .."

Any further help, either to mend GRUB, or to salvage data from the partitions I can't access, or a fresh idea, will be appreciated. But I suspect I will have to re-install Ubuntu, overwriting everything currently on the Acer!

---

### Post by coffeecat on 2011-09-05
> **Mattheu said:**
> I attempted to boot Ubuntu 11.04 from a Live USB and it worked briefly, before starting to give "program error" messages. I was therefore unable to run the boot info script, as requested in reply #5.

OK. Possibly something wrong with the live USB.

> **Mattheu said:**
> But I suspect I will have to re-install Ubuntu, overwriting everything currently on the Acer!

To re-install Ubuntu you would need to be able to boot a live Ubuntu CD or USB, which you can't do at the moment, and if you do manage to do that then you might as well run the boot script **before** you re-install to see what the situation is. Check the md5 hash of the downloaded ISO to make sure it is good. If the ISO is good, try creating another live USB - perhaps that pendrive is failing. Or burn a CD.

---

### Post by pappusarkar on 2011-09-05
I'm also a fellow sufferer.this helped me a lot.

First, you have to boot the live CD. If you are using a thumb drive, also boot from it.
After booting, you have to determine which of your hard-disk partitions is the root (/) partition. You can do this by typing

Code:
sudo fdisk -l
in the terminal.
Note: If you only have one partition or you already know the address of your root partition, you can skip this step.

The output of the above command on my computer is as shown below

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb21e563c

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15147   121664576    7  HPFS/NTFS
/dev/sda2           15148       15427     2249100   82  Linux swap / Solaris
/dev/sda3           15428       30401   120277697+   f  W95 Ext'd (LBA)
/dev/sda5           15428       17251    14649344   83  Linux
/dev/sda6           17252       30401   105627343+  83  Linux
Admittedly, this can be a little confusing and might not really tell you which of your partitions is the root partition. Most of the time, what i do is to open up the file manager (nautilus) and check for the partition that resembles my root partition either as a result of the size or maybe a label (if you’re d kinda person that does that). i will then mount that partition from nautilus. After that, i go to the terminal and type the following

Code:
$ cat /etc/mtab
Amongst all the text that will be printed, the one containing the address of your root partition will be there. This is the output from my own system. Note that this will not show up if the partition is not mounted so ensure that only the root partiton is mounted so u dont get confused. alternatively, you can use gparted to also know the partiton address of the root partition.

/dev/sda5 /media/a2455o3f539io43pofp342 ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0
The line showing my root partition is highlighted in bold on d text above. From this, you can deduce the address of your root partition. I can see that mine is /dev/sda5. Once this has been done, the next step is to mount that partiton in a more easily accessible place.  Ubuntu will by default mount the partition according to its UUID (Universally Unique Identifier) in the /media folder as you can see above. However, this makes for a very long file path and makes it very easy to make a mistake.

Go to nautilus again and this time, unmount the previously mounted partition.

Then, use the terminal to mount that partition in the /mnt folder.
In my case, i will use the following command

Code:
$ sudo mount /dev/sda5 /mnt
Replace /dev/sda5 with a appropriate address for your root partition gotten above.

after this, it is time to install grub2. To do this, use the following command

Code:
$ sudo grub-install --root-directory=/mnt /dev/sda
This command should not be edited if you followed all the steps above. this installs grub2 in the MBR of the Harddisk. This will take a short while after which a confirmatory message will come up.

That is it. To confirm your settings, type in

Code:
$ sudo update-grub
in the terminal. However, even if this gives an error message, most of the time, the installation is already done. If you receive an error message though, you might not see other operating systems on your Computer especially if they were installed after the Ubuntu installation. To remedy this, boot into your freshly repaired Ubuntu and run the above command from there. That should sort it out.

Sources :- [http://ubuntunigeria.wordpress.com/2010/09/02/how-to-restore-grub2-using-an-ubuntu-live-cd-or-thumb-drive/](http://ubuntunigeria.wordpress.com/2010/09/02/how-to-restore-grub2-using-an-ubuntu-live-cd-or-thumb-drive/)

---

### Post by Mattheu on 2011-09-09
Thanks Coffeecat, the Live USB drive was indeed faulty. I bought a new USB drive and have now successfully run Ubuntu using that.

RESULTS.txt from the boot info script follow, as requested in reply #5, although it ends with an error message. Does this help? When things were working, Ubuntu 11.04 booted by default. 
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos7)/boot/grub on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.02 debian-20101016 ...........>...r>.......@......0...~.k...~...f...M.f.f....f..8~....>2}
    Boot sector info:   Syslinux looks at sector 1490144 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    24,578,047    24,576,000  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     24,578,048    24,782,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda3          24,782,848   122,439,097    97,656,250   7 NTFS / exFAT / HPFS
/dev/sda4         122,439,678   488,392,064   365,952,387   5 Extended
/dev/sda5         381,736,593   483,942,059   102,205,467  83 Linux
/dev/sda6         483,942,123   488,392,064     4,449,942  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4004 MB, 4004511744 bytes
116 heads, 51 sectors/track, 1322 cylinders, total 7821312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32     7,821,311     7,821,280   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       942ebbc7-f9ab-45a3-9a0b-d7acc8712346   ext3       
/dev/sda1        DAA41C49A41C2B11                       ntfs       PQSERVICE
/dev/sda2        921C18621C18441F                       ntfs       SYSTEM RESERVED
/dev/sda3        288CD9FA8CD9C28C                       ntfs       ACER
/dev/sda5        f285df19-6bcb-43db-b0c3-1f31af97dbe3   ext4       
/dev/sda6        29c40127-55c4-4658-a6ac-323b96745bc1   swap       
/dev/sdb1        D015-EAB2                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
search --no-floppy --fs-uuid --set f285df19-6bcb-43db-b0c3-1f31af97dbe3
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
menuentry "Ubuntu, Linux 2.6.31-9-rt" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set f285df19-6bcb-43db-b0c3-1f31af97dbe3
    linux    /boot/vmlinuz-2.6.31-9-rt root=UUID=f285df19-6bcb-43db-b0c3-1f31af97dbe3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-9-rt
}
menuentry "Ubuntu, Linux 2.6.31-9-rt (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set f285df19-6bcb-43db-b0c3-1f31af97dbe3
    linux    /boot/vmlinuz-2.6.31-9-rt root=UUID=f285df19-6bcb-43db-b0c3-1f31af97dbe3 ro single 
    initrd    /boot/initrd.img-2.6.31-9-rt
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
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set daa41c49a41c2b11
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 921c18621c18441f
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda3)" {
    insmod ntfs
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 288cd9fa8cd9c28c
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=f285df19-6bcb-43db-b0c3-1f31af97dbe3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=29c40127-55c4-4658-a6ac-323b96745bc1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 188.271835804 = 202.155344384  boot/grub/core.img                             1
 208.809174061 = 224.207143424  boot/grub/grub.cfg                             1
 208.947510242 = 224.355680768  boot/initrd.img-2.6.31-9-rt                    2
 184.268112659 = 197.856379392  boot/vmlinuz-2.6.31-9-rt                       1
 208.947510242 = 224.355680768  initrd.img                                     2
 184.268112659 = 197.856379392  vmlinuz                                        1

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

unlzma: Decoder error
boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected


```

---

### Post by coffeecat on 2011-09-09
@Mattheu, your boot script output shows that grub in the mbr is looking to sda7, but there is no sda7. This would have been your Ubuntu root partition (11.04 since you have grub 1.99 in the mbr) but you seem to have deleted it. This is why you are getting the grub error. Your Windows recovery partition is still there (sda1).

You have Ubuntu 9.10 on sda5. You could re-install grub2 to the mbr so that you could boot 9.10, but you really need a 9.10 live CD to do this. The version of grub 2 in 9.10 was 1.97~beta4 and there are some differences between that and the 1.99 used in Ubuntu 11.04, so using the 11.04 live CD may lead to problems.

If you need help with the details of re-installing grub, post back.

---

### Post by Mattheu on 2011-09-10
Right, I now have an Ubuntu 9.10 Live USB working. (Unfortunately the Ubuntu Studio releases which I have on CD don't offer live booting.)

I am using [https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2) to learn how to re-install GRUB2, but it offers five alternative methods.

Please can you advise me which would be the most straightforward method for someone like me to use?

Also, can I disable the Acer recovery procedure which I believe I must have selected accidentally via GRUB and which I believe  caused these problems (eg deleting my Ubuntu 11.04 partition) in the first place?

---

### Post by coffeecat on 2011-09-10
> **Mattheu said:**
> 
I am using [https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2) to learn how to re-install GRUB2, but it offers five alternative methods.

An embarrassment of riches! :)

I find the Copy live CD files method to be straightforward. You need sda5 and sda, thusly:

```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Your grub.cfg will give you three Windows entries. The sda2 one is the one you need for booting into Windows itself.

**EDIT**: sorry - forgot to respond to this bit:

> **Mattheu said:**
> Also, can I disable the Acer recovery procedure which I believe I must have selected accidentally via GRUB and which I believe  caused these problems (eg deleting my Ubuntu 11.04 partition) in the first place?

Your recovery partition is on sda1 and yes there is a grub entry for it. To remove that from the menu requires a bit of fiddling. You have to disable os-prober and create custom entries in the 40_custom file for Windows itself. I believe there is a GUI app which makes all this much simpler but I have no experience of it and can't advise. Perhaps someone else could.

I have an Acer laptop and I'm 99% sure that it's possible to boot into the recovery partition and exit gracefully without it doing any damage, but I can understand your caution.

---

### Post by Mattheu on 2011-09-11
Hurrah! Everything (other than the deleted partition) appears to be working again, and fortunately most of my data is in the surviving partitions.

I've decided not to disable the grub entry for the recovery partition.

Thanks Coffeecat for guiding me through this with such clarity - and the outcome has far exceeded my expectations.

As far as I'm concerned, the thread can be closed - but it was started by Roland07.

---

### Post by coffeecat on 2011-09-11
@Mattheu, I'm glad it worked for you. Good luck!

> **Mattheu said:**
> 
As far as I'm concerned, the thread can be closed - but it was started by Roland07.

The OP doesn't appear to have logged in again since the day they posted. I could close the thread but I'll leave it for now in case the OP comes back. Sometimes people do take time out from a thread and return after a couple of weeks.

---

