---
title: "AMD PCNet 79C978 HomePna card does not connect to internet"
date: 2005-03-29
forum: Networking &amp; Wireless
---

### Post by BORTKOMMEN on 2005-03-29
Hello Ubuntu world!

I have an AMD PCNet 79C978 HomePna card. The card does not connect to Internet with the new kernel 2.6 Linux-distributions, but there are no problems with the old 2.4 kernel. I noticed that with Knoppix 3.7. As default Knoppix boots with kernel 2.4 and I had immediate Internet access but when I booted with kernel 2.6 the connection failed.

Five operation systems are installed on my computer: windows 2000, Fedora Core3, Mandrake 10.1, Suse 9.2 and Ubuntu warty. All my Linux's have kernel 2.6 and I use DHCP.

I managed to solve the problem for Fedora and Mandrake after googling around. The solution ( from Barry K. Nathan ) was very simple and I write it down exactly as it was on the website:

“Assuming the card is eth0, try adding either of these lines:

options eth0 homepna=1
options pcnet32 homepna=1

to your /etc/modprobe.conf. (I would then run “depmod -a” and reboot). Maybe a “depmod -a; /etc/init.d/network restart” or a reboot alone would suffice, however”

There is certainly a similar solution to Suse and Ubuntu but because the file names are different in Ubuntu (and in Suse) I need a little bit help.

I tried adding the line “pcnet32 homepna=1” in /etc/modules as one suggested on this forum but it did not help, not “eth0 homepna=1” either.

The content of /etc/network/interfaces is:
auto lo
iface lo inet loopback

Here are the outputs of some commands:
root@ubuntu:/etc/network # iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
sit0      no wireless extensions.

root@ubuntu:/etc/network # dhclient
Internet Systems Consortium DHCP Client V3.0.1rc14
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/sit0/
Sending on   LPF/sit0/
Listening on LPF/eth0/00:e0:7d:9b:57:67
Sending on   LPF/eth0/00:e0:7d:9b:57:67
Listening on LPF/lo/
Sending on   LPF/lo/
Sending on   Socket/fallback
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database – sleeping.

root@ubuntu:/etc/network # ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:E0:7D:9B:57:67
          inet6 addr: fe80::2e0:7dff:fe9b:5767/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:12 dropped:0 overruns:0 carrier:12
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:2772 (2.7 KiB)
          Interrupt:177 Base address:0xd800

lo        Link encap:Local Loopback
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:31294 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31294 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2261900 (2.1 MiB)  TX bytes:2261900 (2.1 MiB)

sit0      Link encap:IPv6-in-IPv4
          inet6 addr: ::127.0.0.1/96 Scope:Unknown
          UP RUNNING NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

I hope this information might help you to solve the problem and i am thankful for any advice.

---

### Post by BORTKOMMEN on 2005-04-02
Bump

---

### Post by BORTKOMMEN on 2005-04-14
I found the solution at last:

Added in /etc/modules these lines

eth0 homepna=1
pcnet32 homepna=1

Then the command “modprobe pcnet32 pcnet32_homepna=1”

and “depmod -a” and rebooted.

---

