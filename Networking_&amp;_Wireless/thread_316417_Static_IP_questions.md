---
title: "Static IP questions"
date: 2006-12-10
forum: Networking &amp; Wireless
---

### Post by bcw on 2006-12-10
Hi,

I have a static IP working over a wireless link to a D-link DSL-502T router (via a D-Link Access Point).  But I don't understand some things, and I really would like to.

I didn't purchase this gear - it's in a friend's house where I'm staying.  I'm the only technical person here, and I've got them all on the wireless they've chosen (see above).  I've about talked them into letting me lock down the AP with WPA.

I'm setting up to do some development work on my own systems, and I'm putting put static IPs on my machines - all the rest remains DHCP.

The D-Link box uses 10.1.1.x - I'm used to 192.168.1.x on my WRT54G.

eth0 is the (unused) cable nic, and eth1 the Intel 2200 wireless nic.

I have my first static IP set up as follows:
```
root@ganesha:/etc# cat network/interfaces
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
        address 10.1.1.220
        netmask 255.255.0.0
        gateway 10.1.1.1
        wireless-essid default

auto eth2
iface eth2 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```

I've put that ip into the D-Link router against the MAC for eth1.  This works so far.

But ifconfig and route show some things I don't understand.  Am I missing something in my setup, or do I just not understand?  Why the '169.254.102.135' stuff, and what about the netmask entry?

Thanks in advance...
```
root@ganesha:/etc# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:25:43:2C:79
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0x8000 Memory:c0220000-c0240000

eth1      Link encap:Ethernet  HWaddr 00:0E:35:95:06:70
          inet addr:169.254.102.135  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5613 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5145 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000
          RX bytes:4682026 (4.4 MiB)  TX bytes:594971 (581.0 KiB)
          Interrupt:11 Memory:c0214000-c0214fff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1210 (1.1 KiB)  TX bytes:1210 (1.1 KiB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01
          inet addr:192.168.158.1  Bcast:192.168.158.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08
          inet addr:192.168.208.1  Bcast:192.168.208.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

root@ganesha:/etc# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.208.0   *               255.255.255.0   U     0      0        0 vmnet8
192.168.158.0   *               255.255.255.0   U     0      0        0 vmnet1
10.1.0.0        *               255.255.0.0     U     0      0        0 eth1
169.254.0.0     *               255.255.0.0     U     0      0        0 eth1
default         10.1.1.1        0.0.0.0         UG    0      0        0 eth1

```

---

### Post by technodigifreak on 2006-12-10
> **bcw said:**
> Hi,

I have a static IP working over a wireless link to a D-link DSL-502T router (via a D-Link Access Point).  But I don't understand some things, and I really would like to.

I didn't purchase this gear - it's in a friend's house where I'm staying.  I'm the only technical person here, and I've got them all on the wireless they've chosen (see above).  I've about talked them into letting me lock down the AP with WPA.

I'm setting up to do some development work on my own systems, and I'm putting put static IPs on my machines - all the rest remains DHCP.

The D-Link box uses 10.1.1.x - I'm used to 192.168.1.x on my WRT54G.

eth0 is the (unused) cable nic, and eth1 the Intel 2200 wireless nic.

I have my first static IP set up as follows:
```
root@ganesha:/etc# cat network/interfaces
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
        address 10.1.1.220
        netmask 255.255.0.0
        gateway 10.1.1.1
        wireless-essid default

auto eth2
iface eth2 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```

I've put that ip into the D-Link router against the MAC for eth1.  This works so far.

But ifconfig and route show some things I don't understand.  Am I missing something in my setup, or do I just not understand?  Why the '169.254.102.135' stuff, and what about the netmask entry?

Thanks in advance...
```
root@ganesha:/etc# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:25:43:2C:79
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0x8000 Memory:c0220000-c0240000

eth1      Link encap:Ethernet  HWaddr 00:0E:35:95:06:70
          inet addr:169.254.102.135  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5613 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5145 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000
          RX bytes:4682026 (4.4 MiB)  TX bytes:594971 (581.0 KiB)
          Interrupt:11 Memory:c0214000-c0214fff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1210 (1.1 KiB)  TX bytes:1210 (1.1 KiB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01
          inet addr:192.168.158.1  Bcast:192.168.158.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08
          inet addr:192.168.208.1  Bcast:192.168.208.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

root@ganesha:/etc# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.208.0   *               255.255.255.0   U     0      0        0 vmnet8
192.168.158.0   *               255.255.255.0   U     0      0        0 vmnet1
10.1.0.0        *               255.255.0.0     U     0      0        0 eth1
169.254.0.0     *               255.255.0.0     U     0      0        0 eth1
default         10.1.1.1        0.0.0.0         UG    0      0        0 eth1

```

I'm going to ask something that may be a very stupid question.  Did you restart networking after you commited the changes?

---

### Post by bcw on 2006-12-10
Yes, I restarted networking.  That IP number is in the range of ad-hoc network addresses, so I'm doubly curious why it's there.

---

### Post by spd106 on 2006-12-11
Hi, you often get this when you have zeroconf installed. To check that you have the static IP set try **ip addr**, you should see two IP addresses for eth1.

Though it won't stop you interface working, I'm not sure how to stop this happening without removing zeroconf.

This is a bug known upstream in debian.

---

