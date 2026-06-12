---
title: "[SOLVED] Strange router problem"
date: 2008-02-23
forum: Networking &amp; Wireless
---

### Post by pianoman on 2008-02-23
Got an odd problem...


Background -

* I've run Gutsy on my laptop fine since the beginning of the year

* I connect to wireless networks at university and at my folks' home when I go back every few weekends

* Parents home has 2 permanent Windows PCs with no connection problems

* On my university wireless, I connect fine and and dandy


The problems begin -

* At home, dhclient collects an ip address from the router as confirmed by [ ifconfig ] and [ lshw -C network ], i have never had a problem with this.

* [ iwconfig ] shows that I _am_ connected to the network, and that the connection is "Managed"

* Despite apparently being connected, I can't access anything. Internet, router, whatever.

* I have stripped off all filtering and encryption on the router and despite connecting to it via dhcp, [ ping ] reports complete packet loss and browsing via Firefox to the router set-up utility fails.

* [ ping ] gives some other quirks - external ip addresses report complete packet loss rather than "host unreachable" errors

* I am slightly suspicious of "network manager" - i have recently started using its roaming mode for university with no noticeable change in service but I wasn't using this mode the last time I was able to connect to the home network.


Any ideas?

---

### Post by nixscripter on 2008-02-24
If your computer is convinced it has an IP, a route, a working interface, and kernel authorization to let the packets out (i.e. no firewall), then it sounds like the problem is not between your computer and the router, but between the router and the destination.

Silly question: have you indepedently verified internet connectivity by hooking up another computer to the router?

---

### Post by pianoman on 2008-02-24
Thanks for the reply

Yep, we have 2 other windows computers in the house that use the same router (also as DHCP server) that haven't even dropped a packet. From these computers, I can see the internet, I can access the router via web browser and I can talk to you now, none of which I have on the Gutsy laptop.

Some stats for clarity - ath0 is my wireless interface, NETGEAR is the router essid and it is located at 192.168.0.1.

$ ifconfig

```

ath0      Link encap:Ethernet  HWaddr 00:C0:A8:BD:CE:4B
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1300 (1.2 KB)  TX bytes:2851 (2.7 KB)

eth0      Link encap:Ethernet  HWaddr 00:14:0B:00:9B:57
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0x2000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-C0-A8-BD-CE-4B-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:303 errors:0 dropped:0 overruns:0 frame:0
          TX packets:126 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199
          RX bytes:28725 (28.0 KB)  TX bytes:8723 (8.5 KB)
          Interrupt:19

```

$ iwconfig

```

lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"NETGEAR"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:09:5B:AD:26:10
          Bit Rate:54 Mb/s   Tx-Power:16 dBm   Sensitivity=1/1
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=30/70  Signal level=-18 dBm  Noise level=-48 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

$ route -n

```

Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 ath0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 ath0
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 ath0


```

$ cat /etc/network/interfaces

```

auto lo
iface lo inet loopback





iface ath0 inet dhcp
wireless-essid NETGEAR

auto ath0

```


Any help greatly appreciated

---

### Post by nixscripter on 2008-02-24
All of the info you sent confirms that the computer is convinced it has a connection. Now for some trial and error from the other end.

1. Check the router, and make sure that the machine's IP is in the DHCP table for it, and other configuration stuff is okay.

2. Try pinging the machine from another computer.

3. Make sure that the machine doesn't have any firewall software running, and that the kernel's routing tables aren't making it drop packets. The latter can be done with: ```
sudo iptables -L
```

And just to make sure: if you ping the router from the machine, the packet drops; there is no error message, right?

---

### Post by pianoman on 2008-02-24
nixscripter - the iptables gave me the clue: my moblock daemon was stopping everything!

i had forgotten to configure it after reinstalling it. Stopping it lets me go clean through.
Curious thing though, why would it stop my more permissive home router from connecting properly but allow my university connection?

Problem solved though, thanks for your help.

---

### Post by nixscripter on 2008-02-24
Perhaps the ban list included (perhaps by wildcard) all of the addresses on the local network. If it was set up to avoid strange traffic, it might not have recognized the private network IP range.

I don't know either, but that's just an idea. I'm glad you solved the problem.

---

