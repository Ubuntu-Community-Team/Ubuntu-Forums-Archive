---
title: "Windows 7 Ubuntu 10.10 dual boot black screen blinking curser after bios splash"
date: 2010-10-27
forum: New to Ubuntu
---

### Post by synthevol on 2010-10-27
Hello,
I have an Acer Aspire 11.6" notebook, can't remember exact series
4 gb of ram
ati radeon hd4225
320 gb toshiba hd

dual boot Ubuntu 10.10 64bit and Windows 7 home 64 bit

The problem that I am having is that after the acer splash screen that allows me to go into bios I get a black screen with a blinking cursor. 

    This started after I installed some updates and shut the computer down for about a week. Before this problem the dual boot system was working fine, I installed all needed updates, including the proprietary ATI and broadcomm drivers. Then the next time I used it I installed some more needed updates, shut it down for the last week and now it won't boot.

Things I have tried.

    Went into the bios and changed the boot order from usb first to the hard drive.

     I held down shift when booting up, when I did this I got Grub Loading. and then below that a blinking cursor and it hung there.

     I used my live usb and was able to boot into Ubuntu Live, checked to make sure the hard drive was there it was under acer and /hd1 I think, both partitions showed up and the data was there, internet access was fine etc on the live boot. Then I powered down hoping that it might work again and had the same black screen.

I have searched the forums and found some fixes however I am a newbie and they didn't make a lot of sense to me, so I'm looking for a way to fix it I guess using a Live USB or a simpler method.

---

### Post by for.i.am.root on 2010-10-27
Did you try sudo grub-install /dev/hdd?

Replace hdd with the name of your hdd. This *might* get rid of the Windowz entry, however, it should get your linux box booting. You can then add the Windowz line back to grub.

I just realized that Ubuntu 10.10 uses the new grub not legacy grub (my preference). I'm not sure how to edit the menu (it's no longer /boot/grub/menu.lst) to re add the Windowz boot line.

---

### Post by synthevol on 2010-10-27
I am having trouble finding what the name of the partiton Ubuntu is on. When I am booted in the live usb it just says 137 gb filesystem.

---

### Post by synthevol on 2010-10-27
Well after reading through tons of articles and forum messages, I used the mount command to find the name of the ubuntu drive, then I tried the sudo grub-install, however it said something about /dev not being mounted I'm guessing that's because I was booted in live and not logged into Ubuntu. So I decided to just go ahead and reinstall ubuntu, since there was nothing important on it. I deleted the partitions, then created a /boot, root, /home and a swap. Grub loaded up fine, and I choose to go into Ubuntu, the only problem now is I have a screen with Ubuntu then 5 circles that keep filling and unfilling under that it says The disk drive for /boot is not ready yet or not present and under that is Continue to wait; or press S to skip mounting or M for manual recovery. It's been roughly 5 minutes at this screen now. Any suggestions for what I should do.

---

### Post by newstargate on 2010-10-28
Hi ..I am having the same problem with different symptoms
my hardware:

ATI Radeon 4800
Intel Core I7
4GB RAm
2 HardDrives:
(/dev/sda) 1 TB that has windows 7 (64) on it
(/dev/sdb) 500 gb that has ubuntu 10.10 (64) on it

I installed ubuntu and updated the ATI driver like what synthevol did ..and started to get the black screen with the blinking dash!
but the funny things ...it sometimes work !! 
stupid scenario:
my pc was off ..I tried to turn it on ..picked ubuntu ..and booted like charm ..then i restarted ..the black screen stuck again !!..then i did many restarts after that still the black screen sticking there with that damned dash ..
then desperately I turn off the pc for a while ..then return it on, then booted without any problems !!!! I am having the same problem ..but it is not permanent 
this is the second installation ..I reinstalled ubuntu twice with the same problem.
the GRUB is working ..coz i can enter windows 7 any time I want ..but ubuntu needs luck :( 
I am newbie to linux distributions so I am hoping to find some support here ..

---

### Post by amjjawad on 2010-10-28
[URL="https://help.ubuntu.com/community/Grub2"]GRUB2
[/URL]
Hope this will help.
If not, please let us know :)

