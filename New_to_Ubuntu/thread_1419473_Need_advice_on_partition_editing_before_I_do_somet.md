---
title: "Need advice on partition editing before I do something stupid"
date: 2010-03-01
forum: New to Ubuntu
---

### Post by rebuild on 2010-03-01
So when I was first getting Karmic up and running I had a few issues and had to reinstall.  However I believe that I may have made a few mistakes with that reinstall.  I was left with the old (slightly) unusable Karmic on a very large partition and my happier install on the small one.  I then used gParted to resize the old one but now my unallocated space is two partitions away. (See attached screenshot)  So my plan is this: can I delete sda5 (old unused karmic), delete sda8 (linux-swap), expand sda7 to encompass the unallocated and then keep sda6 as a usable swap?  All the partitions just seem so cluttered because of this now.  Help?

---

### Post by Miljet on 2010-03-01
Yes, it is possible to do what you have suggested, but there is a very good chance of breaking your existing system. That is because when you start deleting/resizing partitions the UUID for the partitions will change and you will have to update entries in Grub and /etc/fstab.

It looks like you have plenty of space so I would leave it as is until you are ready to upgrade to Lucid. Then you can use gparted to clean up the partitions and do a clean install at that time. Just my opinion.

---

### Post by rebuild on 2010-03-02
Thanks! I appreciate that!  Just so I'm good to go when the time comes; I'll go ahead with that original plan using gparted from the Lucid live cd, then just immediately upgrade at that same time?

---

### Post by coffeecat on 2010-03-02
> **Miljet said:**
> That is because when you start deleting/resizing partitions the UUID for the partitions will change and you will have to update entries in Grub and /etc/fstab.

Point of information:

It's good to be aware of the potential for changed UUIDs when repartitioning, but the version of Gparted in Karmic doesn't change the UUIDs when you resize and move a partition.

Long story short: I was doing some re-ordering on sda on my main machine the other day with the Karmic live CD. I'd shrunk Vista on sda1 and needed to shuffle everything else to the left to use the space and also to resize the Ubuntu ext3/4 partitions. Sda2 (ntfs Data) moved to the left but not resized, Jaunty root (Ext3) shrunk 62GB > 20GB and moved to the left, and Karmic root (Ext4) shrunk 62GB > 60GB and moved to the left. All achieved - much to my pleasant surprise - without UUID changes, and without data loss. Although I did do backups of everything before starting.

And, yes, I did shrink the Vista partition (90 > 70GB) with Gparted. And, no, it didn't bork Vista. And, yes, this was after trying Vista's own partition resizing utility which hung on me. :rolleyes:

Game, set and match to Gparted!

**Edit:** @rebuild, re-reading your post, and based on my experience, if you expand sda7 once you've deleted sda5 and sda8, the UUID won't change. Hopefully! :wink: But I have a suggestion for you. At present, sda7 is 212 GiB - which is big. If you expand it as you suggest, it will be over 600 GiB. Which is enormous. Why not create a data partition formatted NTFS? That way you can keep your personal files on the NTFS partition and have them available to both Ubuntu and Windows. NTFS read-write is reliable in Ubuntu and you've got Windows to do a chkdsk if the filesystem ever needs repair.

Just a thought.

---

### Post by bumanie on 2010-03-02
What you plan to do is basically OK. Although you are getting rid of swap on /dev/sda8, the one on /dev/sda6 is 17gb - swap of 2gb is ample for most installations. I guess space doesn't matter much on a drive that size, but a swap of that size is not necessary - you can keep it that size if you want. That's one of the great things about linux, one can do most things they wish to without restriction, if you want a swap partition that large, by all means keep it.

---

### Post by rebuild on 2010-03-02
All right, so I just went ahead and did it.  I deleted sda5 and the smaller swap and then expanded sda7 through the live cd.  During reboot however I now get this message before grub loads, 

GRUB loading
error: no such partition
grub rescue> 

I'm hoping there is an easy way to rename everything in grub that I don't know about.  Help? haha I appreciate it all so far!

---

### Post by coffeecat on 2010-03-02
Despite my experience with unchanging UUIDs, that could be a UUID problem - or something else. Perhaps grub was booting from your older sda5 installation. Whatever - we need some detailed information to see what has gone wrong. Boot up from the live CD, mount your Ubuntu root (sda7) partition from the Places menu, and post the following:

1 - terminal output of "sudo blkid"

2 - Contents of the file /boot/grub/grub.cfg (from your sda7 installation)

2 - Contents of the file /etc/fstab (from your sda7 installation)

We'll take it from there. You'll need to do copy and paste for all that lot - you'll never be able to copy it by hand.

**Edit:** please post those outputs in [noparse]```

```[/noparse] tags otherwise they are difficult to read.

---

