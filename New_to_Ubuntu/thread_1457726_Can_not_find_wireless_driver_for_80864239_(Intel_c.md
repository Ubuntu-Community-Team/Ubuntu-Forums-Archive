---
title: "Can not find wireless driver for 8086:4239 (Intel chip, HP laptop)"
date: 2010-04-19
forum: New to Ubuntu
---

### Post by homebound on 2010-04-19
I am new to Linux. I purchased an HP i7 laptop and need to install linux on it.

I have tried many different things to get the wireless to come up but to no avail. According to the ubuntu forums ([https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Installing%20Windows%20driver%20using%20ndisgtk%20%28ndiswrapper%20graphical%20interface%29](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Installing%20Windows%20driver%20using%20ndisgtk%20%28ndiswrapper%20graphical%20interface%29)), I need to find the windows driver for this HP laptop which uses an Intel wireless chipset (Intel 8060:4239). 

Here is the lspci output: 
02:00.0 Network controller: Intel Corporation Device 4239 (rev 35)
and 
02:00.0 0280: 8086:4239 (rev 35)

and the output for ifconfig is:
ifconfig -a
eth0      Link encap:Ethernet  HWaddr c8:0a:a9:24:47:37  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::ca0a:a9ff:fe24:4737/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7422 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6169 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7832593 (7.8 MB)  TX bytes:982500 (982.5 KB)
          Interrupt:35 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:23:14:30:de:34  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-23-14-30-DE-34-00-00-00-00-00-00-00-00-00-00  
          [NO FLAGS]  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


It appears that the only location that I would be able to download this driver is at [http://wiki.debian.org/iwlagn](http://wiki.debian.org/iwlagn). The instructions seem quite complex. Can someone confirm that I am going down the right path and that I have to follow the above instructions?

Thank you
Marcus

---

### Post by lisati on 2010-04-19
Thread closed, duplicate of [http://ubuntuforums.org/showthread.php?t=1457727](http://ubuntuforums.org/showthread.php?t=1457727)

---

