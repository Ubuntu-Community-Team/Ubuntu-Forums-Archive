---
title: "network not working on PCMCIA"
date: 2005-10-13
forum: Networking &amp; Wireless
---

### Post by spike666 on 2005-10-13
(I mistakenly posted this in the 5.04 forums yesterday... Here's a repost.)

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

### Post by spd106 on 2005-10-15
Forgive me if this sounds rather patronising, but you never said that you tried **sudo ifup eth0**. Nor did you run **sudo dhclient eth0** to ask for an ip address.

This should not excuse the manual config from not working though:confused: 

How about checking over the /etc/network/interfaces file?
Do you see any activity lights on the router when you plug it in? 
Have you enabled MAC address filtering?
What does **sudo arp -a** show?

---

### Post by spike666 on 2005-10-16
it's ok. I'm glad to at least have a response. ;)

The light on the port on the PCMCIA card and the light on the switch both illuminate when I plug the cable in.

if I set up an IP with ifconfig and I ping something on my LAN, I get a blinking on the switch.

once I configure an ip on the machine, if I try to ping it from another machine (attached to the same switch), I get this:

```
Alberto:~ spike$ ping 192.168.1.120
PING 192.168.1.120 (192.168.1.120): 56 data bytes
ping: sendto: No route to host
ping: sendto: Host is down
ping: sendto: Host is down
ping: sendto: Host is down
ping: sendto: Host is down
^C
--- 192.168.1.120 ping statistics ---
10 packets transmitted, 0 packets received, 100% packet loss
```

ifup is pretty much the same thing as calling ifconfig eth0 up. in fact, the ifup manpage explicitly says that it uses ifconfig to do that.

```
root@yellowcalx:/home/spike# ifup eth0
ifup: interface eth0 already configured
```

here's /etc/network/interfaces:
```
root@yellowcalx:/home/spike# cat /etc/network/interfaces
# Used by ifup(8) and ifdown(8). See the interfaces(5) manpage or
# /usr/share/doc/ifupdown/examples for more information.

iface lo inet loopback

iface eth0 inet dhcp

auto eth0
```

here's the arp command:
```
root@yellowcalx:/home/spike# arp -a
root@yellowcalx:/home/spike#
```

I also noticed that lo doesn't have an IP!!!!! I set an IP and got semi-networking working. I can't ping the local machine from it's IP or 127.0.0.1 when lo does't have an IP:

```
root@yellowcalx:/home/spike# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:00:86:19:63:5F
          inet addr:192.168.1.120  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:117 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:327902 (320.2 KiB)
          Interrupt:3 Base address:0x300

root@yellowcalx:/home/spike# ping localhost
connect: Network is unreachable
root@yellowcalx:/home/spike# ping 127.0.0.1
connect: Network is unreachable
root@yellowcalx:/home/spike# ifconfig lo
lo        Link encap:Local Loopback
          LOOPBACK  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

root@yellowcalx:/home/spike# ifconfig lo 127.0.0.1
root@yellowcalx:/home/spike# ping 192.168.1.120
PING 192.168.1.120 (192.168.1.120) 56(84) bytes of data.
64 bytes from 192.168.1.120: icmp_seq=1 ttl=64 time=0.202 ms
64 bytes from 192.168.1.120: icmp_seq=2 ttl=64 time=0.148 ms
64 bytes from 192.168.1.120: icmp_seq=3 ttl=64 time=0.143 ms
64 bytes from 192.168.1.120: icmp_seq=4 ttl=64 time=0.144 ms

--- 192.168.1.120 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2999ms
rtt min/avg/max/mdev = 0.143/0.159/0.202/0.026 ms
```

when I try to ping another machine on my network, it still doesn't work (first the router, then one of my desktop machines:

