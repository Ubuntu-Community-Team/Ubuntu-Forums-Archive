---
title: "Lost windows partition by setting swap for Ubuntu"
date: 2010-10-21
forum: New to Ubuntu
---

### Post by pagemaker on 2010-10-21
Hello everyone!

Yesterday I tried to install Ubuntu 10.10 on my laptop as a second OS and try it out, experiment and learn.

But my attempt was not so succesful :(

I had 3 partitions on my disk. First one contains Windows and all windows apps, second one my files and the third was meant for Ubuntu.

I installed Ubuntu without any problem but during setup I set the swap file to be on the partition where my files were. So after the installation is complete I cannot see this partition in windows and in Ubuntu shows up like swap...

I had backup of most of the files there but I had some not backed up. Is there any chance I can get those files back?

---

### Post by Rubi1200 on 2010-10-21
Hi and welcome to the forums :)

For recovery options:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

Hope this helps.

---

### Post by pagemaker on 2010-10-21
Thanks for the fast answer...

Would be a good idea to boot into Ubuntu and remove swap from this partition so there won't be any more changes? How can I move the swap to the partition where Ubuntu is installed?

---

### Post by Rubi1200 on 2010-10-21
I would first try and recover the files before taking further action.

However, it would be useful if you could post the results of this command from within Ubuntu **AFTER** you have hopefully recovered your files:

```
sudo fdisk -l
```Also, just to be clear, it is recommended to run Testdisk from a LiveCD:
[http://www.cgsecurity.org/wiki/TestDisk_Livecd](http://www.cgsecurity.org/wiki/TestDisk_Livecd)

---

### Post by AngusH on 2010-10-21
I may be wrong but would it not be a mistake to boot up the copy of ubuntu on the hard disk? If you do boot it up then you run the risk that it will store some data in swap, and in doing so obliterate some of the data you hope to recover.
Angus

---

### Post by pagemaker on 2010-10-21
Thanks again...

Will try that and get back here for the results...

---

### Post by Rubi1200 on 2010-10-21
> **AngusH said:**
> I may be wrong but would it not be a mistake to boot up the copy of ubuntu on the hard disk? If you do boot it up then you run the risk that it will store some data in swap, and in doing so obliterate some of the data you hope to recover.
Angus
Very good point! I will edit my post to reflect this.

Thanks :)

(and welcome back to the forums with your new user name)

---

### Post by pagemaker on 2010-10-21
I already booted into Ubuntu once when the installation was finished and I realized what I've done :P

But I won't boot anymore until I try a recovery procedure...

---

### Post by AngusH on 2010-10-21
> **pagemaker said:**
> I already booted into Ubuntu once when the installation was finished and I realized what I've done :P

But I won't boot anymore until I try a recovery procedure...

It probably isn't a problem. Provided you have a reasonable amount of RAM it's fairly rare for ubuntu to start using swap (about the only time I use it is when one of my C programs memory leaks :)) but like I say it isn't worth the risk if you can avoid it.

@Rubi1200, thanks. I was starting to get sick of calling myself "da burger" in a place I now spend a lot of my time.

Angus

---

### Post by pagemaker on 2010-10-22
Hello again guys!

I managed to recover my files using Easeus Partition Master which I used to create the partitions and was already installed on Windows. Now I have two more questions:

I reformatted the second partition (where I had set the Ubuntu swap) with NTFS so I can use it again with Windows. How can I set the swap to be on the same partition as Ubuntu? Or maybe create another (small) partition and put it there?

The other question is how to make "windows7" appear first in the boot loading screen. My wife also uses the laptop and she mumbles every time she sees it :P

---

### Post by mcduck on 2010-10-22
Just boot with the Ubuntu CD, make sure all the partitions are unmounted and resize the last one on your disk a bit (use the Gparted included on the CD) & create a small swap partition. Gigabyte or two should enough for most situations, but if you want to be able to suspend the machine you should have at least as much swap space as you have RAM.

It *is* possible to create a swap file on the Ubuntu partition, but I'd go for an actual swap partition instead.

---

### Post by pagemaker on 2010-10-22
Thanks! You all have been very helpful!

What about the loading screen? How can I edit it and bring "windows" on top?

---

### Post by JackNocturne on 2010-10-22
Download "Startup Manager" from Synaptic Package manager or Ubuntu Software Centre , it should allow you to edit those options you are asking for.

---

### Post by pagemaker on 2010-10-22
Thanks again to all for one more time!

