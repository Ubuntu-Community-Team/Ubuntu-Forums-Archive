---
title: "Dual Boot XP &amp; 9.10"
date: 2010-02-16
forum: New to Ubuntu
---

### Post by Shugs81 on 2010-02-16
I've got 2 sata drives and and IDE drive in my pc.

XP and Ubuntu are on the IDE drive but it comes up as D: in windows... I've installed 9.10 hoping to dual boot but it boots straight into windows...

how would I go about sorting this out? is there a way i can t the jumpers to different drives so that it shows as c:? i can't remember how to do it!!

---

### Post by spiky001 on 2010-02-16
did you load ubuntu by booting off cd?  or instal it from within windows (wubi) install

---

### Post by Tayashlor on 2010-02-16
I currently have a netbook that is dual booted with windows 7 and ubuntu 9.04. In order to get mine to load correctly I had to make two seperate partitions and install each OS seperatly. When I turn on my computer, about half way through a list comes up and i have to choose between ubuntu and windows, and if you dont press anything it loads to ubuntu. I believe that i Installed windows first and used the windows partition to make one, and when i went to instal Ubuntu i just filled in the extra space. 

I hope this helps.

If you have some troubles I might be able to help. Just email me [email]tayashlor@gmail.com[/email]

---

### Post by michaert on 2010-02-16
It is MUCH easier if you install Windows first, then Ubuntu. That way, Ubuntu recognizes the Windows boot record, and GRUB overwrites Windows Bootloader. In my experience, Installing Windows is the better option. Less headache, and less chances to mess up! ;)

---

### Post by Miljet on 2010-02-16
Right now everyone is just guessing at what your problem is. You can help others help you by giving better information about the problems you are experiencing. 
> XP and Ubuntu are on the IDE drive but it comes up as D: in windows
For example, I have no idea what this means.

> I've got 2 sata drives and and IDE drive in my pc.
What is on the 2 sata drives? Which drive is set to boot first? Did you install Ubuntu inside Windows using Wubi, or did you install it on a separate partition beside XP?

It would be helpful to boot a live CD, open a terminal(Applications -> Accessories -> Terminal), and post the output of:
```
sudo fdisk -l
```
That is a small L, not a one.

---

### Post by bowbalitic on 2010-02-16
Ok, so I'm going to assume you installed ubuntu first (reason for windows drive letter d and unable to boot linux) Windows is a rather rude operating system when it comes to installation. It rewrites the MBR (Master Boot Record, the thing that starts up your operating systems) 

Assuming I'm right, the easiest method will be starting from scratch, backing up all your important data, reformatting your hard drive, and installing windows first. I know it sounds like a pain, but its truly the easiest way. (believe me, 6 hours later and after lines of code and lists of files your going to wish you just reinstalled) Also, assuming that windows was installed on drive D its really the *only* way (again, more code, files, except now you have to deal with that nasty registry) 

Ok, now for directions. Insert and boot to your windows install cd. Manually configure the partitions, ERASE EVERYTHING. Then create a NTFS (filesystem of Windows) partition for your windows, leaving room for your Ubuntu partitions (roughly 20 gb). Make sure that windows is refering to the partition as C. Then install windows as normal. 

AFTER windows is installed, insert and boot to your Ubuntu live cd, run the installer. At the partitions editor, select the option that installs ubuntu onto the empty space after windows. 


I know its alot of info, but hope it helps. If you enjoy learning how things work and improving them you'll love linux.

EDIT.
I forgot to mention, but Miljet reminded me. 

Check your bios boot settings. Type F12, Del, or what ever your bios says when you first boot. Then go to the boot menu, there should be a option like Boot Priority, or Boot Setup, something that lets you change which drive your bios boots to. Also, what are your SATA drives in there for?? You know there much faster than an IDE drive right?? So if your using windows for gaming, you should have windows on one of those anyway.

---

