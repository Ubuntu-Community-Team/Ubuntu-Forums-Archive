---
title: "External Hard Drive mount problem"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by Geo_V on 2009-02-14
Hello everyone again, wonder if anyone could help here..

Ok, i have this external usb 250GB harf drive connected to my laptop. When i press the power button, the drive is recognized by the system but can't be mounted. I get the message 

*"Cannot mount volume.You are not privileged to mount the volume BackUp'."* 

and then another message appears :

[I]Unable to mount BackUp
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.[/I]

If i power the drive before i log in linux it is mounted without any problem, and there where some times, i don't know for what reason, when i powered it after booting into linux and it was mounted without any error.

Thanks in advance for the help..

---

### Post by x33a on 2009-02-14
try to mount it with sudo.

---

### Post by drs305 on 2009-02-14
We need a bit more information. The mounting error after power on is the result of improper permissions. If we know the type of formatting and the device designation we can set up fstab to either automount, or manually mount even if you turn it on later.

If the drive is currently mounted, please post:
```

mount | grep "/dev/" # shows us where the drive is mounted and type of formatting
cat /etc/fstab  # shows us your fstab contents
sudo blkid -c /dev/null  # gives us the UUID of the partitions

```

---

### Post by Geo_V on 2009-02-14
Here are the results of fstab: 

proc /proc proc defaults 0 0
# Entry for /dev/sda5 :
UUID=08222796-bd14-436e-9440-1ecf7ece5105 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda6 :
UUID=85450a56-5e5a-410c-9e56-43206fd48ea9 none swap sw 0 0
/extraswap none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda5 /media/sda5 ext3 defaults 0 0
/dev/sda1 /media/sda1 ntfs defaults 0 0
/dev/sda6 /media/sda6 swap defaults 0 0
/dev/sdb5 /media/sdb5 ntfs defaults 0 0

And here are the results of sudo blkid -c /dev/null

/dev/sda1: UUID="7E809D5B809D1AAB" TYPE="ntfs" 
/dev/sda5: UUID="08222796-bd14-436e-9440-1ecf7ece5105" TYPE="ext3" 
/dev/sda6: UUID="85450a56-5e5a-410c-9e56-43206fd48ea9" TYPE="swap" 
/dev/sdb5: UUID="0A789D68789D5375" LABEL="BackUp" TYPE="ntfs"

---

### Post by drs305 on 2009-02-14
The following assumes sdb5 is the partition you are having difficulties with. Your external appears to be *sdb* and is partitioned to NTFS.

I would recommend you change your fstab a bit. It assumes you are user 1000 (you can check with the "id" command in terminal, uid=XXXX). 

Backup fstab and open for editing (use your favorite text editor if not gedit):
```

sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab

```

Replace this line: 
> /dev/sdb5 /media/sdb5 ntfs defaults 0 0
With this, then save the file:
```
LABEL=BackUp  /media/sdb5 ntfs auto,users,uid=1000,umask=027,utf8 0 0 
```
If you would prefer the UUID instead of the label, change it to:
```
UUID=0A789D68789D5375  /media/sdb5 ntfs auto,users,uid=1000,umask=027,utf8 0 0 
```

*auto* lets it automount during boot, *users* lets any user mount it after boot, *uid=1000* makes user 1000 the owner (otherwise whoever mounts an NTFS partition owns it), and umask sets the permissions.

Test the new fstab setting:
```

sudo umount /dev/sdb5
mount /dev/sdb5

```
If you see nothing in terminal after running the second command it mounted properly. If you get errors, let us know what they are.

---

### Post by Geo_V on 2009-02-14
I did everything drs305 suggested and when i power my drive it still cannot be mounted. The terminal message is :

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb5': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb5 /media/sdb5 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb5 /media/sdb5 ntfs-3g force 0 0

---

### Post by drs305 on 2009-02-14
Now that you are getting that message you need to follow it's instructions. The drive is showing it wasn't cleanly unmounted.

The best option is to reboot into windows, mount the drive and then shut down normally.

If you can't do that, then install ntfsprogs and run ntfsfix to reset the flags:
```

sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sdb5

```

If that doesn't correct things:
```
sudo mount /dev/sdb5 -t ntfs /media/sdb5 -o force
```

You should only have to do this once to correct the problem. Future errors can be avoided if you make sure to shut down normally or unmount the device before unplugging it.

---

### Post by Geo_V on 2009-02-14
Thanks drs305, the ntfsprogrs method worked. I managed to mount the volume just 1 minute ago. However on "power on", the same message appeared again saying the volume can't be mounted. The only way to mount it was using the sudo mount... through the terminal. Is it impossible that it is mounted without having to type any lines in terminal, as it is in windows?

Thanks again.

---

### Post by drs305 on 2009-02-14
Is it the dbus error message you are getting? With SCSI drives there are sometimes problems because some of the drives don't spin up quickly. For the system drive it is solved by adding a bootdelay to grub. Unfortunately I don't know of a way to do this with fstab.

I've searched around and found similar problems but no solutions which would automount the drive when the power is turned on (after boot). The only recommendation I can make is to change "auto" to "noauto" in fstab. That would prevent the drive from trying to mount as soon as it was recognized. Perhaps after a few moments it will mount without error, but you will have to manually initiate the mounting.

If the error isn't the dbus message, please paste it.

Hopefully someone will post here with a better solution.

---

### Post by Geo_V on 2009-02-14
Im sorry, i can't understand what is a "dbus" error..

My external drive however is not scsi, it's sata. What happens is that when i power the drive, the normal message window of linux pops up saying "Can't mount volume etc.." but when i mount it manually using the terminal, it is mounted successfully. It's just that being a computer maniac, you like to have things working the perfect way you know..

---

### Post by drs305 on 2009-02-14
If you aren't getting the dbus message we can ignore that for the moment.

Ok, when you have the drive mounted, run the following and post:
```
mount
```
Also post what command you (successfully) use to mount the device. It will show us where it has been mounted and will probably give us a clue as to why it won't mount with fstab/automatically.

Some things to check:
Does /media/sdb5 exist?
Is that where it mounts when you mount it manually.

---

### Post by Geo_V on 2009-02-14
Ok, the output of the 'mount' command with the external drive already mounted is :

/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
/dev/sda5 on /media/sda5 type ext3 (rw)
/dev/sda1 on /media/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/x-pc2/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=x-pc2)
/dev/sdb5 on /media/sdb5 type fuseblk (rw,noexec,nosuid,nodev,allow_other,default_permissions,blksize=4096)

Also, the command which i use to successfully manually mount the external drive is : mount /dev/sdb5

And finally, yes, the directory /media/sdb5 exists..

---

### Post by Geo_V on 2009-02-14
Well, it seems that im actually getting a dbus message as drs305 mentioned before. There are two pop up windows when the drive is powered which say the following:

1. Cannot mount Volume. Unable to mount the Volume 'Backup'.
Details.
Unpriviliged user cannot mount NTFS block devices using the external FUSE library. Either mount the volume as root, or rebuilt NTFS-3G with integrated FUSE support and make it setuip root. Please see more information at [http://ntfs-3g.org/support.html#unprivileged](http://ntfs-3g.org/support.html#unprivileged)

2. Unable to mount Backup
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not receive a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

Hope this enlightens the situation...

---

