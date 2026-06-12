---
title: "I hosed my XP-Ubuntu dual-boot grub - help please"
date: 2010-03-31
forum: New to Ubuntu
---

### Post by kghastie on 2010-03-31
(This is a more succinct summary of a different post)

Aaargh. I'm pretty new to Ubuntu, and tried to add a dual-boot install to my Win installation on my work laptop (Lenovo T500, downgraded to XP SP3). Installed Karmic successfully, and I was able to boot via Grub 1.974 beta (I think that's the version).

However, I just now started to install Lenovo's Rescue & Recovery program. It asked me to restart, and now I just get a screen that says:

GRUB

And nothing else happens. No F keys do anthing, and the ThinkVantage key does nothing unless I press it at the beginning + F1 to get to the BIOS settings.

Can anyone help me? I have been googling and have been directed to RecoveringUbuntuAfterInstall, but the stuff is so far beyond my experience with MBRs and Grub and the R&R hidden partition that I am afraid I'll do more damage if I try anything without knowing which of the many options to pursue.

My order of preference are as follows:

1) Boot into the existing XP OS successfully, in any way.
2) Be able to boot into the existing Ubuntu installation
3) Be able to run the R&R alongside my dual-boot installation
4) Default to XP for now (during an unattended restart)

#1 is the biggie, but I would definitely take #2 at this point, too.  Here is my GParted info from running a LiveCD:

```

/dev/sda              149.05 GB

/dev/sda1   ntfs       50.00 GB boot-flagged
/dev/sda1   extended   99.05 GB no flags
  /dev/sda5 ext4       94.98 GB no flags
  /dev/sda6 linux-swap  4.07 GB no flags

```I did an install of 9.10 64-bit so I should have Grub 2 (although I remember it saying something about 1.974 beta). Is that "Grub 2" or "Grub Legacy"? I'm not sure how I could have ended up with Legacy since it was a fresh install from the 9.10 LiveCD.
  
 Here is my old fstab from /etc on the linux partition:
 
```
# <file system>                 <mount point>   <type>      <options>               <dump>  <pass>
proc                            /proc           proc        defaults                0       0

# / was on /dev/sda5 during installation
UUID=91f8145a-019c-483a-b471-a5e2cb8e16fb     /               ext4        errors=remount-ro         0       1

# swap was on /dev/sda6 during installation
UUID=ab66a6b3-a06b-4de7-8d8e-7ac1e042449c     none            swap        sw                      0       0

/dev/scd0                       /media/cdrom0   udf,iso9660     user,noauto,exec,utf8         0       0
/dev/sda1                     /media/winxp     ntfs-3g     defaults,locale=en_US.UTF-8     0     0

```I assume that my sysadmin wiped the initial Vista R&R hidden partition, but I might be wrong.

Any assistance would be HUGE - thanks in advance! If you can walk me through some steps, I'll try to be responsive over the next few hours. Otherwise even a link to the most appropriate forum posts or external pages would help...

Sorry for cross-posting, btw but it said I needed 75 posts before I could Visitor-Message a moderator to move this post from here:

[http://ubuntuforums.org/showthread.php?t=1443334](http://ubuntuforums.org/showthread.php?t=1443334)

This post should be more succinct

---

### Post by undecim on 2010-03-31
My guess is that the installer corrupted grub. (to answer one of your questions, grub 1.9xx is usually "Grub 2".)

So to fix that, we'll reinstall grub and reconfigure grub. To do that, you need to go to the live CD, open a terminal, and run these commands:

```
sudo mount /dev/sda5 /mnt
ls /mnt/home 
```

The "ls /mnt/home" command should print out your username. This is to make sure that 1, we have the correct partition and 2, that your installer didn't corrupt it. If you don't see your username here, post the output you do see here.

assuming both of the above commands worked without error, continue with

```
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt
```

If all goes well, you should have a root shell (with a # instead of $), and are effectively in your Ubuntu installation as root. I'm actually bending the forum rules to tell you to do this; we're not supposed to tell people to log in as root because you can break things easily if you don't know what you are doing. (although technically you aren't "logging in")

That being said, be careful while in any root prompt.

If all the commands have worked so far, then all we have left to do is:
```
grub-install /dev/sda
update-grub
exit
```

"exit" should drop your chroot and bring you back to a user shell (with $ at the end). If everything went well, you should be able to reboot and grub should be restored.

---

### Post by kghastie on 2010-03-31
Thanks.  How does this differ from the steps mentioned here:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Overwriting%20the%20Master%20Boot%20Record](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Overwriting%20the%20Master%20Boot%20Record)

Is your method safer or more reliable?  Sorry, I'm just spooked from hosing my system time and time again :)

---

### Post by undecim on 2010-03-31
> **kghastie said:**
> Thanks.  How does this differ from the steps mentioned here:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Overwriting%20the%20Master%20Boot%20Record](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Overwriting%20the%20Master%20Boot%20Record)

