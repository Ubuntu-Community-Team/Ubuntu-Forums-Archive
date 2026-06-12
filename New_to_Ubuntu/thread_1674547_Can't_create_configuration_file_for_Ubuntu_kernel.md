---
title: "Can't create configuration file for Ubuntu kernel"
date: 2011-01-24
forum: New to Ubuntu
---

### Post by Fanatico on 2011-01-24
I need to rebuild Ubuntu kernel, unfortunately the help page for kernel build ([https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)) is outdated.

I don't understand how can I create .config configuration file from existing config flavor files.

Here is contents of my directory:

root@jack-virtual-machine:/usr/src/linux-2.6.35# ls -al ./debian.master/config/i386/
total 32
drwxr-xr-x 2 root root 4096 2011-01-18 12:58 .
drwxr-xr-x 6 root root 4096 2011-01-18 12:58 ..
-rw-r--r-- 1 root root 7071 2011-01-18 12:58 config.common.i386
-rw-r--r-- 1 root root  422 2011-01-18 12:58 config.flavour.custom
-rw-r--r-- 1 root root  423 2011-01-18 12:58 config.flavour.generic
-rw-r--r-- 1 root root  452 2011-01-18 12:58 config.flavour.generic-pae
-rw-r--r-- 1 root root  459 2011-01-18 12:58 config.flavour.virtual

The recommended by help page command "debian/rules updateconfigs" doesn't create any .config files in kernel source root directory. I also tried "debian/rules updateconfigs i386" with no success.

Please help!

---

### Post by [Snc] on 2011-01-24
> **Fanatico said:**
> I need to rebuild Ubuntu kernel, unfortunately the help page for kernel build ([https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)) is outdated.

I don't understand how can I create .config configuration file from existing config flavor files.

Here is contents of my directory:

root@jack-virtual-machine:/usr/src/linux-2.6.35# ls -al ./debian.master/config/i386/
total 32
drwxr-xr-x 2 root root 4096 2011-01-18 12:58 .
drwxr-xr-x 6 root root 4096 2011-01-18 12:58 ..
-rw-r--r-- 1 root root 7071 2011-01-18 12:58 config.common.i386
-rw-r--r-- 1 root root  422 2011-01-18 12:58 config.flavour.custom
-rw-r--r-- 1 root root  423 2011-01-18 12:58 config.flavour.generic
-rw-r--r-- 1 root root  452 2011-01-18 12:58 config.flavour.generic-pae
-rw-r--r-- 1 root root  459 2011-01-18 12:58 config.flavour.virtual

The recommended by help page command "debian/rules updateconfigs" doesn't create any .config files in kernel source root directory. I also tried "debian/rules updateconfigs i386" with no success.

Please help!

The link you provided states at the end it is compatible with karmic and newer ([https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile))

also take a look at this
[http://www.howtogeek.com/howto/ubuntu/how-to-customize-your-ubuntu-kernel/](http://www.howtogeek.com/howto/ubuntu/how-to-customize-your-ubuntu-kernel/)

And note, making custom kernels leaves you without official support :( thus asking about such topics seems rather ignored on such forums, but never the less, google saves ... google it up, its out there.

ps. sorry for the "non-support"

---

