---
title: "Network boot"
date: 2007-03-22
forum: Networking &amp; Wireless
---

### Post by davidcollins001 on 2007-03-22
Hi,

I hope this post is in the correct place, if not I'm sorry and would be grateful if you could direct me to somewhere more appropriate.

I have been trying to network boot a laptop that I have, it doesn't have a cd and won't boot from usb. I have managed to boot using an internet install but that took about 16 hours so I am reluctant to do that again. I would also like to learn more about using nfs.

Anyway, I am sure that I have gotten the whole dhcp, tftp, pxe thing setup correctly because I can boot the kernel and get through that process without any problems. I have installed nfs-kernel-server, nfs-common, and portmap using apt-get and setup my exports file looks like

```
/tftpboot 192.168.0.1/24(rw,no_squash_root,sync)
```

I have tried using dsl to network boot and I get the following error

```

VFS: Cannot open root device "nfs" or 00:ff
Please append a correct "root=" boot option
Kernel panic: VFS: Unable to mount root fs on 00:ff

```

I have done a lot of reasearch and I can't find the answer. I did see it mentioned a few times that the kernel needs to have nfs fixed and not modular so I made a new client kernel and that booted ok, giving me the same error as before - should the nfs support be built into the server and client or just client? The problem is that I am using ubuntu edgy live on my mac so I don't really have the option to use a different kernel on the server.

I am starting the pxeboot with the following pxelinux.cfg/default file

```

DEFAULT nfs
SERIAL 0 57600 0

LABEL nfs
KERNEL bzImage
APPEND root=/dev/nfs ip=dhcp nfsroot=/tftpboot,ro init=/sbin/init,57600

```

I don't have a /dev/nfs device so I tried to make one using

```
sudo mknod /dev/nfs c 0 255
```

but I don't know if that is correct or not?

Any help would be much appreciated, thanks!
David

---