### Post by Shugs81 on 2010-02-17
I've got a 1tb sata drive, a 160gb sata drive and a 250gb IDE drive... was planning to have the IDE drive for the os' only and have all games etc on the sata drives... but saying that.... given how cheap sata drives are i may just buy another one and be done with it!!

I installed windows first but i think the boot record is on the sata drive therefor ubuntu hasn't picked it up.... the more i think about it the more i need to get a second sata drive... the only reason for this is cause i couldn't dual boot with windows 7 and destroyed the boot record...

shopping time!!

---

### Post by bowbalitic on 2010-02-17
Also, I tried that setup (games on seperate drives) and it did NOT work out so well...

I know it sounds wierd, but games didn't install properly, they were slow, I had to replace files in the game, and other stuff. First let me note I'm not really an experienced windows user, I can manipulate the registry a little but thats it. 

Just to give you an example on performance difference
Call of duty 4 on C drive 
125 fps 50 ping
on D drive (separate drive)
100fps with lags of 30, 94 ping 
I know these aren't really technical specs but they let you know that it isn't working properly. Also, these are in game only, not system wide. 

I simply plugged in a ntfs partitioned drive and installed the games. I didn't alter the registry, or tweak any settings. So I don't know if you'll have the same problem. 

Just giving a heads up, good luck.

---

### Post by presence1960 on 2010-02-17
> **Shugs81 said:**
> I've got 2 sata drives and and IDE drive in my pc.

XP and Ubuntu are on the IDE drive but it comes up as D: in windows... I've installed 9.10 hoping to dual boot but it boots straight into windows...

how would I go about sorting this out? is there a way i can t the jumpers to different drives so that it shows as c:? i can't remember how to do it!!
We need to see exactly what you have on that machine as far as setup & boot process goes. 

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

### Post by Shugs81 on 2010-02-19
reet... bought a 1.5tb hd.... finally managed to get ubuntu and windows xp on the same drive which is calssed as C through windows... that took some effort mind!!

Now when it boots, after prompting that it's checking CD drives it just says GRUB and freezes.... is there a way to repair this using the live CD?? only just d/lded the live 9.10 cd so should be as up to date as possible...

---

### Post by kansasnoob on 2010-02-19
> **Shugs81 said:**
> reet... bought a 1.5tb hd.... finally managed to get ubuntu and windows xp on the same drive which is calssed as C through windows... that took some effort mind!!

Now when it boots, after prompting that it's checking CD drives it just says GRUB and freezes.... is there a way to repair this using the live CD?? only just d/lded the live 9.10 cd so should be as up to date as possible...

Post the output of the Boot Info Script as Presence1960 asked. Without it all we can do is guess.

---

### Post by Shugs81 on 2010-02-19
Reet... Will see what I can do...

---

### Post by Shugs81 on 2010-02-19
Reet.... Did boot script as told...

Sda = ntfs 1003gb - empty

Sdb1 = boot ntfs 150gb windows
Sdb2 = swap 1gb 
Sdb3 = ext4 mounted as root

Sdc = ntfs 1.5tb with 180gb of stuff I need to keep...

All went tits up... Unplugged Sdc so it can't be c: and starting again with 2 blank sata drives... Bah.... Sure it wasn't this much trouble last time... Was planning on putting ubuntu studio on too... 

Having to use phone hence no code box...

Joy!

Wish me luck!

---

### Post by Shugs81 on 2010-02-19
joy of effing joys...............

It won't create a windows partition now....

---

### Post by presence1960 on 2010-02-19
> **Shugs81 said:**
> Reet.... Did boot script as told...

Sda = ntfs 1003gb - empty

Sdb1 = boot ntfs 150gb windows
Sdb2 = swap 1gb 
Sdb3 = ext4 mounted as root

Sdc = ntfs 1.5tb with 180gb of stuff I need to keep...

All went tits up... Unplugged Sdc so it can't be c: and starting again with 2 blank sata drives... Bah.... Sure it wasn't this much trouble last time... Was planning on putting ubuntu studio on too... 

