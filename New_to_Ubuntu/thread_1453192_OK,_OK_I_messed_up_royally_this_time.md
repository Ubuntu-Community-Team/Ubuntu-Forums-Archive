---
title: "OK, OK I messed up royally this time"
date: 2010-04-12
forum: New to Ubuntu
---

### Post by atk_nut on 2010-04-12
OK, I had some video issues and I tried to fix the problem myself using some previous posts...recipe for disaster.  I added a couple lines to my xorg.conf file.  I rebooted, then wham-o.  I couldn't log in.  It gives me a 'cannot authenticate....general fault' (or something like that.)

Anyway, I fumbled my way to a command prompt, and to the xorg.conf. but I can't restore my backup, or edit the file.  It's all read only. It reports "read only file system"  Even with root (sudo).  I'm hoping some guru out there can help.....PLEASE!

Thanks.

BTW It's version 9.10

---

### Post by bug67 on 2010-04-12
Maybe you can boot from the LiveCD, access your files, back them up and reinstall.

Hopefully, someone more knowledgeable than me can pipe in before it comes to that.

---

### Post by Drone4four on 2010-04-12
If you have a terminal or a tty up and no X server running, then  this command should write you a new xorg.conf:
```

sudo X -configure

```

---

### Post by Drone4four on 2010-04-12
> **bug67 said:**
> Maybe you can boot from the LiveCD, access your files, back them up and reinstall.

Hopefully, someone more knowledgeable than me can pipe in before it comes to that.

Reinstalling is a last resort.

---

### Post by wojox on 2010-04-12
Reboot and hold down the left shift key.
Choose the recovery mode option.
Drop into a root shell.
Run:

```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old 
```

Then :

```
reboot
```

---

### Post by bug67 on 2010-04-12
See?  :)

---

### Post by atk_nut on 2010-04-12
> **Drone4four said:**
> If you have a terminal or a tty up and no X server running, then  this command should write you a new xorg.conf:
```

sudo X -configure

```

For this one, I get:

"Fatal server error:
Could not create lock file in /tmp/.tX0-lock"

---

### Post by atk_nut on 2010-04-12
> **wojox said:**
> Reboot and hold down the left shift key.
Choose the recovery mode option.
Drop into a root shell.
Run:

```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old 
```

Then :

```
reboot
```

For this one, I get "cannot move .. to ..: Read-only file system"

---

### Post by atk_nut on 2010-04-12
Sorry, one other thing.  I can't get to the netroot, or root menu items on the recovery menu.  When I hit the down arrow, I get to dpkg, then the menu kicks out saying "mountall cancelled general error mounting filesystems.  A maintenance shell will now be started."  Then I'm in a very unusable shell.

If I reboot and hit "ESC" a bunch of times as it's booting, I can get to the shell that I'm working in.

Thanks.

---

### Post by Drone4four on 2010-04-13
> **atk_nut said:**
> For this one, I get "cannot move .. to ..: Read-only file system"

For the mv command you have to add "sudo" in front:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

---

### Post by atk_nut on 2010-04-13
> **Drone4four said:**
> For the mv command you have to add "sudo" in front:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

Yep, did that.  That's why I'm so stuck.  I still get the read-only message.

Thanks.

---

### Post by sigurnjak on 2010-04-13
Try booting with live cd and removing offending file that way while your HD install is dormant .

---

### Post by adam814 on 2010-04-13
I'd recommend booting from the LiveCD and running fsck on your Ubuntu partition(s).  It'll probably be different for you, but on this machine I'd run "sudo fsck /dev/sda5" from a terminal on the LiveCD.

If that doesn't show any errors with the drive and you're still stuck with it mounted read-only you can do this:
```
sudo mount -o remount,rw /
```

---

### Post by faraz_k86 on 2010-04-13
> **Drone4four said:**
> If you have a terminal or a tty up and no X server running, then  this command should write you a new xorg.conf:
```

sudo X -configure

```

i love this command appears to be useful in many of my messups.. 

why didnt it work here?

if its a permission thing.. sudo should have fixed that.. right?

---

### Post by gradinaruvasile on 2010-04-13
The OP probably had an unclean reboot and the partition mounted itself read-only. It did happen to me a few times with ext4 and jfs (never with ext3).
Solution in this case is to select recovery mode, and when at the prompt type:

```
mount
```

You will get something like this (will be different for you!! i have 3 messed up hdds):

```
$ mount
[COLOR="Red"]/dev/sda1 on / type ext3 (rw,errors=remount-ro)[/COLOR]
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
/dev/hdb1 on /media/hdb1 type fuseblk (rw,allow_other,blksize=4096)
/dev/hdb5 on /media/hdb5 type fuseblk (rw,allow_other,blksize=4096)
/dev/hdb6 on /media/hdb6 type fuseblk (rw,allow_other,blksize=4096)
/dev/hdb7 on /media/hdb7 type fuseblk (rw,allow_other,blksize=4096)
/dev/hdb8 on /media/hdb8 type fuseblk (rw,allow_other,blksize=4096)
/dev/sda5 on /media/sda5 type ext3 (rw)
/dev/sda6 on /media/sda6 type ext3 (rw)
/dev/sda7 on /media/sda7 type ext3 (rw)
/dev/sda9 on /media/sda9 type ext3 (rw)
/dev/sda10 on /media/sda10 type ext3 (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
truecrypt on /tmp/.truecrypt_aux_mnt1 type fuse.truecrypt (rw,nosuid,nodev,allow_other)
/dev/mapper/truecrypt1 on /media/truecrypt1 type vfat (rw,uid=1000,gid=1000,umask=077)
/dev/sdb1 on /media/bad-data type ext4 (rw)


```

