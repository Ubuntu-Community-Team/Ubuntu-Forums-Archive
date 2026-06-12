---
title: "Network stopped working"
date: 2006-09-17
forum: Networking &amp; Wireless
---

### Post by FrederikVds on 2006-09-17
My network randomly stopped working yesterday.

`sudo ifdown eth0` gives:
   send_packet: Network is unreachable
   send_packet: please consult README file regarding broadcast address.

`sudo ifup eth0` fails

What should I check? The network works in XP.

To be clear: I don't expect anyone to be able to solve it with this information, but please give me ideas about what to post to help you help me, 'cause I'm new to Linux.

---

### Post by bernied on 2006-09-17
Try ifconfig. Here's my output:
```
bernie@kubu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0F:EA:AC:9C:AF
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1006 errors:0 dropped:0 overruns:0 frame:0
          TX packets:980 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:489067 (477.6 KiB)  TX bytes:90806 (88.6 KiB)
          Interrupt:17 Base address:0xd800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

```
If there is no entry for eth0, then check the hardware and the kernel module. For hardware, use lspci. Here's the relevant bit of mine:
```
.
.
0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
.
.
```
You can also use lspci -v for more verbose output.
That SiS900 is also the name of the module that is the kernel driver.

Use lsmod to look at which kernel modules are running. My kernel is a little different as I built the driver in, rather than as a module, so the driver doesn't show up, but yours should. There should be a module for your network card. Google for the driver that should be included. If you can't find it, try:
sudo modprobe sis900
Except of course you would want your driver, which is probably not sis900.

Then try lsmod to se if it loaded, then try ifconfig again.

I'm not sure, but you may need to restart networking:
sudo /etc/init.d/networking restart
ubuntu may ot let you do this in a GUI - I'm going to check...

---

### Post by bernied on 2006-09-17
OK, so you can restart networking from within kde anyway, doesn't seem to upset anything. You may need to do this after any configuration changes you make, before they will take effect:
```
sudo /etc/init.d/networking restart
Password:
 * Reconfiguring network interfaces...                                                                              Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:0f:ea:ac:9c:af
Sending on   LPF/eth0/00:0f:ea:ac:9c:af
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.0.1 port 67
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:0f:ea:ac:9c:af
Sending on   LPF/eth0/00:0f:ea:ac:9c:af
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 192.168.0.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.2 -- renewal in 36474 seconds.

```

Also check your /etc/network/interfaces file. Mine looks like this:
```
cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

```

When you say randomly stopped working, had you done an upgrade on the previous boot? - ie. the last time that you turned the machine on. There was a kernel upgrade recently that may have broken your network interface module.

Post all you results to this stuff, if you can. If you have no internet on the ubuntu machine, save it all to a text file (starting with the contents of this thread), then you can take that with you, either on a shared drive, or a usb stick, or a floppy, between your windows install with internet and back to your unhappy ubuntu.

---

### Post by FrederikVds on 2006-09-17
Here are the results of ifconfig:

```
frederik@PCFrederik-ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:07:E9:42:6C:11
          inet6 addr: fe80::207:e9ff:fe42:6c11/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1516 (1.4 KiB)  TX bytes:2520 (2.4 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:861 errors:0 dropped:0 overruns:0 frame:0
          TX packets:861 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:54620 (53.3 KiB)  TX bytes:54620 (53.3 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:04:E2:66:BC:FF
          inet6 addr: fe80::204:e2ff:fe66:bcff/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2896 (2.8 KiB)  TX bytes:1626 (1.5 KiB)
          Interrupt:185 Base address:0xbc00
```
          
Both eth0 and wlan0 are connected to the same network, one wireless, one wired. Neither of them works.

Here are the complete results of ifup and ifdown (this order):

```
frederik@PCFrederik-ubuntu:~$ sudo ifup eth0
ifup: interface eth0 already configured

frederik@PCFrederik-ubuntu:~$ sudo ifdown eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:07:e9:42:6c:11
Sending on   LPF/eth0/00:07:e9:42:6c:11
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.11.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.

frederik@PCFrederik-ubuntu:~$ sudo ifup eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:07:e9:42:6c:11
Sending on   LPF/eth0/00:07:e9:42:6c:11
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

This seems to be the relevant output of `sudo lspci -v`:
```
0000:02:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 01)
        Subsystem: Intel Corporation Desktop Board D865GBF
        Flags: bus master, medium devsel, latency 32, IRQ 209
        Memory at ff9fe000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at b800 [size=64]
        Capabilities: [dc] Power Management version 2
```

I don't know how to google for the driver that should be included. I tried "8256EZ module" and "8256EZ driver", but that's probably not right?

```
frederik@PCFrederik-ubuntu:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid Corio00053
wireless-key [The right key in hexadecimal]
```

I don't remember what I did (it stopped working about a week ago, but I didn't have a lot of time to investigate it).
The logs seem to tell me the last succesfull connection was September 11th, 18:08.
Am I right to think everything that's installed will be in dpkg.log?
Then the last install was September 10th, sdate (which I removed again a little later) and fakeroot.
I tried booting to 3 different kernels, and the problem didn't change (does what I'm saying now make sense?)

Thanks a lot for the help,
Frederik Vanderstraeten

---

### Post by bernied on 2006-09-17
The hardware all seems to be working - are you sure your network is listening to the DHCP requests?
This is getting a bit beyond me I'm afraid.

---

### Post by FrederikVds on 2006-09-18
> **bernied said:**
> The hardware all seems to be working - are you sure your network is listening to the DHCP requests?
This is getting a bit beyond me I'm afraid.

I didn't change anything about my network, and I can still connect from the same computer with Windows.

---

### Post by xboxrob on 2006-09-18
Not quite sure if this will help but you can check to see what is happening to packets using tcpdump

eg tcpdump -i eth0

this may help check to see what it is actually doing. The only other thing i can think of is having eth0 and wlan0 enabled and trying to connect to the same network as a problem? I am not sure but i cant think of anyother ideas

---

### Post by FrederikVds on 2006-09-18
I'll try that when I have time. I never had problems with this before (for about two months). But I'll try pulling out wlan0.

---

### Post by FrederikVds on 2006-09-24
Hi

Thanks a lot for the help. I somewhat solved it. It turns out this was a problem with DHCP, and it got fixed by choosing a static IP address.
Still no idea why DHCP suddenly stopped working, but I don't really care anyway. My internet works again so I'm happy.

Thanks again
Frederik Vanderstraeten

---

