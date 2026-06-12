---
title: "Blitzz BWU613B BWU613SB won't install, looking for /etc/pcmcia/wireless.opts"
date: 2007-11-16
forum: Networking &amp; Wireless
---

### Post by OnCloudFive on 2007-11-16
So, I'm trying to install a Blitzz BWU613SB (I'm assuming, the BWU613B is on the same disc), and I did what I thought was right, that being I went and decompressed the .tar.gz file from the Linux/ folder on the CD and then I did the whole make config, make clean, all, install thing.  It gives me some fun output.  I'm sure you'd like to see it.  Here it is:

root@compy:/atmelwlandriver# make config
Build all [y/N] : y
[: 17: ==: unexpected operator
Set extra module version information [y/N] : y
[: 112: ==: unexpected operator
X Windows include files missing
Kernel Version Running 2.6.22-14-generic
Found Kernel Source Directory (/lib/modules/2.6.22-14-generic/build)
[: 149: ==: unexpected operator
Finished. Now run make clean, all, install
root@compy:/atmelwlandriver# make clean
find . -name '*.o' -o -name '*.map' |xargs rm -f
root@compy:/atmelwlandriver# make all
Building
root@compy:/atmelwlandriver# make install
set -x
grep: /etc/pcmcia/wireless.opts: No such file or directory
depmod -aq
OK

Needless to say, the thing isn't actually installed, and I've no clue why it's looking in /etc/pcmcia when the thing's a USB device.  Mreh.  I read the Readme and it made zero sense to my little newbie brains.

I now beg before the doors of the Sanctuary of Linux Gurus and implore your assistance in resolving this matter.

My utmost unworthy thanks,
Ben

---

