---
title: "ifconfig eth0 down isn't bringing down eth0"
date: 2008-04-02
forum: Networking &amp; Wireless
---

### Post by Levander on 2008-04-02
I'm playing around with this and just rebooted the box to try to get around anything weird I've done to the state of my network interfaces.  The problem is  'sudo ifconfig eth0 down' isn't bringing down eth0.  All it does it remove the inet and inet6 IP address lines from the output of ifconfig.  But, I can still access the internet.

```

levander@louis:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1D:7D:A2:77:6B  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:7dff:fea2:776b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:495 errors:0 dropped:0 overruns:0 frame:0
          TX packets:763 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:88545 (86.4 KB)  TX bytes:202683 (197.9 KB)
          Interrupt:16 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:449 (449.0 b)  TX bytes:449 (449.0 b)

levander@louis:~$ sudo ifconfig eth0 down
[sudo] password for levander:
levander@louis:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1D:7D:A2:77:6B  
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:606 errors:0 dropped:0 overruns:0 frame:0
          TX packets:900 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:100459 (98.1 KB)  TX bytes:266110 (259.8 KB)
          Interrupt:16 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:449 (449.0 b)  TX bytes:449 (449.0 b)

levander@louis:~$ ping earthlink.net
PING earthlink.net (209.86.93.209) 56(84) bytes of data.
64 bytes from pop08.earthlink.net (209.86.93.209): icmp_seq=1 ttl=253 time=46.2 ms
64 bytes from pop08.earthlink.net (209.86.93.209): icmp_seq=2 ttl=253 time=184 ms
64 bytes from pop08.earthlink.net (209.86.93.209): icmp_seq=3 ttl=253 time=58.3 ms
64 bytes from pop08.earthlink.net (209.86.93.209): icmp_seq=4 ttl=253 time=20.8 ms

--- earthlink.net ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2998ms
rtt min/avg/max/mdev = 20.857/77.402/184.134/63.092 ms

```

Here's /etc/network/resolv.conf.  I thought it was supposed to have an eth0 clause in here, but it's working without it:

```

auto lo
iface lo inet loopback

```

The Network dialog you can pull up from the Administration menu does have eth0 configured, but there's a '-' sign next to it instead of a check mark.  I've seen the '-' sign before in that box, but only think I know what it means when that box has a check mark or is blank.  I think check mark means enabled and blank means disabled.  See attached screen shots.  The first screen shot is the Network dialog.  The second screen shot is where I've selected eth0 in the Network dialog and clicked Properties.

---

### Post by rrwo on 2008-04-02
Do you have NetworkManager running?

Do you have ifplugd running?

Either of those will keep the device from going down entirely.

---

### Post by Levander on 2008-04-02
NetworkManager is running.  It must come standard with Ubuntu because I've never messed with anything like NetworkManager.

I have no idea what ifplugd is and it's not running according to: 'ps -ef | grep ifplugd'.

In the old days (like Feisty, or maybe it was as long ago as Edgy...) you used to just be able to do a very simple 'sudo /etc/init.d/networking stop' to shutdown all networking interfaces.

Is there a simple and consistent way to do it now?  Or, do I have to figure out first how to kill NetworkManager, and then shutdown the interfaces, making it a 2 step process now?

I'm having trouble remembering exactly why.  But it does seem like turning on and off network interfaces is something that comes up occasionally for me.  Right now it's come up because I'm playing with network briding.

---

### Post by rrwo on 2008-04-07
ifplugd will automatically bring your network up or down when it is plugged in/unplugged or a wireless on/off switch is toggled.

(Or at least that's how it's supposed to work.)

---