---

### Post by mcduck on 2010-10-22
> **JackNocturne said:**
> Download "Startup Manager" from Synaptic Package manager or Ubuntu Software Centre , it should allow you to edit those options you are asking for.

That would probably be the easiest way for a new user.

It's of course possible to do the same without installing anything extra, by editing /etc/default/grub and changing the "GRUB_DEFAULT=0" -line to whatever you need. (the numbering starts from 0, so first item on Grub menu is 0, second item is 1 and so on. After that you'd need to run "sudo update-grub".

---

### Post by Rubi1200 on 2010-10-22
You are more than welcome :)

Glad you got it sorted out and managed to recover the files.

Please mark this thread Solved using the Thread Tools near the top of the page.

---

### Post by uzair_thebest on 2010-12-13
i would be very thankful if anyone can help me to sort out this issue.
 the issue is my brother installed ubuntu on my laptop.earlier i was using windows 7  he installed it on other partition but unfortunately ubuntu made my windows 7 partition a swapp partition. now i want to log on to windows can you please guide me

thanks
uzair

---

### Post by julio_cortez on 2010-12-13
Maybe you could use some undelete/recover program that runs from a live CD (like [these ones]("http://www.killdisk.com/products.htm") from active@) to see if you get something back from it.
Then (after trying to recover the data) you might have to reinstall Windows I suppose.

---

### Post by uzair_thebest on 2010-12-13
the problem is on when i select windows 7 it give Error 0xc000000f and when i insert the windows CD it doesent repair as it requires a ntfs partition. in short i want windows to run like it was previously

---

### Post by julio_cortez on 2010-12-13
Again, I don't think you can have it back exactly how it was previously.
What I was suggesting you was to try recovering the most data you can (pointers to the files may have been erased while creating the swap partition, but chances are that the content of the partition is still there even if marked as "free" space), but of course you should try it with a program that is able to read the files even if they're not indexed anymore.

---

### Post by Rubi1200 on 2010-12-13
Hi,
the first thing we need for you to do is run the boot info script (link at the bottom of my post).

Plug in the USB stick with Ubuntu on it and boot the computer. You need to allow booting from the USB drive in BIOS.

Usually, that means pressing something like F2 or F12 when the computer starts. Go to boot device or boot priority (whatever it says) and change the order so you can boot with the USB.

Once you can do that, boot the computer choosing to try Ubuntu. Do NOT pick the option to install!

When you are at the desktop on the live environment, you need an Internet connection to download and then run the script.

There are instructions included in the link. The terminal can be found by going to Applications > Accessories > Terminal.

Post the results back here before we move on to the next step.

If anything is unclear, ask first please.

---

### Post by uzair_thebest on 2010-12-13
what if i directly open the terminal and put that script in ??

---

### Post by Rubi1200 on 2010-12-13
> **uzair_thebest said:**
> what if i directly open the terminal and put that script in ??
Won't work as far as I know.

You need to download the script and put it on the Desktop.

Then run it using this command:
```
sudo bash ~/Desktop/boot_info_script*.sh
```This will generate a RESULTS.txt file on the desktop.

Open it and copy/paste the contents and then post it back here.

Use the code tag # which you can generate from the menu when you start a new post. Put the cursor between the tags and do Ctrl + v to paste, then submit the post.

---

### Post by uzair_thebest on 2010-12-13
wow great.. no ubuntu setup available. now i have to download the whole setup :(

---

### Post by uzair_thebest on 2010-12-13
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for (,msdos3)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 8192.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2    *        206,848   204,802,047   204,595,200  82 Linux swap / Solaris
/dev/sda3         204,802,048   409,602,047   204,800,000  83 Linux
/dev/sda4         409,602,048   625,139,711   215,537,664  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2019 MB, 2019557376 bytes
19 heads, 18 sectors/track, 11533 cylinders, total 3944448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          8,192     3,944,447     3,936,256   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        56741A9B741A7DC5                       ntfs       System Reserved               
/dev/sda2        ae03e771-09c5-4c84-9bd9-5487cadbeab5   swap                                     
/dev/sda3        9d4606f3-74e5-4caf-832c-4f35d82895a7   ext4                                     
/dev/sda4        10EE10B7EE1096D6                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        4F15-AA9B                              vfat       New Volume                    
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro,commit=600)
/dev/sda4        /media/10EE10B7EE1096D6  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1        /media/System Reserved   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /media/New Volume        vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=========================== sda3/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 9d4606f3-74e5-4caf-832c-4f35d82895a7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 9d4606f3-74e5-4caf-832c-4f35d82895a7
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 9d4606f3-74e5-4caf-832c-4f35d82895a7
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=9d4606f3-74e5-4caf-832c-4f35d82895a7 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 9d4606f3-74e5-4caf-832c-4f35d82895a7
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=9d4606f3-74e5-4caf-832c-4f35d82895a7 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 9d4606f3-74e5-4caf-832c-4f35d82895a7
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 9d4606f3-74e5-4caf-832c-4f35d82895a7
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 56741a9b741a7dc5
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda3       /               ext4    errors=remount-ro 0       1
/dev/sda2       none            swap    sw              0       0

