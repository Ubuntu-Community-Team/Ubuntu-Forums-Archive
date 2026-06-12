---
title: "Allocating Disk Spaces to Ubuntu"
date: 2010-03-08
forum: New to Ubuntu
---

### Post by lanetherif on 2010-03-08
Hi, Since I decided to migrate Ubuntu from Windows, I had to change the partition. I followed the instructions given in techotopia.com about the procedure. When finished under &quot;media&quot;, among other parts of the hard disk, I got a folder with a cross on it something like &quot;d66....8fb87&quot;. Searched the forum a bit for the error message &quot;you do not have the permission necessary to view...&quot;, though there were other people with the same people, I couldn't make use of any responses. To be honest, as you may noticed at this point, I have no idea with respect to the problem. Any help will be appreciated.  I don't know whether it will be helpful or not, here is my fstab:   # / was on /dev/sda6 during installation  UUID=7e1369c6-f843-4504-8ebe-f02cfa8a2958 /               ext4    errors=remount-ro 0       1  /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0 /dev/sda4 /vol10 ext3 defaults 0 0  Thanks in advance...

---

### Post by presence1960 on 2010-03-08
> **lanetherif said:**
> Hi, Since I decided to migrate Ubuntu from Windows, I had to change the partition. I followed the instructions given in techotopia.com about the procedure. When finished under **_&quot;media&quot;_**, among other parts of the hard disk, I got a folder with a cross on it something like **_&quot;d66....8fb87&quot;_**. Searched the forum a bit for the error message **_&quot;_**you do not have the permission necessary to view..**_.&quot;_**, though there were other people with the same people, I couldn't make use of any responses. To be honest, as you may noticed at this point, I have no idea with respect to the problem. Any help will be appreciated.  I don't know whether it will be helpful or not, here is my fstab:   # / was on /dev/sda6 during installation  UUID=7e1369c6-f843-4504-8ebe-f02cfa8a2958 /               ext4    errors=remount-ro 0       1  /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0 /dev/sda4 /vol10 ext3 defaults 0 0  Thanks in advance...

please correct the above bold, underlined text so we can have some sort of idea about exactly what your problem is. The current explanation makes no sense.

---

### Post by lanetherif on 2010-03-08
> **presence1960 said:**
> please correct the above bold, underlined text so we can have some sort of idea about exactly what your problem is. The current explanation makes no sense.

 Sure...  I used the guide provided in techotopia about allocating disk space that was formerly used in Windows to Ubuntu. I followed the instructions. What I got under /media was the UUID of the formatted and mounted part of the disk and when I try to open it, I face with the error message that tells me that I don't have the permission necessary to view the contents of the disk. Besides being new to Ubuntu, I am also not used to post in forums and couldn't think that the quote sign would be shown like this.

---

### Post by presence1960 on 2010-03-08
> **lanetherif said:**
> Sure...  I used the guide provided in techotopia about allocating disk space that was formerly used in Windows to Ubuntu. I followed the instructions. What I got under /media was the UUID of the formatted and mounted part of the disk and when I try to open it, I face with the error message that tells me that I don't have the permission necessary to view the contents of the disk. Besides being new to Ubuntu, I am also not used to post in forums and couldn't think that the quote sign would be shown like this.

No harm done, just couldn't figure what you are saying. Can you post a link to that guide so we can see exactly the steps you followed. Also if you can do this so we can see exactly your setup & boot process:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

