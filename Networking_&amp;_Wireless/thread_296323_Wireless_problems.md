---
title: "Wireless problems"
date: 2006-11-09
forum: Networking &amp; Wireless
---

### Post by koma99 on 2006-11-09
Hi all,
I'm new on ubuntu.
Im' trying to set up mi wireless connection.
I have a router and an usb network adapter, both Belkin.
After many hours spent trying to install the corretc drivers, I've finally succeeded to install this drivers.

Now if I try to boot the pc with the usb adapter connected, the pc crashs when it starts the network devices.
Instead, if I boot without the usb adapter,(I connect it in a second moment) ubuntu go on but when I try to run any command (iwconfig, lsusb, ifup wlan0...) the system become extremely slow, and most time I'm forced to shotdown the pc.

I' have just run the following commands:

```
$ ndiswrapper -l
Installed ndis drivers:
bcmrndis                driver present, hardware present
```


```
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

```


```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:80:AD:70:77:07
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::280:adff:fe70:7707/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23156 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22897 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:14029322 (13.3 MiB)  TX bytes:2856414 (2.7 MiB)
          Interrupt:185 Base address:0xb800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)

```


```
$ sudo ifup wlan0

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.

```

Any help ?

---

### Post by FrodoB on 2006-11-09
Start by publishing your USB wireless device's complete model and version name and FCC ID if it has one. Then someone should be able to help you.

---