Having to use phone hence no code box...

Joy!

Wish me luck!

post the entire output from the file RESULTS.txt generated by the boot info script. What you have is not from the boot info script. here is mine so you can see what it looks like:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => Lilo is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 8 Helena - x64 
                       Edition
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda8 and 
                       looks at sector 144229473 on boot drive #1 for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #8 for 
                       /boot/grub/grub.conf.
    Operating System:   This is .()
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

sda9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7408b4a2

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   341,590,094   341,590,032   5 Extended
/dev/sda5                 126    62,910,539    62,910,414  83 Linux
/dev/sda6          62,910,603   125,821,079    62,910,477  83 Linux
/dev/sda7         125,821,143   134,207,009     8,385,867  82 Linux swap / Solaris
/dev/sda8         134,207,073   197,117,549    62,910,477  83 Linux
/dev/sda9         197,117,613   341,590,094   144,472,482   7 HPFS/NTFS
/dev/sda2    *    341,590,095   488,392,064   146,801,970   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x05f07bc0

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   976,768,064   976,768,002  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00009028

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 1,048,578,614 1,048,578,552  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/ramzswap0                                          swap                                     
/dev/sda2        0452923552922C04                       ntfs       vista                         
/dev/sda5        101653d6-6dc9-4c4f-8487-eee283357676   ext4       mint                          
/dev/sda6        e0b415e6-168b-49e7-b62b-0fc42c83a6d7   ext4       karmic                        
/dev/sda7        ec55c54f-caf2-4db5-8f51-f8e5e8629afb   swap                                     
/dev/sda8        47148038-df04-4a25-8a6b-5772d535c8de   ext4       sabayon                       
/dev/sda9        085FE7B3200BEC9A                       ntfs       win-data                      
/dev/sdb1        bd4ff60f-606d-43ac-81f2-6713bed14313   ext4       backup                        
/dev/sdc1        a9ce88a4-7a81-492e-958c-75ed13b54e0a   ext4       data                          

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)
/dev/sdc1        /media/data              ext4       (rw,nosuid,nodev,uhelper=devkit)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set 101653d6-6dc9-4c4f-8487-eee283357676
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

### BEGIN /etc/grub.d/06_mint_theme ###
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set 101653d6-6dc9-4c4f-8487-eee283357676
insmod png
if background_image /boot/grub/linuxmint.png ; then
  set color_normal=white/black
  set color_highlight=white/light-gray
else
  set menu_color_normal=white/black
  set menu_color_highlight=white/light-gray
