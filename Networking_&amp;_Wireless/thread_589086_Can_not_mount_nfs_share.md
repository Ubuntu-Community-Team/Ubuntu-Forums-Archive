---
title: "Can not mount nfs share"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by leupi on 2007-10-23
I had 7.04 and just reformatted and installed Ubuntu 7.10 on my laptop. I have a server running FC5 and have some directories that I share to my other computers. I find that when I try to add entries to /etc/fstab and run
```
mount -a
```
I get this:
> 
mount: wrong fs type, bad option, bad superblock on acsserver:/music,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I /etc/fstab I have this:
```
acsserver:/music        /music  nfs     defaults        0       0
```
I have an entry in /etc/hosts for the IP address of acsserver and I can ping it via the hostname so I do not imagine that that is the problem. I also tried to mount via the IP and had the same error.

I know that the issue is not with the server as my desktop is still able to mount the shares just fine, it is just this laptop on which I reinstalled Ubuntu. Any thoughts?

Thanks,
Todd

---

### Post by Lambert on 2007-10-24
Have you installed the nfs-common package?

nfs is not preintalled on ubuntu.

---

### Post by leupi on 2007-10-24
Ahh, that is probably it...

I will look at that when I get home.

Thanks,
Todd

---

### Post by leupi on 2007-10-24
Yep, that was it, it worked like a charm.

Thanks,
Todd

---

