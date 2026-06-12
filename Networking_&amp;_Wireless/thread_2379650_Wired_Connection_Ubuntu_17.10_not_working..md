---
title: "Wired Connection Ubuntu 17.10 not working."
date: 2017-12-07
forum: Networking &amp; Wireless
---

### Post by rekfulpvp on 2017-12-07
so I've had this laptop laying around for a while, I decided a while back to install ubuntu and have some stuff run on it. I installed Ubuntu 13.XX and it worked just fine. I recently decided to start all fresh and install the new 17 version and found myself with a problem. It doesnt seem to find my ethernet port, now I'm pretty new at this and I'm hoping to get some help from this lovely community.
This is what I get when I do ifconfig -a:
```


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 531270  bytes 47478813 (47.4 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 531270  bytes 47478813 (47.4 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlp3s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.122  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::7841:54e3:d956:3ba6  prefixlen 64  scopeid 0x20<link>
        ether d0:df:9a:70:20:2a  txqueuelen 1000  (Ethernet)
        RX packets 299592  bytes 124768682 (124.7 MB)
        RX errors 0  dropped 1  overruns 0  frame 0
        TX packets 222884  bytes 68659299 (68.6 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0



```

Now as I stated, I'm no expert but I'm pretty sure I'm supposed to have Eth0 thing for my ethernet port? Right? When I connect an ethernet cable to the port on the laptop it doesnt do anything at all, Ethernet worked just fine on an older version of Ubuntu.

---

### Post by ub-newbie on 2017-12-07
Is the wlp3s0 interface your Wi-Fi?

---

### Post by rekfulpvp on 2017-12-08
> **ub-newbie said:**
> Is the wlp3s0 interface your Wi-Fi?
Yes, I've solved the issue. I used the Bootable USB that I used to install Ubuntu and ran a Disk Check and that fixed 2 files that were defected and Ethernet now works fine. - Solved.

---

