---
title: "problems with dpkg in update manager"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by jdshelby on 2010-04-29
Hi All,

This morning I tried to run my update manager as per usual, and while it downloaded the files correctly, when I tried to install them, it gave me this output:

-----------
Extracting templates from packages: 100%
Preconfiguring packages....
(reading database 10%dpkg unrecoverable fatal error, aborting:
failed in buffer_read(fd): files list for package 'amsn-data': input / output error
E: subprocess usr/bin/dpkg returned an error code(2)
A package failed to install. Trying to recover.
-----------------

I'm gonna try and uninstall amsn, and see if that has any effect, but I'd appreciate some insight as to what gives, and what all this means.

Thanks a bunch!
J.

---

### Post by cuberts on 2010-04-29
> **jdshelby said:**
> Hi All,

This morning I tried to run my update manager as per usual, and while it downloaded the files correctly, when I tried to install them, it gave me this output:

-----------
Extracting templates from packages: 100%
Preconfiguring packages....
(reading database 10%dpkg unrecoverable fatal error, aborting:
failed in buffer_read(fd): files list for package 'amsn-data': input / output error
E: subprocess usr/bin/dpkg returned an error code(2)
A package failed to install. Trying to recover.
-----------------

I'm gonna try and uninstall amsn, and see if that has any effect, but I'd appreciate some insight as to what gives, and what all this means.

Thanks a bunch!
J.well try to reinstall that stuff, and tell me if it responds the same way

---

### Post by jdshelby on 2010-05-01
I tried uninstalling AMSN, both from Terminal and from synaptic, but as soon as it tries to use dpkg, it throws the same error.  I can do nothing that has anything to do with dpkg.

Is there any way that I can manually delete amsn and all of its files?

J.

---

### Post by -humanaut- on 2010-05-01
try dpkg --reconfigure -a hopefully that will unlock apt/dpkg atleast

---

### Post by seeker5528 on 2010-05-01
Input/Output errors always make me suspicious that there is something wrong with the hard drive either physically or with the partition or file system.

Usually you can get utilities to test the hard drive from the website of the company the manufactured the drive.  After checking with that, then boot from the Ubunutu installation disk and run fsck.

```
sudo umount /dev/whatever
sudo fsck /dev/whatever
```

As always, you should back up anything that is important to you before doing these things.

Later, Seeker

---

### Post by jdshelby on 2010-05-02
Thanks for your help guys.  I decided that it was probably just easier to copy my files over to a hard drive, format, and begin again with 10.04.  So far, so good.

Thanks -- still wonder what the hell it was though.
J.

---