fi
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Linux Mint 8 Helena x64, linux 2.6.31-19-generic (/dev/sda5)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 101653d6-6dc9-4c4f-8487-eee283357676
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=101653d6-6dc9-4c4f-8487-eee283357676 ro  splash  quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Linux Mint 8 Helena x64, linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 101653d6-6dc9-4c4f-8487-eee283357676
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=101653d6-6dc9-4c4f-8487-eee283357676 ro single  splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Linux Mint 8 Helena x64, linux 2.6.31-17-generic (/dev/sda5)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 101653d6-6dc9-4c4f-8487-eee283357676
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=101653d6-6dc9-4c4f-8487-eee283357676 ro  splash  quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Linux Mint 8 Helena x64, linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 101653d6-6dc9-4c4f-8487-eee283357676
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=101653d6-6dc9-4c4f-8487-eee283357676 ro single  splash
	initrd	/boot/initrd.img-2.6.31-17-generic
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
menuentry "Windows Vista (loader) (on /dev/sda2)" {
	insmod ntfs
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 0452923552922c04
	chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux /boot/vmlinuz-2.6.31-19-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro splash quiet quiet splash
	initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode) (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux /boot/vmlinuz-2.6.31-19-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro single splash quiet
	initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-18-generic (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux /boot/vmlinuz-2.6.31-18-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro splash quiet quiet splash
	initrd /boot/initrd.img-2.6.31-18-generic
}
menuentry "Ubuntu, Linux 2.6.31-18-generic (recovery mode) (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux /boot/vmlinuz-2.6.31-18-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro single splash quiet
	initrd /boot/initrd.img-2.6.31-18-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
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
UUID=101653d6-6dc9-4c4f-8487-eee283357676 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=ec55c54f-caf2-4db5-8f51-f8e5e8629afb none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


   3.8GB: boot/grub/core.img
   1.9GB: boot/grub/grub.cfg
   6.4GB: boot/initrd.img-2.6.31-17-generic
   1.9GB: boot/initrd.img-2.6.31-19-generic
   1.0GB: boot/vmlinuz-2.6.31-17-generic
    .6GB: boot/vmlinuz-2.6.31-19-generic
   1.9GB: initrd.img
   6.4GB: initrd.img.old
    .6GB: vmlinuz
   1.0GB: vmlinuz.old

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
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro splash quiet  quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,6)
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro single splash quiet
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,6)
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro splash quiet  quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,6)
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro single splash quiet
	initrd	/boot/initrd.img-2.6.31-19-generic
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
menuentry "Windows Vista (loader) (on /dev/sda2)" {
	insmod ntfs
	set root=(hd0,2)
	chainloader +1
}
menuentry "Linux Mint 8 Helena x64, linux 2.6.31-19-generic (/dev/sda5) (on /dev/sda5)" {
	insmod ext2
	set root=(hd0,5)
	linux /boot/vmlinuz-2.6.31-19-generic root=UUID=101653d6-6dc9-4c4f-8487-eee283357676 ro splash quiet splash
	initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Linux Mint 8 Helena x64, linux 2.6.31-19-generic (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root=(hd0,5)
	linux /boot/vmlinuz-2.6.31-19-generic root=UUID=101653d6-6dc9-4c4f-8487-eee283357676 ro single splash
	initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Linux Mint 8 Helena x64, linux 2.6.31-17-generic (/dev/sda5) (on /dev/sda5)" {
	insmod ext2
	set root=(hd0,5)
	linux /boot/vmlinuz-2.6.31-17-generic root=UUID=101653d6-6dc9-4c4f-8487-eee283357676 ro splash quiet splash
	initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Linux Mint 8 Helena x64, linux 2.6.31-17-generic (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root=(hd0,5)
	linux /boot/vmlinuz-2.6.31-17-generic root=UUID=101653d6-6dc9-4c4f-8487-eee283357676 ro single splash
	initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Sabayon Linux x86-64 (genkernel-x86_64-2.6.29-sabayon) (on /dev/sda8)" {
	insmod ext2
	set root=(hd0,8)
	linux /boot/kernel-genkernel-x86_64-2.6.29-sabayon root=/dev/ram0 ramdisk=8192 real_root=UUID=47148038-df04-4a25-8a6b-5772d535c8de dolvm init=/linuxrc splash=silent,theme:sabayon vga=791 CONSOLE=/dev/tty1 quiet resume=swap:/dev/sda7
	initrd /boot/initramfs-genkernel-x86_64-2.6.29-sabayon
}
menuentry "Sabayon Linux x86-64 (genkernel-x86_64-2.6.29-sabayon) (safe mode) (on /dev/sda8)" {
	insmod ext2
	set root=(hd0,8)
	linux /boot/kernel-genkernel-x86_64-2.6.29-sabayon root=/dev/ram0 ramdisk=8192 real_root=UUID=47148038-df04-4a25-8a6b-5772d535c8de dolvm init=/linuxrc CONSOLE=/dev/tty1 resume=swap:/dev/sda7 nox acpi=off ide=nodma vga=normal
	initrd /boot/initramfs-genkernel-x86_64-2.6.29-sabayon
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
UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ec55c54f-caf2-4db5-8f51-f8e5e8629afb none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


  37.0GB: boot/grub/core.img
  36.7GB: boot/grub/grub.cfg
  45.1GB: boot/initrd.img-2.6.31-19-generic
  39.5GB: boot/initrd.img-2.6.31-20-generic
  40.4GB: boot/vmlinuz-2.6.31-19-generic
  37.0GB: boot/vmlinuz-2.6.31-20-generic
  39.5GB: initrd.img
  45.1GB: initrd.img.old
  37.0GB: vmlinuz
  40.4GB: vmlinuz.old

========================== sda8/boot/grub/grub.conf: ==========================

# grub.conf generated by the Sabayon Linux Installer
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd0,7)
#          kernel /boot/kernel-genkernel real_root=UUID=47148038-df04-4a25-8a6b-5772d535c8de
#          initrd /boot/initramfs-genkernel
#boot=sda8
default=0
timeout=5
splashimage=(hd0,7)/boot/grub/splash.xpm.gz

title Sabayon Linux x86-64 (genkernel-x86_64-2.6.29-sabayon)
	root (hd0,7)
	kernel /boot/kernel-genkernel-x86_64-2.6.29-sabayon  root=/dev/ram0 ramdisk=8192 real_root=UUID=47148038-df04-4a25-8a6b-5772d535c8de dolvm init=/linuxrc splash=silent,theme:sabayon vga=791 CONSOLE=/dev/tty1 quiet resume=swap:/dev/sda7
	initrd /boot/initramfs-genkernel-x86_64-2.6.29-sabayon
	savedefault

title Sabayon Linux x86-64 (genkernel-x86_64-2.6.29-sabayon) (safe mode)
	root (hd0,7)
	kernel /boot/kernel-genkernel-x86_64-2.6.29-sabayon root=/dev/ram0 ramdisk=8192 real_root=UUID=47148038-df04-4a25-8a6b-5772d535c8de dolvm init=/linuxrc CONSOLE=/dev/tty1 resume=swap:/dev/sda7 nox acpi=off ide=nodma vga=normal
	initrd /boot/initramfs-genkernel-x86_64-2.6.29-sabayon
	savedefault

title Other Operating System - Microsoft Windows
	rootnoverify (hd0,1)
	chainloader +1
	savedefault

=============================== sda8/etc/fstab: ===============================

UUID=47148038-df04-4a25-8a6b-5772d535c8de /                       ext4    user_xattr,noatime 1 1
/dev/shm                /dev/shm                tmpfs   defaults        0 0
UUID=ec55c54f-caf2-4db5-8f51-f8e5e8629afb swap                    swap    defaults        0 0

=================== sda8: Location of files loaded by Grub: ===================


  71.8GB: boot/grub/grub.conf
  71.8GB: boot/grub/menu.lst
  73.8GB: boot/grub/stage2
  78.7GB: boot/initramfs-genkernel-x86_64-2.6.29-sabayon
=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg 
```

I don't know what you ran to get the output you posted but that is not what we requested. Please run the script & post the entire contents of the RESULTS.txt file generated by the script.

---

### Post by theozzlives on 2010-02-19
> **bowbalitic said:**
> Ok, so I'm going to assume you installed ubuntu first (reason for windows drive letter d and unable to boot linux) Windows is a rather rude operating system when it comes to installation. It rewrites the MBR (Master Boot Record, the thing that starts up your operating systems) 

Assuming I'm right, the easiest method will be starting from scratch, backing up all your important data, reformatting your hard drive, and installing windows first. I know it sounds like a pain, but its truly the easiest way. (believe me, 6 hours later and after lines of code and lists of files your going to wish you just reinstalled) Also, assuming that windows was installed on drive D its really the *only* way (again, more code, files, except now you have to deal with that nasty registry) 

Ok, now for directions. Insert and boot to your windows install cd. Manually configure the partitions, ERASE EVERYTHING. Then create a NTFS (filesystem of Windows) partition for your windows, leaving room for your Ubuntu partitions (roughly 20 gb). Make sure that windows is refering to the partition as C. Then install windows as normal. 

AFTER windows is installed, insert and boot to your Ubuntu live cd, run the installer. At the partitions editor, select the option that installs ubuntu onto the empty space after windows. 


I know its alot of info, but hope it helps. If you enjoy learning how things work and improving them you'll love linux.

EDIT.
I forgot to mention, but Miljet reminded me. 

Check your bios boot settings. Type F12, Del, or what ever your bios says when you first boot. Then go to the boot menu, there should be a option like Boot Priority, or Boot Setup, something that lets you change which drive your bios boots to. Also, what are your SATA drives in there for?? You know there much faster than an IDE drive right?? So if your using windows for gaming, you should have windows on one of those anyway.

Erase everything?!!! what are you mad?
Boot off the live CD, go to terminal and type:
```
sudo -i
mount /dev/sdb3 /mnt
install-grub /mnt/ /dev/sdb
```

If that's your boot drive you should reboot with Ubuntu then go:
```
sudo update-grub
```

---

### Post by Shugs81 on 2010-02-20
i'll definately try that ozz...

I've removed the 250gb hd as that seemed to be competing for top hd... had to unplug the 1.5tb hd just to be sure...

ubuntu is on there but grub doesn't seem to want to work properly...

is there anywhere i can d/l it so i can indtall it either from windows or live cd?

---

### Post by bowbalitic on 2010-02-22
> Erase everything?!!! what are you mad?

I had to laugh at this I wont lie. :P

From what I understood, he really didn't like the drive letter assignment for his windows partition. From my limited understanding, this is a rather difficult and annoying process in windows. I also assumed that it was a fresh install so he didn't have a large amount of data to back up anyway. 

I apologize and next time I'll wait till there are no options left to suggest a complete re-installation. Personally, I go through a complete reinstall of windows every 2 months any way. It's a rather easy way to clean up a computer used for gaming only.

---

### Post by presence1960 on 2010-02-22
> **bowbalitic said:**
> I had to laugh at this I wont lie. :P

From what I understood, he really didn't like the drive letter assignment for his windows partition. From my limited understanding, this is a rather difficult and annoying process in windows. I also assumed that it was a fresh install so he didn't have a large amount of data to back up anyway. 

I apologize and next time I'll wait till there are no options left to suggest a complete re-installation. Personally, I go through a complete reinstall of windows every 2 months any way. It's a rather easy way to clean up a computer used for gaming only.

It is possible to change the letters assigned to drives/devices in windows through computer management.

---

### Post by bowbalitic on 2010-02-22
Again, I'm sorry. The results I found on google suggested that  changing the drive letter often led to programs not working and registry errors and that it was easier to simply reinstall windows. I've never tried it so I don't know.

---

### Post by presence1960 on 2010-02-22
> **bowbalitic said:**
> Again, I'm sorry. The results I found on google suggested that  changing the drive letter often led to programs not working and registry errors and that it was easier to simply reinstall windows. I've never tried it so I don't know.

No need to be sorry. No harm done.

---

### Post by Shugs81 on 2010-03-08
bah... the stress is over... and new ones begin!!

can't get online now!! lol!! seems that it doesn't seem to pick up the broadcom card at all...

new horrors await!!

---

### Post by JerichoKru on 2010-03-08
> **Shugs81 said:**
> bah... the stress is over... and new ones begin!!

can't get online now!! lol!! seems that it doesn't seem to pick up the broadcom card at all...

new horrors await!!

Which card is it?

---

### Post by Shugs81 on 2010-03-09
its a belkin fd75001uk or something like that... tried ndiswrapper and the gtk front end... seems to instal and mentions about not finding hardware then fwcutter seems to fail... it has worked in the past too...

can anyone reccomend a suitable wireless N card that's compatable out of the box??? as an alternate...

---

