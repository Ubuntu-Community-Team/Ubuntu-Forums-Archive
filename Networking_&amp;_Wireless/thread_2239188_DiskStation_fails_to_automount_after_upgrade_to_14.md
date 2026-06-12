---
title: "DiskStation fails to automount after upgrade to 14.04"
date: 2014-08-12
forum: Networking &amp; Wireless
---

### Post by livinwell on 2014-08-12
I have recently upgraded from 12.10 to 14.04. Prior to the upgrade, I had the following, in fstab, and it worked flawlessly to automount my DiskStation, on reboot:

192.168.1.50:/volume1/monarda    /media/DiskStation    nfs    rsize=8192,wsize=8192,timeo=14,intr

Since the upgrade, the DiskStation will not automount. I can mount it manually, using:

sudo mount 192.168.1.50:/volume1/monarda /media/DiskStation

So I know that the NAS is accessible. I would like to get things set up so that it can automount, on reboot, again.

I currently have the following, in fstab:

192.168.1.50:/volume1/monarda    /media/DiskStation    nfs    rw,hard,intr 0 0

No joy.

FWIW, sudo mount -a will mount the drive. Unless I'm mistaken, that means that the fstab entry is OK, but I'm fairly new at this.

---

### Post by cfaber on 2014-10-03
Hi,

I can confirm the same issue here, In my case I'm mounting with:

auto,vers=3,rsize=1048576,wsize=1048576,,retrans=10,timeo=35,soft,rw,_netdev

I've tried with and without auto, and _netdev and it seems to make no difference.  I haven't had enough time to really dig into why automount no longer works but I suspect it has something to do with the countless reports of other file systems no longer automounting on boot as well.

---

