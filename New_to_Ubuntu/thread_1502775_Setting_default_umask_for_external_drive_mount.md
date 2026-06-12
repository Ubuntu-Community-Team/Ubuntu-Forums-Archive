---
title: "Setting default umask for external drive mount"
date: 2010-06-06
forum: New to Ubuntu
---

### Post by jervill on 2010-06-06
Hi, I am trying to find a way to mount an external drive (NTFS) so that anyone can read to it. Right now by default it mounts as drwx------ (700). When I share it on the network with Samba, guest users cannot even read the files. I've mounted it with the mount command specifying umask as 0022 and that did the trick. Now I'm trying to find a way for the drive to automatically mount as drwxrw-rx- as soon as it is plugged in.

I've already tried the following solutions and the drive still automatically mounts only as drwx------...
[LIST=1]
[*]adding the line "umask = 0022" to /etc/profile
[*]adding the line "umask = 0022" to ~/.bashrc
[*]adding the line "session optional pam_umask.so umask=022" to /etc/pam.d/common-session
[/LIST]

Any help would be greatly appreciated. Thanks!

---

### Post by geoffjay on 2010-06-06
did you try

$ sudo mount -o umask=0022 /dev/sdx /path/to/mnt

?

---

### Post by jervill on 2010-06-06
Thanks for the reply geoffjay, that sets the permissions right. But the problem is that every time I plug the drive in, Ubuntu automatically mounts it with permissions 700. I'd then have to umount it, then mount it again the way you described to make the permissions 755. I want to avoid umounting, then mounting again each time I plug the drive in so I was hoping there was a way to set it up so that the moment I connect a drive, Ubuntu automatically mounts it with 755 permissions.

---

### Post by geoffjay on 2010-06-06
You'll need to create an fstab entry that uses auto mount, I haven't done this in a long time but you could try adding the following to /etc/fstab:

/dev/sdx  /path/to/mnt  ntfs-3g  auto,users,uid=1000,gid=100,dmask=022,fmask=133  0  0

Then umount and try plugging it back in to see if that works. If you just want the same permissions for file/directory you could replace f/dmask with umask.

---

### Post by jervill on 2010-06-06
> **geoffjay said:**
> You'll need to create an fstab entry that uses auto mount, I haven't done this in a long time but you could try adding the following to /etc/fstab:

/dev/sdx  /path/to/mnt  ntfs-3g  auto,users,uid=1000,gid=100,dmask=022,fmask=133  0  0

Then umount and try plugging it back in to see if that works. If you just want the same permissions for file/directory you could replace f/dmask with umask.

Thanks! This solution sort of works for me now. The problem is whenever I simply plug in the device, I get an error saying:
> "Unprivileged user can not mount NTFS block device using the external FUSE library. Either mount the volume as root or rebuild NTFS-3G with integrated FUSE support and make it setuid root. Please see more information at [http://ntfs-3g.org/support.html#unprivileged](http://ntfs-3g.org/support.html#unprivileged)
From what I read, the "users" option on the fstab should *normally* allow any user to mount the drive, but apparently that option [does not work with NTFS-3G]("http://tuxera.com/community/ntfs-3g-faq/#useroption2"). So now what I do is type "sudo mount -a" which mounts the volume as root, as the error suggested, and it mounts the drive as specified in the fstab. It's not as ideal as having the thing mount the moment it is plugged, but it is much better than unmounting and than mounting again. I'm happy with that for now, thanks for the help!

---

### Post by geoffjay on 2010-06-07
You're welcome.

---

### Post by rykel on 2010-07-03
I am facing exactly the same "unprivileged user" nonsense and feeling very frustrated by it!

Is there a way to reset the way Ubuntu reads/mounts external drives, partitions and USB thumbdrives?

Thanks for helping.



UPDATE

I solved my own problem!

Simply purge 3rd party drive managers (eg. Storage Device Manager), comment out all the NTFS lines in /etc/fstab, do a "sudo blkid", reboot, plug in the devices and let Ubuntu auto-detect/auto-setup the UUID of the devices. I hope this solves your problems too!

The problem seems to be due to the fact that Lucid does NOT use /dev to identify devices anymore, and uses UUID instead.

---

### Post by Morbius1 on 2010-07-03
If the problem is isolated to this:
> Right now by default it mounts as drwx------ (700). When I share it on  the network with Samba, guest users cannot even read the files.The solution is this:
Add the following line to /etc/samba/smb.conf:
```
force user = jervill
```*[COLOR=Blue]Changing jervill to your actual login user name.[/COLOR]* 

It will act as a mask and convert the remote user to you for that share. Where you put that line depends on what method of samba sharing you're using:

For Nautilus-share ( right click > Sharing options ) you need to put it in the [global] section of smb.conf

For Classic-share you need to put it in the share definition section itself in smb.conf

---

### Post by ross.ackland on 2010-08-16
This is really frustrating that you cant easily change the default umask for automounting USB drives. In my case (runing Mythbuntu 10.04) my NTFS USB 1TB drive mounts with 700 permissions and my USB memory stick (VFAT) mounts with 755 permissions. Putting an entry in fstab seems like a brute force workaround which is disk specific. Surely being able to change the default setting is not a big ask???
 
This thread seems to explain the problem: 
[[FONT=Calibri][SIZE=3][COLOR=#0000ff]https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/482501[/COLOR][/SIZE][/FONT]]("https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/482501")
 
If anyone can shed more light on this, please post.

---

