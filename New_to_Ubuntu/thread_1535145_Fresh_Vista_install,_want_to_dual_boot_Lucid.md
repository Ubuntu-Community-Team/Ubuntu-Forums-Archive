---
title: "Fresh Vista install, want to dual boot Lucid"
date: 2010-07-20
forum: New to Ubuntu
---

### Post by AndyP79 on 2010-07-20
Hi Ya'll,
 Okay, first, before anyone says google it.... I have been searching around the last several day how to do this, and nothing seems to make sense or pertain to me...so here it is;
 I am currently installing a fresh go of Vista on my laptop. I have a 500GB HD, so plenty of space. I want to install Lucid 10.04 as a dual boot. Fair enough. I would like BURG on there also, so I can have something that looks factory installed. What do I need to do to Vista first to shrink it? I would like it to be only about 100GB and about 300GB dedicated to Lucid. That way I have another 100GB to use as a space to play with something, like Maverick Alpha for instance, that can be erased and reloaded as needed.


What do I do first? Alot of people lately seem to be interested in my Linux Adventures, and I want them to see something truly professional, not, uh... like how I normally do it, which is very caveman like, as in, beat with a club! LMAO! 

Anyone got anything on this?

---

### Post by jerenept on 2010-07-20
I do not know about BURG, but dual-boot is really easy to do. the installer detects other os's. You can set up a dual-boot system from there.

---

### Post by oldfred on 2010-07-20
Use windows tools to shrink the Vista partition.

