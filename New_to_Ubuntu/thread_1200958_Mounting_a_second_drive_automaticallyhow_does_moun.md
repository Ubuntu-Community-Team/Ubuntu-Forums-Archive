---
title: "Mounting a second drive automatically/how does mount work under &quot;places&quot;?"
date: 2009-06-30
forum: New to Ubuntu
---

### Post by protargol on 2009-06-30
So I'm trying to have a second partition mount automatically upon bootup.  Right now, I manually have to go to "Places" and then click on the drive for it to mount to it's location (/media/disk).  My question is what is/are the commands that are run when I click on the unmounted drive under places?

/media/disk does not exist until I mount the drive this way, and so I'm not able to put ```
/dev/sde5       /media/disk     ext3    0 2
``` into my fstab file.  Also, after I mount the disk using places, the timestamp for the last edit of /media/disk is in the past, so I don't think that it's being created (as in mkdir disk) everytime.  Any tips?

---

### Post by nandemonai on 2009-06-30
> **protargol said:**
> So I'm trying to have a second partition mount automatically upon bootup.  Right now, I manually have to go to "Places" and then click on the drive for it to mount to it's location (/media/disk).  My question is what is/are the commands that are run when I click on the unmounted drive under places?

/media/disk does not exist until I mount the drive this way, and so I'm not able to put ```
/dev/sde5       /media/disk     ext3    0 2
``` into my fstab file.  Also, after I mount the disk using places, the timestamp for the last edit of /media/disk is in the past, so I don't think that it's being created (as in mkdir disk) everytime.  Any tips?

You could manually create the mount point if that's where you want it, then add the /etc/fstab entry?

```
sudo mkdir /media/disk
```

---

### Post by Revolutionary101 on 2009-06-30
This link might help [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

