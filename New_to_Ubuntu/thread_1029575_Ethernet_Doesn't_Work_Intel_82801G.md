---
title: "Ethernet Doesn't Work Intel 82801G"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by jackmackerel on 2009-01-03
Edit: I installed Ubuntu 8.04 and now the internet works, so if anyone else is having this same problem, that might be an easy solution.  Thanks again Cog for your help.

Hi Everyone,

I just installed Ubuntu 8.10 yesterday on an old Dell 9100.  I'm totally new to this whole thing, and have been banging my head against the wall for a few hours trying to figure out why my wired internet connection doesn't work.

Here's what happens when I type lspci in the terminal:
jason@ibex:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GR/GH (ICH7 Family) SATA AHCI Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]
05:08.0 Ethernet controller: Intel Corporation 82801G (ICH7 Family) LAN Controller (rev 01)


and here's what happens with ifconfig:

jason@ibex:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:12:3f:6f:fd:3b  
          UP BROADCAST RUNNING MULTICAST  MTU:64  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1240 (1.2 KB)  TX bytes:1825 (1.8 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:242 errors:0 dropped:0 overruns:0 frame:0
          TX packets:242 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15132 (15.1 KB)  TX bytes:15132 (15.1 KB)

I'm really in over my head, thanks in advance to everyone who helps.

---

### Post by The Cog on 2009-01-03
According to ifconfig, your ethernet is working, and is both sending and receiving packets. But hasn't been given an IP address. Try this command:
**sudo dhclient eth0**
and if it doesn't get an IP address, try it again while running this command in a different window:
**sudo tcpdump -i eth0**
And paste the outputs here.

---

### Post by jackmackerel on 2009-01-03
> **The Cog said:**
> According to ifconfig, your ethernet is working, and is both sending and receiving packets. But hasn't been given an IP address. Try this command:
**sudo dhclient eth0**
and if it doesn't get an IP address, try it again while running this command in a different window:
**sudo tcpdump -i eth0**
And paste the outputs here.

Ok, here's what happened the first and second time I entered that in the terminal:

sudo dchlient eth0:
jason@ibex:~$ sudo dhclient eth0
[sudo] password for jason: 
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No buffer space available
Listening on LPF/eth0/00:12:3f:6f:fd:3b
Sending on   LPF/eth0/00:12:3f:6f:fd:3b
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
send_packet: Message too long
No DHCPOFFERS received.
No working leases in persistent database – sleeping.


jason@ibex:~$ sudo dhclient eth0
There is already a pid file /var/run/dhclient.pid with pid 7356
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
SIOCSIFADDR: No buffer space available
Listening on LPF/eth0/00:12:3f:6f:fd:3b
Sending on   LPF/eth0/00:12:3f:6f:fd:3b
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
send_packet: Message too long
No DHCPOFFERS received.
No working leases in persistent database – sleeping.

And in the other window with sudo tcpdump -i eth0:
jason@ibex:~$ sudo tcpdump -i eth0
[sudo] password for jason: 
tcpdump: WARNING: eth0: no IPv4 address assigned
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes
16:04:20.996743 arp who-has 192.168.254.254 tell 192.168.254.34
16:04:41.346874 arp who-has 169.254.6.249 tell 0.0.0.0
16:04:43.238362 arp who-has 169.254.6.249 tell 0.0.0.0
16:04:44.430344 arp who-has 169.254.6.249 tell 0.0.0.0
16:04:46.434551 arp who-has 169.254.6.249 tell 169.254.6.249
16:04:48.438359 arp who-has 169.254.6.249 tell 169.254.6.249
16:06:02.104884 IP 192.168.254.34.netbios-dgm > 192.168.254.255.netbios-dgm: NBT UDP PACKET(138)


I don't know if this helps or is related but:
Right when the desktop loads, it says it has a connection, but Firefox won't load a page and shortly after it has the popup window that says there is no connection.  It also tells me the connection is disabled.
Audio also doesn't work
The desktop gets messed up if I switch Visual Effects to Normal or Extra

Thanks for the help!

---

### Post by The Cog on 2009-01-04
Sounds like a rigth mess. It makes me wonder if your installation CD is burned OK.

The line **send_packet: Message too long** looks bad to me. I think it's going through the process of trying to send the DHCP request but giving up because of some error. 

Looking again, I see that the MTU for your eth0 is 64. This is the Maximum Transmission Unit, the biggest packet it can physically handle. And 64 is very wrong. It is normally 1500 and I don't think it should ever be much less. You could try this command:
[B]sudo ifconfig eth0 mtu 1500
sudo dhclient eth0[/B]
but I suspect things are so wrong that it still won't work.

If you run the live CD on that box, does it say MTU 64 then?
I really wouldn't know what to do from here except maybe re-install or try a different version/distro.

---

### Post by jackmackerel on 2009-01-04
> **The Cog said:**
> Sounds like a rigth mess. It makes me wonder if your installation CD is burned OK.

The line **send_packet: Message too long** looks bad to me. I think it's going through the process of trying to send the DHCP request but giving up because of some error. 

Looking again, I see that the MTU for your eth0 is 64. This is the Maximum Transmission Unit, the biggest packet it can physically handle. And 64 is very wrong. It is normally 1500 and I don't think it should ever be much less. You could try this command:
[B]sudo ifconfig eth0 mtu 1500
sudo dhclient eth0[/B]
but I suspect things are so wrong that it still won't work.

If you run the live CD on that box, does it say MTU 64 then?
I really wouldn't know what to do from here except maybe re-install or try a different version/distro.

Thanks Cog, I tried both commands, no luck.  I also did ifconfig on the live cd, same thing, MTU is 64.  Unless anyone else has a suggestion, I'm going to try a different version.  Thanks again.

---