Resize windows partition info:
[https://help.ubuntu.com/community/RecoveringWindows#Resizing%20a%20Windows%20Partition%20in%20Windows](https://help.ubuntu.com/community/RecoveringWindows#Resizing%20a%20Windows%20Partition%20in%20Windows)

Dual Boot Win7 & Ubuntu
[http://ubuntuguide.org/wiki/Ubuntu:Lucid#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Dual-Booting_Windows_and_Ubuntu)

[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)
[http://www.thpc.info/how/shrink_partition_in_windows_7_vista.html](http://www.thpc.info/how/shrink_partition_in_windows_7_vista.html)

I have several system partitions for Ubuntu. 9.04, 9.10 and a couple of 10.10 installs. I link my data partition into all of them with a simple script. But only will copy some /home settings and do not share /home even with Ubuntu being common (Ubuntu upgrades with same /home will work, but not recommended otherwise).

---

### Post by AndyP79 on 2010-07-20
I understand that the Ubuntu installer just works. BUT... shouldn't I resize my windows first or something from Windows? I have tried the dual booting thing before with the Ubuntu installer, but it always seems finicky. I am doing a fresh install right now, I forgot to add, because windows stopped booting. No matter what I did, following all kinds of different advise, it would not boot, just reboot itself into Lucid. I need to add here, that I had also wiped Lucid and re-installed it. So I think something crazy happened to the Vista install. SO what I am asking to do, does not seem to work so nice with the standard Ubuntu Installer.      
 So... like I said, what first?

---

### Post by AndyP79 on 2010-07-20
oldfred, this seems to be what I was looking for. I got a chance to scan through those links, and they seem to adress the Windows issues from Windows first, Thank You. I will let you know what happens here in a few hours after Vista finishes loading! Damn Windows!

---

### Post by anon.jdh on 2010-07-20
Another option is WUBI ([http://wubi-installer.org/](http://wubi-installer.org/)).
If you put the install disk into the machine while running Windows, The WUBI installer will come up allowing you to install Ubuntu within Windows.

This will give you a dual-boot system that you can un-install within Windows without hurting anything.

---

### Post by AndyP79 on 2010-07-20
> **anon.jdh said:**
> Another option is WUBI ([http://wubi-installer.org/](http://wubi-installer.org/)).
If you put the install disk into the machine while running Windows, The WUBI installer will come up allowing you to install Ubuntu within Windows.

This will give you a dual-boot system that you can un-install within Windows without hurting anything.

Isn't this the same really as running Windows full time though? I am not sure if I understand the WUBI thing. Is it more like running a virtual machine? What happens when Windows crashes, wouldn't I lose my Linux OS then also? I was looking at some things, and something I saw, after working over Windows from within Windows, would be setting up Ubuntu in the newly created free space, making a nice size swap, putting all my files into a /home partition, and then putting my Ubuntu on to whatever is remaining, leaving what I want to add other another OS later to play with. How would that fair in comparison to other choices?

---

### Post by oldfred on 2010-07-20
If Vista will not shrink enough you can use gparted but the checkbox prevents bigger issues. I would always resize outside the installer and reboot Vista several times to make sure it has recognized its new size.

starting with Vista - MSoft made some changes to the way it installs itself in a partition. Gparted can deal with it but should have the round to cylinder unchecked.
Herman on checkbox
[http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17](http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17)
Vista and Partitioning - details
[http://www.multibooters.co.uk/partitions.html](http://www.multibooters.co.uk/partitions.html)

---

### Post by anon.jdh on 2010-07-20
Wubi is what I used to install Linux on my work computer to make it dual-boot. 

Yes, if you lose your Windows partition you will lose your Linux installation.

Still - when you boot the machine you will be presented with the option of booting into Windows or Linux. Linux does not "run" inside of Windows it is only *installed* there. And it can just as easily be un-installed without causing trouble.

Just an option...

---

### Post by AndyP79 on 2010-07-21
Still working at this. Windows is a bitch to work with. Had to get things set up on it to where I wanted them, then do the shrink thing. Hopefully tomorrow I can wrap this up and I will post my results and how I did it all so I can help others trying to do what I am trying to do. See ya'll in the morning.

---

### Post by MooPi on 2010-07-21
Hey AndyP79, I'm with you on the non-wubi deal. Wubi seems to limit the Ubuntu experience in my estimation.  I have a suggestion for your partitioning. I always partition first then install my operating systems later.  I do my partitioning  so that the OS fits and any additional applications will have room then leave a larger space for data.  So in your instance give Vista a larger space for install because it needs it and enough room for your Windows apps then maybe a slightly smaller space for Ubuntu and your extra space for future installs.  Then a much larger partition for data. Makes it easy to swap out new installs in the future without having to move your data as well. In my case I have 320 gig hard drive that has a 17g Ubuntu, 23g XP, and the remainder left for my storage bin and swap. If you plan on any gaming, give yourself plenty of room for that on your Windows partition because modern games chew up hard drive space.

---

### Post by AndyP79 on 2010-07-21
Hey Ya'll,
 MooPi, sounds like you got what I want. So far, after ours sitting with this stupid !@#$% Windows deal, I currently have about 65GB for Windows and about 10Gb for D drive. Here in lays my question; they are at opposite sides of the hard drive, there is a HUGE 300+ GB space in the center. I got that not allocated to anything at the moment, but before I go on, is this okay? I can seem to shrink it anymore or defrag it anymore and I don't know if it can be moved so that D drive is next to C drive. Does this matter? Before I go out my fresh and clean Ubuntu on there and start adding space for home and sharing files and all that good jazz, I need to know if this is okay first. 
Thanks everyone for the help so far,

---

### Post by oldfred on 2010-07-21
Partitions can be anywhere. gparted will let you move partitions but of course the more you move things around the higher the risk.

The main caveat is that the extended partition with all the logicals inside must be contiguous. You cannot have two extended partitions.

---

### Post by AndyP79 on 2010-07-21
Okay, was looking at some of the web pages that were posted by oldfred. I caught something there about the shrinking, which led to gparted. in g parted, can i actually move the D drive so that it sits next to the C drive, and how has the luck been with gparted?

 I have now spent the better part of working on 3 days trying to get this all sorted out, and I still have not got to the Ubuntu install part! LMAO! !@#$% Windows, I am forced to use it at the moment, @!#$%^& sucks!

---

### Post by AndyP79 on 2010-07-21
> **oldfred said:**
> Partitions can be anywhere. gparted will let you move partitions but of course the more you move things around the higher the risk.

The main caveat is that the extended partition with all the logicals inside must be contiguous. You cannot have two extended partitions.

Man your quick, I was asking the question as you were writing the answer!  Okay, so having two extended patations would be if I manually extended them instead of shrinking? Obvious answer?  Cause if so, I am good there, i think. 
I am wondering though, since you say I can have the partitions anywhere, maybe I should just leave them where they are. If I want to share the home partition with windows, add ubuntu and then leave some free space, will this effect anything? Number of partitions allowed maybe?

---

### Post by AndyP79 on 2010-07-21
Okay, so, I am the point of installing Ubuntu manually. BUT.... in everything I see, it says that you start boot at sda1, and it goes from there. BUT.... on mine it looks like this so far;

/dev/sda1  ntfs      65923MB  
freespace            423079MB
/dev/sda2  ntfs      11098MB

the ntfs is Vista, but you guys probably knew that.


So, I know I want to put the Ubuntu in that free space. I understand what swap is, kinda like virtual memory, and to give it about twice what I have currently of 2GB of actual memory. So, 4GB it is going to be. But how much do I need to give to boot, home and root? Home should be where all my music and photos go right? So I should give that the larger amount I believe. Root, is that where Ubuntu is actually stored? I add a serious amount of extra applications to a fresh install. Don't they say you normally need about 4GB for that? So, should I give that about 30GB to hold all the applications or more? And I don't understand boot, don't even have a clue what is going there or how much to allocate it. 

To top all that off, when I add these, will it create them in numerical order, as in, dev/sda3  dev/sda4 and so on, and will that affect anything?
Boy, I am getting deep into this.

---

### Post by AndyP79 on 2010-07-21
Okay, new issue, sorta. I started to do the partitions in the free space, and I gave 50MB to boot, 4GB to swap, and then after that, it won't let me add anymore partitions. Now what? I guess 4 is the limit?

---

### Post by oldfred on 2010-07-21
If you manually partition you create the extended partition first to use all the free space in the middle.

Then inside the extended  partition create a 20-25GB partition for / (root) and format it ext3 or ext4. You only need a little more than 2GB for swap. 1x RAM is fine for over 2GB and equal to RAM will let you hibernate if you want. Make the rest /home. (2X RAM was the rule when memory was only 256MB).

During install you choose the partitions you have created. Or you can create as part of the manual install and choose format.

I have installed lots of applications and am all the way up to 6GB used. If you want to create a DVD it will need 4+GB in tmp to store the data, so 10GB is the minimum I recommend for root. You can get by with less but have to be carefull on what you install or create.

---

### Post by AndyP79 on 2010-07-21
> **oldfred said:**
> If you manually partition you create the extended partition first to use all the free space in the middle.

Then inside the extended  partition create a 20-25GB partition for / (root) and format it ext3 or ext4. You only need a little more than 2GB for swap. 1x RAM is fine for over 2GB and equal to RAM will let you hibernate if you want. Make the rest /home. (2X RAM was the rule when memory was only 256MB).

During install you choose the partitions you have created. Or you can create as part of the manual install and choose format.

I have installed lots of applications and am all the way up to 6GB used. If you want to create a DVD it will need 4+GB in tmp to store the data, so 10GB is the minimum I recommend for root. You can get by with less but have to be carefull on what you install or create.
Okay, let me make sure I understand this first. When I check manual, and I get the screen that is showing where things are and how much they have, check "new partition table" and give it the whole amount of free space and then add my boot, swap, home and root in that?

---

### Post by AndyP79 on 2010-07-21
Okay, I think where I am getting confused is where this "extended partition is coming from? cause at this point I am kinda lost. Obviously.

---

### Post by oldfred on 2010-07-21
You can only have 4 primary partitions. But you can convert one primary to an extended. In gparted when you create the partition for the unallocated space choose extended partition. Do not remember but you  may have to right click to choose partition type. Then you can create the logical partitions inside the extended.

---

### Post by AndyP79 on 2010-07-21
> **oldfred said:**
> You can only have 4 primary partitions. But you can convert one primary to an extended. In gparted when you create the partition for the unallocated space choose extended partition. Do not remember but you  may have to right click to choose partition type. Then you can create the logical partitions inside the extended.

Okay, that makes sense. So all the boot, root, swap, and home are all logical not primary when I choose how to set them up? And I just to make sure, I need to run gparted from the live cd first right?

---

### Post by oldfred on 2010-07-21
Yes, and it is usually better to run gparted from a liveCD. In fact the standard install does not download it. I always download it as I may have unmounted partitions or just to see where things are at.

---

### Post by AndyP79 on 2010-07-21
Okay, so far so good. It appears everything is working. Both the Vista and Ubuntu are booting. 
Thank You very much for all the help. I will post tomorrow, what I went through and what I got at the end. 
Thanks again.
Andy

---

### Post by AndyP79 on 2010-07-23
!@#$% WINDOWS!!!! Okay, so today WAS good, until.... windows won't load! 
So, I have been able to go back and forth between Windows and Ubuntu all day. Probably 10 times I have done it, and everything went off without a hitch. All right I thought. I took my time and carefully added my applications to Ubuntu, have done nothing to the Windows set up. I had it all set up before starting the dual boot process. I had to do work in the Windows and got a bunch done, but..... All of a sudden no Windows. When I start the computer, I get the screen to choose between the two OS, and when I choose Windows now it asks if I want to do the system recovery, starrts to load, has the little Microsoft loading bar that pops up, then restarts and I am back at the choices screen.
So, we are back to where do I go from here? I really need it to do what I got to do at the moment, and I am feed up to my eyeballs in frustration..ugghh.  How do I get this Windows back without starting all over from scratch, I can't keep doing this over and over again, I am wasting sooo much time in this, and it is killing my productivity.

Okay, so I am done venting for the moment. Oh, on a positive note, Ubuntu seems to be just fine and no problems there, I am using it to do this as we speak, and I can see my Windows partition in the file browser.

Thanks for everyone who dedicates their time on here to helping each other fix these things. I understand that ya'll give up a lot of your own free time to help us, and want to let you know that it is appreciated. 

Andy

---

### Post by AndyP79 on 2010-07-23
Okay I was able to get it to do the system check repair deal. It basicly told me that it can not repair it. So.. two questions;
1) If I put my Vista Recory disks back in, will it recognize that the hard disk has an extended partition and leave it alone and only reload on the partition it is currently on? And will it bork my Ubuntu system?

2) What if I just with with a virtual machine. Just run Vista inside Ubuntu. I have played with Virtual box a couple of time, and really can't stand the little screen that I have to work out of, that is not really ideal for working with documents. I have seen parrells(?) on a Mac once, and it look like it had windows running almost seemlessly? I saw something in virtual box about a seemly mode, but it will not let me choose it. Maybe another program or even a paid for version? 

okay, time for bed, i will check back in the morning

---

### Post by oldfred on 2010-07-23
Generally windows does not even see any linux partitions just FAT & NTFS.

Run this script to see if something looks out of place. You may just need to run windows chkdsk or other repairs.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by AndyP79 on 2010-07-23
Hi Oldfred, 
 Okay, got your post this morning, and this is what I got. Hope this explains something. I am holding off on doing any other extreme measures, like starting over until I hear back from you.
Thanks again for all the help
ANdy


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /grub.
 => No boot loader is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /BOOT/BCD

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /etc/fstab

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   128,757,757   128,757,695   7 HPFS/NTFS
/dev/sda2         955,084,800   976,760,831    21,676,032   7 HPFS/NTFS
/dev/sda3         128,757,758   855,083,007   726,325,250   5 Extended
/dev/sda5         128,757,760   128,952,319       194,560  83 Linux
/dev/sda6         128,954,368   132,952,063     3,997,696  82 Linux swap / Solaris
/dev/sda7         132,954,112   795,082,751   662,128,640  83 Linux
/dev/sda8         795,084,800   855,083,007    59,998,208  83 Linux


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 2000 MB, 2000682496 bytes
64 heads, 63 sectors/track, 969 cylinders, total 3907583 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                 129     3,907,007     3,906,879   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        2A6C2D786C2D3FC5                       ntfs                                     
/dev/sda2        16C6E546C6E52729                       ntfs       RECOVERY                      
/dev/sda3: PTTYPE="dos" 
/dev/sda5        7f819db7-03e2-42dc-bf13-795ab4f2aa33   ext4                                     
/dev/sda6        1ae90f8f-926e-48f0-a374-ad0c53ad34e4   swap                                     
/dev/sda7        8590a35a-01aa-4a43-a2a2-e3863334e7ac   ext4                                     
/dev/sda8        055eb43f-8c95-4e87-a4a3-840eab39a33e   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdd1        8019-9E92                              vfat                                     
/dev/sdd: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda8        /                        ext4       (rw,errors=remount-ro)
/dev/sda5        /boot                    ext4       (rw)
/dev/sda7        /home                    ext4       (rw)
/dev/sdd1        /media/8019-9E92         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


============================= sda5/grub/grub.cfg: =============================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,8)'
search --no-floppy --fs-uuid --set 055eb43f-8c95-4e87-a4a3-840eab39a33e
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
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 7f819db7-03e2-42dc-bf13-795ab4f2aa33
set locale_dir=($root)/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 7f819db7-03e2-42dc-bf13-795ab4f2aa33
	linux	/vmlinuz-2.6.32-23-generic root=UUID=055eb43f-8c95-4e87-a4a3-840eab39a33e ro   quiet splash
	initrd	/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 7f819db7-03e2-42dc-bf13-795ab4f2aa33
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/vmlinuz-2.6.32-23-generic root=UUID=055eb43f-8c95-4e87-a4a3-840eab39a33e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 7f819db7-03e2-42dc-bf13-795ab4f2aa33
	linux	/vmlinuz-2.6.32-21-generic root=UUID=055eb43f-8c95-4e87-a4a3-840eab39a33e ro   quiet splash
	initrd	/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 7f819db7-03e2-42dc-bf13-795ab4f2aa33
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/vmlinuz-2.6.32-21-generic root=UUID=055eb43f-8c95-4e87-a4a3-840eab39a33e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 7f819db7-03e2-42dc-bf13-795ab4f2aa33
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 7f819db7-03e2-42dc-bf13-795ab4f2aa33
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 2a6c2d786c2d3fc5
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 16c6e546c6e52729
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== sda5: Location of files loaded by Grub: ===================


  65.9GB: grub/core.img
  65.9GB: grub/grub.cfg
  65.9GB: initrd.img-2.6.32-21-generic
  66.0GB: initrd.img-2.6.32-23-generic
  65.9GB: vmlinuz-2.6.32-21-generic
  65.9GB: vmlinuz-2.6.32-23-generic

=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=055eb43f-8c95-4e87-a4a3-840eab39a33e /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda5 during installation
UUID=7f819db7-03e2-42dc-bf13-795ab4f2aa33 /boot           ext4    defaults        0       2
# /home was on /dev/sda7 during installation
UUID=8590a35a-01aa-4a43-a2a2-e3863334e7ac /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=1ae90f8f-926e-48f0-a374-ad0c53ad34e4 none            swap    sw              0       0

=================== sda8: Location of files loaded by Grub: ===================


 407.1GB: initrd.img
 407.1GB: initrd.img.old
 407.1GB: vmlinuz
 407.1GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdd1

00000000  eb 3c 90 4d 53 44 4f 53  35 2e 30 00 02 40 01 00  |.<.MSDOS5.0..@..|
00000010  02 00 02 00 00 f8 ef 00  3f 00 40 00 81 00 00 00  |........?.@.....|
00000020  3f 9d 3b 00 80 00 29 92  9e 19 80 4e 4f 20 4e 41  |?.;...)....NO NA|
00000030  4d 45 20 20 20 20 46 41  54 31 36 20 20 20 33 c9  |ME    FAT16   3.|
00000040  8e d1 bc fc 7b 16 07 bd  78 00 c5 76 00 1e 56 16  |....{...x..v..V.|
00000050  55 bf 22 05 89 7e 00 89  4e 02 b1 0b fc f3 a4 06  |U."..~..N.......|
00000060  1f bd 00 7c c6 45 fe 0f  38 4e 24 7d 20 8b c1 99  |...|.E..8N$} ...|
00000070  e8 7e 01 83 eb 3a 66 a1  1c 7c 66 3b 07 8a 57 fc  |.~...:f..|f;..W.|
00000080  75 06 80 ca 02 88 56 02  80 c3 10 73 ed 33 c9 fe  |u.....V....s.3..|
00000090  06 d8 7d 8a 46 10 98 f7  66 16 03 46 1c 13 56 1e  |..}.F...f..F..V.|
000000a0  03 46 0e 13 d1 8b 76 11  60 89 46 fc 89 56 fe b8  |.F....v.`.F..V..|
000000b0  20 00 f7 e6 8b 5e 0b 03  c3 48 f7 f3 01 46 fc 11  | ....^...H...F..|
000000c0  4e fe 61 bf 00 07 e8 28  01 72 3e 38 2d 74 17 60  |N.a....(.r>8-t.`|
000000d0  b1 0b be d8 7d f3 a6 61  74 3d 4e 74 09 83 c7 20  |....}..at=Nt... |
000000e0  3b fb 72 e7 eb dd fe 0e  d8 7d 7b a7 be 7f 7d ac  |;.r......}{...}.|
000000f0  98 03 f0 ac 98 40 74 0c  48 74 13 b4 0e bb 07 00  |.....@t.Ht......|
00000100  cd 10 eb ef be 82 7d eb  e6 be 80 7d eb e1 cd 16  |......}....}....|
00000110  5e 1f 66 8f 04 cd 19 be  81 7d 8b 7d 1a 8d 45 fe  |^.f......}.}..E.|
00000120  8a 4e 0d f7 e1 03 46 fc  13 56 fe b1 04 e8 c2 00  |.N....F..V......|
00000130  72 d7 ea 00 02 70 00 52  50 06 53 6a 01 6a 10 91  |r....p.RP.Sj.j..|
00000140  8b 46 18 a2 26 05 96 92  33 d2 f7 f6 91 f7 f6 42  |.F..&...3......B|
00000150  87 ca f7 76 1a 8a f2 8a  e8 c0 cc 02 0a cc b8 01  |...v............|
00000160  02 80 7e 02 0e 75 04 b4  42 8b f4 8a 56 24 cd 13  |..~..u..B...V$..|
00000170  61 61 72 0a 40 75 01 42  03 5e 0b 49 75 77 c3 03  |aar.@u.B.^.Iuw..|
00000180  18 01 27 0d 0a 49 6e 76  61 6c 69 64 20 53 79 73  |..'..Invalid Sys|
00000190  74 65 6d 20 44 69 73 6b  ff 0d 0a 44 69 73 6b 20  |tem Disk...Disk |
000001a0  49 2f 4f 20 65 72 72 6f  72 ff 0d 0a 52 65 70 6c  |I/O error...Repl|
000001b0  61 63 65 20 74 68 65 20  64 69 73 6b 2c 20 61 6e  |ace the disk, an|
000001c0  64 20 74 68 65 6e 20 50  72 65 73 73 20 41 6e 79  |d then Press Any|
000001d0  20 4b 65 79 0d 0a 00 00  49 4f 20 20 20 20 20 20  | Key....IO      |
000001e0  53 59 53 4d 53 44 4f 53  20 20 20 53 59 53 7f 01  |SYSMSDOS   SYS..|
000001f0  00 41 bb 00 07 60 66 6a  00 e9 3b ff 00 00 55 aa  |.A...`fj..;...U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

---

### Post by oldfred on 2010-07-23
Did you end up using gparted to shrink Vista and not remove the checkbox setting to round to cylinders?

Your Vista partition starts at 63 not 2048. 63 was the standard for both Ubuntu and XP but Vista/7 and the newest Ubuntu's use 2048 as the start for the first partition.

Vista7 will work with the partition starting at 63 as it can reinstalled into an XP partition, but the move often confuses it and you have to run windows repairs to get it to see its new location.

Vista or 7 repair
Comments by others:
Repair often does not work, some say run 3 times others recommend the command line bootrec.exe
Always run chkdsk and run again until there are no errors, that may be all that is required

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r /f (may have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

You may want to let it also run the fixmbr so you can directly test that it boots windows ok, but will then have to reinstall grub2 from the liveCD.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Install from LiveCD install on sda5 and want grub2 in drive sda's MBR:
Find linux partition, change sda5 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
sudo mkdir /mnt/sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt /dev/sda

---

### Post by AndyP79 on 2010-07-23
O-my-lord! Oldfredd, I think what might be easier is if I tryagian from the begining? Because this sounds like it may not always work? I don't remember clicking the box to round the cylinders or not. This is probably the most advancedd stuff I ever done, so my head is spinning. If I find out that the above does not work, I can use gparted from the live cd to fully format the whole drive to nothing right? Then start fresh

---

### Post by 29732 on 2010-07-23
sorry bout windows 
by the way, if you ever get it all fixed, i know how to install burg if you didnt already

---

### Post by AndyP79 on 2010-07-27
Okay, So I gave up on this. Trying to dual boot is just way too difficult. Screw Windows. For now, I will just have to go back to printing what I need and filling out applications by hand. This all started because Linux does not have true PDF support. that is time for another post though.
Thanks to everyone for your help and patience.

---

### Post by 29732 on 2010-07-28
maybe we can try again
i can only think of one way:
either formatting the hard drive completely and before that backing up everything and the installing vista first so it'll be the default system and then ubuntu so it should be almost pain-free :P

---

### Post by cj13579 on 2010-07-28
> **29732 said:**
> maybe we can try again
i can only think of one way:
either formatting the hard drive completely and before that backing up everything and the installing vista first so it'll be the default system and then ubuntu so it should be almost pain-free :P

Having set-up multiple dual boots you should make sure that the Windows OS is the first OS on the system as its bootloader is very particular. Also, the Windows CD's generally just re-write the whole disk, which is obviously not ideal if you already have an OS installed.

You can refer to the Ubuntu docs for help on Dual booting: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by 29732 on 2010-07-28
> **cj13579 said:**
> Having set-up multiple dual boots you should make sure that the Windows OS is the first OS on the system as its bootloader is very particular. Also, the Windows CD's generally just re-write the whole disk, which is obviously not ideal if you already have an OS installed.

You can refer to the Ubuntu docs for help on Dual booting: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

well, what he said does look pretty good, try that first

---

### Post by AndyP79 on 2010-07-28
> **29732 said:**
> well, what he said does look pretty good, try that first

okay, so maybe next week, i might give this another shot. I am just getting tired of re-setting everything up after each time i try this. I have at the moment Ubuntu 10.04 loaded up. I have A LOT of PPAs and configurations done to it. What is the best way to do a COMPLETE back-up of what I am currently using? Everything. Everything works great, all my programmes and applications are in place, can I make an exact duplicate of abosloutly eveything on my computer right now? If I can do this, I might give the dual boot another shot, as it is convenient having both systems available. 
Thanks for all ya'lls time on this.
Andy

---

### Post by 29732 on 2010-07-28
make a gedit doc that has all your notes of your programs and ppas and etc. is all i can say

---

### Post by AndyP79 on 2010-07-28
will the gedit doc be able to restore all of them? or is it just a refernece sheet?

---

### Post by oldfred on 2010-07-28
this will list all the packages you have installed:

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

and using synaptic
[http://ubuntuforums.org/showthread.php?t=1057608](http://ubuntuforums.org/showthread.php?t=1057608)

sudo cp /etc/apt/sources.list ~/sources.list.backup
Otherwise if you have added any PPAs or other sources, the tip will only reinstall Ubuntu files,

The gedit file will just be a doc to help you remember what to install.  When I converted to Karmic with a clean install I new I was also going to install on my portable so I tried to do as much as possible from command line. Then I copied history to a bash file and cleaned up the errors and edited out the sudos. I then could run the bash file and it auto reinstalled just about everything.

I also just ran across this but have not tried it. It looks like a general purpose version of what I do.
[http://helpdeskgeek.com/windows-xp-tips/easily-customize-a-fresh-install-of-ubuntu-10-04-with-a-script/](http://helpdeskgeek.com/windows-xp-tips/easily-customize-a-fresh-install-of-ubuntu-10-04-with-a-script/)

You could run that and then still use the dpkg  reinstall procedure.

---

### Post by 29732 on 2010-07-28
lol
those ppl know much more than me on how to backup stuff and references of programs :P

---

### Post by oldfred on 2010-07-28
29732
Almost everything I know is in gedit files.:) It certainly is not in my memory. And I have a lot of info on things I have done to Karmic and now Lucid.

I started by finding answers  with google and found many of the good answers were in this forum. I have learned more just by reviewing other posts and saving lots of useful info. Some info I add to an old Ubuntu Unleashed (6.06) and the rest I add to gedit files.

---

### Post by 29732 on 2010-07-30
> **oldfred said:**
> 29732
Almost everything I know is in gedit files.:) It certainly is not in my memory. And I have a lot of info on things I have done to Karmic and now Lucid.

I started by finding answers  with google and found many of the good answers were in this forum. I have learned more just by reviewing other posts and saving lots of useful info. Some info I add to an old Ubuntu Unleashed (6.06) and the rest I add to gedit files.

I didn't do much to my ubuntu so almost everything is in my head 

i don't really have any books about ubuntu.... all the stuff i learn is either by these forums or trial and error :D i know a website that is like a giant reference to everything but i never get the chance to read at least some of it  

do you have any useful places to learn ubuntu better than i know it now?? 
then i will be somewhat qualified to help people :P

---

### Post by oldfred on 2010-07-30
I have learned from breaking things, usually not intentionally and following those threads with those who know more about many topics than I and learning from them.

Some links:
Ubuntu Documentation:
[http://ubuntu-manual.org/](http://ubuntu-manual.org/)
[https://help.ubuntu.com/10.04/index.html](https://help.ubuntu.com/10.04/index.html)

Do not know how much you have learned so far so maybe these also:
[http://ubuntuforums.org/showthread.php?t=73885](http://ubuntuforums.org/showthread.php?t=73885) (Terminal for Beginners) 
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