### Post by lanetherif on 2010-03-08
> **presence1960 said:**
> No harm done, just couldn't figure what you are saying. Can you post a link to that guide so we can see exactly the steps you followed. Also if you can do this so we can see exactly your setup & boot process:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose &quot;try ubuntu without any changes&quot;, when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

 [http://www.techotopia.com/index.php/Allocating_a_Windows_Partition_to_Ubuntu_Linux#Editing_the_Boot_Menu](http://www.techotopia.com/index.php/Allocating_a_Windows_Partition_to_Ubuntu_Linux#Editing_the_Boot_Menu)  This the page used. Unfortunately, I have neither the cd - a friend of mine has borrowed -, nor usb.

---

### Post by lanetherif on 2010-03-08
Still, I restarted PC in a regular way and this is the text file generated: >                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => No boot loader? is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 225. But according to the info from fdisk, 
                       sda5 starts at sector 353157120.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x641354fd

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   260,134,911   259,928,064   7 HPFS/NTFS
/dev/sda3         260,140,545   512,120,069   251,979,525   f W95 Ext d (LBA)
/dev/sda5         353,157,120   512,118,783   158,961,664   7 HPFS/NTFS
/dev/sda6         260,140,671   353,156,894    93,016,224  83 Linux
/dev/sda4         512,120,070   976,768,064   464,647,995  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000 MB, 1000341504 bytes
16 heads, 32 sectors/track, 3816 cylinders, total 1953792 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x05452135

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32     1,953,791     1,953,760   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        DE4AA4E94AA4C01F                       ntfs       System Reserved               
/dev/sda2        6474865074862540                       ntfs       Ce                            
/dev/sda4        c9936920-2c8a-44da-aec5-a0e24b847b34   ext3       Yer1                          
/dev/sda5        9498E4AE98E48FD2                       ntfs       De                            
/dev/sda6        7e1369c6-f843-4504-8ebe-f02cfa8a2958   ext4                                     
/dev/sdb1        8076BE9C76BE9280                       ntfs       SEED-ReadyBoost               

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/SEED-ReadyBoost   fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda2        /media/Ce                fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda5        /media/De                fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda1        /media/System Reserved   fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda4        /vol10                   ext3       (rw)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root=(hd0,6)
search --no-floppy --fs-uuid --set 7e1369c6-f843-4504-8ebe-f02cfa8a2958
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
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 7e1369c6-f843-4504-8ebe-f02cfa8a2958
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=7e1369c6-f843-4504-8ebe-f02cfa8a2958 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 7e1369c6-f843-4504-8ebe-f02cfa8a2958
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=7e1369c6-f843-4504-8ebe-f02cfa8a2958 ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 7e1369c6-f843-4504-8ebe-f02cfa8a2958
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=7e1369c6-f843-4504-8ebe-f02cfa8a2958 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 7e1369c6-f843-4504-8ebe-f02cfa8a2958
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=7e1369c6-f843-4504-8ebe-f02cfa8a2958 ro single 
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 7e1369c6-f843-4504-8ebe-f02cfa8a2958
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=7e1369c6-f843-4504-8ebe-f02cfa8a2958 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 7e1369c6-f843-4504-8ebe-f02cfa8a2958
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=7e1369c6-f843-4504-8ebe-f02cfa8a2958 ro single 
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
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set de4aa4e94aa4c01f
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=7e1369c6-f843-4504-8ebe-f02cfa8a2958 /               ext4    errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda4 /vol10 ext3 defaults 0 0


=================== sda6: Location of files loaded by Grub: ===================


 134.7GB: boot/grub/core.img
 138.7GB: boot/grub/grub.cfg
 133.8GB: boot/initrd.img-2.6.31-14-generic
 134.5GB: boot/initrd.img-2.6.31-19-generic
 138.5GB: boot/initrd.img-2.6.31-20-generic
 133.7GB: boot/vmlinuz-2.6.31-14-generic
 133.8GB: boot/vmlinuz-2.6.31-19-generic
 134.7GB: boot/vmlinuz-2.6.31-20-generic
 138.5GB: initrd.img
 134.5GB: initrd.img.old
 134.7GB: vmlinuz
 133.8GB: vmlinuz.old

---

### Post by lanetherif on 2010-03-09
Any idea?

---

### Post by presence1960 on 2010-03-09
> **lanetherif said:**
> Any idea?

OK, your boot info script looks good. Are you able to boot into Ubuntu? Are you able to boot into windows 7? Just what is the problem you are encountering & what are you trying to do when you encounter the problem?

P.S. I looked at that link you gave and those instructions are for deleting windows from a dual boot setup. You still have windows on your machine.

---

### Post by audiomick on 2010-03-09
@presence

```
sda5: __________________________________________________  _______________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    [COLOR=Red]Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 225. But according to the info from fdisk, 
                       sda5 starts at sector 353157120.[/COLOR]
    Operating System:  
    Boot files/dirs:   

```is this not a bit odd?

---

### Post by presence1960 on 2010-03-09
> **audiomick said:**
> @presence

```
sda5: __________________________________________________  _______________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    [COLOR=Red]Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 225. But according to the info from fdisk, 
                       sda5 starts at sector 353157120.[/COLOR]
    Operating System:  
    Boot files/dirs:   

```is this not a bit odd?

Yes it is. But I am trying to figure out what the OP is trying to do when he encounters the problem and just what is the problem. Obviously the OP can boot into Ubuntu., should be able to boot to windows 7. The expalanation the OP gave of the problem is rather vague to me- I can't ascertain exactly what the OP is trying to do. The guide the OP posted a link to that the OP says was followed is for removing windows from a dual boot setup. The OP still has windows 7 which further adds to the confusion. I just want a simple explanation of what exactly the OP is trying to do when the error is encountered.

If the Op wants to delete windows there is a better way to do than that guide.

---

### Post by audiomick on 2010-03-09
> **presence1960 said:**
> Yes it is. But...I just want a simple explanation of what exactly the OP is trying to do when the error is encountered.
Yes, fair enough too. I am not exactly sure what the OP was up to either.

---

### Post by lanetherif on 2010-03-09
> **presence1960 said:**
> OK, your boot info script looks good. Are you able to boot into Ubuntu? Are you able to boot into windows 7? Just what is the problem you are encountering & what are you trying to do when you encounter the problem?

P.S. I looked at that link you gave and those instructions are for deleting windows from a dual boot setup. You still have windows on your machine.

Besides the Linux partition, I had 3 other, one for windows system files and two for documents. What I was planning to do was to change the disk parts to linux part by part in order that no data would be loss. So, I still have the partition that windows uses since there are files that I don't want to lose on it. 
At the moment, when I use gparted I can see the partition /dev/sda4 at mount point /vol10 with label Yer1. However, under media it won't show up.

---

### Post by lanetherif on 2010-03-09
By the way, I have re-downloaded Ubuntu iso, so I can just re-install it, if it will solve my problem.

---

### Post by mechro on 2010-03-09
So you want to use /vol10 as some sort of data partition??

As far as I can see it needs mounting to /media/vol10 in your etc/fstab file on sda6.

---

### Post by lanetherif on 2010-03-09
> **mechro said:**
> So you want to use /vol10 as some sort of data partition??

As far as I can see it needs mounting to /media/vol10 in your etc/fstab file on sda6.

Thanks, I did it as you said. Now it is visible. Yet, I still can't copy anything on it. Error message reads :> There was an error copying file into /media/UUID of the partition/filename Error opening file ... : Permission denied 
What should I do now?

---

### Post by cgroza on 2010-03-09
if your partition is ntfs , then install ntfs-config and run it from the menu.
To install it just run "  sudo apt-get install ntfs-config  " and then run it from the menu... 
After you open it , enable write-read support and click ok...
Hope that helps :D

---

### Post by mechro on 2010-03-09
It's possibly the options you're mounting it with.

Here is my fstab entry(amended to suit you) for a data partition...

```
/dev/sda4  /media/vol10   ext3   relatime    0    2
```

See if that works.

---

### Post by audiomick on 2010-03-09
One way, perhaps not the best, which should work is start the file manager using
```
gksu nautilus
```from the terminal. This will give you a file manager with root privileges. You will very likely get some error messages as it starts, but that is "normal".

In the file manager you have opened, navigate to /media, right click on the entry for the partition, choose preferences and see if you can change the owner to you instead of root.

This can also be done with the command "chown", probably need a "sudo" in front of it, but I am not sure of the right syntax. You can look it up using
```
man chown
```

edit: try mechro's suggestion first.

---

### Post by lanetherif on 2010-03-09
> **audiomick said:**
> One way, perhaps not the best, which should work is start the file manager using
```
gksu nautilus
```from the terminal. This will give you a file manager with root privileges. You will very likely get some error messages as it starts, but that is "normal".

In the file manager you have opened, navigate to /media, right click on the entry for the partition, choose preferences and see if you can change the owner to you instead of root.

This can also be done with the command "chown", probably need a "sudo" in front of it, but I am not sure of the right syntax. You can look it up using
```
man chown
```edit: try mechro's suggestion first.

I tried both. First mechro's suggestion which didn't work. Then yours, at first it worked and I was able to copy a file to there. Then, I restarted the computer. At the moment, I am able to see it in places but with a error message that tells me that only root can mount /dev/sda4 on /media/vol10. Moreover, the partition doesn't show up in nautilus. By the way, at the time being my fstab is like mechro advised it to be. 

It is like -if it was possible- things are taking place at random. :D

I also tried using chown command. I tried chown seed /dev/sda4 then chown -R seed:seed then chown -R seed (I saw the last two last night while searching for a solution) all ended up with message operation not permitted. I tried them after using su seed.

---

### Post by audiomick on 2010-03-09
Ok, it still looks like the partition is getting mounted as being owned by root, which is what both mechro's and my suggestions were aimed at changing. :confused:

I am afraid you will have to wait a bit to see if someone else has an idea. I haven't actually had the problem directly, so any further suggestion I make would be wild guesses at this point. sorry...

---

### Post by mechro on 2010-03-09
> **lanetherif said:**
> 
It is like -if it was possible- things are taking place at random. :D

I also tried using chown command. I tried chown seed /dev/sda4 then chown -R seed:seed then chown -R seed (I saw the last two last night while searching for a solution) all ended up with message operation not permitted. I tried them after using su seed.

Sheesh! I think the randomness may have something to do with chucking random commands at the problem :D

I don't think you can chown a device (/dev/sda4), it has to be a file/directory.

Try this...

```
sudo chown -R yourusername /media/vol10
```

---

### Post by lanetherif on 2010-03-09
> **mechro said:**
> Sheesh! I think the randomness may have something to do with chucking random commands at the problem :D

I don't think you can chown a device (/dev/sda4), it has to be a file/directory.

Try this...

```
sudo chown -R yourusername /media/vol10
```

Thank you. :)
 I, before seeing this post, was tinkering with it a bit with motivation stemming only from my complete ignorance (after all at any point I could delete the lines from fstab and delete the partition by gparted :P) and somehow I was able to both see it and copy files in it. I was about to write about this. Is there a possibility at the moment that will cause me to lose it again?
