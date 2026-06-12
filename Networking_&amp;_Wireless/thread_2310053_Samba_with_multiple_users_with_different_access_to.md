---
title: "Samba with multiple users with different access to the same share"
date: 2016-01-15
forum: Networking &amp; Wireless
---

### Post by byb3 on 2016-01-15
Hi,

I have a simple directory structure like below, say this is shared via Samba with the name "media":

Photos/
ISOs/
Videos/

I have two user accounts assigned to a single person, one called "patrick" and the other called "patrick-a".  I am using the getfacl/setfacl for user permissions and they are working as expected.

The user "patrick" has read access to all folders and files but no write access.  The user "patrick-a" has read/write access to all folders and files.

By default the shares are mounted with the "patrick" account.  However when the need comes to write then the share has to be unmounted and re-mounted with the other credentials.

Is there a quick way that I can right click a folder, with an option like "Open with user".  I am using XFCE/Xubuntu so Thunar is my typical application to use for this.  Without facing the wrath of the community here, in Windows when I tried to access a folder where an account was not permitted access a prompt was given for you to type in an account that did.  This would be the ideal scenario.

Also is this a typical workflow for anyone else?  The idea is that if anything drastic were to happen such as CryptoLocker or a virus then having only read access there would be little risk to the data.  The write access is only required rarely so should only be needed on an ad-hoc basis.

Regards,

byb3

---

### Post by blueridgedog on 2016-01-16
Just to clarify, these are remote shares and you are accessing them from your Ubuntu workstation?

If that is the case, then you could mount and unmount them as needed from the command line.

---

### Post by byb3 on 2016-01-16
Yes they're remote shares.  I think you could probably do it from a script, but the idea is that the write access is only granted temporarily and should revert back to the read access when finished.  I'm not sure how to tackle that.

---

### Post by blueridgedog on 2016-01-16
You would want one smbfs mount script to mount it as your RW user, then another to unmount it and remount it as our R user.

Such as:
```
mount_smbfs //RWUser@SERVER/folder /path/to/mount/point
```

Then the other:
```
umount /path/to/mount/point
mount_smbfs //RUser@SERVER/folder /path/to/mount/point
```

---

