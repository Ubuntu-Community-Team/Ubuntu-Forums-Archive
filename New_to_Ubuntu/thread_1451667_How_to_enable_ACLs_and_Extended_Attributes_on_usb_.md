---
title: "How to enable ACLs and Extended Attributes on usb disk"
date: 2010-04-10
forum: New to Ubuntu
---

### Post by Ralph L on 2010-04-10
I am trying to backup my documents, which contain Access Control Lists (ACLs) and potentially extended user attributes (EAs), to a usb removable disk.  

To enable ACLs and EAs on my hard disk partitions I edited /etc/fstab to include acl,user_attr in the option field.  This works fine and I can use ACLs and EAs on my hard disk partitions.  One of my hard disk partitions is ext3 and the other is ext4.  Both work.

However, when I plug in my usb drive into my laptop, it makes no entry in the /etc/fstab.  Therefore I can't edit any entry for the removable usb disk.  I can read and write the usb disk fine, but I can't make it support ACLs and EAs.  Note: I am running an ext3 partition as my backup target on the usb disk.

Anybody know how to enable ACLs and EAs on usb removable disks.  Is there another file (like fstab) for removable usb devices?  I am running Karmic with all recent updates.  Have a Dell D610 laptop.

Any help very much appreciated.

Thanks
Ralph

---

### Post by blueridgedog on 2010-04-10
Unmount the disk manually, then add an entry in your fstab file to mount it as you wish - or simply remount it manually using the mount command.

---

### Post by psusi on 2010-04-10
You should probably be using tar or dump or something to make backups, which will grab the permissions and extended attributes and pack them into the archive, rather than copy the files directly to the external media.  As ralph said, if you really want to use the external media that way you can add an entry to fstab for it or manually mount it on the command line.

---

### Post by Ralph L on 2010-04-11
Blueridgedog:

Could you be a little more specific on what I need to do get ACLs and EAs to work on my usb disk.

I tried creating an entry in fstab.  This was my entry taken from /etc/mtab with the removable mounted: 
/dev/sdb2 /media/toshiba_ext3 ext3 rw,nosuid,nodev,uhelper=devkit 0 0

Note that I did try to ad the acl or ea.  I dismounted and unplugged the removable.  Then I plugged it in again.  It would not mount.  I tried:
"sudo mount /dev/sdb2" with various options.  Still wouldn't mount.
I tried a lot of variations to the fstab entry, but I could get the disk to mount.  

It seems like mounting of a usb disk is done completely independently of fstab.  Am I correct about that.  In fact the only way I know of to remount a usb drive after it has been unmounted is to unplug it and then plug it back in again.  When the disk is unmounted the only evidence I can find that it was ever in the system is the /dev/sdb2 entry.  When I unplug the drive even the /dev/sdb2 entry goes away.

Any additional thoughts are appreciated.

Ralph

Psusi:

I didn't know any of the archive/tar programs would preserve ACLs and EAs.  Are you sure about this?  I have found several sites complaining about the fact that almost all backup systems don't support ACLs and EAs.  So far the only one I have found is rdiff.

Ralph

---

### Post by blueridgedog on 2010-04-11
What is your output when you do the following - unmount it manually (do not remove it), make a mount point with sudo then mount it with your desired options as a sudo command.  

Here is an example, not using ACL though:

```
james@Ripstop:/$ mount
/dev/sdc1 on /media/KINGSTON type vfat 
james@Ripstop:/$ umount /dev/sdc1
james@Ripstop:/$ sudo mkdir /mnt/test
james@Ripstop:/$ sudo mount /dev/sdc1 /mnt/test
james@Ripstop:/$ mount
/dev/sdc1 on /mnt/test type vfat (rw)
```

---

### Post by psusi on 2010-04-11
Yes, gnu tar and dump have supported acls and extended attributes for several years now.

---

### Post by Ralph L on 2010-04-30
I was able to enable ACLs and Extended User Attributes on the ext3 partition on my usb removable drive.  It works most of the time.  It often gets an error the first time I plug in the drive after a boot up from scratch.  When it mounts with an error I can't unmount it with Nautilus.  I have to use Terminal.

For details please see the web site [http://ubuntulinuxnoviceguide.webs.com/](http://ubuntulinuxnoviceguide.webs.com/) .  In the box at the top that lists Sections select "Sec 5 Multi-User".  Then scroll down the page until you find the header "Enabling ACLs and EUAs on automounted usb removable disks".

---

