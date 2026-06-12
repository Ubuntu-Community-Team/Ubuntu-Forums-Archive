---
title: "Unable to get internet access using Ubuntu 8"
date: 2008-03-05
forum: Networking &amp; Wireless
---

### Post by danflasher on 2008-03-05
I just installed Ubuntu 8 on my laptop and I'm unable to get the hardwired and wireless network connections running.
Can anyone help me with this issue.
I included the outout of the (iwconfig & ifconfig -a) commands.

**_iwconfig_**

lo          no wireless extentions
eth0        no wireless extensions
wmaster0    no wireless extensions

wlan0       IEEE 802.11g ESSID: “”
            Mode: Mananged Channel:0 Access Point: Not-Associated
            Tx-Power=0 dBm
            Retry min limit=7 RTS thr:off Fragment thr=2346 B
            Link Quality:0 Signal level:0 Noise level:0
            Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid fraq:0
            Tx excessive retries:0 Invalid misc:0 Missed beacon:0


**_ifconfig –a_**

eth0        Link encap:Ethernet HWaddr 00:15:c5:0b:6a:73
            inet6 addr: fe80::215:c5ff:fe0b:6a73/64 Scope:Link
            UP BROADCAST RUNNING MULTICAST MTU:1500 metric:1
            Rx packets: 4983 errors:0 dropped:0 0 overruns:0 frame:0
            TX packets: 54 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000
            Rx bytes:390939 (381.7 KB) Tx bytes:9566 (9.3KB)
            Interrupt:16

eth0:avahi  Link encap:Ethernet HWaddr 00:15:c5:0b:6a:73
            inet addr:169.254.5.168 Bcast:169.254.255.255 Mask:255.255.0.0
            UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
            Interrupt:16

lo          Link encap: Local Loopback
            inet addr:127.0.0.1 Mask: 255.0.0.0
            inet6 addr: ::1/128 Scope: Host
            UP LOOPBACK RUNNING MTU:16436 Metric:1
            Rx packets: 44 errors: 0 dropped: 0 overruns:0 frame:0
            Tx packets: 44 errors: 0 dropped: 0 overruns:0 carrier:0
            collisions:0 txqueuelen:0
            Rxbytes:3112 (3.0 KB) Tx bytes:3112 (3.0 KB)

wlan0       Link encap: Ethernet HWaddr 00:16:ce:62:67:1f
            BROADCAST MULTICAST MTU:1500 Metric:1
            Rx packets:0 errors:0 dropped:0 overruns:0 frame:0
            Tx packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000
            Rx bytes:0 (0.0 B) Tx bytes:0 (0.0 B)

wmaster0    Link encap:UNSPEC HWaddr 00-16-CE-62-67-1F-00-00-00-00-00-00-00-00-00-00
            BROADCAST MULTICAST MTU:1500 Metric:1
	    Rx packets:0 errors:0 dropped:0 overruns:0 frame:0
	    Tx packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000
            Rx bytes:0 (0.0 B) Tx bytes:0 (0.0 B)

---

### Post by Hightide on 2008-03-05
Hi Danflasher

what kind of a wireless device do you have/  can you post output of
```

 sudo lshw -C network
```

regards

:)

---

### Post by danflasher on 2008-03-05
sudo lshw -C network

description: Ethernet Interface
product: NetXtreme BCM5751 Gigibit Ethernet PCI Express
vendor: Broadcom Corporation
physical id:0
bus info: pci@0000:02:00.0
logical name: eth0
version:01
serial: 00:15:c5:0b:6a:73
capacity: 1GB/s
width: 64bits
clock: 33MHZ

---

