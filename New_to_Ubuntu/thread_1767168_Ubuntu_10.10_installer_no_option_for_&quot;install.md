---
title: "Ubuntu 10.10 installer: no option for &quot;install to largest free space&quot;"
date: 2011-05-25
forum: New to Ubuntu
---

### Post by swarup on 2011-05-25
I am installing Ubuntu 10.10 on a Dell dimension E520 desktop. It is a 160 GB HD, and there is 10 GB of unallocated, contiguous free space-- plenty for Ubuntu. The rest is taken up by Windows. We do not want to do any resizing of partitions-- just install to the "largest free space". This always used to be an option on previous versions, but has now been removed. The option to "install side by side (with other existing OS's)" wants to downsize the Windows partition to 128 GB. Is there some way to reject any changing of partition sizes, and just install to the existing 10 GB space? I am not familiar with doing it manually, selecting a mount point etc, so it would be easier to just let it automatically set up the install but without partition resizing. Thanks!

---

### Post by aeiah on 2011-05-25
when you're in the livecd, use gparted to make an ext4 partition in your free space. the installer should see this partition and you should be able to choose it to install ubuntu to. worth a try.

---

### Post by compmodder26 on 2011-05-25
> **aeiah said:**
> when you're in the livecd, use gparted to make an ext4 partition in your free space. the installer should see this partition and you should be able to choose it to install ubuntu to. worth a try.

You also will need to make a swap partition too (unless you are absolutely certain that you won't exhaust your RAM).  Typical recommendation is to make the swap partition the same size as the amount of RAM you have.

---

### Post by swarup on 2011-05-25
> **compmodder26 said:**
> You also will need to make a swap partition too (unless you are absolutely certain that you won't exhaust your RAM).  Typical recommendation is to make the swap partition the same size as the amount of RAM you have.

I was afraid you guys were going to tell me to set it up manually. So they don't offer to do if for you anymore, eh. Alright-- I'll do it. 

I guess I'll set up an extended partition of 10GB, then within that a 9 GB Ext 4 primary partition and a 1 GB swap. But they also ask you for the "mount point" for each partition. What is the standard mount point?

---

### Post by oldfred on 2011-05-25
You set up an extended partition which is one of the 4 primary partitions allowed. Inside the extended partition you can create as many logical partitions as you want.

I also suggest a shared NTFS partition for any data you may want in both Ubuntu & Windows. Windows does not like other systems writing into its system partition. Also many Windows users suggest a D: drive for data so when you have to reinstall windows you do not have to reinstall all your data (backups still required).

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by kansasnoob on 2011-05-25
You might find my notes here helpful:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

---

### Post by swarup on 2011-05-25
I went into GParted and create an extended partition of 10 GB, and then inside that, an ext4 of 9 GB, and a swap of 1 GB. (The person using this computer has very simple needs and will not be accessing Windows, so this should be fine.) Then went back to the installer and told it to do a side-by-side installation, alongside other existing OS's. It immediately saw the partitions I had created, and indicated graphically that it would use those. But when I then select "install", I get a message that states: 

> Write previous changes to disk and continue? Before you can select a new partition size, any previous changes have to be written to disk. You cannot undo this operation. Please note that the resize operation may take a long time.

When I have already created, sized, and formatted the partitions using Gparted, then why am I getting such a message from the installer about writing previous changes to disk, and about impending resizing operations? I have not requested the installer to do any resizing. I just want it to accept what I created in Gparted, and install to those partitions which I made.

---

### Post by Quackers on 2011-05-25
As stated by kansasnoob, the 10.10 installer has a nasty habit of eating previous installations!
The install alongside option is not recommended.

When you created the new partitions in gparted did you apply the changes by clicking on the green arrow in the toolbar?

Also how many primary partitions were in use on your hard drive before creating another?

---

### Post by swarup on 2011-05-25
> **Quackers said:**
> As stated by kansasnoob, the 10.10 installer has a nasty habit of eating previous installations!
The install alongside option is not recommended.

When you created the new partitions in gparted did you apply the changes by clicking on the green arrow in the toolbar?

Also how many primary partitions were in use on your hard drive before creating another?

I waited for a half hour, but when I didn't get any reply I thought I would move ahead and see what happens. So in gparted, yes I did apply the changes. As for partitions, there is sda1 (Dell Utility Partition), sda2 (Windows Vista loader), and sda3 (Main windows partition). Anyhow, when I clicked install everything seemed to go very smoothly without any apparent resizing.

But NOW most of the way through the install, I just got an error message stating it is not possible to install the bootloader at the specified location (sda)-- which the installer seems to have selected. It is asking that I instead select sda1 (Dell Utility Partition), sda2 (Windows Vista loader), sda3 (Main windows partition), or sda5 (ext4, where Ubuntu is being installed). Which one should I select?

---

### Post by Quackers on 2011-05-25
It should install without problem to /dev/sda. The only time I have seen problems is when a raid array is being used, or, occasionally, when a usb device is plugged in and is causing the usb device to be designated as /dev/sda.
If you are really stuck you can install it to /dev/sda5, but the system will not then boot (but at least it should get installed ok).
You could then attempt to install grub from the live desktop later.

---

### Post by swarup on 2011-05-25
> **Quackers said:**
> It should install without problem to /dev/sda. The only time I have seen problems is when a raid array is being used, or, occasionally, when a usb device is plugged in and is causing the usb device to be designated as /dev/sda.
If you are really stuck you can install it to /dev/sda5, but the system will not then boot (but at least it should get installed ok).
You could then attempt to install grub from the live desktop later.

It is not accepting to install to /dev/sda. That is the error message. And there is no usb device plugged in. I don't know what a raid array is but I assume it isn't be used. So I guess I am stuck, right? I mean, I'd love to install it to /dev/sda as usual, but it isn't accepting that. Who knows why. So I guess your suggestion then is to install it to /dev/sda5 in order to complete the installation, and then install grub "from the live desktop later". I'm going to move ahead with this, then. 

It does give one other option, though: "continue without a bootloader". I guess since I'm going to have to install grub again later anyone, it doesn't really matter much whether I put it at sda5, where it won't work, or whether I don't install it at all. Does it matter?

When you say to install grub from the live desktop, I guess you mean from the livecd desktop right? Where is the option found for doing that, once I get there?

---

### Post by Quackers on 2011-05-25
Yes, that's right (although I suspect there may be an underlying problem - but I've been wrong before! ).
If you complete the installation then reboot when it asks, you can see if it boots without the cd in, but that's very unlikely.
If that is the case you can then boot from the live cd and select "try ubuntu" then open up a terminal and run these 2 commands one at a time
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
These assume that /dev/sda5 is in fact your Ubuntu root partition.
The installation should report no errors.
You can then reboot when, hopefully, Ubuntu will boot directly.

---

### Post by swarup on 2011-05-25
Well, I tried installing it at /dev/sda5, and it wouldn't accept that either. So then I tried the option to not install a bootloader at all-- and as soon as I selected that and clicked "continue", I got another message stating "Installer crashed". So it ultimately could not be installed.

Plus last night I was trying to install 11.04, and that wouldn't install either. So now I don't know what to install.

---

### Post by Quackers on 2011-05-25
Has this hard drive been used in another pc?

---

### Post by swarup on 2011-05-25
No, it has never been used in another computer. But let me tell you what happened. I refreshed gparted just now, and found out that, although prior to installing I created an extended partition with an ext4 9 GB and a swab 1GB instide, still the "install side by side" option stole part of the 9 gB and created ANOTHER ext4 and ANOTHER swap. So there were two ext4 partitions and two swap partitions! No wonder the installation failed!

Perhaps best will be to proceed again, this time trying the manual option. The only thing unclear to me there is what to select as the "mount point" for each partition.

---

### Post by Quackers on 2011-05-25
That's the easy part :-)
I would delete all partitions within the extended partition first with gparted. Then in the manual partitioning stage double click on that extended partition (or the free space within it) and a new window will open up. 
Select the size of the swap partition in MB and select type as logical and then as swap. Click ok.
Then double click on the extended partition again and a new window will open up with the remaining space filled in. Select logical partition type, select format to ext4 and check the box to format it. 
Set the mount point to " / " for root, from the drop-down box in that field. Click OK and then install.

---

### Post by swarup on 2011-05-25
Before getting your reply I had already done part of what was needed in gparted i.e. deleted the excess partitions within the extended partition, and rexpanded to full size (9GB) and reformatted the one I wanted to keep. So there is a 9GB ext4, and a 1GB swab freshly set up. In the manual setup I opted to mount the ext4 at "/" as you said, and now it is installing. 

Let's see what happens! This time I told it not to download updates during the install, so we'll find out more quickly if it is in fact going to install.

---

### Post by Quackers on 2011-05-25
I stopped installing 3rd party programs and updates at the time of installation some time ago. It has caused problems for me in the past not doing so.
Hopefully it will go better this time :-)

