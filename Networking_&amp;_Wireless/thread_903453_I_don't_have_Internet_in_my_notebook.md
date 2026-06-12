---
title: "I don't have Internet in my notebook"
date: 2008-08-28
forum: Networking &amp; Wireless
---

### Post by banditos on 2008-08-28
I have also similar problem. I have a notebook with marvell yukon 88e8055 PCI-E Gigabit Ethernet Controller. I have Internet in windows and I haven't it in ubuntu. In ubuntu I haven't 'eth0':

```

michal@michal-laptop:~$ ifconfig -a
lo Link encap:Local Loopback
          inet addr:127.0.0.1 Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING MTU:16436 Metric:1
          RX packets:1910 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1910 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:96148 (93.8 KB) TX bytes:96148 (93.8 KB)

michal@michal-laptop:~$ sudo modprobe sky2
michal@michal-laptop:~$ ifconfig -a
lo Link encap:Local Loopback
          inet addr:127.0.0.1 Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING MTU:16436 Metric:1
          RX packets:1910 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1910 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:96148 (93.8 KB) TX bytes:96148 (93.8 KB)

michal@michal-laptop:~$ sudo ifconfig eth0 up
eth0: ERROR while getting interface flags: No such device
michal@michal-laptop:~$ dmesg | grep sky2
[ 40.510076] sky2 0000:06:00.0: cannot obtain PCI resources
[ 40.510104] sky2: probe of 0000:06:00.0 failed with error -16
michal@michal-laptop:~$

```

Help me please :(

I have written also there: [https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/261519](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/261519)

---

