---
title: "Gnome network manager is connected but no internet??"
date: 2007-10-06
forum: Networking &amp; Wireless
---

### Post by mattgaunt on 2007-10-06
Hey everyone

Im using feisty fawn and i can connect to my router using the mac address filtering

Everything works fine with windows, when i connect using gnome network manager it says i can connect and have about 50% signal and the router registers the computer as being attached but the internet doesn't work.

If i right click on the networking logo and click connection information it says there is no ip address.

Does anyone know how i could fix this??

Thanks in advance

Matt

---

### Post by Lambert on 2007-10-07
> **mattgaunt said:**
> Hey everyone

Im using feisty fawn and i can connect to my router using the mac address filtering

Everything works fine with windows, when i connect using gnome network manager it says i can connect and have about 50% signal and the router registers the computer as being attached but the internet doesn't work.

If i right click on the networking logo and click connection information it says there is no ip address.

Does anyone know how i could fix this??

Thanks in advance

Matt

You are attached to your router but the next step of assigining an ip hasn't happened for what ever reason. Does your router act as a dhcp server? If so try this command from a terminal.

```

sudo dhclient 

```

check to see if you are assigned an ip now.

---

### Post by mattgaunt on 2007-10-07
cheers lambert ill giv it a go and let u kno what happens

Matt

---

### Post by mattgaunt on 2007-10-08
I did the sudo dhclient command and it started to work but then stopped, i repeated it, it started to work again and then stopped.

Now at the end of each time it just says the stuff and at the end the following

```
No DCHPOFFERS received.
No working leases in persistent database - sleeping
```

My computer also doesn't to connect to the wireless network without me playing around with the manual configuration and then gnome network manager.

It might just be me but gnome network manager and ubuntu's old network manager seem to conflict a little bit.

Any ideas what i should try or do?

Matt

---

### Post by Lambert on 2007-10-08
The DHCP server is not issuing you an ip offer for what ever reason. Try setting a static ip.

from terminal

```

sudo ifdown wlan0

```

replace wlan0 with your interface.

Open the file /etc/network/interfaces and edit it like this. You will need to do this via root permissions.

auto wlan0
iface wlan0 inet static
        address 192.168.0.10
        netmask 255.255.255.0
        gateway 192.168.0.1

the numbers after address, replace with whatever is in your subnet and make sure it's not a number in you dhcp address pool, this will prevent another machine connecting and getting assigned the same address.

if your gateway is a different address, then change this to match.

Save the file and run this command

```

sudo ifup wlan0

```

test connection now.

You're using mac filtering. Are you using any other encryption/security measures?

---

### Post by mattgaunt on 2007-10-08
This is what i get from dhclient

```
:~$ sudo dhclient 
There is already a pid file /var/run/dhclient.pid with pid 12343 
killed old client process, removed PID file 
Internet Systems Consortium DHCP Client V3.0.4 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit http://www.isc.org/sw/dhcp/ 

Listening on LPF/ra0/00:11:50:90:c7:41 
Sending on   LPF/ra0/00:11:50:90:c7:41 
Listening on LPF/eth1/00:0f:ea:64:68:c3 
Sending on   LPF/eth1/00:0f:ea:64:68:c3 
Listening on LPF/eth0/00:0f:ea:5d:6d:2b 
Sending on   LPF/eth0/00:0f:ea:5d:6d:2b 
Sending on   Socket/fallback 
DHCPREQUEST on ra0 to 255.255.255.255 port 67 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4 
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6 
DHCPREQUEST on ra0 to 255.255.255.255 port 67 
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14 
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 4 
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 10 
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7 
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 14 
No DHCPOFFERS received. 
No working leases in persistent database - sleeping. 
```

And i just typed ifconfig and got the following - really weird cos i have 2 ethernet ports and one wireless port

```
:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:0F:EA:5D:6D:2B  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:16 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr 00:0F:EA:64:68:C3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:19 

eth0:avah Link encap:Ethernet  HWaddr 00:0F:EA:5D:6D:2B  
          inet addr:169.254.5.134  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          Interrupt:16 Base address:0x6000 

eth1:avah Link encap:Ethernet  HWaddr 00:0F:EA:64:68:C3  
          inet addr:169.254.8.127  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:160 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:160 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:15658 (15.2 KiB)  TX bytes:15658 (15.2 KiB) 

ra0       Link encap:Ethernet  HWaddr 00:11:50:90:C7:41  
          inet6 addr: fe80::211:50ff:fe90:c741/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:425 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:326347 errors:17 dropped:17 overruns:0 carrier:0 
          collisions:256 txqueuelen:1000 
          RX bytes:180953 (176.7 KiB)  TX bytes:14371473 (13.7 MiB) 
          Interrupt:19 

ra0:avahi Link encap:Ethernet  HWaddr 00:11:50:90:C7:41  
          inet addr:169.254.6.195  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          Interrupt:19 
```

Also i dont know what ip address and what gateway and subnet address to use

Is there anyway to sort of reset all the network connections so i can start fresh, ill have a look at your suggestion and try to make it work

The router only uses MAC Filtering there is no security or WEP keys

Matt

---

### Post by Lambert on 2007-10-08
Ok so try this from terminal

```

sudo ifdown eth0
sudo ifdown eth1
sudo ifdown ra0
sudo ifup ra0
sudo dhclient ra0

```

You have a device with a ralink chipset in it. network manager doesn't work that well with it.

The next release of gutsy gibbon 7.10 has improved support for these devices. Hopefully everything will work better for you.

Do a search on this forum for RutilT. It's another application for managing wireless connections, specifically for this chipset. That should help you.

don't worry about my last post suggesting static ip, try what I gave you in this post.

---

### Post by mattgaunt on 2007-10-08
cheers lambart it seems to be working jus using ifdown and ifup but im looking into installing RutilT

Thanks again

Matt

---