---

### Post by swarup on 2011-05-25
Oops, I did let it install the 3rd party programs. Hopefully that won't be a problem. Well, thank you for all your help... so far so good (now it's downloading language packs). I'll let you know when the installation is done!

---

### Post by philinux on 2011-05-25
> **swarup said:**
> Oops, I did let it install the 3rd party programs. Hopefully that won't be a problem. Well, thank you for all your help... so far so good (now it's downloading language packs). I'll let you know when the installation is done!

I've not had one problem on the last three install doing this. And I let it install the updates too.


This was with natty 11.04 by the way.

---

### Post by Quackers on 2011-05-25
> **philinux said:**
> I've not had one problem on the last three install doing this. And I let it install the updates too.


This was with natty 11.04 by the way.

I've not had a problem with the 3rd party stuff, but I installation of 11.04 failed on my system several times until I de-selected the updates option, when installation completed without a problem.
I have absolutely no idea why that would happen.

---

### Post by swarup on 2011-05-25
Ok, the install went smoothly. :)

Only one problem is left-- grub has not included the Windows partition. Actually, the grub screen doesn't appear at all. :( When I turn on the computer, it just boots right up into Ubuntu. What do I need to do to problem-solve this?

---

### Post by Quackers on 2011-05-25
That's normal.
If you open up a terminal and run ```
sudo update-grub
``` you should see the Windows Loader picked up as grub.cfg is run.
If that is the case, reboot and you should then see a grub menu with the choice of both systems. Try booting Windows to make sure that it's still happy :-)

---

### Post by swarup on 2011-05-25
great, thanks. I'll do it now.

---

### Post by swarup on 2011-05-25
I did the update as you instructed, and in the terminal window I saw it pick up both Ubuntu and Windows. So, there everything looked fine. But when I rebooted, it again booted straight into Ubuntu, without showing the Grub screen. What should I do now?

---

### Post by Quackers on 2011-05-25
Please run it again and quote the output from the terminal in your next post.

---

### Post by swarup on 2011-05-25
message deleted

---

### Post by compmodder26 on 2011-05-25
Not sure about your password issue, but when you boot your computer, right after your BIOS screen disappears, hold down Shift until you see the Grub menu appear.  By default Grub is set to automatically boot the default OS/Kernel, which is Ubuntu.

Hope that helps you.

---

### Post by Quackers on 2011-05-25
Make sure your shift lock or numlock is not engaged.

---

### Post by swarup on 2011-05-25
I deleted the password posting (I had just typed my password wrong)...but you guys were too quick for me. Here is the terminal output:

```
:~$ sudo update-grub
[sudo] password for xxxx: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Dell Utility Partition on /dev/sda1
Found Windows Vista (loader) on /dev/sda2
Found Windows Recovery Environment (loader) on /dev/sda3
done
```
 
Let me know.

@compmodder26: Interesting :). Let's say though, that hitting the shift key were to work-- I don't want my friend to have to do that every time he wants to boot into windows. How can we get the grub screen to appear by default, like it's supposed to.

---

### Post by compmodder26 on 2011-05-25
> **swarup said:**
> @compmodder26: Interesting :). Let's say though, that hitting the shift key were to work-- I don't want my friend to have to do that every time he wants to boot into windows. How can we get the grub screen to appear by default, like it's supposed to.

You can edit "/etc/default/grub":

```
gksudo gedit /etc/default/grub
```

Then change this line:

```
GRUB_HIDDEN_TIMEOUT=0
```

to:

```
GRUB_HIDDEN_TIMEOUT=
```

This will display the grub menu until GRUB_TIMEOUT seconds have elapsed.  After that amount of time, the default OS/kernel will boot.

You can also change the default OS/Kernel by editing this line:

```
GRUB_DEFAULT=0
```

To another number.  The numbers correspond the order of the entries in the menu (0 for the first, 1 for the second, etc.)

This page has good information on that file:

