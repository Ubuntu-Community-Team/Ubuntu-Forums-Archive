---
title: "How to get rid of rogue Vmware ethernet adapter?"
date: 2007-09-25
forum: Networking &amp; Wireless
---

### Post by compdata on 2007-09-25
I have windows xp running on vmware server 1.0.3 build-44356 on my ubuntu 7.04 machine. I initially installed this with the Bridged internet connection options, but when i did that the internet only worked from within the xp install running on the vmware server. So i switched to NAT which seems to have fixed that issue.

However now every 3rd or 4th time that i boot up my computer my internet doesn't work at all from xp or ubuntu. When i do a route it shows me that my routing table is not correct.

Normal Route:

lucasandnaomi@ig-88:~$ route
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
192.168.2.0 * 255.255.255.0 U 0 0 0 eth0
192.168.152.0 * 255.255.255.0 U 0 0 0 vmnet8
link-local * 255.255.0.0 U 1000 0 0 eth0
default 192.168.2.1 0.0.0.0 UG 0 0 0 eth0

Bad Routeing table:

lucasandnaomi@ig-88:~$ route
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
192.168.2.0 * 255.255.255.0 U 0 0 0 vmnet1
192.168.2.0 * 255.255.255.0 U 0 0 0 eth0
192.168.152.0 * 255.255.255.0 U 0 0 0 vmnet8
link-local * 255.255.0.0 U 1000 0 0 eth0

This lead me to believe that one of the vmware ethernet adapters (vmnet1) was my issue. Doing ifconfig i see the following for that adapter:

lucasandnaomi@ig-88:~$ ifconfig vmnet1

vmnet1 Link encap:Ethernet HWaddr 00:50:56:C0:00:01
inet addr:192.168.2.1 Bcast:192.168.2.255 Mask:255.255.255.0
inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:70 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)

I tried disabling that adapter and trying to recreate the default route, but it doesn't seem to work.

lucasandnaomi@ig-88:~$ sudo ifconfig vmnet1 down
lucasandnaomi@ig-88:~$ sudo route -v add default gw 192.168.2.1
SIOCADDRT: Network is down

Any ideas on what might be causing this issue? And or make sure that vmnet1 doesn't start up when i boot my computer?

---

### Post by kenden on 2008-04-23
Hi,

I am having the same issue on Hardy RC.
If I turn off the machine (or it crashes) with the Vmware Server Console still running, after restarting, there is a vmnet8 Ethernet adapter that makes it impossible to connect to a gateway.

When I check the routing table, there is no line with a "UG" flag.
If I try to add a gateway with:
sudo route add default gw 10.31.20.1

then the gateway is added to the vmnet8 adapter.

If I set the vmnet8 adapter down with
sudo ifconfig vmnet8 down
(sudo ifdown vmnet8 doesn't work)
And then add a gateway again, I get the message:
SIOCADDRT: Network is down

Restarting the networking service:
sudo /etc/init.d/networking restart
does not help.

Any idea?

Thanks,
kenden

Note: there is no Vmware package available at this time, so it was installed directly from vmware.

---

### Post by kenden on 2008-04-23
I have found a way to get rid of the vmnet8 Ethernet Adapter:
kill the vmware processes in the memory:
Find them with:
ps -A | grep vm
 5776 ?        00:00:00 vmnet-bridge
 5789 ?        00:00:00 vmnet-netifup
 5795 ?        00:00:00 vmnet-natd
 5805 ?        00:00:00 vmnet-dhcpd
 5806 ?        00:00:01 vmware-serverd

Then kill them:
sudo kill 5776
sudo kill 5789
sudo kill 5795
sudo kill 5805
sudo kill 5806
(Probably only one of them should be killed, but I haven't tested which one).

Now, typing "route -n" does not return a vmnet8 adapter anymore, and you can add the gateway:
sudo route add default gw 10.31.20.1
(10.31.20.1 is MY gateway, use the ip of yours)
The gateway is added to the correct adapter, eth0 for me.

Afterwards, you can restart the vmware services with:
sudo vmware-config.pl
Just press enter each time, as this should be already configured.

Hope this helps,
kenden

---