### Post by rebuild on 2010-03-02
> **coffeecat said:**
> Despite my experience with unchanging UUIDs, that could be a UUID problem - or something else. Perhaps grub was booting from your older sda5 installation. Whatever - we need some detailed information to see what has gone wrong. Boot up from the live CD, mount your Ubuntu root (sda7) partition from the Places menu, and post the following:

1 - terminal output of "sudo blkid"

2 - Contents of the file /boot/grub/grub.cfg (from your sda7 installation)

2 - Contents of the file /etc/fstab (from your sda7 installation)

We'll take it from there. You'll need to do copy and paste for all that lot - you'll never be able to copy it by hand.

**Edit:** please post those outputs in [noparse]```

```[/noparse] tags otherwise they are difficult to read.
Ok!  Here goes:

Sorry I don't know how to get rid of those code tags :(  Also, in case it helps, the original sda7 is now known as sda 6 in gparted.  Thanks again!

**1 - terminal output of "sudo blkid"**

ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/loop1: UUID="61e0e578-6d2d-4c01-a968-8ab3532b6baa" TYPE="ext3" 
/dev/sda1: UUID="7042203942200686" LABEL="PQSERVICE" TYPE="ntfs" 
/dev/sda2: UUID="10CA20DCCA20C038" LABEL="SYSTEM RESERVED" TYPE="ntfs" 
/dev/sda3: UUID="B87622C176227FEC" LABEL="Acer" TYPE="ntfs" 
/dev/sda5: UUID="f899f388-2dee-4867-800d-cf6c184c2ad5" TYPE="swap" 
/dev/sda6: UUID="c97427fc-5019-42a1-9f83-460c080a6cc5" TYPE="ext4" 
/dev/sdb1: LABEL="" UUID="FE25-97EE" TYPE="vfat" 

