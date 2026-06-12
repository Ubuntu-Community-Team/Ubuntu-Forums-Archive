---
title: "Slow IPv6 transfer speeds"
date: 2016-07-09
forum: Networking &amp; Wireless
---

### Post by jjalling on 2016-07-09
Hi,

I have a couple of Ubuntu boxes on my network. When I use IPv4 for file transfers, I get around 200MB/s, which is ok. But when doing the same file transfer over IPv6, I only get around 1-2MB/s. Has anyone experienced something similar? And does anyone have a suggestion on what could be the problem?

Below is the the transfer via IPv4:
```

jonas@calculon:~$ scp 1Gfile.bin  jonas@192.168.1.30:/dev/null
jonas@192.168.1.30's password:
1Gfile.bin                                    100% 1024MB 204.8MB/s   00:05

```

... and IPv6 (I used a 200MB file instead of a 1G file):
```
jonas@calculon:~$ scp -6 200MB.bin jonas@\[2a00:xx::y\]:/dev/null
jonas@2a00:xx::y's password:
200MB.bin                                      10% 2336KB   1.0MB/s   00:19 ETA^C

```

Thanks,

BR Jonas

---

### Post by inunex on 2016-07-11
Hi jjalling,

The IPv6 address you are transferring your files to is not a unicast site local address (FEC0::/48) but looks to be a global route-able address. Therefore, depending on your routing this might be trying to route externally rather than on your LAN. Therefore maybe try a unicast site local address and see if you experience the same speed issue? Also you could try a trace route or the equivalent to see where this routes through as well.

Please correct me If I am wrong; IPv6 is not something I tend to deal with very often!

---

