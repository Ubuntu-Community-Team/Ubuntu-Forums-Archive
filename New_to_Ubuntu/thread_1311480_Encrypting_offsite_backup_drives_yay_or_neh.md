---
title: "Encrypting offsite backup drives: yay or neh?"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by CharlesA on 2009-11-02
Hi all,

I was getting ready to have some backups stored off-site, but I was wondering if it's smart to encrypt the drives so that if they are stolen or lost or whatever, the data will be unreadable.

I'm just not quite sure if that's possible, and if it's worth the overhead.

I'll be using an external drive using EXT3, if that makes a difference. Server is running 9.04 atm.

Any advice would be great. :)

---

### Post by bodhi.zazen on 2009-11-02
Depends on how valuable your data is, only you can decide.

If you decide to encrypt it, and you loose the password or key, your data will likely be lost, so there may be a downside.

If you wish to encrypt, you can use LUKS or truecrypt.

---

### Post by FakeOutdoorsman on 2009-11-02
Another option is to encrypt the backups instead of the whole drive.  I use the [Duplicity](http://duplicity.nongnu.org/) script to create incremental and encrypted backups to my offsite account at Rackspace Cloud Files.  Duplicity is free and in the repository.  Don't let the "beta" scare you from Duplicity as it is currently being used in many production environments.

---

### Post by CharlesA on 2009-11-02
Thanks for the replies! I'll look into those encryption programs. :-)

---

### Post by ericab on 2009-11-02
for what fakeoutdoorsman was talking about, see here;

[http://blog.chmouel.com/2009/09/02/rsync-like-backup-to-rackspace-cloud-file-with-duplicity/](http://blog.chmouel.com/2009/09/02/rsync-like-backup-to-rackspace-cloud-file-with-duplicity/)

---

