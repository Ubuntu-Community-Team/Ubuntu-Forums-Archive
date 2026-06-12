---
title: "wi-fi slow and unreliable"
date: 2014-12-15
forum: Networking &amp; Wireless
---

### Post by Lars Noodén on 2014-12-15
Wireless in 14.04 LTS is slow and unreliable since a few days back.  It's bad even on other access points, but here is what I get right now via wireless:

```

$ ping -c 5 192.89.123.230
PING 192.89.123.230 (192.89.123.230) 56(84) bytes of data.
64 bytes from 192.89.123.230: icmp_seq=1 ttl=248 time=4730 ms
64 bytes from 192.89.123.230: icmp_seq=2 ttl=248 time=4174 ms
64 bytes from 192.89.123.230: icmp_seq=3 ttl=248 time=3176 ms
64 bytes from 192.89.123.230: icmp_seq=4 ttl=248 time=2236 ms

--- 192.89.123.230 ping statistics ---
5 packets transmitted, 4 received, 20% packet loss, time 3999ms
rtt min/avg/max/mdev = 2236.619/3579.726/4730.772/954.639 ms, pipe 5

```

but from ethernet it is much faster:

```

$ ping -c 5 192.89.123.230
PING 192.89.123.230 (192.89.123.230) 56(84) bytes of data.
64 bytes from 192.89.123.230: icmp_seq=1 ttl=248 time=23.2 ms
64 bytes from 192.89.123.230: icmp_seq=2 ttl=248 time=23.9 ms
64 bytes from 192.89.123.230: icmp_seq=3 ttl=248 time=22.9 ms
64 bytes from 192.89.123.230: icmp_seq=4 ttl=248 time=23.0 ms
64 bytes from 192.89.123.230: icmp_seq=5 ttl=248 time=24.4 ms

--- 192.89.123.230 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4005ms
rtt min/avg/max/mdev = 22.962/23.541/24.444/0.589 ms

```

What information do I need to collect to find the problem?

---

### Post by ajgreeny on 2014-12-15
I presume 192.89.123.230 is the IP of your router?
What hardware have you got particularly, of course, the wireless adapter.

Let's see the output of **lspci**

---

### Post by Lars Noodén on 2014-12-15
The above pings are to the ISP's DNS but the slowness is there with wifi regardless of ISP.  Here is to my WLAN's router, the first set is via wireless, the second set via ethernet.

```

$ ping -c 5 10.0.2.1
PING 10.0.2.1 (10.0.2.1) 56(84) bytes of data.
64 bytes from 10.0.2.1: icmp_seq=1 ttl=255 time=1.15 ms
64 bytes from 10.0.2.1: icmp_seq=2 ttl=255 time=0.991 ms
64 bytes from 10.0.2.1: icmp_seq=3 ttl=255 time=1.01 ms
64 bytes from 10.0.2.1: icmp_seq=4 ttl=255 time=0.991 ms
64 bytes from 10.0.2.1: icmp_seq=5 ttl=255 time=0.979 ms

--- 10.0.2.1 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4004ms
rtt min/avg/max/mdev = 0.979/1.027/1.158/0.075 ms

$ ping -c 5 10.0.2.1
PING 10.0.2.1 (10.0.2.1) 56(84) bytes of data.
64 bytes from 10.0.2.1: icmp_seq=1 ttl=255 time=0.307 ms
64 bytes from 10.0.2.1: icmp_seq=2 ttl=255 time=0.334 ms
64 bytes from 10.0.2.1: icmp_seq=3 ttl=255 time=0.236 ms
64 bytes from 10.0.2.1: icmp_seq=4 ttl=255 time=0.311 ms
64 bytes from 10.0.2.1: icmp_seq=5 ttl=255 time=0.255 ms

--- 10.0.2.1 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 3998ms
rtt min/avg/max/mdev = 0.236/0.288/0.334/0.041 ms

```

Here is the lspci output.  

```

$ lspci
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5)
00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d5)
00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d5)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM86 Express LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
03:00.0 Network controller: Intel Corporation Wireless 3160 (rev 83)
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5289 (rev 01)
04:00.2 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0a)

```

It worked fine until the other day.

---

### Post by darkshadow on 2014-12-15
I see a Intel Wireless network card so I suggest trying this. It worked for my 5100
[http://bernaerts.dyndns.org/linux/74-ubuntu/322-ubuntu-trusty-intel-centrino-6235-slow](http://bernaerts.dyndns.org/linux/74-ubuntu/322-ubuntu-trusty-intel-centrino-6235-slow)

---

### Post by jeremy31 on 2014-12-15
> **darkshadow said:**
> I see a Intel Wireless network card so I suggest trying this. It worked for my 5100
[http://bernaerts.dyndns.org/linux/74-ubuntu/322-ubuntu-trusty-intel-centrino-6235-slow](http://bernaerts.dyndns.org/linux/74-ubuntu/322-ubuntu-trusty-intel-centrino-6235-slow)
I would not do exactly as that website suggest as it will overwrite the existing file, instead```
echo "options iwlwifi 11n_disable=8" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
```  You can probably forget about the second code on that page

---

### Post by Lars Noodén on 2014-12-16
> **darkshadow said:**
> I see a Intel Wireless network card so I suggest trying this. It worked for my 5100
[http://bernaerts.dyndns.org/linux/74-ubuntu/322-ubuntu-trusty-intel-centrino-6235-slow](http://bernaerts.dyndns.org/linux/74-ubuntu/322-ubuntu-trusty-intel-centrino-6235-slow)

I've tried that both with modprobe to reload and with a full reboot.  The wireless is still quite slow (79.40kB/s  right now) and drops occasionally.  Where else should I look?

---

### Post by Lars Noodén on 2014-12-26
The wireless is basically too slow and unreliable to be considered usable at this point.  What data do I need to collect and against which package should I file a bug?

```

$ lspci 
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5)
00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d5)
00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d5)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM86 Express LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
03:00.0 Network controller: Intel Corporation Wireless 3160 (rev 83)
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5289 (rev 01)
04:00.2 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0a)


$ iwconfig 
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"xxxx"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: xx:xx:xx:xx:xx:xx   
          Bit Rate=1 Mb/s   Tx-Power=22 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-39 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:6   Missed beacon:0

$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         10.0.2.1        0.0.0.0         UG    0      0        0 wlan0
10.0.2.0        *               255.255.255.0   U     9      0        0 wlan0

```

"route" takes an awful long time to return any output.

---

### Post by jeremy31 on 2014-12-26
I see that power management is on, try ```
sudo iwconfig wlan0 power off
```
What encryption is being used on the router?  WPA2-AES is the most secure that should provide the best speed

Here is where you can file a bug report if you wish [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)

---

