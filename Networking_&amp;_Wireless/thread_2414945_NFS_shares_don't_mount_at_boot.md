---
title: "NFS shares don't mount at boot"
date: 2019-03-17
forum: Networking &amp; Wireless
---

### Post by BobvanderPoel on 2019-03-17
I have a couple of nfs mounts activating in my /etc/fstab. This has been working flawlessly  ... like forever. But I just discovered that it's not. Did a bunch of time-wasting sleuthing, and installed 18.10 hoping that might change things. Nope. I've done what debugging that I can, but don't see any errors.

In /etc/fstab I have

```

 mellowood:/ftp /ftp                       nfs rsize=8192,wsize=8192,timeo=14,auto,user 0 0

```

But, no luck with that. 

However, using "mount -a nfs" in a command line prompt after booting works perfectly. I have changed the timeo value to 3000 and just deleted the option. No change.

```

$ journalctl | grep nfs
Mar 14 20:01:04 mellownet kernel: Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
Mar 14 20:01:06 mellownet kernel: NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Mar 14 20:01:11 mellownet systemd[1]: Mounting /media/nfs-usb...
Mar 14 20:01:11 mellownet kernel: FS-Cache: Netfs 'nfs' registered for caching
Mar 14 20:01:11 mellownet mount[948]: mount.nfs: Network is unreachable
Mar 14 20:01:11 mellownet systemd[1]: media-nfs\x2dusb.mount: Mount process exited, code=exited status=32
Mar 14 20:01:11 mellownet systemd[1]: Failed to mount /media/nfs-usb.
Mar 14 20:01:11 mellownet systemd[1]: media-nfs\x2dusb.mount: Unit entered failed state.
Mar 14 20:01:11 mellownet mount[947]: mount.nfs: Network is unreachable
Mar 14 20:03:18 mellownet sudo[2003]:      bob : TTY=pts/0 ; PWD=/home/bob ; USER=root ; COMMAND=/bin/mount -a nfs

```

Tells me that the network can't be reached ... that's silly since it's a Ethernet cable between computers. Besides, if I do:

```

 mount -a nfs

```

A few seconds after booting it works just fine.

Suggestions?

---

### Post by TheFu on 2019-03-18
I would check for name resolution issues.  Can the client ping the server using the name above?  Have you tried the IP address?  What does showmount -e show?

The errors show NFSv4.  That is a very different protocol than NFSv3.  You can force ver=3 in the mount options to keep the older protocol.  Or you can learn to setup kerberos to make v4 NFS work.

---

### Post by BobvanderPoel on 2019-03-18
> **TheFu said:**
> I would check for name resolution issues.  Can the client ping the server using the name above?  Have you tried the IP address?  What does showmount -e show?


Yes, tried mounting directly to the address instead of the name. Nope. Client can ping server ... but that's after boot, not at the point where mount is happening (or in this case, not happening). But, pinging mellowood works fine.

> 
The errors show NFSv4.  That is a very different protocol than NFSv3.  You can force ver=3 in the mount options to keep the older protocol.  Or you can learn to setup kerberos to make v4 NFS work.

Actually it's vern=3 (just for future reference). But that made no difference. I also tried using the 'bg' option. Again, no difference. No idea why kerberos would make a difference?

About the only other thing I can think of is to try with a different ethernet cable. I think I have one which might reach ... I really don't want to start moving things around! 

The annoying part of all this is that it worked just fine until late Jan. of this year.

Other things I might try?

---

### Post by BobvanderPoel on 2019-03-18
So ... pulled the plug from the network switch and plugged it into the router beside it. And ... miracle ... it worked. This is leading me to think that the guy who made up the original cable for me might not have been the best :) Oh, and no, that wasn't me.

I will install new plugs on both ends of the cable later today and see what happens. The cable runs though the attic and isn't all that easy to get to, so I want to avoid that route.

Thanks ... will post results.

---

