---
title: "Wired Laptop DNS Issues"
date: 2006-11-20
forum: Networking &amp; Wireless
---

### Post by daverice on 2006-11-20
I am having problems with a recently installed Edgy server.

I get an IP adddress from my router and I can ping computers on my network as well as machines on the Internet as long as I enter the IP address. 

I realize this implies I have some sort of a DNS error, but cannot understand how this computer would not receive the same DNS information from the router as the other computers on my network.  

How can I explicitly tell the computer where a DNS server is?

Here's my ifconfig
[INDENT]eth0[INDENT]Link encap:Ethernet  HWaddr 00:00:86:3A:C4:1C
inet addr:192.168.2.9 Bcast:255.255.255.255 Mask:255.255.255.0
UP BROADCAST RUNNING MULTICAST MTU:1500 METRIC:1
RX packets:333 errors:0 dropped:0 overruns:0 frame:0
TX PACKETS: 43 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:90290 (88.1 Kib) TX bytes: 9799 (9.5 KiB)
Interrupt:10 Base address:0x2000

[/INDENT]
lo[INDENT]Link encap:Local loopback
inet addr:127.0.0.1 Mask:255.0.0.0
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:2 errors:0 dropped:0 overruns:0 frame:0
TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:176 (176.0 b) TX bytes:176 (176.0 b)
[/INDENT]
[/INDENT]

If there are any typographical errors there, it is because I cannot ssh into or out of this maligned machine.

Thank you in advance for any help you may provide.  

I will continue searching for solutions myself as well.

---

### Post by dataw0lf on 2006-11-20
What is contained in your /etc/resolv.conf?

(this is where your domain nameserver ips should be contained)

Oh, and by the way, you wouldn't be using an Actiontec router, would you?

---

### Post by daverice on 2006-11-20
All that my resolv.conf file says is 
[INDENT]nameserver 192.168.2.1[/INDENT]

That is the IP address of my router and it is an Airport Extreme.  

Thanks for the question.  

What should I do now?

---

### Post by dataw0lf on 2006-11-20
Did your ISP give you any DNS nameservers?  Check your router configuration for the IPs of these.  What nameservers are you using on the other machine?

---

### Post by stream303 on 2006-11-21
The easiest solution if you are running dhcp is to place your isp's dns servers into your router's setup page.

Failing that, you can force the inclusion of your isp's nameservers into /etc/resolv.conf by editing the prepend line of /etc/dhcp3/dhclient.conf

This thread might help (although I don't use OpenDNS, just my isp's nameservers)

[http://www.ubuntuforums.org/showthread.php?t=282034&highlight=resolv.conf](http://www.ubuntuforums.org/showthread.php?t=282034&highlight=resolv.conf)

---

