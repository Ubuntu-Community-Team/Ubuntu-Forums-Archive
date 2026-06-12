---
title: "unregister device problem: hard reset"
date: 2006-08-26
forum: Networking &amp; Wireless
---

### Post by mailmaldi on 2006-08-26
```
root@sprint-haven:/home/milind# uname -r
2.6.15-26-386

```
is the kernel i am using.

i use rp-pppoe to connect to my isp for internet access...

everything was working fine till i got up in the morning & switched on the monitor to see this following message on my already open terminals

```
unregister_netdevice: waiting for ppp0 to become free. Usage count = 1
```

i could not start any more terminals or any other system application & i tried to reboot by switching to console & pressing ctrl + alt + del.

but i got the same message in an infinite loop & finally had to hard reset.

i used to get the same messages when i used to try and reboot without bringing down the active connections

---

