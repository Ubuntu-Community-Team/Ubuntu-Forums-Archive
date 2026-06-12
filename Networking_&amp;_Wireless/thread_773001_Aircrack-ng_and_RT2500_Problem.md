---
title: "Aircrack-ng and RT2500 Problem"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by colsandurz on 2008-04-28
Hi I am trying to crack a WEP enabled server as part of a project for an electrical engineering course.

I am trying to use the aircrack-ng suite, however I am having a problem with my ralink card:

```
devin@devin-laptop:~$ sudo airmon-ng start wlan0 6


Interface	Chipset		Driver

wlan0		Ralink 2500 PCI	rt2500pci - [phy0]/usr/sbin/airmon-ng: 833: cannot create /sys/class/ieee80211/phy0/add_iface: Directory nonexistent
Error for wireless request "Set Mode" (8B06) :
    SET failed on device mon0 ; No such device.
mon0: ERROR while getting interface flags: No such device

				(monitor mode enabled on mon0)


```

```
devin@devin-laptop:~$ sudo airmon-ng check


Found 7 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID	Name
4831	NetworkManager
4845	NetworkManagerD
4878	avahi-daemon
4879	avahi-daemon
4993	dhcdbd
5721	wpa_supplicant
5749	dhclient
Process with PID 5749 (dhclient) is running on interface wlan0

```

```
devin@devin-laptop:~$ ifconfig
wlan0     Link encap:Ethernet  HWaddr 00:13:d3:75:d8:62  
          inet addr:192.168.1.123  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d3ff:fe75:d862/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4184 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2233 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2538252 (2.4 MB)  TX bytes:349931 (341.7 KB)
```
Note: I cut out my other interfaces.

I've looked around and found that some places call for new drivers, but I haven't been able to figure what driver I need to use exactly.  However, I think I just need to disaable some of those processses in the second command I've shown.  If it's that simple... how do I disable(not remove) those processes.

I would really appreciate any help.

---

### Post by colsandurz on 2008-04-28
[http://www.aircrack-ng.org/doku.php?id=rt2500](http://www.aircrack-ng.org/doku.php?id=rt2500)

I seemed to have found the problem and the solution here.... but I have different questions now.

1) How do I find out what driver I am using now?
2) How can I switch between these drivers?

Thanks again

---

