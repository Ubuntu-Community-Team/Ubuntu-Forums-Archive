---
title: "Howto Forward public IPV6s pool to Docker/LXC VM's?"
date: 2014-04-30
forum: Networking &amp; Wireless
---

### Post by kevzettler on 2014-04-30
I want to use my Linode provided ipv6 pool as public addresses for Docker/Lxc containers. I've tried a few methods now with no success. Networking is not really my skillset I appreciate any help.


After a few attempts I learned that Linode uses custom kernels by default which may or may not respect some ipv6 syctl settings


 so I have since changed to a distributed kernel.
```
Linux li166-218 3.8.0-35-generic #50-Ubuntu SMP Tue Dec 3 01:24:59 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```


Docker networking works like this. Docker containers are created and managed by a Docker daemon This daemon upon start will bind itself to a bridged network interface. You can provide a preconfigured interface that Docker will use, otherwise by default it creates its own interface 'docker0' The VMs that docker then creates have their own interfaces which are configured based off the docker bridge.


My current host networking looks like the following. I added **2600:3c01:e000:83::1** from my pool to docker0


```
docker0   Link encap:Ethernet  HWaddr 56:84:7a:fe:97:99
          inet addr:172.17.42.1  Bcast:0.0.0.0  Mask:255.255.0.0
          inet6 addr: fe80::5484:7aff:fefe:9799/64 Scope:Link
          inet6 addr: 2600:3c01:e000:83::1/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:437 errors:0 dropped:0 overruns:0 frame:0
          TX packets:528 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:427625 (427.6 KB)  TX bytes:50181 (50.1 KB)


eth0      Link encap:Ethernet  HWaddr f2:3c:91:6e:25:63
          inet addr:173.230.156.218  Bcast:173.230.156.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:63829 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40706 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:203827140 (203.8 MB)  TX bytes:5330561 (5.3 MB)
          Interrupt:76


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:53 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5528 (5.5 KB)  TX bytes:5528 (5.5 KB)


lxcbr0    Link encap:Ethernet  HWaddr 3a:3c:69:7c:80:6c
          inet addr:10.0.3.1  Bcast:10.0.3.255  Mask:255.255.255.0
          inet6 addr: fe80::383c:69ff:fe7c:806c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:848 (848.0 B)


vethmbiK0d Link encap:Ethernet  HWaddr fe:be:72:ef:1b:61
          inet6 addr: fe80::fcbe:72ff:feef:1b61/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:66 errors:0 dropped:0 overruns:0 frame:0
          TX packets:86 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:9159 (9.1 KB)  TX bytes:9365 (9.3 KB)
```




I can ping both the ipv6 addresses on eth0 and docker0 from the internet


The network on the VM looks like the following. I added the ** 2600:3c01:e000:83::2** address to eth0 using lxc config


```
eth0      Link encap:Ethernet  HWaddr e6:96:c0:8f:d8:32
          inet addr:172.17.0.2  Bcast:0.0.0.0  Mask:255.255.0.0
          inet6 addr: fe80::e496:c0ff:fe8f:d832/64 Scope:Link
          inet6 addr: 2600:3c01:e000:83::2/64 Scope:Global
          UP BROADCAST RUNNING  MTU:1500  Metric:1
          RX packets:51 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:6283 (6.2 KB)  TX bytes:5623 (5.6 KB)


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```


I can ping the VM's ipv6 from the host machine. But I can't ping 2600:3c01:e000:83::2 from the internet.


At this point I need help investigating the forwarding to the VM.


I've tried to setup **radvd** on the bridge interface and enable **net.ipv6.conf.all.forwarding**. But it seems like anytime I enable **net.ipv6.conf.all.forwarding** I cant ping my public ipv6 addresses. 


i've also tried tweaking
```
net.ipv6.conf.all.use_tempaddr
net.ipv6.conf.default.use_tempaddr
```
but if I set them to anything besides 1 I again can't ping my ipv6 address


I'm wondering if i've hit some networking limitation with Linodes Xen setup.

---