In gparted it is shown as /dev/sda4, and mount point is blank. In fstab, it is written /dev/sda3 media/vol10 ext3 realtime 0 2 . Also I did what you said.


And this the result of the script presence1960 provided run in live cd:
>                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => No boot loader? is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 225. But according to the info from fdisk, 
                       sda5 starts at sector 353157120.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x641354fd

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   260,134,911   259,928,064   7 HPFS/NTFS
/dev/sda3         260,140,545   512,120,069   251,979,525   f W95 Ext d (LBA)
/dev/sda5         353,157,120   512,118,783   158,961,664   7 HPFS/NTFS
/dev/sda6         260,140,671   353,156,894    93,016,224  83 Linux
/dev/sda4         512,120,070   976,768,064   464,647,995  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000 MB, 1000341504 bytes
16 heads, 32 sectors/track, 3816 cylinders, total 1953792 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x05452135

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32     1,953,791     1,953,760   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        DE4AA4E94AA4C01F                       ntfs       System Reserved               
/dev/sda2        6474865074862540                       ntfs       Ce                            
/dev/sda4        a6ba8898-12c0-42c8-aff4-61efbee10bac   ext3                                     
/dev/sda5        9498E4AE98E48FD2                       ntfs       De                            
/dev/sda6        7e1369c6-f843-4504-8ebe-f02cfa8a2958   ext4                                     
/dev/sdb1        8076BE9C76BE9280                       ntfs       SEED-ReadyBoost               

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda4        /media/a6ba8898-12c0-42c8-aff4-61efbee10bac ext3       (rw,nosuid,nodev,uhelper=devkit)
/dev/sda2        /media/Ce                fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root=(hd0,6)
search --no-floppy --fs-uuid --set 7e1369c6-f843-4504-8ebe-f02cfa8a2958
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
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 7e1369c6-f843-4504-8ebe-f02cfa8a2958
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=7e1369c6-f843-4504-8ebe-f02cfa8a2958 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 7e1369c6-f843-4504-8ebe-f02cfa8a2958
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=7e1369c6-f843-4504-8ebe-f02cfa8a2958 ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 7e1369c6-f843-4504-8ebe-f02cfa8a2958
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=7e1369c6-f843-4504-8ebe-f02cfa8a2958 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 7e1369c6-f843-4504-8ebe-f02cfa8a2958
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=7e1369c6-f843-4504-8ebe-f02cfa8a2958 ro single 
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 7e1369c6-f843-4504-8ebe-f02cfa8a2958
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=7e1369c6-f843-4504-8ebe-f02cfa8a2958 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 7e1369c6-f843-4504-8ebe-f02cfa8a2958
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=7e1369c6-f843-4504-8ebe-f02cfa8a2958 ro single 
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
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set de4aa4e94aa4c01f
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=7e1369c6-f843-4504-8ebe-f02cfa8a2958 /               ext4    errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda4  media/vol10 ext3 realtime 0 2


