---
title: "eth0 isup but not connection"
date: 2006-12-19
forum: Networking &amp; Wireless
---

### Post by hashimoto on 2006-12-19
Hi,

Something strange is happening with my network connection: It worked all fine this morning, but now I can't read email or surf the web. No updates or anything else that could cause this. Luckily my laptop seems to be OK so I can at least ask for help.

Ifconfig seems to be OK and if I run ifdown eth0 and then ifup eth0, dhcp correctly  assigns an ip address and my ISP confirms that it is correct. Yet, this evening I cant read email (Thunderbird) or surf the web (Firefox). And I can't even ping; if I try the cursor just blinks and after a long while tells "Unknown host xxx". 

Running Edgy, no router, just a simple ADSL modem.

I'm begging for help.

EDIT: Just great! This morning I booted my laptop to see any replies to this thread but even that is now non-connecting... What is going on? Absolutely no updates, software installation, change of settings or messing with terminal/sudo (also running Edgy).

---

### Post by hashimoto on 2006-12-20
Here is my ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:40:05:E4:B0:6A  
          inet addr:xx.xxx.xx.xxx  Bcast:xx.xxx.xx.xxx  Mask:255.255.224.0
          inet6 addr: xxxx::xxx:xxx:xxxx:xxxx/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19 errors:0 dropped:0 overruns:0 frame:0
          TX packets:493 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2495 (2.4 KiB)  TX bytes:109708 (107.1 KiB)
          Interrupt:10 Base address:0xd000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:191 errors:0 dropped:0 overruns:0 frame:0
          TX packets:191 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17182 (16.7 KiB)  TX bytes:17182 (16.7 KiB)


Could this be an ipv6 problem as I seem to have inet6 addr assigned, too?

---

### Post by Iowan on 2006-12-20
> **hashimoto said:**
>  And I can't even ping; if I try the cursor just blinks and after a long while tells "Unknown host xxx". 
Can't ping by name or IP address?
IPv6 **might** cause problems w/ DNS, but dunno if it messes up pinging by IP address.

---

### Post by hashimoto on 2006-12-21
Iowan, thanks. Here is where I stand now:

Laptop: 
WAN is up again. Why, don't ask me; I did absolutely nothing but boot the system yesterday.

Desktop:
I disabled ipv6 on the desktop but that didn't help. I was able to ping my laptop in LAN but nothing in WAN (Not dns-servers by ip-number, nothing with name).

Frustrated, I decided to do a reinstall. (After all, I did compile some kernel modules and mess with the desktop otherwise so maybe I just broke something). Previously I have never had any problems with connections after a fresh install (Hoary, Warty, Dapper, Edgy, you name it). This time the problem still exists. I can still ping LAN, but WAN is dead. I seem to get the ip-address with "sudo ifup eth0" (though this command takes much longer to finish after acquiring the ip than on laptop)

All connections wired.

Please help!

---

