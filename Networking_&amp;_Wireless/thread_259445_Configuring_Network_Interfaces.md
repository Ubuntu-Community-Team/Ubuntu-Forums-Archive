---
title: "Configuring Network Interfaces"
date: 2006-09-17
forum: Networking &amp; Wireless
---

### Post by esquilo on 2006-09-17
I have a Wireless card working fine in Ubuntu, but at booting process the "Configuring Network Interfaces" take a long time (about 15 seconds. Is it normal?

my /etc/network/interfaces is:

auto lo
iface lo inet loopback
auto wlan0
iface wlan0 inet static
address 192.168.1.55
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid home

and if config:

eth0      Link encap:Ethernet  HWaddr 00:50:BF:AA:C4:B1
          inet6 addr: fe80::250:bfff:feaa:c4b1/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:3 dropped:0 overruns:0 carrier:6
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:201 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:26 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1332 (1.3 KiB)  TX bytes:1332 (1.3 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:40:F4:E5:F0:FF
          inet addr:192.168.1.55  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::240:f4ff:fee5:f0ff/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7779 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5665 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5641977 (5.3 MiB)  TX bytes:503384 (491.5 KiB)
          Interrupt:209 Memory:e7010000-e7020000

---

### Post by jd65pl on 2006-09-17
Hello,

Mine did that are you using ndiswrapper?

Thanks

J

---

### Post by esquilo on 2006-09-17
yes, I'm using ndiswrapper. It's all perfect in my networking spite this long  time to process the "configuring network interfaces" in boot. Do you think that ndiswrapper is the problem?

thank for the help.

---

### Post by jd65pl on 2006-09-17
Try this

Create a file in "/ect/modprobe.d" called ndiswrapper

add this line:
alias wlan0 ndiswrapper

Reboot

---

### Post by jd65pl on 2006-09-17
If that doesn't work try following every step on this guide

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

---

### Post by esquilo on 2006-09-17
Thanks!

I've found the problem with your tips. I haven't input the ndiswrapper in the /etc/modules. Now, my boot take around 45 seconds for boot.Before were 1.10!

---

### Post by jd65pl on 2006-09-18
Gald it worked for you! ndiwrapper was a learning curve for me!

Thanks

J

---