=================== sda6: Location of files loaded by Grub: ===================


 134.7GB: boot/grub/core.img
 138.7GB: boot/grub/grub.cfg
 133.8GB: boot/initrd.img-2.6.31-14-generic
 134.5GB: boot/initrd.img-2.6.31-19-generic
 138.5GB: boot/initrd.img-2.6.31-20-generic
 133.7GB: boot/vmlinuz-2.6.31-14-generic
 133.8GB: boot/vmlinuz-2.6.31-19-generic
 134.7GB: boot/vmlinuz-2.6.31-20-generic
 138.5GB: initrd.img
 134.5GB: initrd.img.old
 134.7GB: vmlinuz
 133.8GB: vmlinuz.old

Last state: My supposedly working vol10 turned out to be a part of the main ubuntu partition which has a capacity of 40gb, I understood it when I started to copy files to there. :D However, I, by luck, have been able to both create the correct partition and been able to grant permissions to myself. In a sense, my problem is solved. In fact, if it isn't, it will end with loss of my whole data. :) So, I don't think that I will be here to ask for more advices, if it is the case. 
Thanks for everybody for their help and advices.

---

### Post by mechro on 2010-03-09
[QUOTE=]In gparted it is shown as /dev/sda4, and mount point is blank. In fstab, it is written /dev/sda3 media/vol10 ext3 realtime 0 2[/QUOTE]