**2 - Contents of the file /boot/grub/grub.cfg (from your sda7 installation)**

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
set root=(hd0,7)
search --no-floppy --fs-uuid --set c97427fc-5019-42a1-9f83-460c080a6cc5
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
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set c97427fc-5019-42a1-9f83-460c080a6cc5
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=c97427fc-5019-42a1-9f83-460c080a6cc5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set c97427fc-5019-42a1-9f83-460c080a6cc5
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=c97427fc-5019-42a1-9f83-460c080a6cc5 ro single 
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set c97427fc-5019-42a1-9f83-460c080a6cc5
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=c97427fc-5019-42a1-9f83-460c080a6cc5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set c97427fc-5019-42a1-9f83-460c080a6cc5
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=c97427fc-5019-42a1-9f83-460c080a6cc5 ro single 
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set c97427fc-5019-42a1-9f83-460c080a6cc5
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=c97427fc-5019-42a1-9f83-460c080a6cc5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set c97427fc-5019-42a1-9f83-460c080a6cc5
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=c97427fc-5019-42a1-9f83-460c080a6cc5 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 7042203942200686
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 10ca20dcca20c038
    chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (on /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set e2917bfc-0b98-4870-8342-9a4a5e036cae
    linux /boot/vmlinuz-2.6.31-17-generic root=UUID=e2917bfc-0b98-4870-8342-9a4a5e036cae ro quiet splash
    initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set e2917bfc-0b98-4870-8342-9a4a5e036cae
    linux /boot/vmlinuz-2.6.31-17-generic root=UUID=e2917bfc-0b98-4870-8342-9a4a5e036cae ro single
    initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (on /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set e2917bfc-0b98-4870-8342-9a4a5e036cae
    linux /boot/vmlinuz-2.6.31-15-generic root=UUID=e2917bfc-0b98-4870-8342-9a4a5e036cae ro quiet splash
    initrd /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set e2917bfc-0b98-4870-8342-9a4a5e036cae
    linux /boot/vmlinuz-2.6.31-15-generic root=UUID=e2917bfc-0b98-4870-8342-9a4a5e036cae ro single
    initrd /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set e2917bfc-0b98-4870-8342-9a4a5e036cae
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=e2917bfc-0b98-4870-8342-9a4a5e036cae ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set e2917bfc-0b98-4870-8342-9a4a5e036cae
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=e2917bfc-0b98-4870-8342-9a4a5e036cae ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
[B]
3 - Contents of the file /etc/fstab (from your sda7 installation)

[/B]# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=c97427fc-5019-42a1-9f83-460c080a6cc5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=4d7ef4c1-9546-4386-87fb-7e3fef50976e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

Thanks again!!

---

### Post by oldfred on 2010-03-02
Your swap is referring to the partition you have deleted:

/dev/sda5: UUID="f899f388-2dee-4867-800d-cf6c184c2ad5" TYPE="swap" 

# swap was on /dev/sda8 during installation
UUID=4d7ef4c1-9546-4386-87fb-7e3fef50976e none            swap    sw              0       0

edit your fstab to the UUID of the swap you have. Copy and paste into this:

gksudo gedit /etc/fstab

---

### Post by rebuild on 2010-03-02
> **oldfred said:**
> Your swap is referring to the partition you have deleted:

/dev/sda5: UUID="f899f388-2dee-4867-800d-cf6c184c2ad5" TYPE="swap" 

# swap was on /dev/sda8 during installation
UUID=4d7ef4c1-9546-4386-87fb-7e3fef50976e none            swap    sw              0       0

edit your fstab to the UUID of the swap you have. Copy and paste into this:

gksudo gedit /etc/fstab

I copied and pasted 

[I]/dev/sda5: UUID="f899f388-2dee-4867-800d-cf6c184c2ad5" TYPE="swap" 

# swap was on /dev/sda8 during installation
UUID=4d7ef4c1-9546-4386-87fb-7e3fef50976e none            swap    sw              0       0[/I] 

into fstab.  However when I rebooted I am still seeing the same error and am not allowed into grub.  Back in the live cd, I took another look at my gksudo gedit /etc/fstab and it is back to the way it was before I copied and pasted and saved.  

[I]aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0[/I]

Should I be trying to edit the fstab from sda6?  Right now it is a read only and wont let me make any changes.  What else do you think?

---

### Post by oldfred on 2010-03-02
My edit was from a working install and you need to edit from the liveCD.

I think this will work but I cannot test it:

sudo mount /dev/sda6 /mnt
gksudo gedit /mnt/etc/fstab

or 

This will give you superuser rights but be very careful not to modify anything else.
gksudo nautilus

Browse to /etc/fstab and open with gedit

---

### Post by coffeecat on 2010-03-02
> **rebuild said:**
>   What else do you think?

There's a second and more serious problem that's causing grub to fail. The erroneous swap partition reference in /etc/fstab wouldn't have caused grub to fail, merely a failure to mount a swap partition at bootup - which is serious but not fatal.

The problem is this in your grub.cfg file:

```
### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set c97427fc-5019-42a1-9f83-460c080a6cc5
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=c97427fc-5019-42a1-9f83-460c080a6cc5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic
}
```Also the same problem in every stanza that refers to your (previously sda7) installation. Although the UUID has not changed and is correct, the "set root=(hd0,7)" is wrong and needs to be changed to "set root=(hd0,6)" because sda7 is now sda6.

Normally, one shouldn't edit grub.cfg directly - one should run 'sudo update-grub' - but that has to be done from "inside" the hard drive installation. To do that you'd need to chroot from the live CD. Easier, I think, (but pace the purists) is to edit the grub.cfg file from the live CD, just to get you booting up. Edit just that first stanza that I've quoted so that (hd0,7) becomes (hd0,6). If you can then boot up, open a terminal and run "sudo update-grub' and that should rewrite the grub.cfg file will all correct entries (and take out the superfluous ones).

Hopefully. :?

Good luck!

**Edit:** just seen oldfred's latest post. Yes, you'll need to mount sda6 in the way he describes and then edit /mnt/boot/grub/grub.cfg, otherwise you'll edit the wrong grub.cfg

---

### Post by rebuild on 2010-03-02
> **coffeecat said:**
> 
**Edit:** just seen oldfred's latest post. Yes, you'll need to mount sda6 in the way he describes and then edit /mnt/boot/grub/grub.cfg, otherwise you'll edit the wrong grub.cfg

So I managed to try and edit that section, but it wont let me save the file because its on a read-only disk.  Strange that it will let me try and save fstab but not the grub. hmmm...

---

### Post by coffeecat on 2010-03-02
> **rebuild said:**
> So I managed to try and edit that section, but it wont let me save the file because its on a read-only disk.  Strange that it will let me try and save fstab but not the grub. hmmm...

Oops sorry, forgot that grub.cfg is read only. :oops: Warning! Dirty hack coming up!! :wink:

From live CD.

Make sure you have sda6 mounted on /mnt with 'sudo mount /dev/sda6 /mnt'.

Now (dirty hack). From a terminal:

```
sudo chmod 600 /mnt/boot/grub/grub.cfg
```Then edit the file with:

```
gksudo gedit /mnt/boot/grub/grub.cfg
```Save the edit and see if you can boot into Ubuntu on sda6. I'll post this straight away and then post again to tell you how to undirty the hack.

---

### Post by coffeecat on 2010-03-02
OK, I posted my previous post quickly to give you something to be working with. The 'sudo chmod 600' changes the read only permission on grub.cfg to read-write for root. Which it shouldn't be. But neither should you be editing it. Except these are special circumstances.

Assuming this all works, once you've got yourself booted into Ubuntu on sda6, open a terminal and...

```
sudo chmod 400 /boot/grub/grub.cfg
```... to change the permission back to read only. Then...

```
sudo update-grub
```... to regenerate grub.cfg properly. The superfluous entries for the installation that was on sda5 should now disappear as well.

Lastly, if you haven't already done so, edit /etc/fstab with the correct swap partition UUID.

---

### Post by rebuild on 2010-03-02
Boo, everything is edited in grub but still  I'm stuck without getting into grub with

GRUB loading
error: no such partition
grub rescue>

I feel like this should be the answer as well but I don't know why its not letting me in.  BAH!

---

### Post by coffeecat on 2010-03-02
There are six stanzas for sda6 - three versions of the kernel and a standard and recovery stanza for each. Make sure you have edited the one you are trying to boot from - or you're booting from the one you edited. Better still, post the edited stanza and we can check whether everything is OK.

---

### Post by rebuild on 2010-03-02
Ok here is the grub file and I put in bold the one I edited! 

PS - thanks again for all the help!

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
set root=(hd0,7)
search --no-floppy --fs-uuid --set c97427fc-5019-42a1-9f83-460c080a6cc5
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
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    **set root=(hd0,6)**
    search --no-floppy --fs-uuid --set c97427fc-5019-42a1-9f83-460c080a6cc5
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=c97427fc-5019-42a1-9f83-460c080a6cc5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic
}

---

### Post by coffeecat on 2010-03-02
Got it!

I hope. :|

> **rebuild said:**
> Ok here is the grub file and I put in bold the one I edited! 

PS - thanks again for all the help!

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
[COLOR=red]**set root=(hd0,7)**[/COLOR]
search --no-floppy --fs-uuid --set c97427fc-5019-42a1-9f83-460c080a6cc5
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
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    **set root=(hd0,6)**
    search --no-floppy --fs-uuid --set c97427fc-5019-42a1-9f83-460c080a6cc5
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=c97427fc-5019-42a1-9f83-460c080a6cc5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic
}

