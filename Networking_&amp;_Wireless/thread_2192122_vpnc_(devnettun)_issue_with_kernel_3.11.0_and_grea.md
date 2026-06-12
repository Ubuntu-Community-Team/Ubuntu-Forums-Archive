---
title: "vpnc (/dev/net/tun) issue with kernel 3.11.0 and greater"
date: 2013-12-06
forum: Networking &amp; Wireless
---

### Post by errsta on 2013-12-06
**compiled kernels from source @ kernel.org **

VPNC worked fine in 3.10.9 and below. 


With 3.11.0 and now 3.12.1, I get the following error when trying to connect:


```

root@system:/home/user# vpnc ./vpn.conf 
Enter password for user@vpnserver.company.com: 
vpnc: can't open /dev/net/tun, check that it is either device char 10 200 or (with DevFS) a symlink to ../misc/net/tun (not misc/net/tun): No such device
vpnc: can't initialise tunnel interface: No such device

```


Here is the output for "ls -l /dev/net/tun'


```

crw-rw-rw- 1 root root 10, 200 Dec  4 11:15 /dev/net/tun

```


Looks fine. Device char 10, 200 as stated in the error.


With 3.10.9 (and before), I would have to ensure that the tun module was loaded ("modprobe tun") for /dev/net/tun to appear (and vpnc to work).


Since 3.11.0, /dev/net/tun just appears. No module. No tun.ko, no tun.c/tun.h in the linux source. I moved the device and rebooted, and sure enough it automagically reappeared. 


Any ideas what's changed with tun/tap since 3.11.0? More importantly: any clue on how to get vpnc to play nice with it?

---

### Post by errsta on 2013-12-06
Confirmed that as of 3.10.10, tun is no longer a kernel module.

Now to figure out how to get vpnc to play ball.

---