From gparted /dev/sda4's mount point will vary depending on whether you are running gparted from a Ubuntu LiveCD, from any other LiveCD, from your Ubuntu installation, or before and after editing your fstab in sda6.

According to the *boot info script* fstab doesn't say "/dev/sda3 media/vol10 ext3 realtime 0 2", it says "/dev/sda4 media/vol10 ext3 realtime 0 2"

I'm now at a similar position as other posters in this thread... what is the problem?

---

### Post by lanetherif on 2010-03-09
> **mechro said:**
> From gparted /dev/sda4's mount point will vary depending on whether you are running gparted from a Ubuntu LiveCD, from any other LiveCD, from your Ubuntu installation, or before and after editing your fstab in sda6.

According to the *boot info script* fstab doesn't say "/dev/sda3 media/vol10 ext3 realtime 0 2", it says "/dev/sda4 media/vol10 ext3 realtime 0 2"

I'm now at a similar position as other posters in this thread... what is the problem?

Sorry... :) I am in a sense illiterate in explaining the situation. I will retell my story. There were 4 partitions at the very beginning. C,D,E and the one that runs Ubuntu. E being the largest was where I put most of the documents. When I decided to quit Windows totally, I relocated the data in other two partitions. Then through Ubuntu, I formatted it. At first, the reason I wrote at forum was that the newly formatted partition was shown with its UUID and was inaccessible. Later on after deleting and allocating the partition with the hints I have taken from your answers, I have been able to use it. At this moment, it is visible under places as vol7 (I have changed the volume number) and visible under media (Let it be a proof of my ignorance, I am not sure that even the first part of my sentence entails this second part and unnecessary). When the file transfer from other windows partitions to this newly created vol7 finished, I have to start over the procedure for those two other. 
I have no idea how come I have been able to do it, except running the nautilus and this is a problem. Also, I am not sure if it is meant to be, but the label I have assigned it doesn't show up in places although it is written in gparted. This the last shape of my gparted and fstab: 
> dev/sda4    ext3       /media/vol7             yeni1

> /dev/sda4 media/vol7 ext4 defaults 0 0

I just now figured out that one is ext3 and the other ext4... It is working at the moment should I change it? :D

---

### Post by mechro on 2010-03-09
> =============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# / was on /dev/sda6 during installation
UUID=7e1369c6-f843-4504-8ebe-f02cfa8a2958 / ext4 errors=remount-ro 0 1
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
**/dev/sda4 media/vol10 ext3 realtime 0 2**

That last line should read...

/dev/sda4 /media/vol10 ext3 realtime 0 2

---

### Post by lanetherif on 2010-03-10
> **mechro said:**
> That last line should read...

/dev/sda4 /media/vol10 ext3 realtime 0 2

When I became sure that my files on sd4 won't be lost, I decided to  delete the other partitions including the Ubuntu and to install it  again. A fresh start... :) I chose /home as mount point for sda4 in  installation screen. I don't know whether it is the best choice, but it  is working fine at the moment. 
Thank you for your concern and useful tips. :)

---

### Post by mechro on 2010-03-10
> **lanetherif said:**
> When I became sure that my files on sd4 won't be lost, I decided to  delete the other partitions including the Ubuntu and to install it  again. A fresh start... :) I chose /home as mount point for sda4 in  installation screen. I don't know whether it is the best choice, but it  is working fine at the moment. 
Thank you for your concern and useful tips. :)

That should be fine. On the installation screen you could have chosen to mount sda4 on /media/somename and the correct entries would have been entered in the fstab file.

---

