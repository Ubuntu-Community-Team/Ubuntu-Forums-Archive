---
title: "Installing multiple Ubuntu versions using a namespace"
date: 2011-04-01
forum: New to Ubuntu
---

### Post by Blutkoete on 2011-04-01
Hello!

I was wondering whether there is a possibility to use kind of a namespace for an installation. Like having folders with *maverick_* and some folders with *natty_* or some with *maverick_ *and some with *backup_*, resulting in de facto two systems installed at the same time.

In my opinion, it should be (theoretically) possible, the two systems only sharing maybe the *boot* folder (there shouldn't be any problems with the kernel images as they don't share the same version number).

That way I won't need an extra partition for testing new versions or after doing something stupid that crashes my systems, I can just boot into the backup system.

If this is simply weird please forgive me.

Thank you,

Blutkoete

P.S.: The advantage in my opinion to simply installing two systems on two or more different partitions is that I can re-use and/or test things without problems or share folders easily that I want to share (like *home*).

---

### Post by oldfred on 2011-04-01
Do not share /boot, you might be able to share home but that is not recommended unless you are just upgrading as then the software updates to the new settings. Older versions of software may get confused with the new settings.

I have multiple installs of Ubuntu, all in 20 to 25GB partitions. I now keep /home in each and copy some settings from an older to a newer but do not attempt to share settings.

All my data is in larger partitions. I have a /data in Linux format & /shared in NTFS for sharing with my old XP install. I mount the /data in /mnt/data in fstab and link all the folders into my /home.

You can also directly mount partitions into /home or use bindfs.

kansasnoob's sharing and Morbius1 use of bindfs
[http://ubuntuforums.org/showthread.php?t=1495798](http://ubuntuforums.org/showthread.php?t=1495798)
HowTo: Create shared directory for local users (with bindfs).
[http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)
Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of data linking from above blog, based on more from comments - I now mount in /mnt and link from there.
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

---

### Post by Paqman on 2011-04-01
> **oldfred said:**
> you might be able to share home but that is not recommended

You can share a home partition, just use different account names.

---

### Post by Blutkoete on 2011-04-01
Thank you!

But I've already installed multiple systems on multiple partitions - I was wondering whether it is possible to install multiple systems on *one* partition if all those systems use the same file systems - having multiple folders:

E.g. a folder *Maverick*, with all the Maverick files (etc, sbin, bin, ...), a folder *Natty* (etc, sbin, bin, ...) and maybe a folder *Fedora* with all the Fedora files. That way I don't need to worry about which OS to give what partition size, and, if programs are compatible (like e.g. a MATLAB installation), I would only need one installation of that for all OSes.

One of them would be the master to control GRUB.

---

### Post by Paqman on 2011-04-02
> **Blutkoete said:**
> I was wondering whether it is possible to install multiple systems on *one* partition

AFAIK, no.

---

