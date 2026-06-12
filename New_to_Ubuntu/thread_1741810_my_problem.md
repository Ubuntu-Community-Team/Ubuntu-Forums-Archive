---
title: "my problem"
date: 2011-04-28
forum: New to Ubuntu
---

### Post by nooneastern on 2011-04-28
well first off i LOVE Ubuntu (both in look and performance)
so i will try to explain as best i can what my problem is
sorry if this is long or doesn't make sense....
i've tried to install Ubuntu 4 times in the past few days
3 times with the WUBI installer
and this 4th time with a burned CD

each time has had the same result
it installs perfectly
it runs perfectly
i update all the files through the update manager and customize everything
i am able to restart or shutdown 3 or 4 times no problem
but at some point the same thing happens
when the computer starts
it loads the GRUB screen without issue
i choose Ubuntu
a screen pops up with a blinking cursor in the top left corner
then some words flash by
then the cursor comes back but is no longer blinking
and there is no disc activity

i have no idea what is causing this
even the "recovery mode" doesn't work
i'd love to get rid of Windows completely
and i was planning on having tried Ubuntu for a few days by now
and had planned to switch over entirely today when the new version of Ubuntu came out

any suggestions for me ?
or is there any info about my computer i could give that might make this more obvious to someone much smarter about all this than me ?

---

### Post by Rubi1200 on 2011-04-28
Hi and welcome to the forums :-)

Is Windows booting normally?

Take a look here for solutions:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

Most likely problem # 2, solution #1.

Let me know what happens.

---

### Post by josephmills on 2011-04-28
> **nooneastern said:**
> well first off i LOVE Ubuntu (both in look and performance)
so i will try to explain as best i can what my problem is
sorry if this is long or doesn't make sense....
i've tried to install Ubuntu 4 times in the past few days
3 times with the WUBI installer
and this 4th time with a burned CD

each time has had the same result
it installs perfectly
it runs perfectly
i update all the files through the update manager and customize everything
i am able to restart or shutdown 3 or 4 times no problem
but at some point the same thing happens
when the computer starts
it loads the GRUB screen without issue
i choose Ubuntu
a screen pops up with a blinking cursor in the top left corner
then some words flash by
then the cursor comes back but is no longer blinking
and there is no disc activity

i have no idea what is causing this
even the "recovery mode" doesn't work
i'd love to get rid of Windows completely
and i was planning on having tried Ubuntu for a few days by now
and had planned to switch over entirely today when the new version of Ubuntu came out

any suggestions for me ?
or is there any info about my computer i could give that might make this more obvious to someone much smarter about all this than me ?
please take out any ip or hw address open up your terminal and type in 
```

lshw

```
that will give us all your hardware in the computer that is seen.

---

### Post by nooneastern on 2011-04-28
thanks for the quick reply Rubi1200
yes, Windows is loading perfectly fine and working perfectly fine

i will try your suggestion

but before i do --
i should let you know this current install of Ubuntu i have is NOT from the Windows Installer
will that make a difference ?

this install is from a CD i burned of Ubuntu 10
i just downloaded Ubuntu 11 and was wondering if there was a way to use that disc to correct this somehow

---

### Post by nooneastern on 2011-04-28
hello joesphmills

thanks for your reply too
i would love to run that
but i can't get into Ubuntu in order to run the terminal

---

### Post by nooneastern on 2011-04-28
could this possibly be because of the three previous installs of Ubuntu i did using WUBI ?
maybe somehow something is lingering from that install ?

---

### Post by nooneastern on 2011-04-28
sorry for another post to my thread ...

i am considering just installing the new version of Ubuntu and killing my Windows entirely
since it seems GRUB is the culprit it would probably work a lot better without Windows at all
and if Ubuntu would load every time i would have no use for Windows anyway...

is that foolish thinking on my part ?

---

### Post by Rubi1200 on 2011-04-28
Wait, stop!!! 

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. Before you do anything else, do the following so we can see what is really going on with your system:

---

### Post by nooneastern on 2011-04-28
ok awesome
i am going to try this right now
thanks again !

---

