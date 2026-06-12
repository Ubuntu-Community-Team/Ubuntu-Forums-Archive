---
title: "They back ported the driver for the marvell yukon"
date: 2006-12-10
forum: Networking &amp; Wireless
---

### Post by Levander on 2006-12-10
The last comment in this bug report says they "back ported" the driver for the marvell yukon cards in the last couple of weeks:

[https://bugs.launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/68338](https://bugs.launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/68338)

How am I supposed to get my hands on this "back port"?

---

### Post by ciscosurfer on 2006-12-10
Enable your backports repo.  For example:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

---

### Post by Levander on 2006-12-11
Would this driver be in the latest kernel package in backports?  If not, which package would it be in.

I guess I need to read more about my /etc/apt/sources.list file, but I've always been hesitant to enable backports, because I want to stick to the mainstream repositories as much as possible.  Is it possible to configure sources.list to only take specified packages from backports?  Like, I don't want backports upgrading my Firefox installation.  I only want it to upgrade the packages I specify.

---

### Post by ciscosurfer on 2006-12-11
> **Levander said:**
> Would this driver be in the latest kernel package in backports?  If not, which package would it be in.

I guess I need to read more about my /etc/apt/sources.list file, but I've always been hesitant to enable backports, because I want to stick to the mainstream repositories as much as possible.  Is it possible to configure sources.list to only take specified packages from backports?  Like, I don't want backports upgrading my Firefox installation.  I only want it to upgrade the packages I specify.An easy way to handle this is to manually update your packages (by name).  So, let's say we know the name of a package that's been backported, we can specify said package in an install line:```
sudo aptitude install super-duper-backported-package
```You can then comment out (disable) the backports line in your /etc/apt/sources.list file, that way you do regular upgrade and dist-upgrade (or let the update manager handle it for you) without hassle.  Hope that somewhat clears up your concerns! ;)

ciscosurfer

---

### Post by Levander on 2006-12-11
Thanks ciscosurser.  I just found another way to specify which packages come from which repositories, called Pinning:

[https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto)

Now, I'm really wondering what package this backported network driver is in?  Is it just in the kernel package?

---

### Post by ciscosurfer on 2006-12-11
> **Levander said:**
> Thanks ciscosurser.  I just found another way to specify which packages come from which repositories, called Pinning:

[https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto)

Now, I'm really wondering what package this backported network driver is in?  Is it just in the kernel package?Seems they have backported the new sky2 driver to ubuntu-edgy-updates.git

So I'm guessing this means if you uprade your box, you should get the new driver (meaning, I don't believe the new driver is actually in the backports repo, I think it's in the edgy-updates repo).

---

