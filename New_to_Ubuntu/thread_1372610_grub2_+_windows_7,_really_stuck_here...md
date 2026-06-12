---
title: "grub2 + windows 7, really stuck here.."
date: 2010-01-04
forum: New to Ubuntu
---

### Post by blampars on 2010-01-04
I've been running the windows 7 RC since march or so when I built my new machine.  Over the weekend I decided that I wanted to put Ubuntu 9.10 on my desktop, since I rarely use my old ubuntu laptop any more.

I started out with two partitions, a windows xp partition and a windows 7 partition.  I never used the XP partition so I erased it and made a / partition, a /home partition and a swap partition out of it.  Ubuntu installed just fine and everything seemed perfect.  Reboot.
Computer boots fine, gets to loading grub, then just straight boots to ubuntu with no options for windows 7.
No big deal, I will just add an entry for windows 7 as instructed from this post, as suggested by a member of this forum in another topic: [http://erickoo.wordpress.com/2009/06/14/how-to-add-vista-partition-to-grub-2-ubuntu-9-10-karmic-koala/](http://erickoo.wordpress.com/2009/06/14/how-to-add-vista-partition-to-grub-2-ubuntu-9-10-karmic-koala/)

It doesn't work.  Instead, I get the following error:
error: too many titles for menuentry: 7&#8243;
then it boots to ubuntu

Okay, so I'm going to reinstall windows 7 bootloader on the MBR and just use that, following this post: [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

On the window where you're supposed to select your drive, none are listed.  It's blank.  I don't have any drivers to load for my internal hard drive, so I click next and go to a command prompt to try to enter the commands anyway.  the first command (bootrec.exe /fixboot) brings up an error about no drives found (i think) and the second command (bootrec.exe /fixmbr) seems to work, as no errors come up.  I reboot.

I get an error about no operating systems found.
I then resinstall grub and am able to boot back into ubuntu so I can at least use my computer.

Keep in mind that using the fdisk -l command shows all my partitions are there and all seems to be in order.  I just can't, for the life of me figure out how to get this fixed.  I'm going on 3 hours of searching and trying different things to no avail, and so now I post and hope some of you all can help me out.

My system is:
Asus MB
AMD Phenom x4
4gb RAM
250gb HD

I have ubuntu 9.10 x64 installed, as well as Windows 7 RC x64 installed

Sorry for such a long post,
-Brad

---

### Post by Methuselah on 2010-01-04
Did you follow the steps to execute update-grub and all that.
Karmic has Grub 2 which is a different version from the one in previous releases.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by blampars on 2010-01-04
yes, I followed all the instructions including updating grub after i added my entries.

---

### Post by theozzlives on 2010-01-04
Karmic is known for not detecting Windows but a simple
```
sudo update-grub
```
should've fixed it. no need to add entries.

---

### Post by blampars on 2010-01-04
the entries i'm talking about are adding for windows 7 to grubs boot list as a selectable item at boot, using the /etc/grub.d/40_custom file, (because grub isn't finding it itself) saving it, making it executable and then sudo update-grub so it shows in the grub.cfg, which it does.

but that leads me to the following error upon reboot:
error: too many titles for menuentry: 7&#8243;

and then I boot into ubuntu, with no grub menu first to select anything else (if it were there to begin with).

-brad

---

### Post by Methuselah on 2010-01-04
Is there any chance you grub.cfg actually has multiple entries for windows now?

gedit /boot/grub/grub.cfg and look

If it does you should probably remove the 11_windows file you added and just run update-grub again.

Honestly, I would copy it elsewhere and try that anyway.

---

### Post by blampars on 2010-01-04
i didn't use the 11_windows file, i opted for 40_custom using those directions from that guys blog.

If I remove the 40_custom file and update grub, I get no windows 7 entry in my grub.cfg.

Rebooting the machine, and holding shift to force the grub menu to open, i see the following options to be selected:
Ubuntu, Linux 2.6.31-14-generic
Ubuntu, Linux 2.6.31-14-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)

---

### Post by Methuselah on 2010-01-04
Post your fdisk -l

That might help someone who knows the format compose a menu entry for you.

---