[https://help.ubuntu.com/community/Grub2#/etc/default/grub (file)](https://help.ubuntu.com/community/Grub2#/etc/default/grub (file))

---

### Post by Quackers on 2011-05-25
Hmm, and is that what you saw the first time you ran it?
I see no reason why the grub menu should not be appearing.
(Incidentally with the Windows system being Vista, you may need to select the Recovery environment Loader on sda3 to boot it, but that doesn't help you at the moment).
Try rebooting again and see if grub appears this time.

If it doesn't please boot Ubuntu and go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder).
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by swarup on 2011-05-25
@Quackers-- ok, I'll do this right now. But one question: what do you think of what compmodder26 has written? Could it be that everything is fine and grub defaulted to be hidden for some reason? If that is the case, I guess I'd just need to follow what he wrote to make it appear.

---

### Post by Quackers on 2011-05-25
Unless there is a problem somewhere, the grub menu should be appearing as soon as a second operating system is found.

---

### Post by swarup on 2011-05-25
@compmodder26: I just implemented what you suggested, i.e. changed 

```
GRUB_HIDDEN_TIMEOUT=0
```

to

```
GRUB_HIDDEN_TIMEOUT=
```

Then I did 

```
sudo update-grub
```

Then I rebooted, and still it went straight to the ubuntu desktop, without showing the grub screen. 

Now, I should mention that the line you mentioned actually has a "#" in front of it-- but without a space. That is:

```
#GRUB_HIDDEN_TIMEOUT=0
```

I don't know whether the "#" affects anything, but there was no other such line which did not have a "#".

---

### Post by compmodder26 on 2011-05-25
Yeah, Quackers is right.  Grub should display the menu if another OS has been detected/added to the list.  Been a while since I've run another OS next to Ubuntu.

At any rate, it wouldn't hurt to do a simple reboot and hold Shift after your BIOS screen disappears to rule out the possibility that it somehow didn't alter hidden menu functionality.

---

### Post by swarup on 2011-05-25
> **Quackers said:**
> Unless there is a problem somewhere, the grub menu should be appearing as soon as a second operating system is found.

ok. I'm going to do what you said now, and report back.

Incidentally, could this be related with the current problem: 

> Incidentally with the Windows system being Vista, you may need to select the Recovery environment Loader on sda3 to boot it, but that doesn't help you at the moment.

That is, could it be that a second operating system is not being found because of what you state here?

---

### Post by compmodder26 on 2011-05-25
> **swarup said:**
> @compmodder26: I just implemented what you suggested, i.e. changed 

```
GRUB_HIDDEN_TIMEOUT=0
```

to

```
GRUB_HIDDEN_TIMEOUT=
```

Then I did 

```
sudo update-grub
```

Then I rebooted, and still it went straight to the ubuntu desktop, without showing the grub screen. 

Now, I should mention that the line you mentioned actually has a "#" in front of it-- but without a space. That is:

```
#GRUB_HIDDEN_TIMEOUT=0
```

I don't know whether the "#" affects anything, but there was no other such line which did not have a "#".

Yeah, then what I suggested the fix for isn't the problem.  What is the value of GRUB_TIMEOUT?

The "#" is a comment meaning that line has been commented out and won't be taken into account.  Which essentially has the same effect as removing the 0 after the "="

---

### Post by Quackers on 2011-05-25
> **swarup said:**
> That is, could it be that a second operating system is not being found because of what you state here?

I wouldn't have thought so, but I'm open to suggestions :-)

---

### Post by swarup on 2011-05-25
> **compmodder26 said:**
> Yeah, Quackers is right.  Grub should display the menu if another OS has been detected/added to the list.  Been a while since I've run another OS next to Ubuntu.

At any rate, it wouldn't hurt to do a simple reboot and hold Shift after your BIOS screen disappears to rule out the possibility that it somehow didn't alter hidden menu functionality.

I tried that-- it did not show up.

---

### Post by Quackers on 2011-05-25
Very odd, please try the boot script from post #32 to get some more information.

---

### Post by swarup on 2011-05-25
Here is the boot script output information:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for (,msdos5)/boot/grub.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

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
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         81,920    21,053,439    20,971,520   7 NTFS / exFAT / HPFS
/dev/sda3          21,053,440   292,016,127   270,962,688   7 NTFS / exFAT / HPFS
/dev/sda4         292,018,174   312,498,175    20,480,002   5 Extended
/dev/sda5         292,018,176   310,411,263    18,393,088  83 Linux
/dev/sda6         310,413,312   312,498,175     2,084,864  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        07D7-0605                              vfat       DellUtility
/dev/sda2        62B01238B01212E1                       ntfs       FreeAgent Drive
/dev/sda3        E6C4163AC4160D85                       ntfs       C Drive
/dev/sda5        1686567a-88ad-4e5d-b744-57ea9a6bf2f4   ext4       
/dev/sda6        202e855e-dfbb-4d03-82ba-6185f72c1254   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 1686567a-88ad-4e5d-b744-57ea9a6bf2f4
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 1686567a-88ad-4e5d-b744-57ea9a6bf2f4
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
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 1686567a-88ad-4e5d-b744-57ea9a6bf2f4
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=1686567a-88ad-4e5d-b744-57ea9a6bf2f4 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 1686567a-88ad-4e5d-b744-57ea9a6bf2f4
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=1686567a-88ad-4e5d-b744-57ea9a6bf2f4 ro single 
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
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 1686567a-88ad-4e5d-b744-57ea9a6bf2f4
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 1686567a-88ad-4e5d-b744-57ea9a6bf2f4
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Dell Utility Partition (on /dev/sda1)" {
	insmod part_msdos
	insmod fat
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 07d7-0605
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 62b01238b01212e1
	chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set e6c4163ac4160d85
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=1686567a-88ad-4e5d-b744-57ea9a6bf2f4 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=202e855e-dfbb-4d03-82ba-6185f72c1254 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 145.687175751 = 156.430413824  boot/grub/core.img                             1
 141.842956543 = 152.302714880  boot/grub/grub.cfg                             2
 141.133640289 = 151.541092352  boot/initrd.img-2.6.35-22-generic              2
 145.686614990 = 156.429811712  boot/vmlinuz-2.6.35-22-generic                 1
 141.133640289 = 151.541092352  initrd.img                                     2
 145.686614990 = 156.429811712  vmlinuz                                        1


```

---

### Post by Quackers on 2011-05-25
sda1 is a Dell partition. Is that a recovery partition?
What's actually in sda2 please?

---

### Post by oldfred on 2011-05-25
Either Vista or grub reverse the Vista entires on recovery partition and main boot partition. Have you tried booting the other. If it is the recovery DO NOT start the recovery process.

---

### Post by Quackers on 2011-05-25
Thanks oldfred, but the OP is not getting a grub menu at all. Can you see why that may be, I can't :-(

---

### Post by swarup on 2011-05-25
sda1 is a 39 MB partition, labelled in gparted as "DellUtility". My colleague, who uses this computer, is not certain what it is for. sda2 is a 10GB partition, labelled in gparted as "FreeAgent Drive"-- my colleague explains that THIS is the Windows restoration software. This partition is what they gave him in place of a DVD containing the OS.

---

### Post by Quackers on 2011-05-25
Ok, thanks. It does pose another question though.
The boot flag (which is something that only Windows uses, really) is set on sda2, not sda3.
Also sda2 has Windows type boot files in it, but they are not the normal type for a recovery partition (ie  /bootmgr and /Boot/BCD rather than /BOOTMGR and /BOOT/BCD )
I take it that before Ubuntu was installed Windows booted normally?

---

### Post by swarup on 2011-05-25
Yes, Windows was booting perfectly normally. As a matter of fact, I have been putting Ubuntu side-by-side with Windows on this computer since Gutsy. Never had a problem. The old Ubuntu install software used to pick everything up perfectly, and the dual boot would work out of the box.

So, perhaps the boot flag needs to be reset to sda3? That is what I was asking you about earlier. Perhaps the installer got confused as to which partition is the actual running Windows partition. Let's reset the boot flag to sda3-- does that sound like what is needed? If so, please remind me how to do so. I've dealt with grub-related issues before, on various computers, but not frequently enough to remember what to do. Thanks.

---

### Post by oldfred on 2011-05-25
Boot flag will not make any difference to grub booting windows. Boot flag is only for windows boot loader or windows needs it to know what partition to repair if you are doing repairs.

Windows is not case sensitive so capitalization does not matter.

If you do not get grub menu, does holding down shift key from BIOS until menu appears give you a menu?

---

### Post by Quackers on 2011-05-25
You can set the boot flag with gparted.
Right-click on sda3 and select "manage flags" then in the new box check the box marked "boot". Then you should see the work boot on the right hand side of the screen move from sda2 to sda3.
You should then run sudo update-grub again.

I think you said earlier that you wished Windows to be the default option. If you have done that on previous systems you must have edited /etc/default/grub.
Could you possibly have also changed the default timeout or default_hidden_timeout lines in there too? :-) That might explain things.

---

### Post by swarup on 2011-05-25
@oldfred: holding shift key after bios screen does not give a grub screen. I should also add here that the computer always pauses after the bios screen finishes, giving the following screen:

> Drive 5 not found: Serial ATA, SATA-5
Strike F1 key to continue

But that has been for years, and seems linked with the fact that my colleague has put in and removed multiple drives over the years. But as I say, it has been like this almost since we got the computer, and several Ubuntu distributions have been installed since with never a problem. After the above screen goes away, the grub screen comes.

@Quackers: We have never reset the default boot option on this computer.

oldfred says the boot flag is irrelevant for the grub boot loader. Do you think it will make a difference if we reset it from sda2 to sda3?

---

### Post by Quackers on 2011-05-25
In all honesty it shouldn't make any difference as far as grub is concerned, unless the Windows boot files in sda2 suddenly started to point to the wrong place, which is most unlikely, I would say.
It certainly won't do any harm, though, and is easily returnable.

---

### Post by swarup on 2011-05-25
I moved the boot flag from sda2 to sda3, and then ran sudo update-grub. On rebooting, the grub menu still doesn't appear.

---

### Post by Quackers on 2011-05-25
Not a major surprise then :-)
I'm at a loss to explain your situation I'm afraid. I really can't think of much else to try.
The only thing I can think of is to repair the Windows bootloader with a Windows Vista repair disc (or installation disc) and get Windows booting again.
Once that's done you can then purge and re-install grub using the CHROOT section of the guide below.
The partition you need to mount is /dev/sda5 and once purged grub should be re-installed to /dev/sda

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Obviously, before taking on such a task, you might choose to see if anybody can spot something I may have missed :-)

---

### Post by swarup on 2011-05-25
If you think that'll take care of it, then it doesn't seem like such a big deal to do-- unless it is going to be a rock-strewn process. If the vista repair disk generally gets vista booting without problem, and the grub repair also is smooth, then, hey-- no big deal at all. I've been working fairly continuously at getting this set up for the last 24 hours-- so would like to wrap it up. (Last night I was working with 11.04, and that wouldn't even install. Then today I've been dealing with install and now boot issues with 10.10.)

If anyone else knows a better approach to getting grub to work, please let me know! :)

---

### Post by oldfred on 2011-05-25
Since you are getting the drive 5 error, Is BIOS set to boot that drive first and then the boot process is not quite normal (it still should be)? I would check BIOS and see if drive 0 or first drive is set at the boot drive.

---

### Post by swarup on 2011-05-25
Ok, I'll check. Is that in setup ? i.e. hitting F2 after the bios screen, should give me the priorities for booting right? Right now for some reason my screen isn't getting signal so I have to get that running to test what you're asking. In a few minutes I should have it on.

---

### Post by oldfred on 2011-05-25
Most computers show a small list of keys to use on the BIOS initial startup screen. One is to get into BIOS for many settings (del on my system) and another is a one time boot key (f12 on mine) that lets you select to boot something other than the default boot that you have set in BIOS.

---

### Post by swarup on 2011-05-25
You know, I have good news. I just started the computer up, and the grub screen came. :) I had just gone into setup (right after the bios screen) and was looking at the boot sequence. Then I exited setup, without saving, and after exiting setup the grub screen appeared. And it booted into Windows too, when we selected it.

But the bad news is, that I am finding that the grub screen ONLY comes if I hit F2 and go into the setup utility. I don't have to do ANYTHING in setup. I just have to go there. And then on exit, the grub screen comes. If I don't hit F2 to go into setup, then the grub screen doesn't come.

So what is this, voodoo? What is the way to make the grub screen come without having to enter setup?

---

### Post by drs305 on 2011-05-25
I only have the time to present some workarounds that might help. I'll have more time to review the entire thread and suggest more detailed solutions (possibly) in a few days. For now:

SHIFT isn't working because your grub.cfg file doesn't include the keystatus check code. Why I'm not sure yet, but if you place this in /etc/grub.d/40_custom and update grub you should gain the ability to use the SHIFT key to display the menu. Just add it to the existing lines, save the file, update-grub and if 40_custom is executable it should add this snippet to grub.cfg:
> 
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep$verbose --interruptible 3 ; then
      set timeout=0
    fi
  fi


Although I would do the above first to see if it works, you should be able to force the menu to show by setting the recordfail timeouts to -1. I can show you later how to set this up in one of the scripts so update-grub doesn't erase it, but for now just manually set it up open grub.cfg for editing:
```
gksu gedit +56 /boot/grub/grub.cfg
```
and find this section and change it:

> if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
[COLOR="Red"][s]  set timeout=10[/s][/COLOR]
**  set timeout=-1**
fi


This is only a workaround to try to get your menu to display. If you run update-grub or the system invokes it after a kernel update you will lose the changes.

---

### Post by swarup on 2011-05-25
@drs305: Thanks a lot for the tips! :) I'll try them. And if you are able to send me something permanent when you get a chance, that will also be wonderful. :)

---

### Post by oldfred on 2011-05-25
It still sounds like a BIOS error that somehow confuses grub2. What drive was the default in BIOS?

 Do you have a one time boot key and does changing the selection there make a difference?

---

### Post by swarup on 2011-05-25
> **oldfred said:**
> It still sounds like a BIOS error that somehow confuses grub2. What drive was the default in BIOS?

 Do you have a one time boot key and does changing the selection there make a difference?

Your questions have led to an interesting discovery.

Yes, there is a one time boot key (F12) which when pressed, gives you a list of alternative media for booting to. The interesting finding is that, if I press F12 and select the very hard drive which would have booted anyway, then the grub menu appears immediately. Whereas if I just let the computer spontaneously boot to the same hard drive on its own, then the grub menu does not appear. 

So it isn't that I have to enter the setup utility (F2) in order to trigger the grub menu to come. If I just hit F12 (one time boot key), then also the grub menu will appear. 

I think what I am calling the setup utility, reached via F2 at the Bios screen, is what you are calling the BIOS.

You asked what drive was the default in Bios. Here is the boot sequence-- don't know if this answers your question or not. 

1. Onboard or USB CD-ROM drive
2. Onboard SATA Hard drive (other than the current boot HD) [none present]
3. Add-in Hard Drive (not present)
4. The current boot HD (Here the serial # of that HD is listed)
5. Onboard Network Controller (not present)
6. USB Device, onboard or usb floppy drive.

Currently there is only one HD connected in the tower. It is identified in the BIOS as "SATA-0", and is listed as #4 item in the boot sequence.

The HD which it looks for and doesn't find "SATA-5", is a HD which is actually in the Tower chassis, but not currently connected. My colleague only uses it sometimes. I think ever since he installed it, the computer asks for it during the boot, if it is not connected. When my colleague connects it, then the computer sees it and so does not ask for it at boot up.

Hope these items of information are helpful. Does it still sound like a BIOS error that somehow confuses grub2? If so, then what is the way to solve it?

---

### Post by swarup on 2011-05-25
> **drs305 said:**
> I only have the time to present some workarounds that might help... 

I implemented both workarounds exactly as you suggested, but neither worked. The only thing I was uncertain of was where you wrote:

> 
if 40_custom is executable it should add this snippet to grub.cfg

I am thinking now that perhaps by this you wanted me to change the permissions in the file, to make it an executable file. I didn't do it-- but perhaps I should go back and try that. Other than this line, I did exactly what you said for both workarounds and neither made the grub menu appear. :(

But I am very grateful for the suggestions, and if you have any further ones, I will be most happy to try them. :)

---

### Post by drs305 on 2011-05-25
> **swarup said:**
> I implemented both workarounds exactly as you suggested, but neither worked. The only thing I was uncertain of was where you wrote:



I wasn't sure if this was a directive for me to do something-- did you mean by this that you wanted me to do something like change the default activity type of this file to be an "executable". Because I didn't do anything in response to this line. Other than this line, I did exactly what you said for both workarounds and neither made the grub menu appear. Don't know why. :(

But I am very grateful for the suggestions, and if you have any further ones, I will be most happy to try them. :)

The 40_custom file has to be executable for it to be added to the script, but it should be by default. You can run the following to be sure:
```
sudo chmod +x /etc/grub.d/40_custom
```

Setting the timeout to -1 should have displayed the menu as long as the file you change is the grub file controlling the boot. Sometimes the user has multiple installations and the system boots off another OS's grub, but that doesn't seem possible in this case.

I'll check back to review the thread this weekend but the other's in the thread would have spotted anything out of the ordinary. It's certainly an interesting one.

---

### Post by swarup on 2011-05-25
Yes, I just browsed to the file in nautilus and checked the permissions. The little box making it an executable file is already checked. So it does seem to have been set up as an executable file. 

Thanks for your help thus far, and I look very much forward to hearing any further thoughts you may have on this problem, as it seems to be fairly unusual.

---

### Post by Quackers on 2011-05-25
It may be worth going into your bios (which looks like that's done by pressing F2 at boot on your system (rather than F12)) and reset your boot priority so that item 4 is moved upwards to position 2 in the list. Save those changes and reboot a couple of times and see if this changes anything.

---

### Post by swarup on 2011-05-26
@Quackers: Your idea sounds perfect. I thought to myself-- "perhaps this will stop the computer from pausing after the bios screen every bootup to look for SATA-5." This delays the boot for 1-2 minutes. 

So I went into the bios and moved item 4 (the bootable HD) up to position 2 in the boot sequence. I also removed what had been items 2 and 3, entirely from the boot sequence. Then saved changes, and booted up. I also rebooted several times after that. To my consternation, it still pauses to look for SATA-5 even though it isn't even in the boot sequence. And it still doesn't give the grub menu. But the worst of all is that now, even if I hit F2 or F12, it will not show the grub menu at bootup. That is, we found last night that if I hit F2 to enter the bios setup or F12 the one time boot key, then by doing so the grub menu will appear. But now that has ceased. No matter what I do, I can't get the grub menu to show any more. 

I went back into the bios and tried making the bootable HD (what was originally item 4) the ONLY item in the boot sequence. Still the computer looks for SATA-5 at bootup, and still no grub menu. I went back into the bios and set the boot sequence back to the original way it was yesterday with six items and the bootable HD at position 4. And STILL, no grub menu.

So what progress we made yesterday-- getting the grub menu to appear by hitting F2 or F12 at bootup-- is now gone. The grub menu does not seem to appear under any circumstances. Bizarre.

---

### Post by Quackers on 2011-05-26
What is sata 5? Is this a sata port on your motherboard? It doesn't sound like a drive name.
This is sounding more and more like a bios problem, as oldfred said.

---

### Post by swarup on 2011-05-26
The Bios lists around seven SATA ports, listed as SATA-0 through SATA-6. Of those, the principal internal HD is on port SATA-0, and the other internal HD, not currently connected, comes on SATA-5. Then there are two DVD drives, each taking up one of the SATA ports. 

Perhaps it is a Bios problem. But as I mentioned earlier, this matter of pausing looking for SATA-5 has been going on for years, and never been a problem for grub in the past. If right now I delete the Ubuntu partitions and install Ubuntu 10.04, or 9.10, or 9.04 or 8.10 in the place of 10.10, any of these will install perfectly without a hitch, and grub will immediately work perfectly. I have experienced it personally with all these installations, on this very computer. So there is definitely some issue with 10.10, due to which this is going on.

---

### Post by Quackers on 2011-05-26
Or your bios!
The fact that you have had other versions working previously may not guarantee that they will work again, although it does seem likely.
What happens if you plug your Ubuntu drive into sata 5?

---

### Post by swarup on 2011-05-26
When I plug our bootable drive into SATA-5 port, then after the Bios screen, the message comes 

```
Drive 0 not found: Serial ATA, SATA-0
Strike F1 key to continue
``` 

When I hit F1, it boots straight into Ubuntu. No grub menu.

The computer got used to having both SATA-0 and Sata-5 ports filled. Whichever one is left empty, it will complain about. If I use two HDs ie both SATA-0 and Sata-5 ports are filled, then it doesn't complain about not finding a drive, and boots right up.

---

### Post by Quackers on 2011-05-26
It's all very odd :-)
So what happens if you plug the Ubuntu drive back into sata 0 and the other drive into sata 5? What boots up then and what error messages, if any?

---

### Post by swarup on 2011-05-26
When I put the primary HD in SATA 0 and the other HD in SATA 5, then boot, first comes the BIOS screen, then a screen stating 
1. Lists details (brand, etc) of the HD on port 0, CD-ROMS on ports 01 and 04, and the HD on port 05.
2. RAID volumes: none defined
2. Details the port#, serial#, and size of the two HDs.
3. States: type <ctrl-I> to enter configuration utility.

Around 20-30 seconds later the computer boots to Ubuntu. No grub menu. No error messages listed at any time during the boot.

---

### Post by oldfred on 2011-05-26
It looks like your computer will automatically try to configure RAID with two drives in certain ports. Plus this post says the ports may be mislabeled.

[http://archive2.avsforum.com/avs-vb/showthread.php?t=776851](http://archive2.avsforum.com/avs-vb/showthread.php?t=776851)

If RAID gets configured it can cause grub problems with hidden data on the drive.

---

### Post by swarup on 2011-05-26
oldfred, what should I do? Are you suggesting that the solution to the problem is related with RAID configuration? If so, what is to be done, to get grub to appear?

---

### Post by oldfred on 2011-05-26
If you are not running RAID it shoud not hurt to run this, but I do not think it will make any difference. It seems like you have a system with a very limited BIOS.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

Did you check to see if there are any updates for your BIOS. Often older systems stop having updates, so you may not have any.

---

### Post by swarup on 2011-05-26
For this computer, the latest Bios Update available from the Dell website, was issued in July 2007. We got the computer in 2007 or 2008. I am not sure of the exact date now. But I think it was after July 2007, in which case there is no new bios update available. By booting into windows, if it were possible, we could find out the Bios version and see if what is available on the website is newer or not.

As for Raid, you expressed that you don't think it will make any difference even if we run it. If it is like that, I guess I'd prefer not to start studying all about what RAID is and how to implement it.

I do really want and need to get grub running though. If you or anyone has any further suggestion for how to get grub running, that will be extremely valuable. 10.10 has some features which will be very helpful to us.

Otherwise, I will regretably have to delete this installation of Ubuntu, and reinstall 10.04, which was running perfectly on this very computer until two days ago when we deleted it in order to install the newer one.

---

### Post by drs305 on 2011-05-26
I really have no idea what the issue is. Before reinstalling the entire OS, did you ever try to completely purge and then restore Grub. I think Quackers mentioned it early on but I didn't see a post that you had actually tried if (if I missed it I apologize). Completely purging and reinstalling G2 may repair any corrupted files. I can't explain why the timeout=-1 didn't work if the grub files are intact and in use.

Anyway, the commands from a booted system (no LiveCD) for completely purging G2 are below. Amplification of the procedures can be found at the "Chroot" link in my signature line (again, from a booted system you shouldn't need to chroot). Also there is a new GUI app called Boot Repair that makes things a bit less complicated. You still have to run a command manually but you may find it preferable.
Purge/Reinstall via Command Line:
```

sudo apt-get update # Ensure your Internet connection works.
apt-get purge grub grub-pc grub-common
apt-get install grub-common grub-pc  # What you'll see is in the 'Chroot' link.

```

Boot Repair App (Post 171):
[http://ubuntuforums.org/showpost.php?p=10864089&postcount=171]("http://ubuntuforums.org/showpost.php?p=10864089&postcount=171")

---

### Post by swarup on 2011-05-26
Thank you! :) I'll try this. I have not purged and reinstalled G2. If someone suggested it in this thread, I must have missed it somehow. But the terminal window commands you've given look very straight forward-- should be simple enough to do. I'll let you know how it goes.

---

### Post by swarup on 2011-05-26
I purged and reinstalled GRUB, using the terminal commands you gave. It went quite smoothly. Then I shut down the computer. Upon booting the computer up, it loaded straight into Ubuntu. No grub menu appeared. So I shut down the computer and again started it up. After the Bios screen, I hit F2 to enter the Bios. I didn't do anything there-- just exited. Then the grub menu appeared, and I selected Windows and it booted up into Windows fine. So one positive change has now come: Last night the computer was giving the grub menu if I first entered the Bios (F2). But all day today that feature was lost, and the computer would not give the grub menu even when entering the Bios first (via F2). Only now, after reinstalling grub, it has again given the grub menu after I enter the bios using F2.

What this all means I do not know. Any thoughts?

---

### Post by Quackers on 2011-05-27
> **swarup said:**
> When I put the primary HD in SATA 0 and the other HD in SATA 5, then boot, first comes the BIOS screen, then a screen stating 
1. Lists details (brand, etc) of the HD on port 0, CD-ROMS on ports 01 and 04, and the HD on port 05.
2. RAID volumes: none defined
2. Details the port#, serial#, and size of the two HDs.
3. States: type <ctrl-I> to enter configuration utility.

Around 20-30 seconds later the computer boots to Ubuntu. No grub menu. No error messages listed at any time during the boot.

Hi again :-)
If you are seeing a screen that tells you to press ctrl + I to enter configuration, it is likely that you have Intel RAID (or Fakeraid, as some call it). I know this because my laptop has it.
If you press ctrl+I when that message pops up (you'll need to be quick) a new screen will pop up with details of any raid settings.
Please give any details of any listed raid arrays or member discs.

---

### Post by swarup on 2011-05-27
Here is what it says on the screen that comes when you press <ctrl-I>:

```
Intel(R) Matrix Storage Manager option ROM v6.0.0.1022 ICH8R
Copyright (C) 2003-6 Intel Corporation. All Rights Reserved.

Main Menu

1. Create Raid Volume
2. Reset Disks to Non-RAID
3. Exit

Disk/Volume Information

RAID Volumes:
None Defined

Physical Disks:
Port  Drive Model     Serial #         Size       Type/Status (Vol ID)
0     ST3160815AS     9RX05...         149.0 GB    non-RAID Disk
5     ST31500341AS    6VS02...         1397.3GB    non-RAID Disk
```

Now for some more interesting information:

As you know, I have to connect the second HD in order to get the option to go to the screen above which you requested. Well this morning in so doing, I have found that regardless of whether or not I opt to go to this screen, by having the two drives connected the grub menu screen is reliably, consistently appearing. Last night when I wrote the posting prior to this one, it was not happening like this. I do not know how to account for the change.

When I remove the second drive, the grub menu screen does not appear-- unless, as noted in posting #81 above from last night, I hit F2 to enter the Bios in which case the grub menu screen DOES today still appear. But if I don't go into the bios, then it boots straight to Ubuntu without grub appearing. And when I connect the second drive, the grub menu appears without having to do anything i.e. without having to hit F2 to enter the bios. The second drive (the larger one listed above) contains a lot of sensitive data, and my colleague does not keep it connected except for when he needs to access the data.

---

### Post by Quackers on 2011-05-27
How very odd :-)
I really don't know what to make of that - I'm lost too!
Somehow, it seems that your bios is expecting to see a raid array when both drives are connected. However, as the Intel Matrix Storage Manager clearly states there are no raid volumes defined.
It is a very odd situation, or at least, it is one that I don't understand :-)
There's a reason for it, but I don't know what that may be.

So when both drives are connected the grub menu consistently appears and all operating systems are bootable from that?
Well that's good :-)  But not really what your friend wants to do :-(
My head hurts!

---

### Post by swarup on 2011-05-27
I have just gone into the bios and deactivated the SATA-5 port, so that the computer does not search for any drive there. Now when I boot even with only one HD connected, it gives the grub menu without having to do anything, and yes both OS's are bootable from grub. So I have discussed this with my colleague-- this arrangement will work for the time being. So long as he keeps only one HD connected, this works perfectly. The only problem now remains that if he wants to connect the second HD then he first has to start the computer, go into the bios, and activate the SATA-5 port. Which never used to be required with previous versions of Ubuntu up through 10.04. Because they would all give the grub screen even when SATA-5 was active and no HD connected there. 

So final issue: if anyone can think of why when SATA-5 port is active and no HD connected to it, grub screen does not appear (unless you hit F2)-- and how to make it appear in this situation (without having to hit F2), then we will have resolved the matter fully.

---

### Post by Quackers on 2011-05-27
If you plug that other drive into a different sata port does the bios start looking for something on that new port first?
Does the other drive have to be bootable or is there only data on it?

---

### Post by swarup on 2011-05-27
I'm not sure how to "plug that other drive into a different sata port". As far as I know, SATA-0 and SATA-5 are the ports assigned for the two HD bays. The upper bay is SATA-0, and the lower bay is SATA-5. As far as I know, these assignments are fixed. If you know how to change that, let me know and I can do so-- if you think it'll help resolve the situation.

The second HD does not have to be bootable, no. Ours just has data on it. The computer just wants to see a HD working there. I guess it gets reassurance by that. Like a baby with its mother. :)

---

### Post by Quackers on 2011-05-27
Sadly I'm unable to help with that. I'm much more used to laptops :-(
Are there no empty sata ports between 0 and 5 to try it? I'm guessing of course:-)

---

### Post by swarup on 2011-05-27
sata ports are there, but as far as I can tell all are pre-assigned and as far as I know, fixed assignments. For example, ports 1 and 4 are the DVD ROM drives, and port 2 and 3 are something else, I forgot what. They aren't even things which this computer has. But I would have no idea how to reassign the HD bay to, say, sata port 2.

---

### Post by Quackers on 2011-05-27
Sorry, I've been away :-)
Can't you literally plug in the drive to one of these ports?

---

### Post by swarup on 2011-05-27
Looking on the motherboard, I see only four sata ports. Two are connected to the two DVD ROM drives, and the other two to the HD's-- one is connected, the other not. I guess I could disconnect one of the DVD ROMs, and connect the wire from that sata port to the HD instead. It shouldn't hurt anything, right? Let me know, and I'll try it.

---

### Post by Quackers on 2011-05-27
I wouldn't have thought that should cause any problems (assuming that the drive you disconnect is empty).

---

### Post by swarup on 2011-05-27
You are correct-- there is no harm done. It is a very simple system. There are four sata ports on the mother board-- ports 0,1,4,5. And we have four drives-- two dvd rom drives, and two HDDs. Any of the ports can be connected to any of the drives, and it will be identified for what it is at the screen immediately following the bios at the time of boot. And if all four ports are kept active and any of them is left "hanging" without being attached to a drive, then that will cause the computer to boot straight to Ubuntu without grub appearing. And if any of the four ports is deactivated in the bios and is then left without being attached to a drive, then of course it is no problem. Grub appears during boot up. 

So ultimately, although we now understand more, the same problem remains-- my colleague wants to keep all 4 sata ports active, and only connect three routinely to drives. That was working fine with the previous Ubuntu installations, but with 10.10 it causes grub not to appear. Was it the same version of grub in 10.04 as in 10.10? Or if so, then I wonder what could have been changed with 10.10 that causes grub not to appear if one of the active sata ports does not have a drive attached? Or do people think that the problem is completely unrelated with Ubuntu, and is due to something in our computer? If so, then the odd point here is that all previous installations of Ubuntu were fine with an unattached active sata port.

---

### Post by Quackers on 2011-05-27
So it seems that when the bios knows it has an active sata port but does not have a drive attached to that port it somehow stops the grub menu from appearing but still allows Ubuntu to boot directly. Ubuntu is the top item in the grub menu, I assume, so it is possibly just defaulting to that first entry.

I don't know what changes were made to grub2 (if any) between 10.04 and 10.10.
Maybe others will know more about that.

---

### Post by oldfred on 2011-05-27
There used to be a device.map file which they obsoleted and it just probes for drives.

I might try just removing the search line in the grub.cfg line. There have been cases where searches that fail cause problems and perhaps an active port then then no drive causes a fail of some sort.

It might still use a device.map if it finds one. It would have to be in /boot/grub folder.

This was mine in Karmic (sdd was actually a flash drive):

(fd0)    /dev/fd0
(hd0)    /dev/sda
(hd1)    /dev/sdb
(hd2)    /dev/sdc
(hd3)    /dev/sdd

---

### Post by drs305 on 2011-05-27
1 Drive connected (before you disconnected SATA-5): You could try changing (you tried this before but now you have restored the default grub files) the timeout in /boot/grub/grub.cfg to **-1**.

I'm going to change what I suggested earlier to add an additional line:
> 
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
[s]  set timeout=10[/s]
  set timeout=**-1**
fi
  set timeout=**-1**


Don't run "update-grub", which would remove the edits. Just reboot when it's convenient and see if the menu shows up.

If this doesn't change the behavior, allow it to reboot and then run "sudo update-grub" to restore the original.

It might be interesting to post new copies of RESULTS.txt with both one and two drive setups, to see what is different, but I really don't know what's happening at the moment. Time for a:  ](*,)

---

### Post by swarup on 2011-05-27
I changed the timeout in /boot/grub/grub.cfg to -1 as per your most recent instructions. I then rebooted and went first into the bios (F2) to activate sata port 5. This is what we want to test-- if the grub menu will appear when sata port 5 is active i.e. all 4 sata ports are active, and only three of them are connected to drives. So having activated sata port 5, I saved the changes, exited the bios, and allowed the computer to boot. It booted straight into ubuntu. No grub menu appeared. So I ran "sudo update-grub" to restore the original.

Here below are the "result" files you requested. (Note that in some or all of these there is a flashdrive, named "TravelDrive" also connected to the computer):

1. RESULTS (One HDD & sata-5 port dormant)


```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for (,msdos5)/boot/grub.
 => No boot loader? is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

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
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2              81,920    21,053,439    20,971,520   7 NTFS / exFAT / HPFS
/dev/sda3    *     21,053,440   292,016,127   270,962,688   7 NTFS / exFAT / HPFS
/dev/sda4         292,018,174   312,498,175    20,480,002   5 Extended
/dev/sda5         292,018,176   310,411,263    18,393,088  83 Linux
/dev/sda6         310,413,312   312,498,175     2,084,864  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1029 MB, 1029439488 bytes
16 heads, 32 sectors/track, 3927 cylinders, total 2010624 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  32     2,009,087     2,009,056   e W95 FAT16 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        07D7-0605                              vfat       DellUtility
/dev/sda2        62B01238B01212E1                       ntfs       FreeAgent Drive
/dev/sda3        E6C4163AC4160D85                       ntfs       C Drive
/dev/sda5        1686567a-88ad-4e5d-b744-57ea9a6bf2f4   ext4       
/dev/sda6        202e855e-dfbb-4d03-82ba-6185f72c1254   swap       
/dev/sdb1        74AD-BD89                              vfat       TravelDrive

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/TravelDrive       vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 1686567a-88ad-4e5d-b744-57ea9a6bf2f4
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 1686567a-88ad-4e5d-b744-57ea9a6bf2f4
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=-1
fi
  set timeout=-1
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
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 1686567a-88ad-4e5d-b744-57ea9a6bf2f4
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=1686567a-88ad-4e5d-b744-57ea9a6bf2f4 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 1686567a-88ad-4e5d-b744-57ea9a6bf2f4
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=1686567a-88ad-4e5d-b744-57ea9a6bf2f4 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 1686567a-88ad-4e5d-b744-57ea9a6bf2f4
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=1686567a-88ad-4e5d-b744-57ea9a6bf2f4 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 1686567a-88ad-4e5d-b744-57ea9a6bf2f4
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=1686567a-88ad-4e5d-b744-57ea9a6bf2f4 ro single 
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
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 1686567a-88ad-4e5d-b744-57ea9a6bf2f4
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 1686567a-88ad-4e5d-b744-57ea9a6bf2f4
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Dell Utility Partition (on /dev/sda1)" {
	insmod part_msdos
	insmod fat
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 07d7-0605
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 62b01238b01212e1
	chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set e6c4163ac4160d85
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=1686567a-88ad-4e5d-b744-57ea9a6bf2f4 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=202e855e-dfbb-4d03-82ba-6185f72c1254 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 145.430713654 = 156.155039744  boot/grub/core.img                             1
 142.089122772 = 152.567033856  boot/grub/grub.cfg                             1
 142.007354736 = 152.479236096  boot/initrd.img-2.6.35-22-generic              2
 142.049804688 = 152.524816384  boot/initrd.img-2.6.35-28-generic              2
 145.754890442 = 156.503121920  boot/vmlinuz-2.6.35-22-generic                 1
 145.506931305 = 156.236877824  boot/vmlinuz-2.6.35-28-generic                 1
 142.049804688 = 152.524816384  initrd.img                                     2
 142.007354736 = 152.479236096  initrd.img.old                                 2
 145.506931305 = 156.236877824  vmlinuz                                        1
 145.754890442 = 156.503121920  vmlinuz.old                                    1


```


2. RESULTS (One HDD & sata-5 port active)

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for (,msdos5)/boot/grub.
 => No boot loader? is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

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
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2              81,920    21,053,439    20,971,520   7 NTFS / exFAT / HPFS
/dev/sda3    *     21,053,440   292,016,127   270,962,688   7 NTFS / exFAT / HPFS
/dev/sda4         292,018,174   312,498,175    20,480,002   5 Extended
/dev/sda5         292,018,176   310,411,263    18,393,088  83 Linux
/dev/sda6         310,413,312   312,498,175     2,084,864  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1029 MB, 1029439488 bytes
16 heads, 32 sectors/track, 3927 cylinders, total 2010624 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  32     2,009,087     2,009,056   e W95 FAT16 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        07D7-0605                              vfat       DellUtility
/dev/sda2        62B01238B01212E1                       ntfs       FreeAgent Drive
/dev/sda3        E6C4163AC4160D85                       ntfs       C Drive
/dev/sda5        1686567a-88ad-4e5d-b744-57ea9a6bf2f4   ext4       
/dev/sda6        202e855e-dfbb-4d03-82ba-6185f72c1254   swap       
/dev/sdb1        74AD-BD89                              vfat       TravelDrive

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/TravelDrive       vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 1686567a-88ad-4e5d-b744-57ea9a6bf2f4
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 1686567a-88ad-4e5d-b744-57ea9a6bf2f4
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
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 1686567a-88ad-4e5d-b744-57ea9a6bf2f4
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=1686567a-88ad-4e5d-b744-57ea9a6bf2f4 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 1686567a-88ad-4e5d-b744-57ea9a6bf2f4
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=1686567a-88ad-4e5d-b744-57ea9a6bf2f4 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 1686567a-88ad-4e5d-b744-57ea9a6bf2f4
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=1686567a-88ad-4e5d-b744-57ea9a6bf2f4 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 1686567a-88ad-4e5d-b744-57ea9a6bf2f4
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=1686567a-88ad-4e5d-b744-57ea9a6bf2f4 ro single 
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
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 1686567a-88ad-4e5d-b744-57ea9a6bf2f4
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 1686567a-88ad-4e5d-b744-57ea9a6bf2f4
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Dell Utility Partition (on /dev/sda1)" {
	insmod part_msdos
	insmod fat
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 07d7-0605
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 62b01238b01212e1
	chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set e6c4163ac4160d85
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=1686567a-88ad-4e5d-b744-57ea9a6bf2f4 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=202e855e-dfbb-4d03-82ba-6185f72c1254 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 145.430713654 = 156.155039744  boot/grub/core.img                             1
 142.091011047 = 152.569061376  boot/grub/grub.cfg                             1
 142.007354736 = 152.479236096  boot/initrd.img-2.6.35-22-generic              2
 142.049804688 = 152.524816384  boot/initrd.img-2.6.35-28-generic              2
 145.754890442 = 156.503121920  boot/vmlinuz-2.6.35-22-generic                 1
 145.506931305 = 156.236877824  boot/vmlinuz-2.6.35-28-generic                 1
 142.049804688 = 152.524816384  initrd.img                                     2
 142.007354736 = 152.479236096  initrd.img.old                                 2
 145.506931305 = 156.236877824  vmlinuz                                        1
 145.754890442 = 156.503121920  vmlinuz.old                                    1


```

3. RESULTS (Two HDDs & sata-5 port active)
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for (,msdos5)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb.
 => No boot loader? is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

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
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2              81,920    21,053,439    20,971,520   7 NTFS / exFAT / HPFS
/dev/sda3    *     21,053,440   292,016,127   270,962,688   7 NTFS / exFAT / HPFS
/dev/sda4         292,018,174   312,498,175    20,480,002   5 Extended
/dev/sda5         292,018,176   310,411,263    18,393,088  83 Linux
/dev/sda6         310,413,312   312,498,175     2,084,864  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048 2,930,274,303 2,930,272,256   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1029 MB, 1029439488 bytes
16 heads, 32 sectors/track, 3927 cylinders, total 2010624 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  32     2,009,087     2,009,056   e W95 FAT16 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        07D7-0605                              vfat       DellUtility
/dev/sda2        62B01238B01212E1                       ntfs       FreeAgent Drive
/dev/sda3        E6C4163AC4160D85                       ntfs       C Drive
/dev/sda5        1686567a-88ad-4e5d-b744-57ea9a6bf2f4   ext4       
/dev/sda6        202e855e-dfbb-4d03-82ba-6185f72c1254   swap       
/dev/sdb1        04FAAA34FAAA2242                       ntfs       C-2 drive
/dev/sdc1        74AD-BD89                              vfat       TravelDrive

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdc1        /media/TravelDrive       vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 1686567a-88ad-4e5d-b744-57ea9a6bf2f4
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 1686567a-88ad-4e5d-b744-57ea9a6bf2f4
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
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 1686567a-88ad-4e5d-b744-57ea9a6bf2f4
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=1686567a-88ad-4e5d-b744-57ea9a6bf2f4 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 1686567a-88ad-4e5d-b744-57ea9a6bf2f4
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=1686567a-88ad-4e5d-b744-57ea9a6bf2f4 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 1686567a-88ad-4e5d-b744-57ea9a6bf2f4
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=1686567a-88ad-4e5d-b744-57ea9a6bf2f4 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 1686567a-88ad-4e5d-b744-57ea9a6bf2f4
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=1686567a-88ad-4e5d-b744-57ea9a6bf2f4 ro single 
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
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 1686567a-88ad-4e5d-b744-57ea9a6bf2f4
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 1686567a-88ad-4e5d-b744-57ea9a6bf2f4
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Dell Utility Partition (on /dev/sda1)" {
	insmod part_msdos
	insmod fat
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 07d7-0605
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 62b01238b01212e1
	chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set e6c4163ac4160d85
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=1686567a-88ad-4e5d-b744-57ea9a6bf2f4 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=202e855e-dfbb-4d03-82ba-6185f72c1254 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 145.430713654 = 156.155039744  boot/grub/core.img                             1
 142.091011047 = 152.569061376  boot/grub/grub.cfg                             1
 142.007354736 = 152.479236096  boot/initrd.img-2.6.35-22-generic              2
 142.049804688 = 152.524816384  boot/initrd.img-2.6.35-28-generic              2
 145.754890442 = 156.503121920  boot/vmlinuz-2.6.35-22-generic                 1
 145.506931305 = 156.236877824  boot/vmlinuz-2.6.35-28-generic                 1
 142.049804688 = 152.524816384  initrd.img                                     2
 142.007354736 = 152.479236096  initrd.img.old                                 2
 145.506931305 = 156.236877824  vmlinuz                                        1
 145.754890442 = 156.503121920  vmlinuz.old                                    1


```

---

### Post by drs305 on 2011-05-29
About the only thing I have left for suggestions is to remove all but the actual menuentry, bypassing all Grub instructions. I've had to remove the *recordfail* check as that function isn't defined.

> menuentry 'Ubuntu, with Linux 2.6.35-28-generic' {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=1686567a-88ad-4e5d-b744-57ea9a6bf2f4 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-28-generic
}

Rename the original grub.cfg, then make the entry above the only contents in /boot/grub/grub.cfg. Save the file, but don't update-grub.
```

sudo cp /boot/grub/grub.cfg /boot/grub/grub.cfg.original
gksu gedit /boot/grub/grub.cfg
```

---

### Post by swarup on 2011-05-30
I executed the above instructions. With sata port 5 inactive, that grub menu worked fine. It appears, with only the ubuntu option showing (as expected). When I then go into the bios and activate sata port 5, but keep the HDD disconnected from port 5, and reboot, then I do not get the grub menu. It boots straight into Ubuntu without that simple grub menu appearing.

Now, I should give a slight bit more detail about what I saw happen in the latter scenario. When I boot, then after the bios screen I get the usual message:
```

Drive 5 not found: Serial ATA, SATA-5
Strike F1 key to continue 
```

After hitting F1, another screen ***does*** flash ever so momentarily on the screen, disappearing before I can see clearly what it is. And the computer then boots into ubuntu. But if I'm not mistaken, that screen which is there as a brief flash is the grub menu. I do not recall getting this brief screen with the normal grub. But I will go restore grub to its normal form now, and see if when sata port 5 is active with no HDD connected, that whether a similar very brief grub menu may be appearing...

---

### Post by swarup on 2011-05-30
And I will also now add that, with this very simple grub in place, and with sata port 5 active but HDD disconnected from it, then if at the bios screen I hit F2 to enter the bios but *make no changes*, just hit esc to exit and boot, then the grub menu appears.

---

### Post by drs305 on 2011-05-30
> **swarup said:**
> 
After hitting F1, another screen ***does*** flash ever so momentarily on the screen, disappearing before I can see clearly what it is. And the computer then boots into ubuntu. But if I'm not mistaken, that screen which is there as a brief flash is the grub menu. I do not recall getting this brief screen with the normal grub. But I will go restore grub to its normal form now, and see if when sata port 5 is active with no HDD connected, that whether a similar very brief grub menu may be appearing...

If it is the grub menu flashing momentarily, it's possible that adding 
> set timeout=10
as the first line of the shortened menuentry might add the delay in that scenario.

Also, these are things that the purge should have taken care of, but look in /boot/grub and make sure you don't have a device.map  or load.cfg file. If you do, inspect them to see what drives they list.

And finally, run "sudo dpkg-reconfigure grub-pc". You select the drive on which to install G2 with the SPACEBAR and tab to OK. See if it lists the phantom drive, but I'd be really surprised if it did. That about covers anything that G2 might have to do with Drive 5.

[COLOR="Red"]Added:[/COLOR] If you see this before posting #103, in the situation where you get the Grub menu, does it await your input or is there a timer that counts down and then it automatically boots?

---

### Post by swarup on 2011-05-30
I'll try adding the 10-second delay as you suggest, and see what happens. 

First though I'll report here what happened after I did sudo update-grub. On then rebooting, with sata 5 active and no HDD connected, after the bios screen comes the usual message:

Code:

```
Drive 5 not found: Serial ATA, SATA-5
Strike F1 key to continue
```

But, unlike with the simple grub you gave me, here with the normal grub installed there was no screen flash after hitting F1. I checked a couple times. No screen flash.

However, if I hit F2 to go into the bios and make no changes, just exit and boot, then even with the normal grub installed it is giving the grub menu. 

I don't know what it is about entering the bios and making no changes, but doing so makes the grub menu appear.

I'll now try the 10-second delay you suggest with the abbreviated grub menu...

---

### Post by swarup on 2011-05-30
> **drs305 said:**
> If it is the grub menu flashing momentarily, it's possible that adding 

set timeout=10 

as the first line of the shortened menuentry might add the delay in that scenario.

Tried it. It still remains only a flash. But now I have watched it so many times that it has become pretty clear to me that that screen is the grub menu.

> **drs305 said:**
> Also, these are things that the purge should have taken care of, but look in /boot/grub and make sure you don't have a device.map  or load.cfg file. If you do, inspect them to see what drives they list.

I looked-- those files are not there.

> **drs305 said:**
> And finally, run "sudo dpkg-reconfigure grub-pc". You select the drive on which to install G2 with the SPACEBAR and tab to OK. See if it lists the phantom drive, but I'd be really surprised if it did. That about covers anything that G2 might have to do with Drive 5.

It does not list the phantom drive.

> **drs305 said:**
> [COLOR="Red"]Added:[/COLOR] If you see this before posting #103, in the situation where you get the Grub menu, does it await your input or is there a timer that counts down and then it automatically boots?

Yes, there a timer that counts down and then it automatically boots.

---

### Post by swarup on 2011-05-30
Any final thoughts on this matter anyone? What do people think may be at the root of this problem. So much time has been been generously spent by various people on this issue, I hate to leave it unsolved. But I don't know in which direction to look.

---

