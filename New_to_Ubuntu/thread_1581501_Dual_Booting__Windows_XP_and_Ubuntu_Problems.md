---
title: "Dual Booting  Windows XP and Ubuntu Problems"
date: 2010-09-25
forum: New to Ubuntu
---

### Post by illinois556 on 2010-09-25
Hello everyone, I am very new to all this, since I am use to Windows rather than Linux and decided to give it a try!

  I installed Ubuntu on my 250GB HDD and XP on my other one. 
Well, when I reboot to try to boot XP/Ubuntu, nothing happens and it goes to a black screen with a flashing -.

So the only way I can get Ubuntu to run is by un-plugging the Windows XP drive (I am on Ubuntu right now.)


How can I fix this so I can boot between them?   (I am running Ubuntu 10.04)


Thank you! :)

---

### Post by john newbuntu on 2010-09-25
First of all, welcome to Ubuntu.

Try changing the boot order of drives in BIOS.  Let the BIOS look at the Ubuntu drive first and then the windows drive.  Here's a guide that may be of some help to you:
[http://support.whitecanyon.com/?_m=knowledgebase&_a=viewarticle&kbarticleid=7](http://support.whitecanyon.com/?_m=knowledgebase&_a=viewarticle&kbarticleid=7)
(Do not try any of the wipe drive features)

If you do manage to boot into Ubuntu, open up a terminal (Applications->accessories->terminal) and type:
```
sudo update-grub
```Then reboot and see if you are able to boot into both the OS.

---

### Post by foxmulder881 on 2010-09-25
Do you mean a flashing "_" with out the quote marks? If so, have you waited long enough for it to boot?

---

### Post by jtarin on 2010-09-25
In Ubuntu open a terminal and enter the command ```
sudo fdisk -l
``` and post the results.I've attached an image of the Grub2 boot screen. Do you get this screen with both drives attached or only Ubuntu?

---

### Post by illinois556 on 2010-09-25
> **john newbuntu said:**
> First of all, welcome to Ubuntu.

Try changing the boot order of drives in BIOS.  Let the BIOS look at the Ubuntu drive first and then the windows drive.  Here's a guide that may be of some help to you:
[http://support.whitecanyon.com/?_m=knowledgebase&_a=viewarticle&kbarticleid=7](http://support.whitecanyon.com/?_m=knowledgebase&_a=viewarticle&kbarticleid=7)
(Do not try any of the wipe drive features)

If you do manage to boot into Ubuntu, open up a terminal (Applications->accessories->terminal) and type:
```
sudo update-grub
```Then reboot and see if you are able to boot into both the OS.

I have tried doing that and put the Ubuntu drive first but without any luck of it loading still.

> **foxmulder881 said:**
> Do you mean a flashing "_" with out the  quote marks? If so, have you waited long enough for it to boot?

Sorry, yes it is the "_" flashing and I let it sit there for about 10-15 minutes flashing to see if it would load, but just stayed there.


> **jtarin said:**
> In Ubuntu open a terminal and enter the command  ```
sudo fdisk -l
``` and post the results.I've attached an image  of the Grub2 boot screen. Do you get this screen with both drives  attached or only Ubuntu?
Alright, I will be attaching the image of what it says.
  Nope, I don't see anything but a black screen with just a flashing "_" and I can't have both drives plugged in at one time without it staying there on the black screen, so I have the XP unplugged for now until I can get help figuring out how to fix it.

---

### Post by beew on 2010-09-25
I don't know, but just making a guess. Suppose you have an OS installed in your hard disk and you configured the BIOS to boot from USB. If you have a bootable USB attached to the computer you will boot from it with no issue. But what if you have an usb without a boot loader attached? You will get the black screen you described because the PC is trying to boot into the usb but it can't so it is stuck.

Here it seems the same phenomenon is happening. PC is configured to boot from Windows drive, but it has become unbootable somehow when you installed Ubuntu  for dual boot with both drives attached. You said you have reset the BIOS to boot into the Ubuntu drive, but sometimes it may not work and you may have to bring up the one time boot menu to set the boot sequence.

Like I said I am only guessing since I have no experience with  PC two hard drives, but I have played with external hard drives and the like so I think the idea may be similar.

To test this hypothesis try just plug in the Windows  drive and see if it boots. I bet it doesn't.

---

### Post by Kr4zyl3gz on 2010-09-25
I see im a lil late to respond to this thread >.>  :(

---

### Post by illinois556 on 2010-09-25
> **beew said:**
> To test this hypothesis try just plug in the Windows  drive and see if it boots. I bet it doesn't.

Nope, I unplugged the drive with Ubuntu on it and plugged my XP drive in and it went to the black screen with the "_" for 2 seconds then loaded right up to XP (which I am on now).

---

### Post by beew on 2010-09-25
Ok, so it is not true that the XP drive alone is not bootable, so there seems to be a conflict between the boot sequence setting in the BIOS (boot from Xp drive) and the dual boot configuration (boot from Ubuntu drive) See if you can bring up the one time boot menu while you boot up and give the boot priority to the Ubuntu drive?  I know you said you have set the boot sequence to Ubutu drive first, but for some reasons some BIOS just ignore the reset still boot based on whatever default they were originally set to  unless you intervene at boot (In one of my Laptops I have to bring up the one time boot menu twice if I  want to boot from a usb drive even though the usb is given priority over CD and internal hd in the bio setting and it is a quite new too)

---

### Post by illinois556 on 2010-09-25
> **beew said:**
> Ok, so it is not true that the XP drive alone is not bootable, so there seems to be a conflict between the boot sequence setting in the BIOS (boot from Xp drive) and the dual boot configuration (boot from Ubuntu drive) See if you can bring up the one time boot menu while you boot up and give the boot priority to the Ubuntu drive?  I know you said you have set the boot sequence to Ubutu drive first, but for some reasons some BIOS just ignore the reset still boot based on whatever default they were originally set to  unless you intervene at boot (In one of my Laptops I have to bring up the one time boot menu twice if I  want to boot from a usb drive even though the usb is given priority over CD and internal hd in the bio setting and it is a quite new too)

I'm confused on what you are wanting me to try?

Did you want me to try plugging both HDD in and bringing up the one time boot menu and boot from Ubuntu drive?   I think that's what I made out of what you said.

---

### Post by jtarin on 2010-09-25
> **illinois556 said:**
> 

 I installed Ubuntu on my 250GB HDD and XP on my other one. 
Well, when I reboot to try to boot XP/Ubuntu, nothing happens and it goes to a black screen with a flashing -.

If you can boot Ubuntu...you have to see the Grub screen in my previous post. It's impossible to boot unless your using another boot manager.You state you have installed Ubuntu on your 250GB drive. What size is the XP drive?

---

### Post by beew on 2010-09-25
> **illinois556 said:**
> I'm confused on what you are wanting me to try?

Did you want me to try plugging both HDD in and bringing up the one time boot menu and boot from Ubuntu drive?   I think that's what I made out of what you said.

Yes.

---

### Post by wilee-nilee on 2010-09-25
Post the bootscript in my signature in code tags. This will give us a overall picture of the setup. Code tags for the results text can be made by clicking on the # in the reply put the text in between.

---

### Post by illinois556 on 2010-09-25
Alright, well I was messing around in the BIOS a little more "munkering" with stuff and found IDE section (Primary, Secondary, Both).

 Well, it was on 'Both', so I tried changing it to secondary and tried and it loaded up XP (with both HDD plugged in).   So, I went back into BIOS and changed it to Primary and TADA;  Ubuntu loaded right up!

SO,  now do I open a terminal and type 'sudo update-grub'?

If so, I just tried that and this is what it says in 'terminal'.

```

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
done

```but it doesn't say anything about XP in there that it added. Did I do something wrong?

Edit:   I just checked to see if it even picked up the other HDD and it's not showing, so I guess changing the IDE to primary it shut off secondary, so I guess that didn't work.



I am unsure why it is showing  Windows Vista/7 in the Boot Info Summary, when I don't even own Vista/7.
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *    204,812,748   468,905,219   264,092,472   7 HPFS/NTFS
/dev/sda2                  63   204,812,684   204,812,622  83 Linux
/dev/sda3         468,905,220   488,392,064    19,486,845   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        868AA6E28AA6CDCD                       ntfs       Extra Drive                   
/dev/sda2        8dd28f53-29f3-4473-b4f4-4f5932d85905   ext3                                     
/dev/sda3        70CCCF0DCCCECC92                       ntfs       Music Drive                   
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext3       (rw,errors=remount-ro)


=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 8dd28f53-29f3-4473-b4f4-4f5932d85905
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1280x1024
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 8dd28f53-29f3-4473-b4f4-4f5932d85905
set locale_dir=($root)/boot/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 8dd28f53-29f3-4473-b4f4-4f5932d85905
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=8dd28f53-29f3-4473-b4f4-4f5932d85905 ro  splash vga=795  quiet splash nomodeset video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 8dd28f53-29f3-4473-b4f4-4f5932d85905
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=8dd28f53-29f3-4473-b4f4-4f5932d85905 ro single  splash vga=795
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 8dd28f53-29f3-4473-b4f4-4f5932d85905
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=8dd28f53-29f3-4473-b4f4-4f5932d85905 ro  splash vga=795  quiet splash nomodeset video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 8dd28f53-29f3-4473-b4f4-4f5932d85905
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=8dd28f53-29f3-4473-b4f4-4f5932d85905 ro single  splash vga=795
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 8dd28f53-29f3-4473-b4f4-4f5932d85905
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 8dd28f53-29f3-4473-b4f4-4f5932d85905
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda2       /               ext3    errors=remount-ro 0       1
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


  63.5GB: boot/grub/core.img
  63.5GB: boot/grub/grub.cfg
  63.5GB: boot/initrd.img-2.6.32-21-generic
  63.5GB: boot/initrd.img-2.6.32-24-generic
  63.5GB: boot/vmlinuz-2.6.32-21-generic
  63.5GB: boot/vmlinuz-2.6.32-24-generic
  63.5GB: initrd.img
  63.5GB: initrd.img.old
  63.5GB: vmlinuz
  63.5GB: vmlinuz.old
```

---

### Post by wilee-nilee on 2010-09-26
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    **Boot files/dirs:  ** 

Your missing the bootfile for XP here, not sure about the vista/7 reference, the bold line should have these.
Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

Not sure about the fix process though.

Are you sure you have two hard drives I only see one and no raid indication. Are you confusing HDs' with the C and D drive lettering in Windows as HDs' rather then partitions?

---

### Post by illinois556 on 2010-09-26
> **wilee-nilee said:**
> Are you sure you have two hard drives I only see one and no raid indication. Are you confusing HDs' with the C and D drive lettering in Windows as HDs' rather then partitions?

I am positive I have 2 Hard Drives (I do have 2 Partitions on my 250GB (D (Misc) and E(Music) & 1 partition for Linux).   On my 40GB HDD I only have just C on it with no partitions.

 I took a few different photos of my BIOS to show you guys what I am looking at a little bit.

The first picture is of the first BIOS screen that pops up.
The second picture I am showing you that there is 2 HDD hooked up (IDE 0 & 2)
The third picture is showing that the 250GB HDD is set to startup first before the 40GB.

Edit:  I just remembered when I got the 250GB (free), the person that gave it to me did have Vista on it, but I did format the whole HDD, but I don't know why it might be still showing vista/7 there.

---

### Post by wilee-nilee on 2010-09-26
The bootscript doesn't show that second IDE the XP one. I thought maybe the sda1 in the script your 250 gig hd probably wasn't the XP install.

It seems that the HD isn't showing. Might see if a XP install disc will see it from the repair section and run a chkdsk if so. Might look if it needs to be reseated.

---

### Post by jtarin on 2010-09-26
If you want Grub to see the XP drive you have to re-install Grub while the XP drive is connected and reinstall it to the MBR of your Primary drive which should be the XP drive. It will overwrite the XP MBR. You will need to use the Live CD.

---

### Post by illinois556 on 2010-09-26
> **jtarin said:**
> If you want Grub to see the XP drive you have to re-install Grub while the XP drive is connected and reinstall it to the MBR of your Primary drive which should be the XP drive. It will overwrite the XP MBR. You will need to use the Live CD.

That's the thing though, I can't have both HD hooked up (tried different things to try to get them to be connected but with no luck).

I can either have the XP hooked up or vice versa but not both, so there will be no way I can re-install Grub while the XP drive is hooked up also.

---

### Post by jtarin on 2010-09-26
Cann you not connect them both and then boot using the Ubuntu CD to reinstall Grub?

---

### Post by wilee-nilee on 2010-09-26
> **illinois556 said:**
> That's the thing though, I can't have both HD hooked up (tried different things to try to get them to be connected but with no luck).

I can either have the XP hooked up or vice versa but not both, so there will be no way I can re-install Grub while the XP drive is hooked up also.

**This makes no sense. Can you plug both drives in and boot a live Ubuntu cd if so post the bootscript again.**

---