---

### Post by primaxx on 2010-10-28
Did you originally install Ubuntu within Windows (Wubi), or was this a normal installation?

The reason I ask is that I had a somewhat simular problem myselsf, which I generated because I upgraded a Wubi 10.04 installation to 10.10, and in this process I managed to say yes to upgrade Grub as well. This caused Grub to not find any of my os'es after the upgrade. My solution was to make a new, normal installation of Ubuntu.


Rgrds, Primaxx

---

### Post by amjjawad on 2010-10-28
> **synthevol said:**
> I am having trouble finding what the name of the partiton Ubuntu is on. When I am booted in the live usb it just says 137 gb filesystem.

Check my signature, there are two links you need to look at: Your first step and Beginners Guide.
These guides won't answer your question directly but as a new Ubuntu User, you need to take a look at these :)

---

### Post by newstargate on 2010-10-28
> **amjjawad said:**
> [URL="https://help.ubuntu.com/community/Grub2"]GRUB2
[/URL]
Hope this will help.
If not, please let us know :)

my GRUB is already version 2
and i dont think it is boot manager problem ..
another idea ?:(

---

### Post by amjjawad on 2010-10-28
> **newstargate said:**
> my GRUB is already version 2
and i dont think it is boot manager problem ..
another idea ?:(

I know it's already GRUB2 :)
That was a link. Did you check it? That should be your first step anyway before even posting here in this forum :)

Check and let us know.

---

### Post by newstargate on 2010-10-28
> **amjjawad said:**
> I know it's already GRUB2 :)
That was a link. Did you check it? That should be your first step anyway before even posting here in this forum :)

Check and let us know.


thnx amjjawad for supporting and yes i read it  but no use...

here is a new information ..while i was diggin , i saw this way to disable the quiet splash so u can see what is goin on ..

in the grub menu (press shift while booting if the grub menu doesnt appear)

press "e" 
then locate "quiet splash" and delete it
then ctrl+x to boot

i had to restart many times so it stuck again ..lol ..and i took a picture of the output where it stuck

[here]("http://www.iimmgg.com/image/2f12f89a6216e97d382e009a8e307b2c")

what bothers me the most is it sometimes gets over this line and complete the boot successfully  
any ideas ? does the CD-ROM have anything to do with this problem !?

[IMG]http://www.iimmgg.com/image/2f12f89a6216e97d382e009a8e307b2c[/IMG]

---

### Post by amjjawad on 2010-10-28
> **newstargate said:**
> thnx amjjawad for supporting and yes i read it  but no use...

here is a new information ..while i was diggin , i saw this way to disable the quit splash so u can see what is goin on ..

in the grub menu (press shift while booting if the grub menu doesnt appear)

press "e" 
then locate "quit splash" and delete it
then ctrl+x to boot

i had to restart many times so it stuck again ..lol ..and i took a picture of the output where it stuck

[here]("http://www.iimmgg.com/image/2f12f89a6216e97d382e009a8e307b2c")

any ideas ? does the CD-ROM have anything to do with this problem !?

[IMG]http://www.iimmgg.com/image/2f12f89a6216e97d382e009a8e307b2c[/IMG]

Okay, I'm very sorry, I missed one of your posts so I posted the wrong info.

First thing first, you had Windows 7 installed then you re-installed Ubuntu 10.10 from your LiveCD/USB, correct?
I see you followed an old unnecessary partitioning scheme. /boot is no longer required.
You could have done this:
/ (root)
/home
swap
3 partitions only.

When you installed Ubuntu 10.10, where did you choose to install GRUB2? did you install it in the MBR? or you installed it in Ubuntu's partition?

---

### Post by newstargate on 2010-10-28
> **amjjawad said:**
> Okay, I'm very sorry, I missed one of your posts so I posted the wrong info.