Is your method safer or more reliable?  Sorry, I'm just spooked from hosing my system time and time again :)

The method shown in your link will reinstall grub, but not configure it. Since in order to use the "update-grub" command effectively, either you need to boot into a working system (which we can't do at the moment) or set up a chroot (which is what my method did).

The chroot is just a way to get into a system without booting it so that we can run commands that will fix the boot process. 

Really, one could have used the method in that link to reinstall grub and hope that the R&R installer didn't do something that would make the configuration obsolete, but I figured since you have to boot a Live CD anyways, might as well kill two birds with one stone.

---

### Post by kghastie on 2010-03-31
> **undecim said:**
> 

```
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt
```
```
grub-install /dev/sda
update-grub
exit
```
"exit" should drop your chroot and bring you back to a user shell (with $ at the end). If everything went well, you should be able to reboot and grub should be restored.

Here's the output.  Restarting - crossing fingers...

```

ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount --bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# grub-install /dev/sda
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda
root@ubuntu:/# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
done
root@ubuntu:/# exit
exit
ubuntu@ubuntu:~$ 

```

---

### Post by kghastie on 2010-03-31
It worked!  Thanks so much!  Is it a pretty simple/safe matter to change the boot order to go into XP by default for now?

Thanks again you guys are all livesavers.

---

### Post by undecim on 2010-03-31
> **kghastie said:**
> It worked!  Thanks so much!  Is it a pretty simple/safe matter to change the boot order to go into XP by default for now?

Sure is. Just press ALT+F2 and type "gksu gedit" and open /etc/default/grub. Find "GRUB_DEFAULT=0" and change the 0 to whichever menu entry you want. 0 = the first option, 1 = the second option, etc.

Once you've changed it, just open a terminal and run "sudo update-grub" to apply the changes to the boot loader.

Also, I don't know how the Lenovo R&R works, but usually those types of things require their own partition. Read through the manual and see if you can find any info about what size partition it needs, and then you can create one using GParted from the Live CD.

---

### Post by undecim on 2010-03-31
This is the only useful information I could find regarding Lenovo R&R and Ubuntu:

[http://forum.thinkpads.com/viewtopic.php?f=9&t=76778](http://forum.thinkpads.com/viewtopic.php?f=9&t=76778)

Were to trying to create the "hidden" partition for use later in case you broke your XP install?

---

### Post by kghastie on 2010-03-31
> **undecim said:**
> This is the only useful information I could find regarding Lenovo R&R and Ubuntu:

[http://forum.thinkpads.com/viewtopic.php?f=9&t=76778](http://forum.thinkpads.com/viewtopic.php?f=9&t=76778)


Thanks that helped

> **undecim said:**
> 
Were to trying to create the "hidden" partition for use later in case you broke your XP install?

I think that's what it was doing, but I'm not sure.  I simply downloaded the Rescue & Recovery app from Lenovo, here: [http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-70034](http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-70034)

I don't see mention of creating a partition in the readme or the instructions on that page.  Otherwise I wouldn't have run it.  However, it sure seems like that might be what it tried to do...

---

### Post by adrinkrahene on 2010-05-04
peace

I tried to follow the information in this post in an attempt to fix my grub.
All was going will I got to the chroot prompt, but could not get pass 
that point. I am new to ubuntu, but I am thinking that it might have 
something to do with partition. I may have confounded the problem 
by rearranging the drive line up in CMOS (done for another reason)
anyway what happens is I get an error    
root@ubuntu:/# grub-install /dev/sda
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.



root@ubuntu:/boot/grub# df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb1            298736972  40681076 242880900  15% /
udev                   1548264       324   1547940   1% /dev
none                   1548264       324   1547940   1% /dev/pts
none                   1548264       324   1547940   1% /dev/shm
none                 298736972  40681076 242880900  15% /var/run
none                 298736972  40681076 242880900  15% /var/lock
none                 298736972  40681076 242880900  15% /lib/init/rw
root@ubuntu:/boot/grub# grub-install /dev/sdb
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

Hopefuly this could help you ,help me!
grub.cfg


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
  save_env prev_saved_entryfi
insmod ext2
set root=(hd1,1)
search --no-floppy --fs-uuid --set c39f1557-229b-4bc7-aac2-2887075968ad
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-20-generic-pae" {
recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
        set quiet=1
        insmod ext2
        set root=(hd1,1)
        search --no-floppy --fs-uuid --set c39f1557-229b-4bc7-aac2-2887075968ad
        linux   /boot/vmlinuz-2.6.31-20-generic-pae root=UUID=c39f1557-229b-4bc7-aac2-2887075968ad ro   quiet splash
        initrd  /boot/initrd.img-2.6.31-20-generic-pae


Thanks for any help you can give.

































































































































































































































































































































  GNU nano 2.0.9                               New Buffer                                                            Modified  

}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda3)" {
        insmod ntfs
        set root=(hd0,3)
        search --no-floppy --fs-uuid --set 627c39c47c3993af
        chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

---

