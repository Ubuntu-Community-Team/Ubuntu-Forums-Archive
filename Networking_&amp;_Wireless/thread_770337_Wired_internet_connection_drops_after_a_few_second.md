---
title: "Wired internet connection drops after a few seconds"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by skip-9456 on 2008-04-27
Hi 
Linux newbie here.  (But working with computers long enough to remember DOS.)

I have just installed Hardy Heron using WUBI.  It looks great but I am having problems with the internet connection.
I have a wired connection to a MAXg DSL Gateway.  It works fine in XP.
In Ubuntu, it sometimes works for a few seconds on booting and then it drops.
I can always see the gateway and log in to it. 
The gateway thinks it is connected to the internet fine.
I can also connect to the internet with another XP computer through the same gateway whilst having problems on Ubuntu. 
I can also connect from this computer whilst using XP with no problems.

If I go into the Network Settings GUI (top left on install). Unlock it, select the wired connection, select properties, disable roaming mode, select DHCP, press ok. Wait for it to reconfigure. select properties again, select roaming, select ok, wait for it to reconfigure. Now I *occasionally* have a few seconds of internet connection before it drops again.

When the connection is down, if I ping anything beyond the gateway I get nothing.
It can not see the DNS server, despite this pointing at the gateway and the gateway being pingable.

ifconfig gives me the following.

eth0      Link encap:Ethernet  HWaddr 00:01:2e:10:99:ea  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::201:2eff:fe10:99ea/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1112 (1.0 KB)  TX bytes:7094 (6.9 KB)
          Interrupt:20 Base address:0xde00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1060 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1060 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:53000 (51.7 KB)  TX bytes:53000 (51.7 KB)

If I go into Network Tools and select the ethernet card and click configure I get an error saying that 'The interface does not exist'. No idea what this means.

According to Ubuntu my ethernet card is a Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
According to XP my ethernet card is a Realtek RTL8139/810x Family Fast Ethernet NIC

Can anyone help please, I would really like to get Ubuntu up and running.

---

### Post by skip-9456 on 2008-04-27
Having read other posts, thought I would post some extra details.

I tried typing 

> sudo dhclient eth0 

into the terminal as suggested on another thread.
It returned:

> Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:01:2e:10:99:ea
Sending on   LPF/eth0/00:01:2e:10:99:ea
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPOFFER of 192.168.1.2 from 192.168.1.1
DHCPREQUEST of 192.168.1.2 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.2 from 192.168.1.1
bound to 192.168.1.2 -- renewal in 36639 seconds.

Internet still down.


Also, another post requested contents of etc/network/interfaces
which reads

> auto lo
iface lo inet loopback

---

### Post by skip-9456 on 2008-04-27
I've almost fixed it.

No idea why the dns is not working, but changing it to the openDNS server has fixed it.

I did this by removing the DNS entry in the Network Settings GUI and adding a new one for 208.67.222.222

This works, but the setting is forgotten every time I reboot, can someone tell me how to make it permanent ( I imagine this should be easy )

---

### Post by ShamanSTK on 2009-01-20
Fixed it! After months of trying to figure it out, the solution isn't any configuration. The gnome network manager is just buggy with some hardware. Switch to Wicd. I did and end of problems immediately.

---