First thing first, you had Windows 7 installed then you re-installed Ubuntu 10.10 from your LiveCD/USB, correct?
I see you followed an old unnecessary partitioning scheme. /boot is no longer required.
You could have done this:
/ (root)
/home
swap
3 partitions only.

When you installed Ubuntu 10.10, where did you choose to install GRUB2? did you install it in the MBR? or you installed it in Ubuntu's partition?


thanks alot for responding 
first i installed it like u said ..only three partitions the "/" and the home and swap ..
now where did i installed the grub2:
in the installation phase where the manual partitioning resides 
there is a combo box to choose where to install grub2
it has many items:
sda (the root of the sda tree -this is how i understood it)
sda1 windows 7 loader 
sda2 (c: i think)
sda2 (d: i think)
sdb (the root of the other hard which contains linux partitions)
.... and other items ..
now what did i select? it was by default the first item "sda 1TB"
so i didnt change it .
and based on the picture i took i think the problem is related to mounting some device ..idk ..

---

### Post by wilee-nilee on 2010-10-28
Post the bootscript in my signature, use code tags when posting the text please. Follow the instructions for code tags in my sig or just click on the (#) in the reply panel and put the text in between. Really without the information that is part of running this script we are just flailing in the dark.

---

### Post by newstargate on 2010-10-28
> **wilee-nilee said:**
> Post the bootscript in my signature, use code tags when posting the text please. Follow the instructions for code tags in my sig or just click on the (#) in the reply panel and put the text in between. Really without the information that is part of running this script we are just flailing in the dark.


ok am on it

---

### Post by amjjawad on 2010-10-28
> **newstargate said:**
> thanks alot for responding 
first i installed it like u said ..only three partitions the "/" and the home and swap ..
now where did i installed the grub2:
in the installation phase where the manual partitioning resides 
there is a combo box to choose where to install grub2
it has many items:
sda (the root of the sda tree -this is how i understood it)
sda1 windows 7 loader 
sda2 (c: i think)
sda2 (d: i think)
sdb (the root of the other hard which contains linux partitions)
.... and other items ..
now what did i select? it was by default the first item "sda 1TB"
so i didnt change it .
and based on the picture i took i think the problem is related to mounting some device ..idk ..

It means you installed GRUB2 (Ubuntu's boot loader) in the MBR. Which means, Windows Boot Loader is overwritten. I had this issue before a month but honestly all what I remember is I formatted and installed again, or perhaps I did something else? not really sure.
Hmmm, how about remove Ubuntu, fix the MBR so that you could boot into Windows then re-install Ubuntu again. I'm just concerned you re-installed without format and that could be the wrong move. I suggest to fix the MBR first then install Ubuntu.
Anyhow, before you install Ubuntu, just make sure everything is working perfectly from the live session (LiveCD/USB). I never install unless everything is fine.

:)

---

### Post by amjjawad on 2010-10-28
You got me guys. I forgot that this thread was started by [synthevol]("http://ubuntuforums.org/member.php?u=1176255")You need to start your own thread, newstargate because it's not allowed.

Anyhow, it's okay for now, after all, I'm not an admin but most probably the admins will advise you the same if they'll see this.

Never mind. Hope we could walk you through to fix your issue and same goes to synthevol even though I didn't read anything from him yet :)

---

### Post by wilee-nilee on 2010-10-28
> **amjjawad said:**
> It means you installed GRUB2 (Ubuntu's boot loader) in the MBR. Which means, Windows Boot Loader is overwritten. **I had this issue before a month but honestly all what I remember is I formatted and installed again, or perhaps I did something else? not really sure.**
Hmmm, how about remove Ubuntu, fix the MBR so that you could boot into Windows then re-install Ubuntu again. I'm just concerned you re-installed without format and that could be the wrong move. I suggest to fix the MBR first then install Ubuntu.
Anyhow, before you install Ubuntu, just make sure everything is working perfectly from the live session (LiveCD/USB). I never install unless everything is fine.

:)

There are very good helpers on this forum that specialize in this specific area amongst others, lets see the bootscript before anything else is done here. 

We are talking about somebodies OS which should at the least be the first in line rather then our personal needs to help somebody.;)

---

### Post by newstargate on 2010-10-28
here u go mr wilee-nilee

```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

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

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   513,779,711   513,572,864   7 HPFS/NTFS
/dev/sda3         513,779,712 1,232,625,663   718,845,952   7 HPFS/NTFS
/dev/sda4       1,232,625,664 1,953,521,663   720,896,000   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,046   211,146,751   211,144,706   5 Extended
/dev/sdb5               2,048    15,624,191    15,622,144  82 Linux swap / Solaris
/dev/sdb6          15,626,240   211,146,751   195,520,512  83 Linux
/dev/sdb2         211,146,752   406,458,367   195,311,616  83 Linux
/dev/sdb3         406,458,368   976,771,071   570,312,704  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 65 MB, 65536000 bytes
5 heads, 32 sectors/track, 800 cylinders, total 128000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             32       127,997       127,966   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        86C8262BC8261A47                       ntfs       System Reserved               
/dev/sda2        34621C12621BD786                       ntfs                                     
/dev/sda3        107A8BAB7A8B8C62                       ntfs       Programs                      
/dev/sda4        181E8F4B1E8F20BC                       ntfs       Learning                      
/dev/sda: PTTYPE="dos" 
/dev/sdb1: PTTYPE="dos" 
/dev/sdb2        03e014f7-046a-476b-a63a-7eaf775cbaed   ext4                                     
/dev/sdb5        6b5194f6-35de-45bd-8ca9-08189dabe3e0   swap                                     
/dev/sdb6        7fd351d3-a366-436c-aae9-3617758d8f94   ext4                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        208E-DC5A                              vfat       KAIN                          
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb2        /home                    ext4       (rw,commit=0)
/dev/sdc1        /media/KAIN              vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sda3        /media/Programs          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sr0         /media/Repair disc Windows 7 64-bit udf        (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077)


=========================== sdb6/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set 7fd351d3-a366-436c-aae9-3617758d8f94
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set 7fd351d3-a366-436c-aae9-3617758d8f94
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
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 7fd351d3-a366-436c-aae9-3617758d8f94
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=7fd351d3-a366-436c-aae9-3617758d8f94 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 7fd351d3-a366-436c-aae9-3617758d8f94
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=7fd351d3-a366-436c-aae9-3617758d8f94 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 7fd351d3-a366-436c-aae9-3617758d8f94
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 7fd351d3-a366-436c-aae9-3617758d8f94
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 86c8262bc8261a47
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

=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb6 during installation
UUID=7fd351d3-a366-436c-aae9-3617758d8f94 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb2 during installation
UUID=03e014f7-046a-476b-a63a-7eaf775cbaed /home           ext4    defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=6b5194f6-35de-45bd-8ca9-08189dabe3e0 none            swap    sw              0       0

=================== sdb6: Location of files loaded by Grub: ===================


  16.7GB: boot/grub/core.img
  42.6GB: boot/grub/grub.cfg
   9.0GB: boot/initrd.img-2.6.35-22-generic
  16.7GB: boot/vmlinuz-2.6.35-22-generic
   9.0GB: initrd.img
  16.7GB: vmlinuz


```

..plz give me a solution that doesnt include formatting ..coz i've been working on ubuntu for 3 days ..and i customized it so much ..it will take time to redo all that ...and as i told u ..this problem only happens 50% of times i boot !!

---

### Post by Mark Phelps on 2010-10-28
newstargate:

Some problems stand out ...

First, the presence of the /grldr directory in your Win7 boot partition indicates that you installed using Wubi -- because that directory holds the GRUB4DOS files that Wubi uses.  Wubi does NOT use GRUB, so obviously, installing or reinstalling GRUB is not going to fix problems with Wubi.

Second, you apparent DID install GRUB anyway.  That's not going to help the Wubi situation, and in many cases, installing GRUB to the Win7 boot partition hoses up Win7 as well.

---

### Post by newstargate on 2010-10-28
> **Mark Phelps said:**
> newstargate:

Some problems stand out ...

First, the presence of the /grldr directory in your Win7 boot partition indicates that you installed using Wubi -- because that directory holds the GRUB4DOS files that Wubi uses.  Wubi does NOT use GRUB, so obviously, installing or reinstalling GRUB is not going to fix problems with Wubi.

Second, you apparent DID install GRUB anyway.  That's not going to help the Wubi situation, and in many cases, installing GRUB to the Win7 boot partition hoses up Win7 as well.


nop i didnt use Wubi , i used the LiveCD
but the problem seems to be that i didnt change the path of installing the boot manager (GRUB2) so it got installed over the MBR
but windows 7 is still working with no problem ..

i just dont want to use it anymore (after i used ubuntu everything changed)
 though i am C# programmer ..but i liked ubuntu so much ..especially the virtualbox ..whatever ..

plz i need a solution ..and sry for asking too much

---

### Post by wilee-nilee on 2010-10-28
I think you just need to put the sdb hd first to be read in the bios and install the grub bootloader to the mbr of sdb. If this works you can reload the MS bootloader to sda if you want to have the choice to do direct booting to it by having that HD read first with a key prompt.

Here is a link for grub2 that defaults to the live cd reinstall instructions. I assume since you can write code you can follow these instructions in the link.;)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by newstargate on 2010-10-28
> **wilee-nilee said:**
> I think you just need to put the sdb hd first to be read in the bios and install the grub bootloader to the mbr of sdb. If this works you can reload the MS bootloader to sda if you want to have the choice to do direct booting to it by having that HD read first with a key prompt.

