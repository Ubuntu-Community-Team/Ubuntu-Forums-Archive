---
title: "change permission of new hard drive"
date: 2010-03-27
forum: New to Ubuntu
---

### Post by medphys on 2010-03-27
Hi all,

I just installed a new hard drive in my computer.  It is the second drive and created a partition sdb1 with GParted and formatted the drive as ext4.  When I mount the drive I need to give permission and it comes up as /_dev_sdb1.  When I try to create a folder it says permission denied.  

How do I change permissions on sdb1 and have it automatically mount on startup?  

I can only see it in the media folder.

thank you

---

### Post by vanadium on 2010-03-27
I think Ubuntu handles this badly by default for a desktop environment.

The best way is the "old" manner of including the drive in /etc/fstab. Then it is seamlessly mounted into your file system upon startup. In order to have write access, you need to grant permissions as needed. By default in a linux system, none has write access to directories outside of his home directory.

---

### Post by r-senior on 2010-03-27
OK, so you created a partition sdb1 and formatted it ext4. Good.

You probably want to mount it as something memorable, like /data, or whatever you plan to use it for. To make the mount permanent, you need to edit your /etc/fstab file.

[https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab")

There's a lot of information on that page, so don't be alarmed. In short, you need an entry in /etc/fstab that looks something like this:

```
# /dev/sdb1
UUID=xxxxxxxxxxxxxxxxxxxxxxx  /data  ext4  relatime,errors=remount-ro  0  1

```

You'll need to create your mount point (make sure it doesn't exist first):

$ sudo mkdir /data

The UUID (xxxxxxxxxxxxxxxxxxxxxxx) is found by running

$ sudo blkid /dev/sdb1

Be careful editing the file (using sudo of course), take a backup first if you are unsure.

Once you have checked the new entry carefully, you can mount it like this:

$ sudo mount -a

If it's already mounted, you might need to unmount it first:

$ umount /dev/sdb1

It should be automatically mounted on a reboot. 

If you want to use the mount exclusively for your user:

$ sudo chown yourusername.yourusername /data 

Then you'll be able to create files and directories, etc.

---

### Post by Paqman on 2010-03-27
Install pysdm, it's a GUI utility for managing your drives. It should be in the default install IMO. There's no need to be messing about with files like fstab manually just to set up a new drive, especially if you don't know what you're doing.

---

### Post by r-senior on 2010-03-27
Hmm. I just tried pysdm Paqman (Xubuntu 9.10) and it doesn't seem to give accurate information:

a. It lists sda1 (my /) but won't show any information for it
b. It lists and shows sdb1 (my /home) reasonably well but thinks it's SCSI when it's not.

:???:

---

### Post by Morbius1 on 2010-03-27
> When I mount the drive I need to give permission and it comes up as /_dev_sdb1. When I try to create a folder it says permission denied.Those two sentences have three components, two of which are occuring by design.

Unless you mount at boot from fstab, mounting a drive will prompt for a password because only root can mount.

When a partition formatted in a linux filetype is mounted it becomes owned by root by default. Even if it's in fstab. To fix that you need to do one of the following things regardless of the method you use to mount it. After the partition is mounted:

*Make yourself the owner :*
Open **Terminal**
Type **sudo chown morbius /media/second_drive**

[COLOR=Blue]Change **morbius** to your own user name and **/media/second_drive **to the actual path to the mount point.[/COLOR]

*Or, keep the owner as root and give everyone the ability to add or delete to the mountpoint:*
Open[B] Terminal
[/B]Type[B] sudo chmod 0777 /media/second_drive

[/B]That leaves the third problem:> it comes up as /_dev_sdb1 You got me on that one. I suggest you post the output of the following commands so we can all see what's up:

Open **Terminal**
Type **sudo blkid -c /dev/null**
Type [B]mount

[/B]*[COLOR=Blue]BTW, I personally wouldn't use pysdm on a dare or a bet - but I'm old school ;)[/COLOR]*

---

### Post by medphys on 2010-03-27
Thants to all,

Got it working.

---