The idea is that you must find your root partition - the partition mounted at /, i made mine (/dev/sda1) red, but yours may and probably will differ.
Also its file system type (mine is ext3, yours might be ext4). Then type ([COLOR="Red"]The red and blue text must be replaced with your partition and file system you see from the previous step!!![/COLOR]):

```
fsck.[COLOR="Red"]ext3[/COLOR] -f [COLOR="Blue"]/dev/sda1[/COLOR]
```

Where:
- the red equals your partition's file system
- the blue equals your partition mounted at /

After its finished,
Reboot - type:

```
reboot
```

Then if X dont work experimenting with the commands the others said before me.

---

### Post by atk_nut on 2010-04-13
Great!  Thanks guys, I'll give those a shot when I get home today.

Where can I get a LiveCD?  (or make one?)

Thanks.

---

### Post by Drone4four on 2010-04-13
> **atk_nut said:**
> Where can I get a LiveCD?  (or make one?)

The CD you used to install Ubuntu in the first place is called a LiveCD.

---

### Post by atk_nut on 2010-04-14
OK, I've tried all of the above suggestions and still no joy.

I can see the partition  and mount it and see the file I need to change from the livecd.  But it still comes up as read only.  Is there a way to force it to mount as read/write?

Thanks.

---

### Post by adam814 on 2010-04-14
My guess is the filesystem itself has errors (in which case it gets mounted read-only as writes could mess it up further).  Try running fsck on it from the LiveCD to see if it clears the errors.

What filesystem are you using?  Is it ext4? ext3? reiserfs?

---

### Post by atk_nut on 2010-04-14
> **adam814 said:**
> My guess is the filesystem itself has errors (in which case it gets mounted read-only as writes could mess it up further).  Try running fsck on it from the LiveCD to see if it clears the errors.

What filesystem are you using?  Is it ext4? ext3? reiserfs?

I tried running fsck from the livecd and the problem still persists.  My CD is ver 8.04 (I'm trying to make a 9.10 version now)

The filesystem is ext3

Thanks

---

### Post by atk_nut on 2010-04-14
OK, I tried the 9.10 cd - no difference.  I'm at the point now of re-installing.  I'd like to get my data out first though.  When I try to copy, I get a permission error.  Any ideas on how I can at least back up my files?   Or am I SOL?

Thanks.

---

### Post by adam814 on 2010-04-16
You should still be able to back up your files.  You just won't be able to back them up to the same partition of course.  I'd probably just use tar or rsync to move the files you need to save to an external drive.

If that fails as well you could copy the entire partition to a file somewhere using dd_rescue.

---

### Post by Didius Falco on 2010-04-16
You could try a chroot from a live CD.

1. Boot the Live CD.

2. Run the following command. In this example, it's mounting /dev/sda3, but yours will probably be different. You can get a listing of the partitions by running

```
sudo blkid 
```Once you know which dev to mount, replace the sda3 part with the correct information and run the following command:

```
sudo mount /dev/sda3 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```In Karmic Koala 9.10, you may need to run:

```
dpkg-divert --local --rename --add /sbin/initctl

```and:
```
ln -s /bin/true /sbin/initctl

```You should make sure you've mounted the correct partition by running:

```
 lsb_release -a
```This will give you root access to the drive, so you can run any commands you need to without using sudo.

After you are done, you need to exit and then unmount the partition:

```
exit
```and then:

```
sudo umount /mnt/dev/pts && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt/dev && sudo umount /mnt
```If deleting the xorg.conf file doesn't do the trick and you decide to reinstall, you can use a chroot to back up your important files.

I hope this helps!

On Edit:

Definitely try to run the fsck check. If you still get the "read-only file system" error, it could be because some fstab files are set to default to read only when their is a problem with the file system. It does this to protect your data. See this for more info:

[https://answers.launchpad.net/ubuntu/+question/23236](https://answers.launchpad.net/ubuntu/+question/23236)

Good luck!

---

### Post by atk_nut on 2010-04-16
Thanks,

I did manage to get rid of xorg.conf finally, but that wasn't my problem.  I still couldn't log in.  So I did a re-install.  I backed up my data to a usb drive.

One question, what is the best way to restore my evolution data?  I didn't do a backup/restore from evolution, I just copied the .evolution directory to my drive.  Can I simply copy it back?

Thanks.

---

### Post by nerdy_kid on 2010-04-16
> **atk_nut said:**
> Thanks,

I did manage to get rid of xorg.conf finally, but that wasn't my problem.  I still couldn't log in.  So I did a re-install.  I backed up my data to a usb drive.

One question, what is the best way to restore my evolution data?  I didn't do a backup/restore from evolution, I just copied the .evolution directory to my drive.  Can I simply copy it back?

Thanks.

yeah that should work...just dont delete the backup until you know for sure.

---