Here is a link for grub2 that defaults to the live cd reinstall instructions. I assume since you can write code you can follow these instructions in the link.;)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

thanks alot ..i will try that on my VirtualBox (which i simulated the situation there) and then do it on my physical pc ..it will take some time ..when it finishes i will give u a feedback ..thanks alot for responding ..

---

### Post by wilee-nilee on 2010-10-28
Thread starter you may also want to post the bootscript as well for help.

---

### Post by newstargate on 2010-10-28
ok ..i did everything ..look :
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

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

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   513,779,711   513,572,864   7 HPFS/NTFS
/dev/sda3         513,779,712 1,232,625,663   718,845,952   7 HPFS/NTFS
/dev/sda4       1,232,625,664 1,953,521,663   720,896,000   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,046   211,146,751   211,144,706   5 Extended
/dev/sdb5               2,048    15,624,191    15,622,144  82 Linux swap / Solaris
/dev/sdb6          15,626,240   211,146,751   195,520,512  83 Linux
/dev/sdb2         211,146,752   406,458,367   195,311,616  83 Linux
/dev/sdb3         406,458,368   976,771,071   570,312,704  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        86C8262BC8261A47                       ntfs       System Reserved               
/dev/sda2        34621C12621BD786                       ntfs                                     
/dev/sda3        107A8BAB7A8B8C62                       ntfs       Programs                      
/dev/sda4        181E8F4B1E8F20BC                       ntfs       Learning                      
/dev/sda: PTTYPE="dos" 
/dev/sdb1: PTTYPE="dos" 
/dev/sdb2        03e014f7-046a-476b-a63a-7eaf775cbaed   ext4                                     
/dev/sdb5        6b5194f6-35de-45bd-8ca9-08189dabe3e0   swap                                     
/dev/sdb6        7fd351d3-a366-436c-aae9-3617758d8f94   ext4                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb2        /home                    ext4       (rw,commit=0)
/dev/sda3        /media/Programs          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sdb6/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set 7fd351d3-a366-436c-aae9-3617758d8f94
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set 7fd351d3-a366-436c-aae9-3617758d8f94
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
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 7fd351d3-a366-436c-aae9-3617758d8f94
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=7fd351d3-a366-436c-aae9-3617758d8f94 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 7fd351d3-a366-436c-aae9-3617758d8f94
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=7fd351d3-a366-436c-aae9-3617758d8f94 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 7fd351d3-a366-436c-aae9-3617758d8f94
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 7fd351d3-a366-436c-aae9-3617758d8f94
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 86c8262bc8261a47
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