### Post by nooneastern on 2011-04-28
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #8 for (,msdos8)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  DEll Restore: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

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
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         80,325    47,231,099    47,150,775   7 HPFS/NTFS
/dev/sda3         149,934,645   156,232,124     6,297,480  db CP/M / CTOS / ...
/dev/sda4          47,231,161   149,934,644   102,703,484   f W95 Ext d (LBA)
/dev/sda5          47,231,163    83,715,628    36,484,466   7 HPFS/NTFS
/dev/sda6         109,001,088   145,854,134    36,853,047   7 HPFS/NTFS
/dev/sda7         145,854,198   149,934,644     4,080,447   7 HPFS/NTFS
/dev/sda8          83,716,096   107,839,487    24,123,392  83 Linux
/dev/sda9         107,841,536   109,000,703     1,159,168  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1              16,128   320,159,384   320,143,257   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   976,768,064   976,768,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        07D6-0103                              vfat       DellUtility                   
/dev/sda2        8480BD7C80BD7570                       ntfs                                     
/dev/sda3                                               vfat       DellRestore                   
/dev/sda4: PTTYPE="dos" 
/dev/sda5        01CB52B8421D55F0                       ntfs                                     
/dev/sda6        01CC01AD3434D770                       ntfs                                     
/dev/sda7        01CBC45C2108EEE0                       ntfs                                     
/dev/sda8        d9f8b212-015d-4d48-a089-547bc8e89b5a   ext4                                     
/dev/sda9        977eb7e1-d291-41fb-926c-68d7c88ebbfa   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        D214B0A014B0894E                       ntfs                                    
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        4C4C901C4C8FFF40                       ntfs                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sda8/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set d9f8b212-015d-4d48-a089-547bc8e89b5a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set d9f8b212-015d-4d48-a089-547bc8e89b5a
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set d9f8b212-015d-4d48-a089-547bc8e89b5a
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=d9f8b212-015d-4d48-a089-547bc8e89b5a ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set d9f8b212-015d-4d48-a089-547bc8e89b5a
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=d9f8b212-015d-4d48-a089-547bc8e89b5a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set d9f8b212-015d-4d48-a089-547bc8e89b5a
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=d9f8b212-015d-4d48-a089-547bc8e89b5a ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set d9f8b212-015d-4d48-a089-547bc8e89b5a
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=d9f8b212-015d-4d48-a089-547bc8e89b5a ro single 
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
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set d9f8b212-015d-4d48-a089-547bc8e89b5a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set d9f8b212-015d-4d48-a089-547bc8e89b5a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Dell Utility Partition (on /dev/sda1)" {
    insmod part_msdos
    insmod fat
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 07d6-0103
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 8480bd7c80bd7570
    drivemap -s (hd0) ${root}
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
UUID=d9f8b212-015d-4d48-a089-547bc8e89b5a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=977eb7e1-d291-41fb-926c-68d7c88ebbfa none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda8: Location of files loaded by Grub: ===================


  43.5GB: boot/grub/core.img
  53.8GB: boot/grub/grub.cfg
  44.3GB: boot/initrd.img-2.6.35-22-generic
  44.4GB: boot/initrd.img-2.6.35-28-generic
  44.2GB: boot/vmlinuz-2.6.35-22-generic
  44.2GB: boot/vmlinuz-2.6.35-28-generic
  44.4GB: initrd.img
  44.3GB: initrd.img.old
  44.2GB: vmlinuz
  44.2GB: vmlinuz.old

