---
title: "Network Nightmare"
date: 2008-06-23
forum: Networking &amp; Wireless
---

### Post by neonkevo on 2008-06-23
hi

I'm really hoping someone can give a linux n00b a hand here. I have a very old pc that i decided to install xubuntu on. Everything works great except for networking/internet. 

The original NIC i had in here was a DEC/DECchip 21140 FasterNet card (tulip). I have tried roaming and forcing dhcp and nothing seems to work. I then switched over to a 3com 3c905 card and i experience the same issues. 

I can't seem to find any help with this problem at all. Any info you guys can give me would be greatly appreciated.

---

### Post by neonkevo on 2008-06-24
anyone?

This is the ifconfig output for both cards

> @xubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:29:00:ec:0c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:1 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:3 Base address:0xdc00 

eth1      Link encap:Ethernet  HWaddr 00:60:08:5a:24:d6  
          inet6 addr: fe80::260:8ff:fe5a:24d6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:13 dropped:0 overruns:0 frame:18
          TX packets:107 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1140 (1.1 KB)  TX bytes:20830 (20.3 KB)
          Interrupt:10 Base address:0xdf00 

eth1:avahi Link encap:Ethernet  HWaddr 00:60:08:5a:24:d6  
          inet addr:169.254.6.61  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:10 Base address:0xdf00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:130 errors:0 dropped:0 overruns:0 frame:0
          TX packets:130 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9444 (9.2 KB)  TX bytes:9444 (9.2 KB)


---

### Post by pokipoki08 on 2008-06-24
Please post the output of these commands

```
dmesg | grep eth
cat /etc/network/interfaces
cat /var/log/messages | grep eth
```

---

### Post by neonkevo on 2008-06-24
> **pokipoki08 said:**
> Please post the output of these commands

```
dmesg | grep eth
cat /etc/network/interfaces
cat /var/log/messages | grep eth
```


thanks so much for the quick response. this is the output i get from those commands.

> 

[   40.397018] eth1: Digital DS21140 Tulip rev 32 at Port 0xdc00, 00:e0:29:00:ec:0c, IRQ 3.
[   43.523747] Driver 'sd' needs updating - please use bus_type methods
[   43.524560]  sda: sda1 sda2 <<4>Driver 'sr' needs updating - please use bus_type methods
[   69.901204] udev: renamed network interface eth1 to eth0
[   69.908289] udev: renamed network interface eth0_rename to eth1
[   89.456803] eth1:  setting full-duplex.
[  122.084183] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  132.248365] eth1: no IPv6 routers present

@xubuntu:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback


---

### Post by pokipoki08 on 2008-06-24
```
gksudo gedit /etc/network/interfaces
```

Add & save [COLOR="RoyalBlue"]text in blue[/COLOR] below into file /etc/network/interfaces

```
[COLOR="Blue"]auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp[/COLOR]
```

Run these commands at the terminal

```
sudo /etc/init.d/networking restart
ifconfig
```

If all is well, you should see an IP address in eth0 or eth1.

---

### Post by neonkevo on 2008-06-24
> **pokipoki08 said:**
> ```
gksudo gedit /etc/network/interfaces
```

Add & save [COLOR="RoyalBlue"]text in blue[/COLOR] below into file /etc/network/interfaces

```
[COLOR="Blue"]auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp[/COLOR]
```

Run these commands at the terminal

```
sudo /etc/init.d/networking restart
ifconfig
```

If all is well, you should see an IP address in eth0 or eth1.

thanks again for your help.