You need the eyes of a hawk, the wisdom of Solomon and the patience of Job to cope with grub 2 configuration files. :( But I've just seen another wrong set root line - I've emboldened it and reddened it for you. Try changing that to (hd0,6) and see what happens.

[-o<

---

### Post by rebuild on 2010-03-02
Hmm ok, I'm a little tired of it all now.  What if I just reinstall over top? Will that fix the issues? - meaning it didn't work this time, haha.  What do you think?

---

### Post by coffeecat on 2010-03-02
Well - I'm certainly out of ideas, so I wouldn't blame you if you re-installed. It's always a pity to do a reinstall though. It's incredibly frustrating when you're hit with a problem like this, but you can learn a lot by trying to fix it - even if you don't succeed. But reinstalling "over the top" should fix the problem simply because it will wipe out the old installation and reinstall grub properly.

Your call, but just a few thoughts and then I need to log off.

As you've probably guessed, grub 2 is somewhat more complicated than what's now called legacy grub - what was used on versions of Ubuntu before Karmic. Grub 2 is still fairly new to most of us, which is why I missed that last bad set root line at first. You don't have that in the legacy grub version of grub.cfg (menu.lst). So - if you want a little light reading (:wink:) around grub 2, here are a couple of links for you:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

If you do decide to reinstall, you might want to completely redo that extended partition. You could adjust the swap partition size and think about what I said about a separate NTFS partition for data to be shared between Windows and Ubuntu. I find that very useful. And/or some people like to have a separate /home partition. Something to think about.

Good luck with whatever you do.

---

### Post by rebuild on 2010-03-02
Well everything is all solved and repaired to its happy glory!  The solution was found in just reinstalling grub on the correct partition!  I found that at this thread:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Thank you coffeecat and everyone else for all the assistance!!!

---

### Post by coffeecat on 2010-03-03
> **rebuild said:**
> Well everything is all solved and repaired to its happy glory!

I'm glad to hear it! :)

When I woke up this morning the penny finally dropped. There was a fourth problem caused by the change of partition number from sda7 to sda6. The clue was in the fact that you weren't even getting the grub menu - and the terse grub error. That meant that the problem was at stage 1.5 - solved by reinstalling grub as you've discovered - congratulations. My apologies for missing that, although everything that oldfred and I told you to do needed doing anyway to get you booting into Ubuntu.

The only comment I'll make is that the thread you've linked starts with instructions for legacy grub which won't work for grub2. The commands for grub 2 are near the end of the thread. In case someone comes across this thread looking for answers, and needs a comprehensive grub2 guide, I'll re-post a link I've already posted specifically for grub2 which contains instructions for how to re-install grub2 from the live CD.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Happy Ubuntu-ing! :)

---

