---
title: "Only one Network connection works at a time"
date: 2008-11-19
forum: Networking &amp; Wireless
---

### Post by patryk77 on 2008-11-19
Hello,

I have finally managed to install Ubuntu on my Acer Aspire One, and am having problems with the networks.

I assume it is a routing problem.

I have a wireless router. When I used a wired connection and disconnected it, the wireless would not work until I ran "sudo ifconfig eth0 down" to disable the wired connection.

Before that, pinging the router by wireless gave me a reply saying "Destination Host Unreachable".

That is not such a big deal, but I am now trying to use Hamachi VPN and it's doing the same thing.

Here is the output from ifconfig and route:

```
ifconfig 
ath0      Link encap:Ethernet  HWaddr 00:23:4d:76:72:81  
          inet addr:192.168.1.67  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:4dff:fe76:7281/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9750 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4325 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7511000 (7.5 MB)  TX bytes:749772 (749.7 KB)

eth0      Link encap:Ethernet  HWaddr 00:1e:68:e7:dd:6b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:3736422548 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:219 Base address:0x4000 

eth0:avahi Link encap:Ethernet  HWaddr 00:1e:68:e7:dd:6b  
          inet addr:169.254.9.47  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:219 Base address:0x4000 

ham0      Link encap:Ethernet  HWaddr 62:a6:44:6f:98:f3  
          inet addr:5.98.45.68  Bcast:5.255.255.255  Mask:255.0.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1200  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:2461 (2.4 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:263 errors:0 dropped:0 overruns:0 frame:0
          TX packets:263 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17188 (17.1 KB)  TX bytes:17188 (17.1 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-23-4D-76-72-81-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:50020 errors:0 dropped:0 overruns:0 frame:27334
          TX packets:5291 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:8544248 (8.5 MB)  TX bytes:999956 (999.9 KB)
          Interrupt:18 

```

```
 route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     2      0        0 ath0
link-local      *               255.255.0.0     U     0      0        0 eth0
5.0.0.0         *               255.0.0.0       U     0      0        0 ham0
default         home            0.0.0.0         UG    0      0        0 ath0
default         *               0.0.0.0         U     1000   0        0 eth0

```

Pinging a host on the VPN (I know it's up, it works from another server)

```
ping 5.236.234.154
PING 5.236.234.154 (5.236.234.154) 56(84) bytes of data.
From 5.98.45.68 icmp_seq=2 Destination Host Unreachable
From 5.98.45.68 icmp_seq=3 Destination Host Unreachable
From 5.98.45.68 icmp_seq=4 Destination Host Unreachable
^C
--- 5.236.234.154 ping statistics ---
4 packets transmitted, 0 received, +3 errors, 100% packet loss, time 3000ms
, pipe 3

```

Thanks for the help :)

---

### Post by iponeverything on 2008-11-19
> route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     2      0        0 ath0
link-local      *               255.255.0.0     U     0      0        0 eth0
5.0.0.0         *               255.0.0.0       U     0      0        0 ham0[COLOR="Red"]
default         home            0.0.0.0         UG    0      0        0 ath0
default         *               0.0.0.0         U     1000   0        0 eth0[/COLOR]

It seem like it wants to do the right thing..

Having a Metric of 1000 on eth0 should make ath0 the preferred default gateway.  The driver for eth0 should sense the the link loss from the cable disconnection and bring down the interface -- but instead the IP address is getting removed and the interface remains in a UP state.

What do you see in /var/log/messages, /var/log/daemon.log and /var/log/syslog at the time when the eth0 is unplugged?

---

### Post by patryk77 on 2008-11-19
It was already unplugged, as I use the wireless connection.

I mostly need to get the VPN working.

Plugging it in and unplugging it gives the following:

