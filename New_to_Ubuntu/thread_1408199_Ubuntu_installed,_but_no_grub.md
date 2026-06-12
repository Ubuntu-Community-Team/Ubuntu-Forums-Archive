---
title: "Ubuntu installed, but no grub"
date: 2010-02-16
forum: New to Ubuntu
---

### Post by fabecool on 2010-02-16
Hi, 

I have installed Ubuntu 9.10 on both my laptop and my desktop from the same CD. Both had an existing WinXP installation, and I proceeded for both in the same way, i.e. I let the installer resize the XP partition to give room for Ubuntu installation. 

No problem on the laptop: when I boot, I now get Grub and can choose what operating system I want to use. 

But the desktop does not present me with the Grub screen and loads straight into Windows. 

By the way, my motherboard is an ASUS K8V SE Deluxe, and I'm using a SATA drive that is on the main VIA controller (the second Promise controller has disks for data storage attached to it).

For the desktop, at first, I was unable to find the disk where I wanted to install when I went into the install options. Then it took me to the live CD, where I could find and mount the drive, then I tried to install from the Live CD and it not only found the drive, but also let me re-size the partitions and install.

Could it be that it has installed Grub on the Raid array MBR instead of on the main disk I use for OS's?

I can now see that Ubuntu has been correctly installed, but since it boots straight into Windows, there is no way I can get in. I have tried to follow several methods to re-install grub (from the live CD), but none has made a difference. Most of the time, I get a message saying that grub is already installed. Then when I tried this:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

I get stuck from the very first stage: I get a message saying 

sudo: Grub: command not found.

Can anybody help, explain to me what's wrong or point me to a thread where this is already discussed? I would really appreciate!

Thanks!

Fa

---

### Post by byStanderone on 2010-02-16
...hope i get it right, you have two hdd in your desktop box, try to configure your cmos to booth on the drive wherein ubuntu is installed.

---

### Post by fabecool on 2010-02-16
Well yes, and no ;)

I have 3 SATA drives on my computer. two are part of a RAID and are on the secondary controller. These have no OS on them and only hold data.

The third one has both OS's. But I'm afraid the grub was installed on the raid array disks. 

It just comes to my mind: I'll disconnect the raid disks and re-install ubuntu with Grub. I'll tell you about the results I get.

Cheers,

Fa

---

### Post by Peter09 on 2010-02-16
Try holding down the shift key during Boot (as soon as possible).

---

