---
title: "Network Issues/no connection"
date: 2007-07-13
forum: Networking &amp; Wireless
---

### Post by rickdog on 2007-07-13
Okay, here's the problem: I'm at work using my 60gb hard drive with Xubuntu loaded on it. I have a job where I move around on site and can connect to a number of work stations all over the place. Essentially it's just a matter of plugging in and rebooting into my hard drive. They use a Websense proxy filter which I adjust for ([http://proxy:8080](http://proxy:8080)) and for the most part it's not a problem for Firefox to negotiate and pop up a login. We have a bunch of Dell GX620's and a few older GX270's and 280's.

Now, the problem is with two of the GX280's and one GX620. I can't connect through the proxy to the internet or get any connection at all. I'm writing this from a GX270 that works and here's the ifconfig from both:

GX270[COLOR="Blue"] (works fine)[/COLOR]

rick@rick-usb:~$ ifconfig

eth1      Link encap:Ethernet  HWaddr 00:0C:46:F0:CD:F2  

          inet addr:131.90.246.124  Bcast:255.255.255.255  Mask:255.255.254.0

          inet6 addr: fe80::20c:46ff:fef0:cdf2/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:6714 errors:0 dropped:0 overruns:0 frame:0

          TX packets:3007 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:3395672 (3.2 MiB)  TX bytes:493988 (482.4 KiB)

          Interrupt:20 Base address:0xdf20 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)



rick@rick-usb:~$ 


GX280 [COLOR="Red"](which doesn't work)[/COLOR]

rick@rick-usb:~$ ifconfig

eth1      Link encap:Ethernet  HWaddr 00:04:E2:99:75:2F  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:1 dropped:0 overruns:0 carrier:2

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

          Interrupt:17 Base address:0xdc00 



eth1:avah Link encap:Ethernet  HWaddr 00:04:E2:99:75:2F  

          inet addr:169.254.6.83  Bcast:169.254.255.255  Mask:255.255.0.0

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          Interrupt:17 Base address:0xdc00 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:44 errors:0 dropped:0 overruns:0 frame:0

          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:4286 (4.1 KiB)  TX bytes:4286 (4.1 KiB)



rick@rick-usb:~$

I can provide more read outs (netstat, etc) if necessary, but I figured I'd start there. Each of the three computers that I cannot access the internet with have that extra "eth1:avah" entry. I'm not sure what it means, but if anyone can help me out that would be great. Thanks.

---

