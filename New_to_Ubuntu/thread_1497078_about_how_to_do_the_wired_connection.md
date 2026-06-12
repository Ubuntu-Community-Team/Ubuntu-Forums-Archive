---
title: "about how to do the wired connection"
date: 2010-05-30
forum: New to Ubuntu
---

### Post by reychun on 2010-05-30
I use Acer Aspire. I entered the correct things of my network. Like going to Terminal, and typing things like "ifconfig", or "route" and putting the information in the network manager's "edit connections" but nothing is working. What should I do?

---

### Post by r-senior on 2010-05-30
If you have a DHCP server set up on your network (which might be provided by your router), you shouldn't need to change any settings in "Edit Connections" or do anything in a terminal. It *should* just be a matter of plugging it in?

The DHCP server will provide an IP address, submet mask, gateway and DNS information.

Do you have other machines running on the same network?

Could you explain more about your network? The type of router you have, the type of connection you have and machines connected to it. Have you configured DHCP?

Do you know the IP address of your router? Have you tried pinging that to see if your machine can see it?

Maybe you could also post the output from ifconfig and route? No options, just type those commands.

---

### Post by reychun on 2010-05-31
> **r-senior said:**
> If you have a DHCP server set up on your network (which might be provided by your router), you shouldn't need to change any settings in "Edit Connections" or do anything in a terminal. It *should* just be a matter of plugging it in?
 
The DHCP server will provide an IP address, submet mask, gateway and DNS information.
 
Do you have other machines running on the same network?
 
Could you explain more about your network? The type of router you have, the type of connection you have and machines connected to it. Have you configured DHCP?
 
Do you know the IP address of your router? Have you tried pinging that to see if your machine can see it?
 
Maybe you could also post the output from ifconfig and route? No options, just type those commands.
 
But the internet does not work even when the the wire is plugged in so I guess there is no DHCP?
 
No, there is no other machines running the same network, I guess. Actually, there is also a wireless connection but it is very bad as compared to the wired one if the wired one was to work. How do I configure my DHCP?
 
Yes I tried the ping and it worked but when I checked the ethernet information, it says that it is idle. 
 
when I type "ifconfig":
 
eth0
Link encap:Ethernet   HWaddr 90:fb:a6:2f:35:78
inet addr:192.168.1.68   Bcast:192.168.1.255   Mask:255.255.255.0
inet6 addr: fe80::92fb:a6ff:fe2f:3578/64   Scope:Link
UP BROADCAST RUNNING MULTICAST   MTU:1500   Metric:1
RX packets: 676   errors:0 dropped:0 overruns:0 frame:0
TX packets:86 erros:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:100
RX bytes: 63389 (63.3KB) TX bytes:7737 (7.7 KB)
Memory: f9fc0000-f9fe0000
 
lo
Link encap: Local Loopback
inet addr: 127.0.0.1   Mask:255.0.0.0
inet6 addr: ::1/128   Scope:Host
UP LOOPBACK RUNNNG   MTU:16436   Metric:1
RX packets: 12   errors:0 dropped:0 overruns:0 frame:0
TX packets:12 erros:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen0
RX bytes: 720 (720.0 B) TX bytes:7737 (720.0 B)
 
wlan0
Link encap:Ethernet   HWaddr 70.1a.04.b3.cf.37
inet addr:192.168.1.65   Bcast:192.168.1.255   Mask:255.255.255.0
inet6 addr: fe80::721a:4ff:feb3:cf37/64   Scope:Link
UP BROADCAST RUNNING MULTICAST   MTU:1500   Metric:1
RX packets: 9463   errors:0 dropped:0 overruns:0 frame:0
TX packets:687 erros:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes: 1272702 (1.2 MB) TX bytes:97945 (97.9 KB)
Interrupt: 19
 
when I type "route":
Kernel IP routing table
destination        Gateway            Genmask         Flags      Metric Ref    Use Iface
192.168.1.0        *                     255.255.255.0    U          0         0        0  eht0
192.168.1.0        *                     255.255.255.0    U          2         0        0  wlan0
link-local            *                     255.255.0.0        U          1000    0        0  eth0
default               menu               0.0.0.0               UG        0         0       0   wlan0
default               menu               0.0.0.0               UG        100      0        0  eth0

---

