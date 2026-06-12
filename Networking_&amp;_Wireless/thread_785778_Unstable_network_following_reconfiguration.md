---
title: "Unstable network following reconfiguration"
date: 2008-05-07
forum: Networking &amp; Wireless
---

### Post by rvallee on 2008-05-07
I have been working on some PHP projects with a VMWared-Ubuntu machine for a while with great success.

I recently reconfigured my network to throw a wireless router in the DSL-VoIP setup and have had very unstable network access to the box since.

The symptoms:
[LIST=1]
[*]Whenever I start the Ubuntu VM, everything works: SCP, SSH, Web (Apache2), etc.
[*]Within about a minute, the connection to the VM drops: SSH and SCP connections drop and I get a connection timed out in Firefox.
[*]Ping works to and from the VM.
[*]Restarting networking (/etc/init.d/networking restart) or waiting a few seconds and everything works again.
[*] Repeat #2
[/LIST]

Now this obviously could be related to VMWare but I haven't changed anything to this setup and since restarting networking in the VM works I doubt VMWare is causing the issue.

Usually if I refresh Firefox at short intervals it will keep working. The connection seems to drop if I don't refresh for more than a few seconds.

When the SCP connection drops (WinSCP), I see that reconnection hangs at 'Searching for host'.

My Apache configuration is fairly simple, with vhosts mapped to domain names that I set in my Windows hosts file. Pinging mt vhost works without a hitch so it's strange that WinSCP would hang at searching for host since it is resolved instantly by ping. But even when I can login, either ssh or scp, there is an awful lag.

When the connection does not respond, I see nothing in Apache's logs so the request does not even get to it. If I do a wget on the same query as I do from my PC in the VM, Apache answers instantly.

The likeliest possibility is that I changed my gateway, although I don't know enough about networking to see how this could affect anything other than changing the value in /etc/network/interfaces. The VoIP router and my wireless router were both set up at 192.168.0.1 so I changed the wireless router (which dials the connection) to 192.168.0.99 and modified my network interface accordingly.

Here is my /etc/network/interfaces file:
[INDENT]# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp

iface eth0 inet static
address 192.168.0.100
netmask 255.255.255.0
#network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.99[/INDENT]

The old setup:
[LIST=1]
[*]DSL modem
[*]Connected to a VoIP modem / router that made the PPoE connection
[*]Connected to my PC (Windows XP) and a dynamic IP
[*]With a static IP for the Ubuntu VM
[/LIST]

The current setup:
[LIST=1]
[*]DSL modem
[*]Connected to my wireless router which dials the DSL connection
[*]Connected to my PC (Windows XP) that has a dynamic IP
[*]Same setup for the Ubuntu VM
[/LIST]

I'm fairly comfortable with Linux but not in networking issues so I don't even know where to begin to identify the cause. Any hints would be greatly appreciated, even if only to identify the possible causes from which I could investigate.

---

### Post by rvallee on 2008-05-07
Oh yeah and in case this could help, here's the output of ifconfig:

[INDENT]eth0      Link encap:Ethernet  HWaddr 00:0C:29:32:17:99
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe32:1799/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3423 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1962 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:859980 (839.8 KiB)  TX bytes:1360233 (1.2 MiB)
          Interrupt:16 Base address:0x1424

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:440 (440.0 b)  TX bytes:440 (440.0 b)[/INDENT]

---

