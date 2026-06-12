---
title: "internet connection not always fast"
date: 2007-07-19
forum: Networking &amp; Wireless
---

### Post by AbredPeytr on 2007-07-19
I hope this isn't already in the forums, but I'm known for missing what's right under my nose.
Anywho, the problem.

I installed Feisty 64bit on my HP Pavilion laptop with no problems and got my Wifi working with very little trouble with help from the forums. Internet (wifi and cable) had worked without problem for about three weeks.  Recently I have the problem that when I login in and try to access the internet it takes a very long time to find the page and begin loading, or it just times out. I thought it was a problem with wifi at first, so connected the cable to the router, same results. Restarting once or twice seems to fix the problem and it's faster than I usually get with  my Vista computer. I'm pretty sure it's not a problem with the router as I've tested the DSL speed using my desktop directly connected to the router gives excellent speed.

Not sure if this will help but ifconfig gives the following:

eth0      Link encap:Ethernet  HWaddr 00:0F:B0:BE:5A:E9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:22 Base address:0xc400 

eth1      Link encap:Ethernet  HWaddr 00:14:A5:64:6B:59  
          inet addr:192.168.2.100  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::214:a5ff:fe64:6b59/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:483 errors:0 dropped:1 overruns:0 frame:0
          TX packets:533 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:476678 (465.5 KiB)  TX bytes:61325 (59.8 KiB)
          Interrupt:10 Base address:0x8000 

eth0:avah Link encap:Ethernet  HWaddr 00:0F:B0:BE:5A:E9  
          inet addr:169.254.9.159  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:22 Base address:0xc400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5332 (5.2 KiB)  TX bytes:5332 (5.2 KiB)

Thanks for any help you're able to provide.

p.s. before anyone asks why I'm using Feisty 64bit, I just wanted to :-) And it's fast.

---

### Post by reckless2k2 on 2007-07-19
if rebooting the modem is "fixing" it temporarily, i'd eval what's on your network and running on all your PCs. for instance, i had a lady that complained of something similar especially after all 5 PCs in her house were connected to net and or on. I came to find that she had limewire running on EVERY machine sharing out hundreds and hundreds of songs on each machine. as each turned on...you can imagine. then, she was broadcasting her network so 2 neighbors with laptops were connecting as well. who knows what they were doing on her connection as well. get the idea?

---

### Post by AbredPeytr on 2007-07-19
> **reckless2k2 said:**
> if rebooting the modem is "fixing" it temporarily, i'd eval what's on your network and running on all your PCs. for instance, i had a lady that complained of something similar especially after all 5 PCs in her house were connected to net and or on. I came to find that she had limewire running on EVERY machine sharing out hundreds and hundreds of songs on each machine. as each turned on...you can imagine. then, she was broadcasting her network so 2 neighbors with laptops were connecting as well. who knows what they were doing on her connection as well. get the idea?

Hi reckless2k2, thanks for the rapid response. I definitely do not have that problem. During all these problems only I had access to the router and only had the laptop on. I do share wifi with my neighbor, but he was out of town at the time. I can't guarantee others aren't using my wifi, but whenever I check, only the allowed computer are connected.  It helps that this old building has thick wall that play havoc with the signal.

BTW, I'm surprised that woman hasn't been arrested by the music police.  All 5 computers sharing music.

---

