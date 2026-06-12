---
title: "setting mount permissions for a user in fstab with NTFS Files system"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by darbid on 2009-01-11
I want to be able to mount my external USB NTFS files system to mount WITHOUT root permission.

fstab is (been trying everything here) but currently
> #Entry for /dev/sdh1 :
UUID=3004A17004A13A2C	/media/Movie1	ntfs-3g	auto,users,rw,owner,umask=000 0	0

This makes the permission like this
> wg@wg-server:~$ ls -l /dev/sdh1 /media/Movie1 $(which ntfs-3g)
-rwsr-xr-x 1 root wg   100578 2009-01-11 10:41 /bin/ntfs-3g
brw-rw---- 1 root disk 8, 113 2009-01-11 13:58 /dev/sdh1

if i try to mount this graphically (i know how to do it with terminal and sudo) but i want it to graphically work as well.  I get that i do not have permission.

I then have to manually every time change the ownership like this

```
wg@wg-server:~$ sudo chown wg:wg /dev/sdh1
```

```
wg@wg-server:~$ ls -l /dev/sdh1 /media/Movie1 $(which ntfs-3g)
-rwsr-xr-x 1 root wg   100578 2009-01-11 10:41 /bin/ntfs-3g
brw-rw---- 1 wg   wg   8, 113 2009-01-11 13:58 /dev/sdh1
```

after this I can mount and unmount graphically. But upon a restart of Ubuntu this is gone and the permission are back to root.

---

### Post by drs305 on 2009-01-11
Make yourself the owner at mounting. Since this is done during boot up with an fstab entry, change your line to something that id's you as the owner (assuming you are uid 1000):
```

#Entry for /dev/sdh1 :
UUID=3004A17004A13A2C /media/Movie1 ntfs-3g auto,[COLOR="DarkRed"]uid=1000[/COLOR],rw,umask=000 0 0 

```

You can leave the 'users' option in there if you want others to be able to mount/umount the device.

---

### Post by darbid on 2009-01-11
> **drs305 said:**
> Make yourself the owner at mounting. Since this is done during boot up with an fstab entry, change your line to something that id's you as the owner (assuming you are uid 1000)
I tried that with uid=1000 which I am pretty sure is the uid but also tried it with uid=wg.  This does not change it and I still cannot mount unless I am root.

Also if I do not use "users" in the options I cannot unmount or mount it from the desktop.

by the way does "sudo mount -a" do the same as a boot when it comes to the fstab?

---

### Post by drs305 on 2009-01-11
> **darbid said:**
> I tried that with uid=1000 which I am pretty sure is the uid but also tried it with uid=wg.  This does not change it and I still cannot mount unless I am root.

Also if I do not use "users" in the options I cannot unmount or mount it from the desktop.

by the way does "sudo mount -a" do the same as a boot when it comes to the fstab?

You can find your uid by running this in terminal: id

*sudo mount -a* attempts to mount all devices listed in fstab with fstab's settings.  *sudo umount -a* will attempt to unmount all the listings but won't be able to unmount system partitions necessary for operating ubuntu (/, /home, etc).

If it isn't mounting with you as the owner then the 'users' option would be necessary.

---

### Post by darbid on 2009-01-11
yes id show that WG=1000

so I now have this
```
#Entry for /dev/sdh1 :
UUID=3004A17004A13A2C	/media/Movie1	ntfs-3g	auto,uid=1000,users,rw,umask=000 0	0
```

From the desktop I can unmount.

from home/wg I can also unmount.

But I cannot re-mount it again unless I first manually change the permissions.

---

### Post by drs305 on 2009-01-11
Have you tried using the NTFS configuration tool? You could try commenting out the line in fstab, then installing and running ntfs-config. I would use a new mountpoint just to make sure no existing setup interferes with it. Whatever mountpoint you enter during setup will be made in /media  (e.g if you enter the name *data* the partition will be mounted in /media/data

```

sudo apt-get update
sudo apt-get install ntfs-config
sudo ntfs-config

```

---

### Post by darbid on 2009-01-11
> **drs305 said:**
> Have you tried using the NTFS configuration tool?
Thanks for making more suggestions.  I do have that already.

After talking to a friend he says the best method is to delete all the entries from fstab and let ubuntu mount it new.

And this works.  From my user I can graphically mount and unmount as i like.

As soon as I touch it with the ntfs config tool or with your disk manager which i see in your signature, my user looses permission and I cannot graphically mount and unmount.

So I have almost solved the problem.  The only problem is that these mounts must stay the same as they are shared points.  So how can i ensure they always mount with the same point each time?

---

### Post by drs305 on 2009-01-11
> **darbid said:**
> So I have almost solved the problem.  The only problem is that these mounts must stay the same as they are shared points.  So how can i ensure they always mount with the same point each time?

It's not really the mountpoint changing that is normally the problem with external devices, it is the device designation. If it is listed as /dev/sd*XX* it can change depending on the order it is mounted.

If the fstab entry is listed as a device such as */dev/sdb1*, you should change it to either a label or UUID. UUID's won't normally change unless the device is reformatted. To confirm the UUID of a device:
```

sudo blkid -c /dev/null

```

Then change the first part of the fstab entry from "/dev/sdXX" to "UUID=XXXX-XXX-XX" just like you had it in your previous post

---

### Post by darbid on 2009-01-14
i agree so I am trying to get a solution here.

One thing that is strange is that if i delete my fstab entries for a mount, then let ubuntu mount it.

From the desktop when I look at properties > volume of the mount it shows

> File System: fuseblk
Mount Options: rw nosuid nodev relatime user_id=0 group_id=0 allow_other

but if I copy this into fstab I do not have permission to mount and unmount.

So as a beginner I think there is some other problem here.

Could you please help.

---

### Post by darbid on 2009-01-21
Thanks to the many many hints from drs305 (Thanks again) I am moving along but still not there.

He gave me these instructions
> For an fstab entry, you WILL need a mount point. So:
sudo mkdir /media/TV
sudo chown -R wg:wg /media/TV
chmod 755 -R /media/TV

Add this to fstab:
#Entry for /dev/sdc7 :
UUID=9860FE2460FE0930 /media/TV ntfs auto,users,uid=1000,umask=007,utf8 0 0

Save the file, then:
sudo umount -a (disregard busy messages)
sudo mount -a 

Then this
```
sudo chown root $(which ntfs-3g)
sudo chmod 4755 $(which ntfs-3g)
```

Also he suggested this if I do not have a fstab entry for automatic mounting, but it did not work (sory drs305)
```
gconftool-2 --set --type=bool /apps/nautilus/preferences/media_automount 'true'
```

The above suggestions mean that I can click on a mount and unmount it - but only root (with a password) can mount it again.

If I try to mount it as a normal user i get
> Error opening /dev/sdc7 Permission denied Failed to mount /dev/sdc7 Permission denied Please check /dev/sdc7 and the ntfs-3g binary permissions and the mounting user ID. More explanation is provided at ...... 

I can stop this from happening by give me ownership of /dev/sd7 but this is not kept and is lost on reboot.

Could someone please help

---

