---
title: "Mounting an EXT3 drive"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by Rhaddad on 2009-07-21
Hello everyone. Can someone tell me how to mount an ext3 drive?

Sorry if this seems like a very bad language.


please help me please

---

### Post by yeats on 2009-07-21
From the command line do

```
sudo mkdir /mnt/disk
sudo mount -t ext3 /dev/[sdc1] /mnt/disk
```

You have to create the directory where the disk will be mounted (mount point), then use the mount command to put it there.  To find out which /dev directory is the right drive, plug in the drive (assuming this is a USB drive?), then do

```
dmesg
```

and look at the end of the output for where a drive got plugged in (it will say something like "/dev/sdc").  In the mount command you use 'sdc1' (assuming that it is called sdc) to mount the primary partition of the drive.

Details can be found through Google or by doing 

```
man mount
```

---

### Post by yeats on 2009-07-21
By the way, if you are working in Ubuntu with a GUI, your device *should* be showing up in the "Places" menu and you should be able to just click on it to mount.

---

### Post by bosmana on 2009-08-01
Please forgive my newby question on this topic, but here it is:

I have Xubuntu installed and have added a second harddrive of 300 GB in the machine. (ext3)

It works to mount the drive, using the SUDO command that is mentioned in this thread.

However, when I shut down the computer, and restart it, then the connection is gone, and I have to do the mounting all over again.

Is there a way to permanently mount my second hard drive?

---

### Post by Happy_Man on 2009-08-01
You could set that command to run on startup.

---

### Post by Malta paul on 2009-08-01
Yes you can mount your HD at startup.
1) sudo mkdir /media/>any name<
2) sudo fdisk -l   > to find the name of your 300GB dsk>
3) sudo gedit /etc/pmount.allow  >add the name found in (2)< and save file.
4) sudo gedit /etc/fstab  >to add to fstab (5) < and save.
5) /dev/>name<     /media/>name in (1)  ext3   relatime,errors=remount-ro      0          0
6) sudo mount -a
7) reboot computer


:cool:

---

### Post by Malta paul on 2009-08-01
You will find that these link instructions are better explained than mine:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

:D

---

### Post by bosmana on 2009-08-01
Thanks !!!

Very helpful, and it works (of course)

A small step closer to understanding Xubuntu, thanks to you guys

CHEERS !

---

