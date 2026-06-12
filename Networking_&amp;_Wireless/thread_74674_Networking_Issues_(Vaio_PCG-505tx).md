---
title: "Networking Issues (Vaio PCG-505tx)"
date: 2005-10-12
forum: Networking &amp; Wireless
---

### Post by spike666 on 2005-10-12
Hey, I recently got Ubuntu (5.10) installed on this vaio laptop (PCG-505tx) that I found in the garbage. I did a lot of testing when I first got it and made sure everything worked. the PCMCIA slot works fine. I got my ethernet card working in windows without any problems, and everything seems to be working fine.

Installation went without a hitch, and after some manual editing of my xorg.conf file, I got the resolution configured properly.

now my only problem is that I can't get the networking to work.

I've got a 3com 3ccfem556 PCMCIA 10/100/modem combo card. Ubuntu detects it and loads the necessary modules if it's plugged in while booting and it shows up in the Networking administration setup. I activated it and set it up to use DHCP to connect.

At first, I thought the thing was using IPv6 to connect (because I only had an IPv6 address in ifconfig on eth0), which I don't need/use. so I followed the instructions in another post to disable it in the /etc/modules/aliases file.

now...

from the terminal:
```
spike@yellowcalx:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:00:86:19:63:5F  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:734 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:197012 (192.3 KiB)
          Interrupt:3 Base address:0x300 

lo        Link encap:Local Loopback  
          LOOPBACK  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

I've got no address for the ethernet.

the light on the ethernet card and switch are both on. so it's connected, which is verified by:
```
spike@yellowcalx:~$ mii-tool
eth0: negotiated 100baseTx-FD, link ok
```

when I unplug the wire and run mii-tool again, it says no connection. so I know that's not the problem. I also tried 2 other different wires.

so I try to ping my router (a linksys BEFSR11):
```
spike@yellowcalx:~$ ping -c 3 192.168.1.1
connect: Network is unreachable
```

so then, I attempted to manually set ifconfig:
```
root@yellowcalx:/home/spike# ifconfig eth0 inet 192.168.1.120
root@yellowcalx:/home/spike# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:00:86:19:63:5F
          inet addr:192.168.1.120  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:734 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:197012 (192.3 KiB)
          Interrupt:3 Base address:0x300

lo        Link encap:Local Loopback
          LOOPBACK  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

root@yellowcalx:/home/spike# ping -c 3 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 1999ms

root@yellowcalx:/home/spike# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:00:86:19:63:5F
          inet addr:192.168.1.120  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:740 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:197194 (192.5 KiB)
          Interrupt:3 Base address:0x300

lo        Link encap:Local Loopback
          LOOPBACK  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

root@yellowcalx:/home/spike# ping google.com
ping: unknown host google.com
```

still doesn't work. notice that ifconfig is showing that it's sending stuff, but nothing is coming back. I haven't set up a firewall, and iptables shows that it's not blocking anything.

/etc/resolv.conf contains nothing. I tried manually setting that to both my router (192.168.1.1) and my real DNS servers, but to no avail.

/var/log/kern.log has these lines in it when I boot the machine:
```
Oct 11 19:27:19 localhost kernel: [87563.493527] eth0: found link beat
Oct 11 19:27:19 localhost kernel: [87563.493573] eth0: autonegotiation complete: 100baseT-FD selected
Oct 11 19:27:20 localhost kernel: [87564.494125] eth0: interrupt(s) dropped!
```

Also, in one of the log files (I can't figure out which one, right now), it had repeated failures at contacting the DHCP server.

I also tried plugging it in, directly, raw, on the internet and configured the IP/subnet/gateway/DNS manually. Still didn't work.

any ideas? did I miss anything? aside from the networking, so far this is a great distro. It's the only one I could get to boot on this vaio.

thanks in advance.

---