=================== sda3: Location of files loaded by Grub: ===================


 165.1GB: boot/grub/core.img
 135.0GB: boot/grub/grub.cfg
 105.2GB: boot/initrd.img-2.6.35-22-generic
 165.1GB: boot/vmlinuz-2.6.35-22-generic
 105.2GB: initrd.img
 165.1GB: vmlinuz

---

### Post by Rubi1200 on 2010-12-13
I don't understand. How was Ubuntu installed? It was either from a CD or USB or from within Windows with Wubi. Is the original no longer available?

---

### Post by uzair_thebest on 2010-12-13
huhh let me explain

windows was running perfectly
my  brother installed ubuntu on another partition as to use both
after the installation from usb when i tried to run windows it gave the error code Error 0xc000000f which said to repair the windows.when i started the setup it showed the partition but i couldnt select any as it says that no ntfs partition available. and also i cant see use or free space of the partition in which windows was installed

---

### Post by Rubi1200 on 2010-12-13
Yes, this I understand. What probably happened it that the install wrote over the Windows installation and formatted it to either ext4 or swap.

In either case, recovering it could be difficult if not impossible.

If you feel confident enough with advanced procedures, we can try, and I emphasize try, to help you recover the partition or the data. 

Otherwise, you might be best taking it to a professional data recovery service (which will cost a lot of money).

---

### Post by uzair_thebest on 2010-12-13
it has formatted it to swap spaace coz wat is can see in GPARTED /dev/sda2 linux swap 
mount point  nothing
label  nothing
size 97.56
used -
unused -
flags boot

---

### Post by uzair_thebest on 2010-12-13
i would really be thankful if you can guide me the procedures because i wont be able to find any professional in my surroundings

---

### Post by Rubi1200 on 2010-12-13
Sorry about the delayed responses; having some connectivity issues at the moment.

So, as you saw sda2 was probably the Windows partition which is now formatted to swap.

The first thing to try is to use a program called Testdisk to try and recover the partition.

Here is a guide on how to use it:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

You can download and run it from a LiveCD/USB.

Give that a try first and let's see if it helps (i.e. recognizes what went wrong and tries to recover it).

Meantime, I will try and find more information for you.

---

### Post by uzair_thebest on 2010-12-13
ok brother m trying

---

### Post by uzair_thebest on 2010-12-14
Brother
m totally unable to do this.is there anyway out??
what if i uninstall ubuntu will this fix the issue??

---

### Post by pagemaker on 2010-12-14
Try something else...

Download Hiren's Boot CD ([http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd)), burn it to a cd and boot your pc with it. It has some nice partition recovery tools like DiskGenius or Smart Partition Recovery (which claims to be able to restore lost ntfs partitions) that might be able to help you out...

---

### Post by Rubi1200 on 2010-12-14
+1 to pagemaker's suggestion.

As I said before, the chances for recovery are slim, but don't give up yet.