### Post by audiomick on 2010-02-16
In order to find out where the boot loader has been installed, you can run meierfra's boot info script.
There are instructions on how to do so here
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
You can post the results.txt file here (use code tags, that is the # button at the top of the post window) if you can't understand it. Someone is likely to be able to help you with it.

---

### Post by kansasnoob on 2010-02-16
In order to see more clearly what you have please boot the Ubuntu Live CD, choosing to Try without changes, and then post the results of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by fabecool on 2010-02-16
Hi guys!

Thanks for your answers.

I had already tried to keep the shift key down, but that would not help.  I eventually got it up and running by re-installing ubuntu with my other drives disconnected. 

But of course, I had to do something stupid right after I got it to run smoothly. I just wanted to change the grub default entry to Windows (so it would not change anything in our household when s.o. turns on the computer and comes back a few minutes later to find windows has loaded). 

That was piece of cake with the previous GRUB, but Jeez! This one's got me wondering what to do now (and what I've done, which is no more than what is told here: [http://www.hackourlives.com/?p=1327](http://www.hackourlives.com/?p=1327)). 

When I start the computer, I get the GRUB menu, but with less entries, and the one highlighted flashing. I can still get into Ubuntu, but no longer in Windows, which gives me an error message about checking the drivemaps (I'll post it with more details later, because I'm writing from Ubuntu and I need to reboot to see it).

Anyway, since my laptop has the same installation, I selected the Windows entry from GRUB and hit the 'e' key and compared the result to what I had on the troubled desktop.

Some parts were the same, and by copying the laptop text to the desktop, I got into windows, but that hasn't fixed GRUB. 

What I have on the laptop is as follows:

> insmod ntfs
set root=(hd0,1)
drivemap -s (hd0) ${root}
chainloader +1 

Anyway, is there some way I can easily fix that? And how can I change the default to be windows? Sorry about these questions, but I'm no IT specialist (oh, you had guessed? ;)) and a lot of what's going on is obscure to me. However, I love the look and feel of Ubuntu, its speed compared to XP, and the whole idea behind it, so I'll try to hang on.

Thanks a lot!

Fa

(EDIT)
oh yeah! I forgot to mention, I've also looked at the following pages, but I don't see what I've done wrong and how I should correct the problem.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by kansasnoob on 2010-02-16
With all drives connected we really need to see the output of that Boot Info Script as I said in post #6 :D

Or we can play guessing games for several days.

---

### Post by philinux on 2010-02-16
> **fabecool said:**
> Hi guys!

Thanks for your answers.

I had already tried to keep the shift key down, but that would not help.  I eventually got it up and running by re-installing ubuntu with my other drives disconnected. 

But of course, I had to do something stupid right after I got it to run smoothly. I just wanted to change the grub default entry to Windows (so it would not change anything in our household when s.o. turns on the computer and comes back a few minutes later to find windows has loaded). 

That was piece of cake with the previous GRUB, but Jeez! This one's got me wondering what to do now (and what I've done, which is no more than what is told here: [http://www.hackourlives.com/?p=1327](http://www.hackourlives.com/?p=1327)). 

When I start the computer, I get the GRUB menu, but with less entries, and the one highlighted flashing. I can still get into Ubuntu, but no longer in Windows, which gives me an error message about checking the drivemaps (I'll post it with more details later, because I'm writing from Ubuntu and I need to reboot to see it).

Anyway, since my laptop has the same installation, I selected the Windows entry from GRUB and hit the 'e' key and compared the result to what I had on the troubled desktop.

Some parts were the same, and by copying the laptop text to the desktop, I got into windows, but that hasn't fixed GRUB. 

What I have on the laptop is as follows:

 

Anyway, is there some way I can easily fix that? And how can I change the default to be windows? Sorry about these questions, but I'm no IT specialist (oh, you had guessed? ;)) and a lot of what's going on is obscure to me. However, I love the look and feel of Ubuntu, its speed compared to XP, and the whole idea behind it, so I'll try to hang on.

Thanks a lot!

Fa

(EDIT)
oh yeah! I forgot to mention, I've also looked at the following pages, but I don't see what I've done wrong and how I should correct the problem.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Easiest option is to install startupmanager. It used to work really well with grub but for grub2 it has limited functionality. However, it can be used for setting the default os.

---

### Post by fabecool on 2010-02-16
Okay, 

So I've downloaded the boot info script (although guessing games sounded nice ;)), and here is the result:

```
    Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=ab6de1fd-9f1a-4a48-adfe-7c2e9ab91069)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       promise_fasttrack_raid_member
    Boot sector type:  Windows XP
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'promise_fasttrack_raid_member'

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x50ecca38

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   625,153,409   625,153,347  42 SFS

/dev/sda1 ends after the last sector of /dev/sda

Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbc2ebc2e

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    97,659,134    97,659,072   7 HPFS/NTFS
/dev/sdc2          97,659,135   160,071,659    62,412,525   5 Extended
/dev/sdc5    *     97,659,198   157,404,869    59,745,672  83 Linux
/dev/sdc6         157,404,933   160,071,659     2,666,727  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1                                               promise_fasttrack_raid_member                               
/dev/sda                                                promise_fasttrack_raid_member                               
/dev/sdb                                                promise_fasttrack_raid_member                               
/dev/sdc1        12A0CA18A0CA01E9                       ntfs                                     
/dev/sdc5        9ddadccf-5035-428e-840b-fba0cf2a7741   ext4                                     
/dev/sdc6        a0275d97-71f2-4925-83d9-61c27fd2fc0e   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdc5        /                        ext4       (rw,errors=remount-ro)


================================ sdc1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sdc5/boot/grub/grub.cfg: ===========================

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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	linux	/boot/vmlinuz-2.6.31-14-generic root=/dev/sdc5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	linux	/boot/vmlinuz-2.6.31-14-generic root=/dev/sdc5 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
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
menuentry "Microsoft Windows XP Professional (on /dev/sdc1)" {
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=9ddadccf-5035-428e-840b-fba0cf2a7741 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=a0275d97-71f2-4925-83d9-61c27fd2fc0e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc5: Location of files loaded by Grub: ===================


  53.5GB: boot/grub/core.img
  50.6GB: boot/grub/grub.cfg
  50.6GB: boot/initrd.img-2.6.31-14-generic
  50.5GB: boot/vmlinuz-2.6.31-14-generic
  50.6GB: initrd.img
  50.5GB: vmlinuz
```

Sooo, what can we do of all this? I think I got this much: Grub2 is installed on 2 different drives (sda and sdc, does this stand for sata disk a and c?).

Anything that would help me get the whole system up and running again?

Thanks!:D

Fa

---

### Post by audiomick on 2010-02-16
I think you just need to go into your BIOS and tell it to boot from whichever drive is sdc.

You are right, there are 2 Grub installs. I guess one is on the RAID array mbr and doesn't point to anything useful. The one on sdc seems to be intact and complete, so it should work if you make that drive the first boot device.

---

### Post by kansasnoob on 2010-02-16
> **audiomick said:**
> I think you just need to go into your BIOS and tell it to boot from whichever drive is sdc.

You are right, there are 2 Grub installs. I guess one is on the RAID array mbr and doesn't point to anything useful. The one on sdc seems to be intact and complete, so it should work if you make that drive the first boot device.

I don't think so. It sounds like it's booting Ubuntu just fine, and possibly was booting Windows fine.

I suspect some changes to /etc/grub.d/00_header. Just now making changes to the BIOS could cause a much worse problem!

---

### Post by oldfred on 2010-02-16
The drive order seems to be the order the drives are plugged into the sata ports. So you must have sdc in higher numbered ports than the other two. It looks like grub saw the wrong drive as the boot drive and installed to sda originally. 

Windows wants to be the first drive. This says it is drive 0 and partition 1.
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

I would try copying your windows entry into 40_custom changing the drivemap from hd0 to hd2 and update grub.

menuentry "Microsoft Windows XP Professional (on /dev/sdc1)" {
    drivemap -s ([COLOR=Red]hd2[/COLOR]) ${root}
    chainloader +1
}

to write changes into grub.cfg:
sudo update-grub

If that does not work print out your device.map in /boot/grub as sometimes grub reorders drives. Which gets real confusing.

---

### Post by audiomick on 2010-02-16
@kansasnoob
oops, you're right of course. I had forgotten what the OP wrote in post #7.

---

### Post by kansasnoob on 2010-02-16
Slow down everyone! Look at the OP's last comments:

> I had to do something stupid right after I got it to run smoothly. I just wanted to change the grub default entry to Windows (so it would not change anything in our household when s.o. turns on the computer and comes back a few minutes later to find windows has loaded).

Then he did this:

> That was piece of cake with the previous GRUB, but Jeez! This one's got me wondering what to do now (and what I've done, which is no more than what is told here: [http://www.hackourlives.com/?p=1327](http://www.hackourlives.com/?p=1327)).

Resulting in this:

> When I start the computer, I get the GRUB menu, but with less entries, and the one highlighted flashing. I can still get into Ubuntu, but no longer in Windows, which gives me an error message about checking the drivemaps (I'll post it with more details later, because I'm writing from Ubuntu and I need to reboot to see it).


Then he tried copying files from another machine:

> Anyway, since my laptop has the same installation, I selected the Windows entry from GRUB and hit the 'e' key and compared the result to what I had on the troubled desktop.

Some parts were the same, and by copying the laptop text to the desktop, I got into windows, but that hasn't fixed GRUB.


Now if we keep just throwing things at this without some real thought and troubleshooting we're only going to make things worse!

---

### Post by kansasnoob on 2010-02-16
I should add I've been on the phone a lot and I don't multi-task!!!!!!!!!!!!!!

---

### Post by kansasnoob on 2010-02-16
> **philinux said:**
> Easiest option is to install startupmanager. It used to work really well with grub but for grub2 it has limited functionality. However, it can be used for setting the default os.

This is exactly right! But now the OP has made some changes to grub2 files so we'll have to fix that first.

---

### Post by kansasnoob on 2010-02-16
Since you've "hosed" some grub2 files anyway and I find that Lucid's grub2 installs in Karmic just fine I suggest booting into Karmic and doing this:

```
sudo apt-get --purge remove grub-pc grub-common
```

Then download the proper (i386 or 64bit) grub-common .deb here (just save to Desktop):

[http://packages.ubuntu.com/lucid/grub-common](http://packages.ubuntu.com/lucid/grub-common)

Likewise with grub-pc:

[http://packages.ubuntu.com/lucid/admin/grub-pc](http://packages.ubuntu.com/lucid/admin/grub-pc)

Then go to the Desktop (or Downloads folder, wherever you saved them) and beginning with grub-common just double click and gdebi will take care of the installation.

Then go back to terminal and run:

```
sudo update-grub
```

And in case the grub2 signature changed in any way:

```
sudo grub-install /dev/sda
```

```
sudo grub-install /dev/sdc
```

Then install Startup Manager:

```
sudo apt-get install startupmanager
```

It will then show up in System > Administration and under the Boot Options tab you can change the "timeout" and Default boot option.

---

### Post by audiomick on 2010-02-16
> **kansasnoob said:**
> ... and I don't multi-task!!!!!!!!!!!!!!
neither do I...;)

---

### Post by fabecool on 2010-02-16
Waw! Thank you for all your posts. I just went down for supper and some quality time with the family, and I'm amazed at how much has happened in this thread in such a short time!

I'll read through all this again, quietly, in order to understand what I am to do (and not to do), and I'll report as soon as it's done (hopefully with a "solved" prefix).

Fa

---

### Post by fabecool on 2010-02-16
Okay... To go with Kansasnoob's last suggestion, and just so that I don't do anything stupid (again), I'd like to make sure about the file I should download.

I have an AMD64 processor, but my WinXP as well as the version of Ubuntu I'm running are the standard 32. So I guess I should go with the i386. Am I right?

Fa

---

### Post by fabecool on 2010-02-16
Alright. I've followed the instructions, and I think everything has worked out for the best (even the StartUp-Manager app is now installed). I'll reboot and keep you up to date with a new post if it works. If it does not, then it will have to wait for tomorrow...

Anyway, thank you guys, you rock!

Fa

---

### Post by fabecool on 2010-02-16
Thank you! It worked! I got my system not only fixed, but also just as I wanted it!

Fa

---

### Post by kansasnoob on 2010-02-16
That really is what makes grub2 sweet! I'll grant you that Karmic's grub2 has a few bugs, but soon we'll be beyond the bugs and very seldom have to edit anything :D

---

### Post by fabecool on 2010-02-16
Oh, by the way, one last question: I did not run the two following lines, because I did not understand what they do. 

```
sudo grub-install /dev/sda
```

```
sudo grub-install /dev/sdc
```

Could you tell me briefly what a signature is? 

Thanks again for everything. And you're probably right, I'm sure I'll get used to GRUB2!

Fa

---

### Post by kansasnoob on 2010-02-16
> **fabecool said:**
> Oh, by the way, one last question: I did not run the two following lines, because I did not understand what they do. 

```
sudo grub-install /dev/sda
```

```
sudo grub-install /dev/sdc
```

Could you tell me briefly what a signature is? 

Thanks again for everything. And you're probably right, I'm sure I'll get used to GRUB2!

Fa

I thought is was doubtfully needed but we were installing a newer version grub2. We wanted to be sure the newer version was the version recognized by grub2 when it tried to boot.

When I said "signature" I simply meant .... well if you took a large check of mine to my bank and presented it for cash they might check the signature. If it doesn't match you might get rejected.

I simply knew that if you included that you'd be fine. I don't like having to go back and forth a dozen times to get things right. Just assume the worst and try to eliminate any errors the first time :D

---

