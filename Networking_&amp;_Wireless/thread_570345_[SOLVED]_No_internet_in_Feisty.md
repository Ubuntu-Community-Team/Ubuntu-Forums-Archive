---
title: "[SOLVED] No internet in Feisty"
date: 2007-10-08
forum: Networking &amp; Wireless
---

### Post by gfixler on 2007-10-08
This has been a frustrating night. I had lots of work to do today, but instead have spent at least 6 hours trying to get my suddenly broken Feisty internet to work again. It started when I tried to play a DVD, and couldn't, and remembered the heavily ignored DVD drive has pretty much never worked right in Feisty - none have - that's another whole issue - and booted up in WinXP to try it there. It didn't work in there, either. After fiddling in the box for a bit, and pulling cables to the DVD drive while the machine was still on (I state this, in case the problem could be that this damaged the mobo somehow), I tried to go back into Ubuntu for something, and the net wasn't working. I've read at least 10 similar problems here in the forum, and most of the replies in them all, but no one seems to get near my own problem. 

Here's some info from System->Administration->Network
```
System->Administration->Network
Network Settings:
	Location: box is empty - no choices available
	Connections:
		Configuration: DHCP
		Enable roaming mode: unchecked
	DNS:
		DNS Servers: 2 listed here
		Search Domains: none
```

More info gleaned from System->Administration->Network Tools
```
System->Administration->Network Tools
Devices:
	Network device:
		Loopback Interface (lo)
			IP Information:
				IPv4 etc...
				IPv6 etc...
		Ethernet Interface (eth0)
			IP Information:
				IPv6 etc...
					IP Address is fe80::... (all hex numbers)
			Interface Information:
				all of this stuff says "not available"
			Interface Statistics:
				over 800 transmitted packages since I logged in
				nothing received
		Ethernet Interface (eth0:avahi)
			IP Information:
				IPv4 etc...
```

Some CLI info (with judicious sprinkling of x's, because I don't know what I shouldn't post):

```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet6 addr: xxxx::xxx:xxxx:xxxx:xxxx/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1045 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:70936 (69.2 KiB)
          Interrupt:16 

eth0:avah Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:169.254.6.29  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:848 errors:0 dropped:0 overruns:0 frame:0
          TX packets:848 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:71654 (69.9 KiB)  TX bytes:71654 (69.9 KiB)

$ sudo ifup eth0
ifup: interface eth0 already configured

$ dmesg | tail
...
[  107.678129] eth0: no IPv6 routers present (this was all that seemed relevant)
```

Firestarter works, and says the firewall is active. In its Preferences, under Firewall->Network Settings it shows the Detected devices(s) as Ethernet device (eth0).


Where do I go from here? What info can you guys use to help me? I've spent a year in Ubuntu, starting in Dapper, and have learned quite a bit, and can diagnose, and fix a lot of problems, but regardless of OS, all of this net stuff boggles me. Almost none of the info above means anything to me, and anything net-related has simply been me copying some diagnostic stuff I've seen in other threads.

Thanks for any help. This net simply refuses to come back. As I said, the net works on the same machine booted into XP, making it at the very least good for something ;)

Thanks!

---

### Post by Lambert on 2007-10-08
Not sure what eth0 is but it could be your wireless or wired nic.

Is your wireless a pci card?
 
Run this command and look for it in the output and post it here. If you need, you can post the entire output. This command identifies all the hardware pieces in your pc. We want to see if it is being recognized by the kernel.

```

sudo lshw

```

---

### Post by gfixler on 2007-10-08
> **Lambert said:**
> Not sure what eth0 is but it could be your wireless or wired nic.

Is your wireless a pci card?
 
Run this command and look for it in the output and post it here. If you need, you can post the entire output. This command identifies all the hardware pieces in your pc. We want to see if it is being recognized by the kernel.

```

sudo lshw

```

Thanks, Lambert. I'll see what that gives me when I get home tonight. eth0 is the ethernet card. It's what's listed in the network connections. There's probably more to it, but again, I'm very underknowledged about this stuff. I don't have any wireless at all. In fact, I don't even have my non-wireless router hooked up at the moment. I'm one of those old-fashioned types who doesn't get what all the fuss is regarding wifi.

---

### Post by Lambert on 2007-10-08
Ok, reading too many posts sometimes make things run together. 

So you have a wired nic but it won't connect to your router.


if you run the following commands what do you get.

```

sudo ifdown eth0

sudo ifup eth0

sudo dhclient eth0

```

the dhclient command might not be necessary, it should be run when ifup is run but just a double check. You can check internet connection between running ifup and dhclient commands.

---

### Post by gfixler on 2007-10-08
Well, it's frustrating, but after so many hours (6+) of getting nothing last night, turning off the PC, going to work, coming home, and turning it back on, the internet works in Feisty. This isn't the first time I've been able to connect in XP, but not in Ubuntu, but it's by far the longest. Usually it's more like 20 minutes or so. What could be causing this? I've had ideas ranging from the modem overheating, to Verizon blocking Linux (or some aspect of its connecting) temporarily, and everything in between.

I would also like to thank you for following up with me, and trying to help me figure it out. I appreciate it.

---

### Post by noob12 on 2007-10-09
Can you post the type of network card you have?  (The output of **lspci -nn**)

---

### Post by gfixler on 2007-10-09
> **noob12 said:**
> Can you post the type of network card you have?  (The output of **lspci -nn**)

Sure. This is what I get:
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5789 Gigabit Ethernet PCI Express [14e4:169d] (rev 11)

It's built into my little Shuttle SB95Pv2.

---

