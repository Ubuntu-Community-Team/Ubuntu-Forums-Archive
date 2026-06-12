---
title: "Cannot get to the Internet"
date: 2006-09-26
forum: Networking &amp; Wireless
---

### Post by joyriderh on 2006-09-26
I have just did a clean install of Ubuntu to my P3. I cannot access the Net from the bundled Firefox. I use a wired Linksys router but the problem is not the router as I still cannot access the Net from a direct connection to the cable modem.

Here's what I have done so far:
1. Disabled IPv6 systemwide and in Firefox.
2. Put in the DNS Servers manually under Network settings.

Under Network settings Ethernet connection eth0 is active and set to DHCP.
When I ping 192.168.1.1 I get " _network is unreachable_ ".

Any help and/or suggestions is much appreciated.

---

### Post by jISh on 2006-09-26
If you're using DHCP from the router then you shouldn't have to put in your DNS servers manually.

Can you ping [www.google.com?](www.google.com?)

---

### Post by joyriderh on 2006-09-26
No I am not able to ping [www.google.com](www.google.com).
Btw I've tried removing the DNS addresses but still no joy. ](*,)

---

### Post by mips on 2006-09-26
Post output of  **lspci -v** here

Just the LAN card part

---

### Post by darrenm on 2006-09-26
Also

```
route
``` and ```
ifconfig -a
```

---

### Post by joyriderh on 2006-09-27
Since I cannot connect to the Net, can you tell me how I can save the output generated from lpsci , route etc. and put it into my Windows machine ?

---

### Post by joyriderh on 2006-09-27
Ok, I have manually copied the output:

1) lspci -v

0000:00:09.0 Ethernet Controller: Digital Equipment
Corporation DECchip 21041 [Tulip Pass 3] (rev 21)
      Flags: Bus Master, Medium devsel , latency 32, IRQ 9
      I/O ports at d000 [size=128]
      Memory at d5800000 (32-bit, non-prefetachable )
[size=128]
      Expansion ROM at 30000000 [disabled] [size=256k]

2) route

Kernel IP Routing table
Destination     Gateway    Genmask      Flags Metric
Ref        Use Iface

3) ifconfig -a
eth0    Link encap:Ethernet  HWaddr 00:e0:29:0a:97:27
        inet6 addr: fe80::2e0:29ff:fe0a:972/64 scope:link
        UP BRAODCAST RUNNING MULTICAST MTU:1500 Metric:1
        Rx packets:0 errors:0 dropped:0 overuns:0 frame:0
        Tx packets:0 errors:0 dropped:0 overuns:0 carrier:0
        collisions:0 txqueuelen:1000
        Rx bytes:0 (0.0 b)  TX bytes:0 ( 0.0 b )
        Interrupt:9 Base address:0x8000

l0      Link encap:Local Loopback
        inet addr:127.0.0.1 mask:255.0.0.0
        inet6 addr:  ::1/128 scope:host
        UP LOOPBACK RUNNING MTU:16436 metric:1
        Rx packets:7 errors:0 dropped:0 overuns:0 frame:0
        Tx packets:7 errors:0 dropped:0 overuns:0 carrier:0
        collisions:0 txqueuelen:0
        Rx bytes:372 (372.0 b)  TX bytes:372 ( 372.0 b )

sit0    Link encap:ipv6-in-ipv4
        NOARP mtu:1480 metric:1
        Rx packets:0 errors:0 dropped:0 overuns:0 frame:0
        Tx packets:0 errors:0 dropped:0 overuns:0 carrier:0
        collisions:0 txqueuelen:0
        Rx bytes:0 (0.0 b)  TX bytes:0 ( 0.0 b )

---

### Post by mips on 2006-09-27
```

1) lspci -v

0000:00:09.0 Ethernet Controller: Digital Equipment
Corporation DECchip 21041 [Tulip Pass 3] (rev 21)
      Flags: Bus Master, Medium devsel , latency 32, IRQ 9
      I/O ports at d000 [size=128]
      Memory at d5800000 (32-bit, non-prefetachable )
[size=128]
      Expansion ROM at 30000000 [disabled] [size=256k]
```

There is your problem, Tulip chipset.

Look here,  [http://www.ubuntuforums.org/showthread.php?t=186430](http://www.ubuntuforums.org/showthread.php?t=186430)

---

### Post by joyriderh on 2006-09-27
Hey mips, you're my man! Many thanks! I'll give a try tonight.

---

### Post by joyriderh on 2006-09-28
Hi mips, you have to give me another idea:

I removed the Tulip driver as below -
[I]Code:
sudo gedit /etc/modules
Then, you need to add "dmfe" to this, without the quotes. Make sure you save.
Finally, you need to blacklist the tulip driver so it wont run at startup. To do this you need to run the following in a terminal.

Code:
sudo gedit /etc/modprobe.d/blacklist
After this is opened, you need to add "blacklist tulip", without the quotations, somewhere in the file. Then save.[/I]

But.... still no internet. Ping doesn't work and there is no IP routing table.  

What next?

---

### Post by mips on 2006-09-28
Reboot and;

[http://doc.gwos.org/index.php/DisableIPV6](http://doc.gwos.org/index.php/DisableIPV6)
[http://www.ubuntuforums.org/showthread.php?t=78337](http://www.ubuntuforums.org/showthread.php?t=78337)

1. Please post output of **ifconfig eth0**  (Depends on your interface number)
2. Please post output of **lspci | grep Eth**
3. Please post output of **route -n**
5. Please post output of [B]cat /etc/network/interfaces

[/B]Do you dual-boot. if you do install the ext2ifs driver in windows so you can read the linux partitions. So you can save the above output in one file then open it from windows.

---

### Post by joyriderh on 2006-09-29
Well my NIC problems are all solved when I switched my card to a DLink NIC. Thanks mips for all your help. Now I am a happy ubuntu camper :p

---

