---
title: "12 Hours Later, Conceding I Need Help - ICS"
date: 2008-03-03
forum: Networking &amp; Wireless
---

### Post by beezkneez on 2008-03-03
Let me preface this by saying I have searched here and the entire net high and low, tried and retried about 6 different "recommended" solutions, along with countless variations of my own, but I cannot for the life of me get my Ubuntu (new to Unbuntu distro, long time Linux and FreeBSD user in a servet/CLI environment, finally getting on the desktop bandwagon though with a little discouragement)

I'll cut the chase, I have a wireless usb adapter, wan1, it works fine. I am reaching you guys from it. I have a wired nic, eth0, also works fine. I am trying to share because this is a HTPC, and I don't want to buy a Xbox360 wireless addon, plus I don't know if they support the latest encryption. I am testing against a XP lappy though since I can get better diagnostics.

THis is the abbrv version for your sake and I can't remember all the things tried, but this is the core.

1) Did the Firestarter method, but using DHCP package and not DCHP3-server. Would assign a IP, but DNS wouldn't work, including static ISP DNS. This was a result of host unreachable. Something was being routed wrong? Static would not work either.

2) Tried IP tables versions, no luck static or DHCP.

3) Tried IPmasq/DNS method, no luck static or DHCP

4) Went back to Firestater. Uninstalled, reinstalled everything, this time dhcp3. The config was screwy with dhcp, finally am back to getting assigned a IP, but it is odd.

I get assigned the last available number in the range. I can ping the ubuntu box, but anything else gives me host unreachable. Say I type:
>ping 216.109.112.135 (a static Yahoo address)
the ping message is:
Reply from 192.168.0.200: Destination host unreachable
(192.168.0.200 is the IP that was assigned to my laptop from the DHCP)

Here is my current configs... any ideas?

# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:E0:4D:60:B9:5B  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4dff:fe60:b95b/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1438 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:107292 (104.7 KB)  TX bytes:10978 (10.7 KB)
          Interrupt:23 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan1     Link encap:Ethernet  HWaddr 00:15:E9:3E:F1:E5  
          inet addr:192.168.1.148  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:e9ff:fe3e:f1e5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3082 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2589 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2238509 (2.1 MB)  TX bytes:497192 (485.5 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-15-E9-3E-F1-E5-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

# more /etc/dhcp3/dhcpd.conf 


ddns-update-style none;

# option definitions common to all supported networks...
option domain-name "example.org";
option domain-name-servers 192.168.1.1;

default-lease-time 600;
max-lease-time 7200;


log-facility local7;

subnet 192.168.0.0 netmask 255.255.255.0 {
option routers 192.168.0.1;
option subnet-mask 255.255.255.0;
option domain-name-servers 192.168.1.1;
option ip-forwarding on;
range dynamic-bootp 192.168.0.180 192.168.0.200;
}

---