Plugging in:
```

/var/log/messages:

ov 19 10:02:56 pcm-netbook kernel: [ 5707.478050] r8169: eth0: link up
Nov 19 10:02:56 pcm-netbook kernel: [ 5707.479657] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready


syslog:

Nov 19 10:02:56 pcm-netbook kernel: [ 5707.478050] r8169: eth0: link up
Nov 19 10:02:56 pcm-netbook NetworkManager: <info>  (eth0): carrier now ON (device state 1) 
Nov 19 10:02:56 pcm-netbook kernel: [ 5707.479657] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Nov 19 10:02:58 pcm-netbook avahi-daemon[4949]: Registering new address record for fe80::21e:68ff:fee7:dd6b on eth0.*.
Nov 19 10:03:07 pcm-netbook kernel: [ 5718.293098] eth0: no IPv6 routers present


daemon.log:

Nov 19 10:00:38 pcm-netbook dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Nov 19 10:00:41 pcm-netbook dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Nov 19 10:00:46 pcm-netbook dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Nov 19 10:00:56 pcm-netbook dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Nov 19 10:01:11 pcm-netbook dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
Nov 19 10:01:28 pcm-netbook dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Nov 19 10:01:39 pcm-netbook dhclient: No DHCPOFFERS received.
Nov 19 10:01:39 pcm-netbook dhclient: Trying recorded lease 192.168.1.66
Nov 19 10:01:39 pcm-netbook avahi-daemon[4949]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.9.47.
Nov 19 10:01:39 pcm-netbook avahi-daemon[4949]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.66.
Nov 19 10:01:39 pcm-netbook avahi-daemon[4949]: Registering new address record for 192.168.1.66 on eth0.IPv4.
Nov 19 10:01:39 pcm-netbook avahi-daemon[4949]: Withdrawing address record for 169.254.9.47 on eth0.
Nov 19 10:01:42 pcm-netbook avahi-daemon[4949]: Withdrawing address record for 192.168.1.66 on eth0.
Nov 19 10:01:42 pcm-netbook avahi-daemon[4949]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.66.
Nov 19 10:01:42 pcm-netbook avahi-daemon[4949]: Interface eth0.IPv4 no longer relevant for mDNS.
Nov 19 10:01:42 pcm-netbook dhclient: No working leases in persistent database - sleeping.
Nov 19 10:01:47 pcm-netbook avahi-daemon[4949]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.9.47.
Nov 19 10:01:47 pcm-netbook avahi-daemon[4949]: New relevant interface eth0.IPv4 for mDNS.
Nov 19 10:01:47 pcm-netbook avahi-daemon[4949]: Registering new address record for 169.254.9.47 on eth0.IPv4.
Nov 19 10:02:56 pcm-netbook kernel: [ 5707.478050] r8169: eth0: link up
Nov 19 10:02:56 pcm-netbook NetworkManager: <info>  (eth0): carrier now ON (device state 1) 
Nov 19 10:02:56 pcm-netbook kernel: [ 5707.479657] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Nov 19 10:02:58 pcm-netbook avahi-daemon[4949]: Registering new address record for fe80::21e:68ff:fee7:dd6b on eth0.*.
Nov 19 10:03:07 pcm-netbook kernel: [ 5718.293098] eth0: no IPv6 routers present

```



Unplugging it again:
```

/var/log/messages:

Nov 19 10:04:27 pcm-netbook kernel: [ 5798.061203] r8169: eth0: link down


syslog:

Nov 19 10:04:27 pcm-netbook kernel: [ 5798.061203] r8169: eth0: link down
Nov 19 10:04:27 pcm-netbook NetworkManager: <info>  (eth0): carrier now OFF (device state 1) 


daemon.log:

Nov 19 10:04:27 pcm-netbook NetworkManager: <info>  (eth0): carrier now OFF (device state 1) 
Nov 19 10:04:48 pcm-netbook dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Nov 19 10:04:55 pcm-netbook dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Nov 19 10:05:01 pcm-netbook dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Nov 19 10:05:09 pcm-netbook dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Nov 19 10:05:23 pcm-netbook dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Nov 19 10:05:34 pcm-netbook dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Nov 19 10:05:49 pcm-netbook dhclient: No DHCPOFFERS received.
Nov 19 10:05:49 pcm-netbook dhclient: Trying recorded lease 192.168.1.66
Nov 19 10:05:49 pcm-netbook avahi-daemon[4949]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.9.47.
Nov 19 10:05:49 pcm-netbook avahi-daemon[4949]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.66.
Nov 19 10:05:49 pcm-netbook avahi-daemon[4949]: Registering new address record for 192.168.1.66 on eth0.IPv4.
Nov 19 10:05:49 pcm-netbook avahi-daemon[4949]: Withdrawing address record for 169.254.9.47 on eth0.

```


DHCP seems to keep trying to get an address even while it's disconnected.

---

### Post by patryk77 on 2008-11-19
I should also add that the problem appeared in Hardy 8.04. I upgraded to 8.10, which solved a lot of my issues, but this one still persists.


Edit:

```

sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:68:e7:dd:6b
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair

```

Could it be because it uses the r8169 drivers when it should be using 8101?

I see from the forums others have trouble with these drivers.

Is there a way to change them in Intrepid? I saw only instructions for Hardy, and the need to use a patch.


Edit 2: after looking around for a while i managed to install r8101 drivers, and it didn't change a thing

---

### Post by patryk77 on 2008-11-20
Bump!

Still not resolved

---

### Post by iponeverything on 2008-11-21
Dig around in launchpad.  If you can't fine that this bug has already been reported -- open a new bug report on.

---