### Post by blampars on 2010-01-04
```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x47014701

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1824    14651248+  83  Linux
/dev/sda2           12749       30401   141797722+   7  HPFS/NTFS
/dev/sda3            1825       12748    87747030    5  Extended
/dev/sda5           12506       12748     1951897+  82  Linux swap / Solaris
/dev/sda6            1825       12504    85787037   83  Linux

Partition table entries are not in disk order

```

Additionally, here is my 40_custom file:
```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry &#8220;Windows 7&#8243; {
set root=(hd0,2)
chainloader +1
}

```

and here is my grub.cfg file
```

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
set root=(hd0,1)
search --no-floppy --fs-uuid --set 33be7a0c-7c25-420e-bbf5-f04bd53d90ad
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 33be7a0c-7c25-420e-bbf5-f04bd53d90ad
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=33be7a0c-7c25-420e-bbf5-f04bd53d90ad ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 33be7a0c-7c25-420e-bbf5-f04bd53d90ad
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=33be7a0c-7c25-420e-bbf5-f04bd53d90ad ro single 
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

menuentry &#8220;Windows 7&#8243; {
set root=(hd0,2)
chainloader +1
}
### END /etc/grub.d/40_custom ###

```

which results in this error: too many titles for menuentry: 7&#8243;
then boots to ubuntu
Holding shift to force grub menu shows that same error for a split second before the menu pops up, but no entry for windows 7 even though it is in the grub.cfg.

edit again:  I've made a bit of progress..  I noticed after I posted my 40_custom and grub.cfg files that my quotations around my menuentry "Windows 7" were not the same (from the copy/paste job from that guys blog).  After correcting the issue and holding shift, I now have a grub entry for Windows 7.
On selecting it, i get the following:

BOOTMGR is missing
Press CTRL+ALT+DEL to restart

What to do from this point, anyone?

---

### Post by Methuselah on 2010-01-04
This is what I found on BOOTMGR is missing error.
I have no personal experience here since I'm not running windows 7 or Vista.

[http://www.howtogeek.com/howto/windows-vista/fixing-bootmgr-is-missing-error-while-trying-to-boot-windows-vista/](http://www.howtogeek.com/howto/windows-vista/fixing-bootmgr-is-missing-error-while-trying-to-boot-windows-vista/)

Those instructions might wiep out GRUB though.

Is the below any help?

[http://ubuntuforums.org/showthread.php?p=2132767](http://ubuntuforums.org/showthread.php?p=2132767)

Sorry, windows is alien to me at this point...lol

---

### Post by blampars on 2010-01-04
yeah, that's what I initially tried at the beginning of all this.  The only problem being that this window [http://www.howtogeek.com/wp-content/uploads/2008/02/image18.png](http://www.howtogeek.com/wp-content/uploads/2008/02/image18.png) wasn't showing any drives in it.
Proceeding onwards to try it anyway, resulted in me not being able to boot anything (wiped grub) and having to reinstall grub from my ubuntu cd, which doesn't recognize windows :P


your second link ([http://ubuntuforums.org/showthread.php?p=2132767](http://ubuntuforums.org/showthread.php?p=2132767)) although interesting, didn't help my problem either. :(

I think the problem is that at first, I had installed Windows XP.  When I installed windows 7, it put it's boot information on the windows xp partition.  When I wiped that windows xp partition clean and installed ubuntu I lost the boot stuff for my windows 7.  the problem I'm facing now is how to get that information back and into my windows 7 partition so that I can boot it.  Without any boot information on the windows 7 partition, it'll be forever unbootable.  I think i've screwed myself, at this point. tbh.

---

### Post by blampars on 2010-01-04
anyone else have any ideas on how I can fix my blunder?

any more help would be appreciated.

---

### Post by Sef on 2010-01-04
D> evice Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1824    14651248+  83  Linux
/dev/sda2           12749       30401   141797722+   7  HPFS/NTFS
/dev/sda3            1825       12748    87747030    5  Extended
/dev/sda5           12506       12748     1951897+  82  Linux swap / Solaris
/dev/sda6            1825       12504    85787037   83  Linux


Windows should be on the first primary partition.

---

