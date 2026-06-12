---
title: "lo and eth0 in interfaces file"
date: 2007-12-24
forum: Networking &amp; Wireless
---

### Post by ikt on 2007-12-24
Hi,

According to:

[https://help.ubuntu.com/7.10/server/C/network-configuration.html#ethernet](https://help.ubuntu.com/7.10/server/C/network-configuration.html#ethernet)

My /etc/network/interfaces should look something like this:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp

--------

Because I have one ethernet device, and acquire my ip via dhcp..

However it doesn't, it looks like this:

auto lo
iface lo inet loopback

and according to the guide:

If you have no ethernet devices, only the loopback interface will appear in this file.

Which is all that is showing yet:

--------

ikt@ikt-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1A:4D:49:D4:5A  
          inet addr:192.168.0.7  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:4dff:fe49:d45a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23985677 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16001145 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:183432852 (174.9 MB)  TX bytes:1295339076 (1.2 GB)
          Interrupt:17 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:748 (748.0 b)  TX bytes:748 (748.0 b)


Where is it getting the information for eth0 from? I would have thought this would be defined in the interfaces file?

---

### Post by spd106 on 2007-12-26
The interfaces file read by the network scripts to configure the connections, it's not where the current settings are stored. I believe ifconfig reads the data from somewhere in /proc when it is run to provide a live status.

Since you have eth0 set to DHCP, the network scripts fetch the configuration information from the DHCP server and store it in /proc. This information is dynamic so there's no need for it to be stored permanently in a configuration file, unless you want the same every time. In that case you add the IP address, netmask etc to the interfaces file.

I recommend that you have a read through the Linux Network Administrators Guide at [http://www.faqs.org/docs/linux_network/index.html](http://www.faqs.org/docs/linux_network/index.html)

---