```

---

### Post by nooneastern on 2011-04-28
my ultimate goal here is a Windows-free setup
with JUST Ubuntu running

i am ready to re-install Ubuntu and eliminate Windows once i get this squared away

---

### Post by Rubi1200 on 2011-04-28
A very quick look at the results suggests everything is normal. So, the problem is likely a graphics issue.

What graphics card do you have installed?

---

### Post by ayenack on 2011-04-28
Have you tried Ubuntu 10.04 LTS? (Long Term Support). These LTS releases tend to be more stable releases. It won't have all the latest gimmicks but if it loads and stays stable them that's what I'd go for until the next LTS release.

For the time being I would not remove Windows.

Also have you tried running the install without any customisation and/or not updating it to see if these could be causing the problem.

Could well be a graphics card problem but seems strange that it'd take a couple of days to manifest.

---

### Post by nooneastern on 2011-04-28
thanks for all the awesome help guys
this is yet another reason why i want to use Ubuntu
the friendly folks

i don't know what kind of graphics card i have
is that something i can find out from within Windows ?

i agree that the fact that the problem takes time to manifest makes it tougher to figure out
not sure which Ubuntu i have installed
it's whichever one was the "main" one before today

i am desperate to make this work

---

### Post by eriktheblu on 2011-04-28
> **nooneastern said:**
> 
i don't know what kind of graphics card i have
is that something i can find out from within Windows ?Yup. Check your device manager in the control panel.

> not sure which Ubuntu i have installed
it's whichever one was the "main" one before today10.10 (according to the boot script). This is a "normal" release which comes out every 6 months. The Long Term Support (LTS) comes out every 2 years and are generally considered more stable. The current LTS release is 10.04.

---

### Post by Rubi1200 on 2011-04-28
According to the script you have 10.10 with the latest kernel installed.

Graphics card; in Windows > To open Device Manager, click **Start**, and then click **Control Panel**. Click **Performance and Maintenance**, and then click **System**. On the **Hardware** tab, click **Device Manager**. 

You should be able to find out from there.

---

### Post by nooneastern on 2011-04-28
sorry to be a dunce here guys but i am in my device manager and there is no "graphics card" listed ?

jumps from "Floppy Disk Drives" and "Human Interfaces Device"
nothing in between them

is there a different sub heading i can look in ?
there is one called "Monitors" that only has "Plug and Play Monitor" listed

i have a Dell setup if that helps ... everything in it (aside from the hard drives) is still Dell from the factory

---

### Post by nooneastern on 2011-04-28
there is also Display Adapters with this in it:
Intel(R) 82865G Graphics Controller

is that what you need to know ?

---

### Post by Rubi1200 on 2011-04-28
Yes, that is the graphics card.

Okay, here is what you need to do to hopefully get this working:

Put the LiveCD in and boot up;

when you see the Ubuntu logo hit Enter;

Important:: hit F6 and then Esc to see the boot line

**file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --**

Now, move the cursor backwards with the arrow key and add the following parameter:

i915.modeset=1

In other words, the boot should look like this:

**file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash i915.modeset=1 --**

Now hit Enter and hopefully you will be at the desktop.

This is only to get you back in. If it works, we can make it more permanent for future boots.

---

### Post by nooneastern on 2011-04-28
ok i did what you said and now am using the Live disk 
what happens now ?
will this fix my real install too ?

i will wait to hear from you before i restart again
\

thanks so much so far ....

---

### Post by Dutch70 on 2011-04-28
I haven't been following this thread, but whatever you do on the live cd, you will have to do with your install too.

---

### Post by nooneastern on 2011-04-28
thanks for the tip man
that's what i figured
i just don't know how to apply that to my install

---

### Post by Dutch70 on 2011-04-28
You're welcome.

I believe you hit "e" while booting and edit it there. That's about all I can tell you, as I've never used it myself.

---

### Post by nooneastern on 2011-04-28
ok
i hit "e" at the grub screen and edited the boot
i added the modeset line to the boot command
it still did not load up

hmmm

---

### Post by ayenack on 2011-04-28
You're running 10.10 according to the info you've given.

When you do finally get back into Ubuntu you can type this in terminal to find out what version you're running:-

**lsb_release -a**

If you're using the same LiveCD you used to install Ubuntu with you can do it with the LiveCD as well.

I don't think this is a graphics problem personally if it was it would normally present immediately.

If you have no important info on the install I suggest re-installing then not updating or customising in any way and see if the install last. If it does try updating and see what happens, by using a process of elimination and patience you should be able to work out what's happening.

Also I'd suggest not logging into Windows at all while you have the new install and see if the install last Windows may be doing something weird.

You could also install Ubuntu 10.04 LTS and see if that works any better I would most certainly try this.

NOTE:-

I had a really strange problem a bit like yours once when I was installing Ubuntu 10.04 on a Mac PowerBook G4 PPC. I'd install and the thing would work fine other than wireless and graphics, wireless was an easy fix but graphics was more or less un-fixable, anyway I'd install and things would work after a bit of tweaking and I could restart and things would be fine but as soon as I shutdown (powered off) and restarted I'd get a black screen and not be able to boot into Ubuntu after some serious patience and scratching of head I finally managed to get everything working (it was a graphics problem which at the time wasn't well documented and I pretty much had to sort it myself). But perseverance and patience got me there in the end.... So I suppose what I'm trying to say to you is stick at it and you'll get there in the end.

---

### Post by nooneastern on 2011-04-30
ok update on my situation here  i re-installed EVERYTHING (i had only installed Windows about a month ago and keep my system partition separate from everything else so i didn't lose anything) so no big deal  after i installed Windows i re-installed Ubuntu through the WUBI it's probably the 11 version, since i re-downloaded it after the update  i never even made it into my desktop once this time even though the install went perfectly and everything  i tried using the modeset idea to log in still with no luck  i am not going to give up though this LTS version you are talking about ... if i download the ISO of it will it have a WUBI installer so i can just try it easily before committing to it ?  are there any other known issues other than the graphic one that could be causing this ? you guys have been so helpful so far ...

---

### Post by ayenack on 2011-04-30
Yes the LTS version has wubi so you can install within Windows no problem. It's worrying that 11 won't install either. Maybe hardware problem.

It seems to point to a hardware problem of some kind if the wubi install and the native install will not work .

I've got a feeling there's something deeper going on here and to be honest it'll be very difficult to solve on the forums.

What I find strange is that it'll work fine and then stop working for apparently no reason this, should not happen. It suggest that something is happening to a config file or GRUB but it's just so hard to work though without being hands on.

Give 10.04 LTS a try and report back.


Do you have detailed specs for your system or the model no/name?

The more info the better.

BTW. This isn't a Dell server machine by any chance is it?

---

### Post by Dutch70 on 2011-04-30
Well you've changed boats in the middle of the river. :)
Here is all I can tell you about Wubi.
[[COLOR="RoyalBlue"]Wubi[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1639198")

I'm sure this hasn't been updated, but it will still have some good info.
[[COLOR="RoyalBlue"]http://www.psychocats.net/ubuntu/wubi[/COLOR]]("http://www.psychocats.net/ubuntu/wubi")

---

### Post by nooneastern on 2011-04-30
well i didn't change boats on purpose
i was doing some messing around on my own late at night
and ended up screwing both operating systems 
(this is a good argument against doing things while tired and frustrated)

what kind of specs would be helpful ?
i could download Everest for Windows and get a pretty good print out of everything
i am determined to get this to work


i'll have to try the LTS version
if that doesn't work either then maybe i will find a magic lamp and a genie will fix it all for me
haha

the computer is a Dell but beyond that i know nothing
i didn't buy it, it was given to me

i'll see what i can find out
and once again
thank you guys so much for the help and patience

---

### Post by ayenack on 2011-04-30
The sort of thing we need to know about the system is:-

Motherboard make and model.
Memory type and make.
Hard Drive make and model.
CD/DVD drive make and model etc.

If you boot using the LiveCD and issue this command in terminal:-

```
sudo lshw -html > hardware_info.html
```

It'll save a file in the home folder called hardware_info.html that will open in your web browser this will give you a run down of what hardware you have in your system save this on a USB stick or something so you've got a copy...

...Maybe by a process of elimination you'll be able to find a culprit for the strange behaviour by doing some research on the net.

Also if you post the file here we'll be able to do some research on it to. Post a as file to make things easier.

BTW. lshw stands for **L**i**S**t **[B]H**[/B]ard**W**are and the -html tells it to save as a html file and the > just pipes it to a file.

---

### Post by nooneastern on 2011-04-30
here is my file:
[http://www.sendspace.com/file/04xiaw](http://www.sendspace.com/file/04xiaw)

---

### Post by ayenack on 2011-04-30
Found another post on the forums where someone couldn't install an earlier version of Ubuntu on same computer model (Dell DE051) as your.

If you hosed your Windows install and you don't want to try to recover it try to install 10.04 LTS on the whole system and see what happens.

By any chance did Ubuntu refuse to boot after you'd just finished a Windows session and tried to boot into Ubuntu?

---

### Post by nooneastern on 2011-04-30
ok here is my update:
i just installed LTS through the WUBI and its working perfectly right now
i am in it as i am typing

installed flawlessly
and is running flawlessly 

the dual boot situation is good so far
would you suggest i not install anything through the Update Manager prompt that just popped up yet ?

not sure what this question means: "By any chance did Ubuntu refuse to boot after you'd just finished a Windows session and tried to boot into Ubuntu?"

but it seemed to be random
sometimes i wouldn't boot into Windows at all and eventually Ubuntu would stop working
but the last several attempts it didn't even boot properly once

however this LTS install is working perfect for now

it just wants me to download 93 files to update things ...

---

### Post by nooneastern on 2011-04-30
DAMN
newer update:
without updating anything from the Update Manager i decided to restart the computer
just to see what would happen, before i got too excited about it working

well
it did the same thing
booted to GRUB
selected Ubuntu
and got a blinking cursor in the top of the screen that eventually froze and all disk activity stopped

bummer

---

### Post by Dutch70 on 2011-04-30
Use google to learn about the i915 modeset boot options for Ubuntu. You may be able to find something here. I've only heard about it. Not really familiar.
[[COLOR="RoyalBlue"]http://ubuntuforums.org/showthread.php?t=1613132[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1613132")

Also, Ubuntu will work with 512MB of RAM, but the "recommended" minimum RAM for Ubuntu is 1GB. 
[[COLOR="RoyalBlue"]SystemRequirements[/COLOR]]("https://help.ubuntu.com/community/Installation/SystemRequirements")
You may also want to try Xubuntu or Lubuntu. Which are made to work better on older hardware & are very nice light weight versions of Ubuntu. They are both linked to in the link above. I would try Xubuntu first.

---

### Post by nooneastern on 2011-04-30
ahhh maybe that is the issue then
though when it DOES actually start up it runs WAAAAAY faster and smoother than Windows
which makes me wonder about the RAM thing
thanks for all the help guys
i'll check out the links and see if i can fix the modeset thing
or i think i might try Xubuntu....
i'll post here if/when things go well just to keep you updated

if it doesn't work out then i will just have to stick with Windows 


if you don't hear from me again then it didn't work out
and thanks again !

---

### Post by nooneastern on 2011-04-30
ok wow
tell me what you think about this .....

i did a little light reading
and decided to try "i915.modeset=0"
in the grub edit menu thing

and restarted FIVE times
(changing it every to that setting every time)
it has worked EVERY time now

does that make sense to you guys ?
did i just accidentally solve this ?
haha

EDIT: if i did solve this -- is there a way to make the change permanent so i don't have to edit each time ?

---

### Post by Dutch70 on 2011-04-30
Please come back and mark the thread solved regardless. You can just edit your first post and say something like..."not really solved, but not needed anymore, so people don't keep trying to help you.

Also, there are people on here that run it with 512MB of RAM and say that it runs fine.

I think your problem is the i915 modeset thing. I think its a simple fix, I'm just not sure what it is.

You may want to try starting another thread with a descriptive title. So that people that know something about your issue will be more likely to check your thread. Give this a quick read.
[[COLOR="RoyalBlue"]http://ubuntuforums.org/showthread.php?t=1422475[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1422475")

Although it sounds like you're windows bound...it's your choice.

---

### Post by nooneastern on 2011-04-30
@[Dutch70]("http://ubuntuforums.org/member.php?u=595401")

i think you might have missed my last post...perhaps you were posting at the same time

i changed the modeset to 0 (instead of 1) and it seems to be working perfectly fine now
i've restarted half a dozen times
even after installing all the updates from the Update Manager
and installing all the programs i wanted 
and doing some quick customizing

so i think this might REALLY BE SOLVED !!!!

thank you guys for pointing me in all the right directions
i will mark this as solved ....

i think i am still Ubuntu bound for sure !!!
wish me luck !

EDIT: i will mark this solved but can you just tell me how to make the modeset setting permanent first ?

---

### Post by Dutch70 on 2011-05-01
Yes, we must have been posting at the same time.


It's in the first link I gave you. Scroll down til you see this...
> **How to permanently set kernel boot options on an installed OS (not wubi)**

---

### Post by ayenack on 2011-05-01
To make changes permanent:-

```
sudo update-grub
```

That simple.

GRUB can be found at:-

/boot/grub/menu.lst

Always a good idea to backup as well so:-

```
cp /boot/grub/menu.lst /boot/grub/menu.lst.old
```

It was a graphics problem after all. Did it only occur after power down or after re-boots as well?

---

### Post by nooneastern on 2011-05-01
everything is perfect right now
i guess i just needed a 0 instead of that 1
hard to believe it's something that simple
i fixed the GRUB permanently and it's all perfect

loving it
i've restarted many times and shut down too
i've even loaded Windows several times
installed many things
customized many things
updated many things

unless this somehow fails  the 1,000th time i startup i feel pretty satisfied

would i be right to assume this would probably continue to work if i updated to Ubuntu 11 ?
i'm not going to do that for a long time
just gonna spend some time getting used to this

thanks everyone again....

---

### Post by Dutch70 on 2011-05-01
*ayenack...menu.lst is from Grub legacy.*


nooneastern, many issues with Ubuntu are easily solved, but if you're not sure what to do, you'll be ](*,)

The best thing to do is give Natty a couple months to get the bugs worked out & try it from a live cd or usb stick before attempting to install it.

Anyway, really glad to hear you got it worked out. Good job! :KS

---

### Post by ayenack on 2011-05-01
> **Dutch70 said:**
> *ayenack...menu.lst is from Grub legacy.*

You're right forgot from 10.04 GRUB2 is used.

---