=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb6 during installation
UUID=7fd351d3-a366-436c-aae9-3617758d8f94 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb2 during installation
UUID=03e014f7-046a-476b-a63a-7eaf775cbaed /home           ext4    defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=6b5194f6-35de-45bd-8ca9-08189dabe3e0 none            swap    sw              0       0

=================== sdb6: Location of files loaded by Grub: ===================


  16.7GB: boot/grub/core.img
  34.2GB: boot/grub/grub.cfg
   9.0GB: boot/initrd.img-2.6.35-22-generic
  16.7GB: boot/vmlinuz-2.6.35-22-generic
   9.0GB: initrd.img
  16.7GB: vmlinuz
```as we can see i have 2 grubs now ..i changed the boot priority (from bios) to the sdb so i will use the second grub
and retry ..same problem :( 
usually i need to do two restarts to boot successfully 
so plz review the pic i posted b4  ([here]("http://www.iimmgg.com/image/2f12f89a6216e97d382e009a8e307b2c")) where the booting always stuck..
sry ..but i am starting to loose hope ..and i think i need to live with it :(

---

### Post by newstargate on 2010-10-28
unsolvable ?

---

### Post by wilee-nilee on 2010-10-28
> **newstargate said:**
> unsolvable ?

You have multiple partitions in sdb that listed one as linux what are those?
sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

---

### Post by newstargate on 2010-10-28
> **wilee-nilee said:**
> You have multiple partitions in sdb that listed one as linux what are those?
sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb2: is the home partition
sdb3: was unused ..i just formatted it and made it NTFS

---

### Post by wilee-nilee on 2010-10-28
That is good information I suspected one was home. This actually makes it easier to just reload Ubuntu if needed in the partition it is in, and making sure that the grub bootloader goes to the mbr of the HD that Ubuntu is in. You have to do a custom install with maverick to have this grub placement option though.

I think we need sharper minds to look at this though with the /bootmgr /Boot/BCD **/grldr** being part of the picture. 

Personally If it was me since you have done a lot of work but all the time doing it you had the bootloader on the wrong partition or the grldr being part of the problem I would chock that up to learning and not limit us on line with asking for specificities in what your willing to do.

If it was me I would just wipe sdb6 reinstall make sure grub goes to the sdb mbr and that it is first in line to me read. Not sure if this is the answer but that is my methodology. I don't mess with fixing things much. I have everything always backed up and hard copies of all my OS.

Really though waiting for a more knowledgeable helper might be the best route as of now.

Sorry I can't be more of help I have to get back to my college studies.

---

### Post by port80web on 2010-10-28
> **for.i.am.root said:**
> Did you try sudo grub-install /dev/hdd?

Replace hdd with the name of your hdd. This *might* get rid of the Windowz entry, however, it should get your linux box booting. You can then add the Windowz line back to grub.

I just realized that Ubuntu 10.10 uses the new grub not legacy grub (my preference). I'm not sure how to edit the menu (it's no longer /boot/grub/menu.lst) to re add the Windowz boot line.

Just to let you all know the new grub (not my favorite either) has some important changes.
[http://www.gnu.org/software/grub/manual/grub.html#Changes-from-GRUB-Legacy](http://www.gnu.org/software/grub/manual/grub.html#Changes-from-GRUB-Legacy)

---

### Post by amjjawad on 2010-10-29
> **port80web said:**
> Just to let you all know the new grub (not my favorite either) has some important changes.
[http://www.gnu.org/software/grub/manual/grub.html#Changes-from-GRUB-Legacy](http://www.gnu.org/software/grub/manual/grub.html#Changes-from-GRUB-Legacy)

GRUB2 was the boot loader for Ubuntu since 9.10.
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by keefytee on 2010-11-15
What an absolute piece or junk

I have done 2 complete installs on a fresh ocz vertex turbo ss hard drive and both times it just defaults to a blinking cursor, please dont say do this and do that i am a linux n00bie and it would be straight over my head.

I can tell you that i can install red hat 6 and it installs and boots properly, how can Ubuntu expect any uptake on an o/s that clearly has this issue and no doubt you need to be some kinda linux guru to fix it and make it boot.

Sorry forgot to say i am NOT trying to install this on a windows dual boot set up either

---

### Post by amjjawad on 2010-11-15
> **keefytee said:**
> What an absolute piece or junk

I have done 2 complete installs on a fresh ocz vertex turbo ss hard drive and both times it just defaults to a blinking cursor,_** please dont say do this and do that i am a linux n00bie**_ and it would be straight over my head.

I can tell you that i can install red hat 6 and it installs and boots properly, how can Ubuntu expect any uptake on an o/s that clearly has this issue and no doubt you need to be some kinda linux guru to fix it and make it boot.

Sorry forgot to say i am NOT trying to install this on a windows dual boot set up either

Then how are we suppose to help then? unless you're just sharing your experience with us so that's different story.

Linux is not Windows, period. Don't expect miracles from FREE Operating System. You get what you pay for and I believe you paid NOTHING to get Ubuntu. However, I've used Windows for 10 years and I'm MORE than happy to be a Linux User. I don't need Windows in my life anymore :)

Good luck!

---

### Post by keefytee on 2010-11-15
A very good point you do get what you pay for and if i HAD paid for Ubuntu i would want my money back.

---

### Post by amjjawad on 2010-11-15
> **keefytee said:**
> A very good point you do get what you pay for and if i HAD paid for Ubuntu i would want my money back.

I had done perhaps 100 installations for the last two months for many Linux Distributions. Unquestionably, not all were successful but that was never a problem. There are over 650 Linux Distributions and there are many new every day. If I have a problem with one and if I don't want to waste few mins over google to search how could possibly fix that problem, I would simply go for another option. That's the power of Linux.

[http://distrowatch.com/](http://distrowatch.com/)

As an advice for you and for everyone else. "***NO OS IS PERFECT, PERIOD.***"
Sorry for the CAPS, I don't mean anything but that's the golden rule in Computer World.
Actually, if there is a perfect OS, everyone would use it so you probably won't find so many Operating Systems.

Good luck with whatever meets your needs :)

---

### Post by wilee-nilee on 2010-11-15
> **keefytee said:**
> A very good point you do get what you pay for and if i HAD paid for Ubuntu i would want my money back.

You might just be making a simple mistake such as where you put the bootloader. If you want to just disregard a open source setup that is your prerogative. It is not that difficult. Ask for some help if you need and start a thread for it.;)

---

### Post by keefytee on 2010-11-15
The point that i am trying to make is that ubuntu for one is trying to make itself more user friendly and mainstream but it is NEVER EVER going to get non believers who have used windoze since 3.1. Its too complicated and involved for everyday doofus's like me to use happily :)

---

### Post by amjjawad on 2010-11-15
> **keefytee said:**
> The point that i am trying to make is that ubuntu for one is trying to make itself more user friendly and mainstream but it is NEVER EVER going to get non believers who have used windoze since 3.1. Its too complicated and involved for everyday doofus's like me to use happily :)

I got your point from your first 3 words ;)

Whenever you have time, check this out: [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by keefytee on 2010-11-15
over-zealous Linux users <----- lol i rest my case :guitar:

---

### Post by keefytee on 2010-11-15
oh and if there is a "retards guide to using Linux" could you point me in the direction of it please :confused:

---