```
root@yellowcalx:/home/spike# ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.120 icmp_seq=2 Destination Host Unreachable
From 192.168.1.120 icmp_seq=3 Destination Host Unreachable
From 192.168.1.120 icmp_seq=4 Destination Host Unreachable
From 192.168.1.120 icmp_seq=6 Destination Host Unreachable
From 192.168.1.120 icmp_seq=7 Destination Host Unreachable
From 192.168.1.120 icmp_seq=8 Destination Host Unreachable

--- 192.168.1.1 ping statistics ---
10 packets transmitted, 0 received, +6 errors, 100% packet loss, time 9000ms
, pipe 3
root@yellowcalx:/home/spike# ping 192.168.1.102
PING 192.168.1.102 (192.168.1.102) 56(84) bytes of data.
From 192.168.1.120 icmp_seq=2 Destination Host Unreachable
From 192.168.1.120 icmp_seq=3 Destination Host Unreachable
From 192.168.1.120 icmp_seq=4 Destination Host Unreachable

--- 192.168.1.102 ping statistics ---
5 packets transmitted, 0 received, +3 errors, 100% packet loss, time 3999ms
, pipe 3
```

running dhclient fails by not finding a DHCP server (which makes sense since it's not communicating over the network)

I just realized that I may be running a pre-release of 5.10, since I downloaded it about 2 or 3 days before it was "released." how do I find out what version? Maybe I should download the new version and reinstall?

---

### Post by breakthestate on 2005-10-16
Not sure if it would make a difference, but shouldn't there be a line of the following in your /etc/network/interfaces file:

[B][FONT=Garamond]auto lo

[/FONT][/B][FONT=Garamond]The rest of your /etc/network/interfaces file looks good. Again, I'm not sure, but it could help to add the line above. Normally, you would have an IP address of 127.0.0.1 for "lo" when you do ifconfig.  I would add the line above and save and then try running:

[B]ifconfig lo down
ifconfig eth0 down
ifconfig lo up
ifconfig eth0 up
dhclient eth0[/B]
[/FONT]

---

### Post by spike666 on 2005-10-16
I don't feel like swapping my USB drive back over to that box right now to save the output, so I'll just type and paraphrase:

I made the change to /etc/network/interfaces and brought eth0 and lo down and back up.

then ran dhclient on eth0:

```
root@yellowcalx:/home/spike# dhclient eth0
Internet Systems Consortium blah blah
all rights reserved
...

Listening on LPF/eth0/00:00:86:19:53:5f
Sending on LPF/eth0/00:00:86:19:53:5f
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
...interval 9
...interval 17
...
...
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

any more ideas?

I'm downloading the release of 5.10. I'll reinstall tomorrow night and see how everything goes. maybe it'll fix it?

---

### Post by breakthestate on 2005-10-16
After you added the line, did lo have an inet addr after you type ifconfig?

---

### Post by spike666 on 2005-10-16
I rebooted just to make sure.

now I don't need to type 'ifconfig -a' to see lo (it wasn't showing up unless I did that, before)

now when I type just 'ifconfig' it shows eth0 (with no IP) and lo (with 127.0.0.1)

so we're making progress. =)

---

### Post by breakthestate on 2005-10-16
sounds better.  so did you try it out yet?, or have you still not swapped your USB drive to that machine?

---

### Post by spike666 on 2005-10-16
same results as earlier.

I can ping localhost without issue.

dhclient isn't connecting to anything

when I manually set an ip on eth0 with ifconfig (ifconfig eth0 192.168.1.120 up), and I try to ping my router or any machine on my LAN, I get "Destination Host Unreachable"

I still can't ping the ubuntu machine from any other machine on the network.

I just went so far as to crack open a brand new 10' ethernet cable and quadruple check that it's not the wire. And still doesn't work.

I wish I had another laptop to plug this card in to confirm that it works, again (even though it worked 2 weeks ago in win98 ).

I'll just reinstall when I get the 5.10 release downloaded. it's not that big of a deal. If it works then, then it was because of something bad in the preview. if it still doesn't work, I'll pull my hair out some more.

I know I have another PCMCIA ethernet card kicking around here, somewhere. I could always try that one, too. It's just a matter of finding it.

---

