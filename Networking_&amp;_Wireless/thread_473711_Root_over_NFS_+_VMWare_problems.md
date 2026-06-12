---
title: "Root over NFS + VMWare problems"
date: 2007-06-14
forum: Networking &amp; Wireless
---

### Post by Twigathy on 2007-06-14
Hi all,

First off, hats off to the Ubuntu devs and wonderous people that allow me to have a free OS :)

I'm trying to boot a machine over NFS, not _quite_ a diskless system in that /boot will end up on a CF card. For testing purposes, I'm doing everything in a VMWare virtual machine with my main box as the NFS server.

NFS works fine - I can mount it and all files and permissions appear correct.

Here's the relevant bit of grub's menu.lst:
```

root (hd0,5)
kernel /vmlinuz-2.6.20-15-server root=/dev/nfs ip=192.168.0.99 nfsroot=192.168.0.15:/mnt/storage/NFS
initrd /initrd.img-2.6.20-15-server

```

Kernel appears to get _somewhere_, but then falls over... (Note that it's already got past "mounting the root filesystem" which suggests NFS is either working or the kernel is silently failing...).

```

ipconfig: 192.168.0.99: SIOCGIFINDEX: No such device
ipconfig: no devices to configure
/init: .: 1: Can't open /tmp/net-eth0.conf
[   239.390268] Kernel panic - not syncing: Attempted to kill init!
[   239.390424] _

```

And here's the relevent bits of fstab:
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/nfs        /               nfs     defaults        1       1
none            /tmp            tmpfs   defaults        0       0
none            /var/run        tmpfs   defaults        0       0
none            /var/lock       tmpfs   defaults        0       0
none            /var/tmp        tmpfs   defaults        0       0

# /dev/hda6
UUID=7dcfffb2-9b85-4c7e-9e7d-f728fc6881e4 /boot           ext3    defaults        0       2

```

Not opening bits of /tmp sounds like tmpfs is b0rked in some way or another.

/etc/network/interfaces has eth0 commented out as the kernel ought to be setting the IP of the NIC itself (Due to the GRUB boot options).

If anyone has any ideas, I'd be very appreciative! :D

Thanks

Twig

---

### Post by jaripetteri on 2007-06-20
Sorry I can't help you but maybe you can help me...

I'm doing similar diskless Ubuntu machine as yours. Booting from SD-card and using rootfs over NFS. 

I have currently up and running MythTV frontend setup on SATA HDD and I would like to get rid of that noisy HDD. My MythTV Backend server could also host an rootfs for frontend. So have you get you setup up and running yet? 

I have another MythTV frontend with 2GB CF and without HDD. I basically just installed Ubuntu on CF and left SWAP out of there. Didn't make any ram drives or so just shutdown log services to save CF write counts. Still up and running after 1/2 year...

This new one I can't boot entirely from 4GB CF. I just get Error 2 on GRUB so I decided to try this cause I sound cool... =)  My SD is 512MB and it should be big enough for boot. Should I make ram drives for /TMP and maybe some other? Any advices?

---