I believe Easeus Partition Manager also claims to be able to rescue NTFS partitions:
[http://www.partition-tool.com/?gclid=CLu_uef266UCFUco3wod5Dm1ow](http://www.partition-tool.com/?gclid=CLu_uef266UCFUco3wod5Dm1ow)

---

### Post by pagemaker on 2010-12-14
I used EASEUS Partition Manager to recover my lost files. But in my case, the Windows partition was intact, so I could boot it up and use the recovery software on the lost partition.

In uzair's case, the Windows partition is completely unusable, so he can only hope in "command-line miracles" :)

---

### Post by Rubi1200 on 2010-12-14
I am no expert on data recovery. 

I know that some users have had success with Testdisk, but as uzair_thebest already said he had no luck with that.

I am clutching at straws here, which is why I suggested the software that I did.

There may be little choice but to reinstall Windows.

---

### Post by uzair_thebest on 2010-12-14
Thank you so very much both of you.will unistalling ubuntu can fix the issue ??

---

### Post by Rubi1200 on 2010-12-14
> **uzair_thebest said:**
> Thank you so very much both of you.will unistalling ubuntu can fix the issue ??
Highly unlikely, and it may make things more difficult in terms of trying to recover any data.

Take a look here:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

I also suggest you ask on a Windows forum since they may have some other ideas about Windows software that can recover your partition:
[http://www.sevenforums.com/](http://www.sevenforums.com/)

---

### Post by uzair_thebest on 2010-12-15
m trying to install test disk but the problem is when i select install and i enter a password there comes a key which indicate DROP all elevated privileges after that the the software doesnt install.can you please help me out

---

### Post by Rubi1200 on 2010-12-15
You need to install it on the LiveCD.

Run this:
```
sudo apt-get install testdisk
```
As far as I know this should work.

---

### Post by uzair_thebest on 2010-12-15
No Harddisk found
You need to be root to use TestDisk..
help me what to do now ?

---

### Post by Rubi1200 on 2010-12-15
> **uzair_thebest said:**
> No Harddisk found
You need to be root to use TestDisk..
help me what to do now ?
You need to run the program with administrative privileges, i.e. sudo.

Use the guide here to help:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by uzair_thebest on 2010-12-15
Brother how would i be able to use it with administrative?

---

### Post by wep940 on 2010-12-15
Notice they said "with SUDO".  Simply preface your command with sudo and a space - that gives you temporary administrative priviledges.

---

### Post by uzair_thebest on 2010-12-15
:-)
m able to run the test disk now

---

### Post by uzair_thebest on 2010-12-15
now wat i see is
1 P HPFS        0  32  33   12  223 19  204800 [system reserved]
2 * linux swap  12 223 20   12748  86  10  204595200
3 P linux       12748  86  11  25496  139  51  204800000
4 P linux swap   25496  139  52  38913  37  36  215537664
4 P linux swap   25496  139  52  38913  37  36  215537664

now what to do??? guide please

---

### Post by Rubi1200 on 2010-12-15
I presume this is after you used Analyse?

You should then have the option to highlight Quick Search (or maybe it is already there, in which case choose to do a Quick Search).

---

### Post by uzair_thebest on 2010-12-15
yes after i choose analyse

there's only 2 options proceed and backup

---

### Post by Rubi1200 on 2010-12-15
Are you able to highlight the entry where you suspect the Windows partition might be?
```
2 * linux swap  12 223 20   12748  86  10  204595200
```If you can, what options are then available?

If not, what does Proceed bring up? Careful! Quit or Esc usually takes you back to the previous screen. If you are unsure, wait and ask first.

---

### Post by uzair_thebest on 2010-12-15
i cant highlight but when i choose proceed it brings

D HPFS - NTFS  0 32 33 12 223 19 2048-- system reserved
D linux swap  
D linux
D-hpfs ntfs

A : add partition L : load backup  T : change type Enter to continue
another option is  P : List files which is not available on D linux swap

---

### Post by Rubi1200 on 2010-12-15
Hold on!!

Do you see the difference?

> 1 P HPFS        0  32  33   12  223 19  204800 [system reserved]
2 * linux swap  12 223 20   12748  86  10  204595200
3 P linux       12748  86  11  25496  139  51  204800000
4 P linux swap   25496  139  52  38913  37  36  215537664
4 P linux swap   25496  139  52  38913  37  36  215537664



> D HPFS - NTFS  0 32 33 12 223 19 2048-- system reserved
D linux swap  
D linux
[COLOR=Red]D-hpfs ntfs[/COLOR]

If you highlight the last entry and press P what do you get?

---

### Post by uzair_thebest on 2010-12-15
nothing... it gave another option 
Enter : to continuesegmentation fault

---

### Post by Rubi1200 on 2010-12-15
> **uzair_thebest said:**
> nothing... it gave another option 
Enter : to continuesegmentation fault
No, you definitely do not want to do that!

I suggest you go through and highlight each entry and press P to see what files it shows you.

If you see anything unusual, post it here.

I am especially interested to know what it will list for the ```
D HPFS - NTFS  0 32 33 12 223 19 2048-- system reserved
``` entry. At the very least, we might be able to restore using that.

Use "q" to Quit and go back to the previous screen as a general rule.

---

### Post by uzair_thebest on 2010-12-15
same for D HFPS

but for D linux it gave
drwxr-xr-x  0  0  4096  15 DEc-2010  15:23

i guess the it is the drive in which linux is installed. it contain files like
 var  etc  media  bin boot  dev  home  lib

---

### Post by uzair_thebest on 2010-12-15
what to do now..
 i think D linux swap is the lost windows partition

---

### Post by Rubi1200 on 2010-12-15
Are you able to highlight the swap entry and use P to see what is there?

What did the NTFS system reserved entry show?

---

### Post by uzair_thebest on 2010-12-15
No there's no option of  P : List files

D HPFS- NTFS is a 100 mb drive

---

### Post by Rubi1200 on 2010-12-15
I don't know what to tell you :-(

I am going to ask some other users to take a look and offer advice on this one.

Hang in there!

---

### Post by uzair_thebest on 2010-12-15
i've never been in this sort of situation. m totally blank here

---

### Post by Rubi1200 on 2010-12-15
I've called for reinforcements ;)

Please wait until some of the others respond and offer their perspectives.

---

### Post by oldfred on 2010-12-15
I am afraid I do not know a lot more about testdisk.

From boot script this is the partition you want to recover.

/dev/sda2    *        206,848   204,802,047   204,595,200  82 Linux swap / Solaris

Note that start is 206848 and end is 204802047, if during install it was not resized then that is the start and end of the NTFS partition you want. Whether it will be readable or not is another issue. If swap wrote any data it may have corrupted system files. If it was just a data partition you could recover it and read at least some of the data.

Does test disk give you the above start & end as a recoverable partition?

---

### Post by uzair_thebest on 2010-12-15
What i see infront of me is 

D HPFS - NTFS  0 32 33 12 223 19 204800 [system reserved]
P linux swap   12 223 20 12748 85 57 20459184
D linux        12748 86 11 25496 139 51 204800000
D HPFS - NTFS  25496 139 52 38913 37 36 215537664

KEYS A : add partition , L:load backup , T :change type , P L list files
Enter : to continue

---

### Post by oldfred on 2010-12-15
D HPFS - NTFS  25496 139 52 38913 37 36 215537664

The start end difference may be because of sectors vs cylinders. The size is close but not exact.

I would try to recover that partition.

The only other choice would be to force a partition table entry and make it NTFS. But if we do not know the exact start it will probably make more problems. I think testdisk is better as it can find old data.

If you have files you want to try to recover from the partition you can use photorec. You have to have lots of space on another drive and it will scan the drive for all files and copy them to the other drive. It takes a very long time to run. And because file table is not there it does not recover file names, although photos & music have internal data that you can use to recover names. It also finds parts of files as I had saved a text file many times and it found the file many times with different changes or only parts of the file.

---

### Post by uzair_thebest on 2010-12-15
how would i be able to recover from here onwards.what would be the next step?

---

### Post by oldfred on 2010-12-15
I would try undeleting the NTFS partition with testdisk, it seems you have nothing to lose.

Then if that does not work use photorec to recover whatever files you can. But you have to have another larger drive to copy the data to.

---

### Post by coffeecat on 2010-12-15
@uzair_thebest, if I could chip in here - I'm one of the reinforcements that Rubi1200 called for - it's been some time since I used testdisk, so I'm going from memory. Your post about three up is listing the four partitions and I agree that you need to try to change sda2 to NTFS. I think this is your only hope. You posted some stuff from what testdisk is prompting you with:

> KEYS A : add partition , L:load backup , T :change type , P L list files
Enter : to continueAre you able to select partition 2 and then press T to change type? This should then prompt you for the various filesystems, among which should be NTFS, which is what you need to choose. I think this is the route you need to take. Sorry if you've tried this before - I can't be sure from what's been posted already.

---

### Post by kansasnoob on 2010-12-15
I'm glad to see that others got involved because I'm clueless.

I just wish I could get the devs to pay attention to these bugs:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950)

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/657397](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/657397)

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/682429](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/682429)

All three are quite related and I'm fighting that battle alone with one arm tied behind my back :(

I've even personally addressed SABDFL and Ayatana, then I tried ubuntu-installer and my last post there was blocked so I'm pretty well cooked on getting this fixed unless someone else gets aggressively involved!

I'd also like to see this option restored:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/652852](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/652852)

I did get this "wishlisted":

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628097](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628097)

Anyone care to help?

---