I tried > gksudo gedit /etc/network/interfaces  but nothing happends. Out of curiosity i tried the command without using gksudo and it says i do not have gedit installed. I tried using to install it but i guess its not anywhere on my machine. :(

---

### Post by pokipoki08 on 2008-06-24
Right click the file in File Manager & select **"Open as Administrator"**

---

### Post by neonkevo on 2008-06-24
> **pokipoki08 said:**
> Right click the file in File Manager & select **"Open as Administrator"**

i don't see that option when i right click on it :(

---

### Post by LeChacal on 2008-06-24
Because you are using xubuntu you don't have gedit and i don't think gksudo ether so you need to do this from the command line.

```
sudo nano /etc/network/interfaces
```

Then add 

```
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
```

Just like pokipoki08 said to do.

---

### Post by pokipoki08 on 2008-06-24
```
sudo nano /etc/network/interfaces
```

^ = CTRL key

When prompted for the password, input the password of the 1st user account created when you install Ubuntu on this machine.

---

### Post by neonkevo on 2008-06-24
> **LeChacal said:**
> Because you are using xubuntu you don't have gedit and i don't think gksudo ether so you need to do this from the command line.

```
sudo nano /etc/network/interfaces
```

Then add 

```
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
```

Just like pokipoki08 said to do.

> **pokipoki08 said:**
> ```
sudo nano /etc/network/interfaces
```

^ = CTRL key

When prompted for the password, input the password of the 1st user account created when you install Ubuntu on this machine.

thanks for the help. I managed to edit the file using nano. saved and went ahead and used the other command mentioned. unfortunately, network still isnt working for either card. this is the output the last command gave me.

> sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:e0:29:00:ec:0c
Sending on   LPF/eth0/00:e0:29:00:ec:0c
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
grep: /etc/resolv.conf: No such file or directory
There is already a pid file /var/run/dhclient.eth1.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:60:08:5a:24:d6
Sending on   LPF/eth1/00:60:08:5a:24:d6
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
grep: /etc/resolv.conf: No such file or directory
                                                                         [ OK ]


---

### Post by Iowan on 2008-06-24
Repost results of **ifconfig** and contents of freshly edited  **/etc/network/interfaces** file.

---

### Post by neonkevo on 2008-06-24
> **Iowan said:**
> Repost results of **ifconfig** and contents of freshly edited  **/etc/network/interfaces** file.

thanks for your response. here is my ifconfig output.

> eth0      Link encap:Ethernet  HWaddr 00:e0:29:00:ec:0c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:1 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:5426 (5.2 KB)
          Interrupt:3 Base address:0xdc00 

eth1      Link encap:Ethernet  HWaddr 00:60:08:5a:24:d6  
          inet6 addr: fe80::260:8ff:fe5a:24d6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:50 errors:130 dropped:0 overruns:0 frame:204
          TX packets:314 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13510 (13.1 KB)  TX bytes:100480 (98.1 KB)
          Interrupt:10 Base address:0xdf00 

eth0:avahi Link encap:Ethernet  HWaddr 00:e0:29:00:ec:0c  
          inet addr:169.254.5.31  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:3 Base address:0xdc00 

eth1:avahi Link encap:Ethernet  HWaddr 00:60:08:5a:24:d6  
          inet addr:169.254.6.61  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:10 Base address:0xdf00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:202 errors:0 dropped:0 overruns:0 frame:0
          TX packets:202 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15832 (15.4 KB)  TX bytes:15832 (15.4 KB)

interfaces file

> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp


---

### Post by neonkevo on 2008-06-24
bump

---

### Post by Iowan on 2008-06-24
To what are these cards connected (ie. what *should* be providing DHCP address)?

---

### Post by neonkevo on 2008-06-24
> **Iowan said:**
> To what are these cards connected (ie. what *should* be providing DHCP address)?


they are hooked up to a linksys wrt router.

---

### Post by pokipoki08 on 2008-06-24
Does your router enforce mac address filtering?

Can you check your router if it receives any dhcp requests from your 2 nics?

---

### Post by neonkevo on 2008-06-25
> **pokipoki08 said:**
> Does your router enforce mac address filtering?

Can you check your router if it receives any dhcp requests from your 2 nics?


thanks for your response. 

No, there is no mac address filtering on this router. I have hooked up countless windows machines on it not including my main vista machine. They have always managed to get on the net on their first attempt.

I checked the routers logs. Nothing at all is coming in from the xubuntu machine. :(

---

### Post by neonkevo on 2008-06-25
bump, any other suggestions?

---

### Post by neonkevo on 2008-06-25
update:
just tried an old set of xubuntu and kubuntu 6.06 livecds and networking doesn't work on them either.

---

### Post by ZariduOmega on 2008-06-25
I am having a very similar problem with my wireless network.  When I first installed Ubuntu 8.04 about a week ago, my wireless network worked perfectly fine (with multiple routers, including the one I am using now).  I am currently using Windows XP on the same computer with the same router to access the network, so I've ruled out hardware issues.  A few days ago I did fiddle around with ifconfig and /etc/network/interfaces to try to set up a virtual alias so that my roommate could get a better connection to our router.  I know little about networks so it was mostly a learning experience, but I was very careful not to do anything that couldn't be easily reset to defaults.

Then, two days ago my wireless network stopped working completely.  I had no problem up to this point, even with my modifications, so I found this rather strange.  I ran ifconfig, iwconfig, tried modified /etc/network/interfaces to set up the wireless device for dhcp and nothing has worked.

The diagnostics I ran give very similar output to neonkevo's:
> **ifconfig output:**
eth0      Link encap:Ethernet  HWaddr 00:11:43:78:b7:07   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:19  
 
eth1      Link encap:Ethernet  HWaddr 00:12:f0:41:39:85   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:32323 errors:9 dropped:9 overruns:0 frame:0 
          TX packets:2290 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:1440 (1.4 KB) 
          Interrupt:18 Base address:0x4000 Memory:dcffd000-dcffdfff  
 
eth2      Link encap:Ethernet  HWaddr 00:05:1b:ff:f1:d2   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
 
eth1:avahi Link encap:Ethernet  HWaddr 00:12:f0:41:39:85   
          inet addr:169.254.6.51  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          Interrupt:18 Base address:0x4000 Memory:dcffd000-dcffdfff  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:3175 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:3175 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:163249 (159.4 KB)  TX bytes:163249 (159.4 KB)
> **iwconfig output**
lo        no wireless extensions. 
 
eth0      no wireless extensions. 
 
eth1      unassociated  ESSID:""  Nickname:"linksys" 
          Mode:Managed  Channel=0  Access Point: Not-Associated    
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0   
          Retry limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 
 
eth2      no wireless extensions.
> **sudo lshw -C network output:**
  *-network:1 
       description: Wireless interface 
       product: PRO/Wireless 2915ABG Network Connection 
       vendor: Intel Corporation 
       physical id: 3 
       bus info: pci@0000:03:03.0 
       logical name: eth1 
       version: 05 
       serial: 00:12:f0:41:39:85 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 link=no maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=unassociated 

As you can see, "eth1" is my wireless interface.  A few things that I've noticed which may be helpful in solving this problem:
[LIST]
[*]When I attempt to set up my eth1 interface using xnetcardconfig or through manually editing the /etc/network/interfaces entry for dhcp, it will not modify the "eth1" entry in ifconfig.  Instead, as can be seen above, it creates what I can only assume is an alias or virtual interface titled "eth1:avahi".  neonkevo also seems to have this entry, so it may be related.
[*]When I use dhclient to set up the "eth1" interface according to kevdog's guide, it does not receive and give the interface an IP.  It outputs the following lines after working: > No DHCPOFFERS received.
No working leases in persistent database - sleeping.
This also appears to affect neonkevo.
[*]I can see the ESSID of my router and attempt to connect to it using Network Manager, but it simply hangs and is unable to acquire the network key.  Disabling roaming and manually attempting to connect does not solve this problem.
[/LIST]

I am very curious about what may be causing this problem.  First of all, neonkevo: what version of xUbuntu are you running?  Is it 8.04 (Hardy)?  It might be a bug with Hardy that no one has picked up on yet.

Any ideas?

---

### Post by neonkevo on 2008-06-25
> **ZariduOmega said:**
> 
I am very curious about what may be causing this problem.  First of all, neonkevo: what version of xUbuntu are you running?  Is it 8.04 (Hardy)?  It might be a bug with Hardy that no one has picked up on yet.

Any ideas?

i'm running Xubuntu 8.04 on this machine. Earlier today i tried xubuntu and kubuntu 6.06 cds that i had laying around in my collection.

I just had this old pc laying around and i wanted to use it as a backup for my every day desktop. At this point if i can't get this sorted it will either get another OS or get torn down.

---

### Post by ZariduOmega on 2008-06-25
> **neonkevo said:**
> i'm running Xubuntu 8.04 on this machine. Earlier today i tried xubuntu and kubuntu 6.06 cds that i had laying around in my collection.

I just had this old pc laying around and i wanted to use it as a backup for my every day desktop. At this point if i can't get this sorted it will either get another OS or get torn down.

What network hardware and drivers are you using?  Use the command:
```
sudo lshw -C network
```
and post the output for the wireless interface.  I'd be curious to know if there are any similarities between our systems.

---

### Post by neonkevo on 2008-06-25
> **ZariduOmega said:**
> What network hardware and drivers are you using?  Use the command:
```
sudo lshw -C network
```
and post the output for the wireless interface.  I'd be curious to know if there are any similarities between our systems.


I'm not on wireless. This is a wired connection. I also removed one of the NICs last night while experimenting.

> *-network               
       description: Ethernet interface
       product: 3c905 100BaseTX [Boomerang]
       vendor: 3Com Corporation
       physical id: 9
       bus info: pci@0000:01:09.0
       logical name: eth1
       version: 00
       serial: 00:60:08:5a:24:d6
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full latency=64 link=yes maxlatency=8 mingnt=3 module=3c59x multicast=yes port=MII speed=100MB/s


---

### Post by neonkevo on 2008-06-25
bump

can anyone help?

---

### Post by neonkevo on 2008-06-26
ok well i bit the bullet and installed windowsxp on this machine. To my surprise, the 3com card refused to work. It suffered from the same issues that it did with xubuntu. It refused to connect and claimed a network cable was unplugged. As for the other card, it did the same. The difference however is, when i changed the second card to 10baseT, it worked.

Now my question is, can i force it to 10base in xubuntu? This PC is really old (700mhz) so i would rather run xubuntu on this machine.

---

### Post by neonkevo on 2008-06-26
got it fixed using the mii-tool command. Thank you everyone for your help. I really appreciate it! :)

---

