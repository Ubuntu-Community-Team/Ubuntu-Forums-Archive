---
title: "Does Grub2 still use device.map?"
date: 2010-07-10
forum: New to Ubuntu
---

### Post by bwallum on 2010-07-10
Hi

I'm trying to find a way of setting up Ubuntu on a usb harddrive without resorting to disconnecting all existing hard drives within the machine that I use to run the live cd.

I know I can 'chroot' into the external drive environment. I also know that the former /boot/grub/device.map file is not installed by default, but can be installed with sudo grub-mkdevicemap.

Does Grub2 still use the device.map file when grub-install is run?

---

### Post by cj.surrusco on 2010-07-10
You shouldn't have to disconnect any other drives to do this. You just need to choose to install to the USB drive and make sure you're not mounting anything on the internal drives, unless you are trying to do something that I don't understand.

---

### Post by drs305 on 2010-07-10
The device.map file is located in /boot/grub/  It isn't required but can be used in Grub 2. The same command as Grub legacy: *grub-mkdevicemap* run as root.

---

### Post by bwallum on 2010-07-10
This is what I am doing.

I boot up with a live cd. The machine used has 3 internal hard drives. I connect my usb harddrive. I install Ubuntu onto my usb harddrive which grub sees as sdd.

I shut down the system, restart and go to the BIOS setup. I tell it to boot the usb drive first. Grub now sees the drive as sda, reads the grub.cfg file and then looks for the grub files on (hd3) because that was what it deduced when it installed from the live cd environment. The boot fails.

What I thought I could try is to edit the device.map on the external usb drive so that it contained only one entry hd0 = sda, then using the live cd environment mount the usb drive to /mnt bind in dev,proc,sys and usr, chroot into /mnt and run grub-install. What I am wondering is will grub-install then use just hd0 so that in the subsequent update-grub command generated grub.cfg file I get set root='(hd0,1)':D and not set root='(hd3,1)' !!!](*,)

---

### Post by john newbuntu on 2010-07-11
Just curious on whether you have tried this.  After booting from a liveCD, re-install grub2 to your external drive.  This is without having a device.map.  Remember to use the --root-directory option.
Step #13 from this post by drs305: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by bwallum on 2010-07-12
> **john newbuntu said:**
> Remember to use the --root-directory option.
Step #13 from this post by drs305: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
Hi John

Thanks for the response. As far as I'm aware the --root-directory option is to point grub to a non standard root on the same device. I think the issue is sorted though, at least to the point where the usb drive works.

When grub installs it automatically uses the UUID identifier of the drive it installs on and automatically assumes the grub files will be in /boot/grub. Here's a snippet from my /boot/grub/grub.cfg file on the usb external hard drive, generated from the00_header file in /etc/grub.d

> ### BEGIN /etc/grub.d/00_header ###
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
set root='(hd3,1)'
search --no-floppy --fs-uuid --set fd0c6442-dc3d-49ba-8e46-91657460fe52
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
set root='(hd3,1)'
search --no-floppy --fs-uuid --set fd0c6442-dc3d-49ba-8e46-91657460fe52
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###The UUID reference is correct for the first partition on my usb drive. When the drive is launched as first to boot in the cmos it now performs ok, in spite of the erroneous > set root='(hd3,1)'line. I don't really understand where the variable is stored (and means of editing) that makes this line appear in the grub.cfg file. There are still some internal workings of grub2 that are a bit mysterious to me! (Probably to the devs as well!)

I guess I shouldn't forget it is beta and be more patient but when things like device.map suddenly drops out of existence (and that was my past fix for similar boot fail issues) then I get a bit twitchy and try to find out what is going on.

---

### Post by bwallum on 2010-07-12
I tried ```
sudo mount /dev/sdd1 /mnt
sudo grub-install --root-directory=/mnt /dev/sdd
sudo umount /mnt
sudo reboot
```but no change to the grub.cfg file (after booting into the usb drive and running sudo update-grub).

How do I get rid of the - set root='(hd3,1)' - line?

---

### Post by oldfred on 2010-07-12
If you are at the grub menu have you tried use e to edit and change the hd3,1 to hd0,1 or hd1,1 or hd2,1?

---

### Post by drs305 on 2010-07-12
> **bwallum said:**
> I don't really understand where the variable is stored (and means of editing) that makes this line appear in the grub.cfg file. There are still some internal workings of grub2 that are a bit mysterious to me! (Probably to the devs as well!)


> 
How do I get rid of the - set root='(hd3,1)' - line? 


The  "set root='(hd3,1)'" is the result of a command run by grub-mkconfig_lib during update-grub:
> 
echo "set root='`${grub_probe} --device ${device} --target=drive`'"

and is incorporated into grub.cfg by the line(s) in /etc/grub.d/00_header which start with:
> 
prepare_grub_to_access_device 


