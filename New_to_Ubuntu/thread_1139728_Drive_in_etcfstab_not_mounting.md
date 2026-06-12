---
title: "Drive in /etc/fstab not mounting"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by aridus on 2009-04-27
Could anybody kindly help me with this curious problem? I have two external usb drives specified in /etc/fstab my Kubuntu 9.04 system, viz:

# External ext3 250 GB USB drive mounted as ext3backup
UUID=0e6fb1ec-8847-4214-8834-1de48a9fb37a /media/ext3backup ext3 user 1 0
# External ext3 120 GB USB drive mounted as ext3backup2
UUID=485f3260-d7be-4765-ae0d-43c5d9226546 /media/ext3backup2 ext3 user 1 0

I have been using this for c. 1 year, and the drives mounted automatically at boot (and through several versions of Ubuntu and/or Kubuntu). However, the drives are no longer automatically mounted (the UUIDs are still correct, I have checked), but I can mount them using partitionmanager. I am not entirely sure whether this broke when I moved to Kubuntu 9.04 (a fresh install) or shortly before.

Could anyone help solve this mystery (mounting manually is a chore, and if I forget to do it by backup system to these disks can't run)?

With thanks!

---

### Post by kpkeerthi on 2009-04-27
Can you run this command and post back the errors it prints?
```
sudo mount -a
```

---

### Post by aridus on 2009-04-27
Ran sudo mount -a before drives are mounted, and there is no output.

---

### Post by MrWES on 2009-04-27
> **aridus said:**
> Ran sudo mount -a before drives are mounted, and there is no output.


Did you cd into the mount point to see if they were mounted after that?

Bill

---

### Post by aridus on 2009-04-27
Sorry, should have said: yes, after running sudo mount -a the drives are mounted and I can access the files.

---

### Post by pokogr on 2009-04-27
I might be wrong but shouldn't "auto" be added as an option to each line in order to have the drives automounted on each boot?

---

### Post by rajeev1204 on 2009-04-27
My /etc/fstab file for reference.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=645d5f36-fbc1-4830-908e-191a1ea3db0a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=3dcd7971-2645-44fc-8806-cbc50e9e2c23 /home           ext3    relatime        0       2
# /dev/sda7
UUID=cca56f8c-1548-4fcf-8e1a-a31138174d2a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

/dev/sda1     /media/windows  vfat iocharset=utf8,umask=000 0 0

Also, this is a good read  [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by me.translucent on 2009-04-27
everthing in the fstab is automatically mounted at  the boot  time .

---

### Post by rajeev1204 on 2009-04-27
Damn my cdrom is not being picked up.

---

### Post by kpkeerthi on 2009-04-27
> **me.translucent said:**
> everthing in the fstab is automatically mounted at  the boot  time .

not when 'noauto' is present :)

---

### Post by kansasnoob on 2009-04-27
Not sure if this is helpful or not, but in Ubuntu I always install pmount from synaptic which makes mounting usb drives a snap!

---

### Post by kpkeerthi on 2009-04-27
> **kansasnoob said:**
> Not sure if this is helpful or not, but in Ubuntu I always install pmount from synaptic which makes mounting usb drives a snap!

Can pmount be used with fstab or mount devices at boot? The OP needs some partitions mounted on boot.

---

### Post by aridus on 2009-04-27
Herewith a slight modification of fstab, with auto on one usb drive and not on the other:

# External ext3 250 GB USB drive mounted as ext3backup
UUID=0e6fb1ec-8847-4214-8834-1de48a9fb37a /media/ext3backup ext3 user,auto 0 0
# External ext3 120 GB USB drive mounted as ext3backup2
UUID=485f3260-d7be-4765-ae0d-43c5d9226546 /media/ext3backup2 ext3 user 0 0

However, as I expected (as auto is the default) neither mounts at boot. Using sudo mount -a after boot does, however, mount them both.

Thus, it is still a mystery....

---

### Post by rajeev1204 on 2009-04-27
> **aridus said:**
> Herewith a slight modification of fstab, with auto on one usb drive and not on the other:

# External ext3 250 GB USB drive mounted as ext3backup
UUID=0e6fb1ec-8847-4214-8834-1de48a9fb37a /media/ext3backup ext3 user,auto 0 0
# External ext3 120 GB USB drive mounted as ext3backup2
UUID=485f3260-d7be-4765-ae0d-43c5d9226546 /media/ext3backup2 ext3 user 0 0

However, as I expected (as auto is the default) neither mounts at boot. Using sudo mount -a after boot does, however, mount them both.

Thus, it is still a mystery....


Try this ```
UUID=485f3260-d7be-4765-ae0d-43c5d9226546 /media/ext3backup2 ext3 defaults 0 0
```

---

### Post by me.translucent on 2009-04-27
i was just curiuos what is this uuid thing ?

---

### Post by rajeev1204 on 2009-04-27
Guaranteed solution :)

sudo sh -c "echo usb_storage >> /etc/modules"

or add usb_storage manually to /etc/modules

Reboot and all will be fine.

Thanks to this thread [http://ubuntuforums.org/showthread.php?t=1128849](http://ubuntuforums.org/showthread.php?t=1128849)

---

### Post by aridus on 2009-04-27
Many thanks, but if only! I read the thread, and it makes sense that this could be the problem. However, usb_storage is now in /etc/modules, but after a reboot sudo mount -a is still required to mount the drives.

---

### Post by aridus on 2009-04-27
> **me.translucent said:**
> i was just curiuos what is this uuid thing ?

A Universally Unique Identifier (UUID) is an identifier standard used in software construction, standardized by the Open Software Foundation (OSF) a... ([http://en.wikipedia.org/wiki/UUID](http://en.wikipedia.org/wiki/UUID)), which I found by reading [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab), which is useful but doesn't help mount my usb drives automatically....

---

### Post by me.translucent on 2009-04-28
thnx dude .. i think that can fix my problem with permissions in mounted ntfs volume :(

---

### Post by aridus on 2009-04-28
Excellent.. but does anybody yet have a solution to ensure that usb drives in /etc/fstab mount? Thanks!

---

