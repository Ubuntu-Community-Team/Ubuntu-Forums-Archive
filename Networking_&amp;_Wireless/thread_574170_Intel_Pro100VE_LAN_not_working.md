---
title: "Intel Pro/100VE LAN not working"
date: 2007-10-12
forum: Networking &amp; Wireless
---

### Post by mrsurf on 2007-10-12
I am trying to work out internet on my LAN using Intel Pro/100 VE LAN and I have failed.
Is SQUID necessary for internet on LAN????
Does UBUNTU 7.04 include this package in one CD installation CD????

Thanks in advance!

One more query my LAN connection does not have any DNS enteries which I tried to find out using "ipconfig" in Windows Xp and it says DNS:connection specific. What values should I enter in DNS field in UBUNTU and if left blank it won't work. My administrator says no DNS values are assigned and they are taken up automatically!  What does it mean??? :(

can any body tell me how to introduce these values??? Or make my LAN work!

---

### Post by noob12 on 2007-10-13
Can you post the output of
```

lspci -nn

sudo lshw -C network

```

---

### Post by mrsurf on 2007-10-13
```
 Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 01)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 [8086:27ca] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 [8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 01)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE [8086:27c4] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 01)
06:00.0 Network controller [0280]: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card [14e4:4311] (rev 01)
08:08.0 Ethernet controller [0200]: Intel Corporation PRO/100 VE Network Connection [8086:1092] (rev 01)
orange@orange-laptop:~$ 

```


and for sudo lshw -C network

```
-network DISABLED      
       description: Wireless interface
       product: Dell Wireless 1390 WLAN Mini-PCI Card
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@06:00.0
       logical name: eth1
       version: 01
       serial: 00:14:a5:a9:11:ff
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-16-generic latency=0 link=no multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:30000000-30003fff irq:18
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@08:08.0
       logical name: eth0
       version: 01
       serial: 00:16:d4:0b:87:a7
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
       resources: iomemory:d0100000-d0100fff ioport:2000-203f irq:21

```


It may be showing network disabled as this time I have not enabled LAN connection!


Thanks in advance

---

### Post by noob12 on 2007-10-13
This one is your wired connection and the **e100** driver seems to have claimed the device normally.  
```

  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@08:08.0
       logical name: eth0
       version: 01
       serial: 00:16:d4:0b:87:a7
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       [COLOR="Red"]configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s[/COLOR]
       resources: iomemory:d0100000-d0100fff ioport:2000-203f irq:21

```
The "**link=no**" in the configuration line here indicates that the driver thinks that there is no link detected, meaning that it thinks the cable is not plugged in or whatever it is on the other side of that cable is not live.  You should check that.

---

### Post by mrsurf on 2007-10-14
But it can ping successfully to nearby swiching unit present on same LAN!

---

### Post by noob12 on 2007-10-14
That is surprising.  

What address are you using to ping the switch and what is the address you've got assigned to your own eth0 (**ifconfig eth0**) ?

---

### Post by mrsurf on 2007-10-15
I have been assigned 10.1..7.value (in 3) and I pinged successfully 
 10.1.7.50

---

### Post by noob12 on 2007-10-15
OK.  I haven't seen that before.  Maybe the link state now reads differently.  Anyway, let's see what all got assigned and try to verify what is working.

Please post the output of these
```

ifconfig -a

route -n

cat /etc/resolv.conf

```

In the **route -n** output you should see line with UG in the Flags column. The second column in that row should be your router's address.  

Try to ping that address.

Also try to ping an external address like this google one
```

ping 74.125.19.99

```
and this open dns server
```

ping 208.67.222.222

```

Try to resolve a hostname
```

host ubuntuforums.org

```
 
Can you report back how much of this worked? and if anything failed, what you got back.

---

### Post by mrsurf on 2007-10-16
For all the above command u asked the output is command not found
Please help that what is wrong

---

### Post by mrsurf on 2007-10-16
```
The post of the command asked by you are:

Link encap:Ethernet  HWaddr 00:16:D4:0B:87:A7
          inet addr:10.1.7.250  Bcast:10.1.7.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d4ff:fe0b:87a7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:170 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:17791 (17.3 KiB)  TX bytes:4247 (4.1 KiB)

eth1      Link encap:Ethernet  HWaddr 00:14:A5:A9:11:FF
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:3

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5296 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5296 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:424648 (414.6 KiB)  TX bytes:424648 (414.6 KiB)


For another command it gives as 

orange@systemsystem:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.1.7.0        0.0.0.0         255.255.255.0   U     0      0        0 eth0



For another 

orange@systemsystem:~$ ping 10.1.7.50
PING 10.1.7.50 (10.1.7.50) 56(84) bytes of data.
64 bytes from 10.1.7.50: icmp_seq=1 ttl=30 time=6.27 ms
64 bytes from 10.1.7.50: icmp_seq=2 ttl=30 time=1.37 ms
64 bytes from 10.1.7.50: icmp_seq=3 ttl=30 time=1.47 ms
64 bytes from 10.1.7.50: icmp_seq=4 ttl=30 time=1.38 ms
64 bytes from 10.1.7.50: icmp_seq=5 ttl=30 time=1.37 ms
64 bytes from 10.1.7.50: icmp_seq=6 ttl=30 time=1.60 ms
64 bytes from 10.1.7.50: icmp_seq=7 ttl=30 time=1.37 ms
64 bytes from 10.1.7.50: icmp_seq=8 ttl=30 time=1.37 ms
64 bytes from 10.1.7.50: icmp_seq=9 ttl=30 time=1.73 ms
64 bytes from 10.1.7.50: icmp_seq=10 ttl=30 time=1.37 ms
64 bytes from 10.1.7.50: icmp_seq=11 ttl=30 time=1.37 ms

--- 10.1.7.50 ping statistics ---
11 packets transmitted, 11 received, 0% packet loss, time 9999ms
rtt min/avg/max/mdev = 1.373/1.883/6.274/1.393 ms

```

---

### Post by mrsurf on 2007-10-16
However it cannot ping to google or my main LAN switch . It gives output as host unreachable

---

### Post by mrsurf on 2007-10-16
cat /etc/resolv.conf  does not give any out put

---

### Post by noob12 on 2007-10-16
Yes.  

You are certainly missing routes.  You lack a default gateway and you may need a static route to the gateway.  Can you tell me what the "main LAN switch" ip address is?  I expect that is your gateway and I suspect that is not on your subnet so a route is required probably via the 10.1.7.50 address.

You are also missing DNS server addresses in the /etc/resolv.conf which you will need to be able to resolve hostnames to addresses.

Are you using DHCP to configure things or are you setting your address manually?

If you are setting things manually, we'll need to know these things: (1) the address and subnet mask you should be using (2) the gateway ip address (3) a local router on your subnet that leads to the "main LAN switch" gateway.  My guess is that is the 10.1.7.50 address, but it would be good if you can find out for sure. (4) one or more DNS server addresses that you should use on your net.   Post the output of **cat /etc/network/interfaces**

If you are setting things using DHCP, then please post the output of
```

cat /etc/dhcp3/dhclient.conf

```
and it may be helpful to know the address of your DHCP server, which you can probably get by looking at where the DHCPOFFER comes from in the output of **tail /var/log/syslog** after you boot.

---

### Post by mrsurf on 2007-10-17
Hi thanks for your help but it says no command found.
I will be out of station for 15 days. Hope u will be help then. See u again

---

