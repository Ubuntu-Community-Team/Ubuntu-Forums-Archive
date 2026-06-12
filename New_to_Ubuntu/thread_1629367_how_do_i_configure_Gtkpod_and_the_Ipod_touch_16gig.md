---
title: "how do i configure Gtkpod and the Ipod touch 16gig with usb?"
date: 2010-11-23
forum: New to Ubuntu
---

### Post by bradmayne04 on 2010-11-23
I've been reading and reading but can't figure this out!  I have gtkpod and the Ipod touch 16 gig.  I can see the selection for the Touch 16gig on the dropdown menu.  However I am prompted to select a "mount point"  and what i see is an area to put in the "ipod mount point" but I can't figure out what to put in there.  I've tried not doing anything and leaving what is there by default which is this: /media/ipod
Everything I have read is for firewire.  I am not using firewire.  I am using the white cable which came with the ipod touch which is a usb connection.  Can someone please give me a quick walkthrough with the correct commands and syntax?  thanx so much in advance to whoever can help!

PS when I go to the shell and cd to media I see the cdrom.  However when i cd to usb i see a media folder so i cd to that and i see the ipod listed. I then tried to mount using this command: mount /usb/media/ipod.  When i do that i get an error which is this:
brad@brad-laptop:~$ mount /usb/media/ipod
mount: can't find /usb/media/ipod in /etc/fstab or /etc/mtab
here is what I the BASH shell is showing step by step:
brad@brad-laptop:~$ ls
AMERICAN_HARDCORE.iso                 libdvdcss2_1.2.9-2medibuntu4_amd64.deb
brasero.iso                           Music
Desktop                               Pictures
Documents                             Public
Downloads                             Templates
examples.desktop                      usb
Firefox_wallpaper.png                 Videos
index.php?origURL=http:%2F%2Fwget%2F  w64codecs_20071007-0medibuntu1_amd64.deb
brad@brad-laptop:~$ cd usb
brad@brad-laptop:~/usb$ ls
media
brad@brad-laptop:~/usb$ cd media
brad@brad-laptop:~/usb/media$ ls
ipod
brad@brad-laptop:~/usb/media$ cd ipod
brad@brad-laptop:~/usb/media/ipod$ ls
iTunes_Control  Photos
brad@brad-laptop:~/usb/media/ipod$ 

and i tried without the "/" and i still get the same error message! i m gonna get mad and turn green LOL

what am i doing wrong?

---

### Post by Wobblybob on 2010-11-30
you can find the mount point of you ipod by connecting it with the cable then opening a Terminal and entering

mount

and pressing enter, you should get something like;

/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sda7 on /home type ext4 (rw,commit=0)
/dev/sda6 on /opt type ext4 (rw,commit=0)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/bob/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=bob)
djmount on /media/upnp type fuse.djmount (ro,nosuid,nodev,allow_other)
/dev/sdb1 on /media/MYIPOD type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)

as you can see my iPod [called MYIPOD] is mounted as;

/dev/sdb1 on /media/MYIPOD type vfat

so then entry should be /media/MYIPOD

I don't use this prog as I found is flakey but you may have better luck, I use Floola but I don't think it supports the itouch but check out their website if you can't get gtkpod to work. Not sure how you have managed to get the mount point to be within your home folder, that's very odd!

---

