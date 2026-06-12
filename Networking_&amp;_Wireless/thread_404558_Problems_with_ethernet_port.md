---
title: "Problems with ethernet port"
date: 2007-04-08
forum: Networking &amp; Wireless
---

### Post by Intell on 2007-04-08
Hi Ubuntu Community,

I have problems connecting to the interenet, and I hope I can get some help here. I am on a brand new installation of Xubuntu, and I'm having problems connecting to the internet using a wired connection. I am on a RevB iMac (233 MHz). I have connected a cat5e cable from the computer to the router, but the internet connection does not work. I do know that the router does work, though. What is wrong with my internet connection?

Thank you in advance,
A Puzzled Xubuntu User

---

### Post by Intell on 2007-04-08
Hello. I have recently learned about ifconfig. If its output could help solve the problem, here it is:

```

eth0: Link encap:Ethernet HWaddr 00:05:02:AB:B4:4E
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:2116 (2.0 KiB)
Interrupt:42 Base address:0xa000

```

Would this information help solve the problem? Thanks!

---

### Post by klock on 2007-04-08
based on your ifconfig, your ethernet interface has not been assigned an i.p. address.

check your /etc/network/interfaces and see if your interface is dhcp or static.

If dhcp: check to make sure that your router is handing you out an ip address and also check to make sure that if it isnt, that you can set up your router to hand them out.

if you arent recieving an ip address, I would set mine to static and find my isp's dns servers, set those addressi in /etc/resolv.conf and your router as GATEWAY in your /etc/network/interfaces file.

---

### Post by Intell on 2007-04-08
My router does hand out IP addresses using DHCP, and I have tried chaning it to static with no luck. Something fishy seems to be going on with this ethernet controller, if you ask me. :(

---

### Post by klock on 2007-04-08
okay, this might sound a little strange.

for my gateway server, since my isp has a dhcp server for its clients, I have to reset my modem to gain an external ip for the gateway.

Try this.
-sudo ifdown eth0
-sudo ifup eth0

and if so, the router should hand out an ip adress to it.

If not, let me know what kind of router you have.

---

### Post by Intell on 2007-04-08
Resetting eth0 still does not seem to fix the problem with my old Netgear MR814 v2. :\ I know that the router's DHCP server does work on other computers, though. :)

---

### Post by Intell on 2007-04-09
Since my router doesn't hand out an IP to this computer, is it possible that my ethernet controller is dead? Even though the computer seems to be detecting the ethernet card, eth0, (or is it?) I think some part of it is dysfunctional. If my ethernet controller continues to not work, what would one recommend me do? Thanks!

Intell

---

### Post by Intell on 2007-04-09
I guess no one can help me with this problem. :(

---

### Post by RJARRRPCGP on 2007-04-09
*We need to know this, if you have Windows, does it work under Windows?*

---

### Post by Intell on 2007-04-09
Yes, it did work when I used Mac OS 8 on it (it is an iMac, like a previously stated).

---

### Post by Intell on 2007-04-10
From the responses I've heard (none in 24 hours), there isn't a fix. However, what is an **alternative**? Thanks!

---

### Post by chili555 on 2007-04-10
May seem too simple, but I haven't seen the answer yet. What is the output of:```
sudo dhclient eth0
```Thanks.

---

### Post by Intell on 2007-04-11
```

{snip}
Listening on LPF/eth0/00:05:02:ab:b4:4e
Sending on LPF/eth0/00:05:02:ab:b4:4e
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

---

### Post by Intell on 2007-04-13
The problem still persists. I would just like an alternative if wired ethernet doesn't work. Thank you. :) I just need support, as I've never run into a networking problem on Linux.

---

### Post by chili555 on 2007-04-14
Would you please run ```
sudo ethtool eth0
```and look at the end to see if a link is detected. This will help rule out the cable or router as a suspect. Ifconfig looks like any healthy perfectly working ethernet interface.

---

### Post by mellonGW on 2007-04-22
Same problem for me, I have and old imac 266mhz I believe, and the ethernet worked fine on ox10 and when I Finally installed ubuntu the ethernet wouldn't work. I can log onto my router and change settings but it just won't let me like connect to the internet.

---