You can insert any value you want to replace "(hd3,1)" by commenting the "prepare_grub_to_access_device" and using CAT to insert your own values on the two lines (set root= & search). I hesitate to give you the precise instructions as I have no idea how such a change to 00_header would affect the overall running of grub. Not to mention that this would be a brute force change that undoubtedly could be better accomplished by some other means (unknown to me unfortunately).

---

### Post by john newbuntu on 2010-07-12
So are you able to boot from the USB and get to the grub menu (and possibly boot an OS)?

In drs305's quote:
> 
echo "set root='`${grub_probe} --device ${device} --target=drive`'" 			 		

Actually in this very same line, if you replace 'drive' in the end by 'fs_uuid' without the quotes, you will have everything referenced by UUID.  But what would happen after the next grub update??

But I have a feeling that it is the 'search' line in grub.cfg that decides the root variable.  It does not matter what you set the 'root=' variable to. Try it first after backing up grub.cfg.  If this is true, then the "root=" variable is inconsequential.

---

### Post by bwallum on 2010-07-13
> **john newbuntu said:**
> So are you able to boot from the USB and get to the grub menu (and possibly boot an OS)?......


But I have a feeling that it is the 'search' line in grub.cfg that decides the root variable.  It does not matter what you set the 'root=' variable to. Try it first after backing up grub.cfg.  If this is true, then the "root=" variable is inconsequential.

I have tried e to edit the grub menu at boot and have managed to override an erroneous UUID in the past. 

I think that if the UUID is correct then you are right, it takes precedence and the 'set root='(hd3,1)'' command is overridden. I can see the benefit of leaving it in though, in the event that the UUID is wrong, then there remains a chance to manually set root to a BIOS designated hard drive

EDIT
I should add that the changes made by editing the grub commands at boot don't stick. They just work for the one boot. My concern with the set root='(hd3,1)' line is that if I plug my usb harddrive into a machine with four hardrives and drive 4 has a grub installation then does the root='(hd3,1)' take precedence and therefore I can't boot from my usb in that scenario. Any thoughts on precedence if both root= and search point to valid grub installations?

---

### Post by bwallum on 2010-07-13
I think I've answered my own question. This is the Grub2 command set at boot on my external usb drive> recordfail
insmod ext2
set root='(hd3,1)'
search --no-floppy --fs-uuid --set fd0c6442-dc3d-49ba-8e46-91657460fe52
linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=fd0c6442-dc3d-49ba-8e46-91657460fe52 ro   
initrd    /boot/initrd.img-2.6.32-24-genericThe machine I have experimented on has 3 internal drives with Ubuntu (and Grub2) installed on one of them. When I try substituting hd0,1;hd1,1 and hd2,1 in the "set root='(hdX,Y)' line Grub2 always goes for the root=UUID=fd0.... choice for the grub.cfg file. (I know this because the internal bootable drive has a different set root designation and UUID in it's grub.cfg file.). That is the 'set root=' command appears to have no effect (unless it does transiently set root and then gets superceded by the subsequent 'root=UUID=' command)

---

### Post by oldfred on 2010-07-13
I found on my USB flash drive even though the UUID was correct it installed as sdg and did not work. I have no sdd or sdf. The search must not go past empty drives or more than one as it did not find my flash to boot. When I manually reset drive number it worked. And it worked with the wrong drive number in my portable (it was sdb) so the UUID does overide the drive setting if found.

---

### Post by bwallum on 2010-07-13
I thought I would try and use the files in grub.d as that is where we are supposed to tweak grub with, is it not.

I created a 'custom' file and numbered it to start right at the top of the grub.cfg file. > #
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/-0_SetRoot ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
set root=UUID=fd0c6442-dc3d-49ba-8e46-91657460fe52

### END /etc/grub.d/-0_SetRoot ###

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
set root='(hd3,1)'
search --no-floppy --fs-uuid --set fd0c6442-dc3d-49ba-8e46-91657460fe52
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
.
.
.I don't know if putting -0_SetRoot (my 'custom' name for the file) before 00_header is right or not. However update-grub ran ok and grub.cfg was updated as you can see above. The external usb drive also continued to boot to Desktop which was a relief!

I've put the custom bit ahead of everything else because I think I remember that once a variable is set as grub boots, it ignores any further lines that might change it. E.g. the first set root= command is acted upon and then any other set root= statement is ignored. Is this correct??

I have also seen the grubenv file in /boot/grub/ which is currently commented out> # GRUB Environment Block
########...for 1000 columns...##Is it possible to set up variables such as root in this file?

What variables are already embedded in the part of grub that resides on the MBR and how can these be edited?

Is there a 'developers' version of a grub manual that explains more fully how the internals of grub work?

I think I'm learning the hard way so please forgive me asking blind questions.

---

