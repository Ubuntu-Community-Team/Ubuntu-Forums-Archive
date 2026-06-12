---
title: "WEP not working on Intel 3945ABG"
date: 2007-05-14
forum: Networking &amp; Wireless
---

### Post by QuartersMostly on 2007-05-14
Hi everyone,

I just got a new laptop and installed Feisty Kubuntu (Vista is actually as much of a hassle as people say it is). Unfortunately, I'm unable to get wireless working with WEP enabled on my router. I know the wireless card works properly because my neighbor is temporarily kindly supplying me with unsecured wireless access so that I can post this. 

I've read a bunch of posts about the card, and none of the suggestions I've encountered have helped. I admit that I'm probably doing something incredibly stupid. I have linux-restricted-modules installed. Here's the output of sudo lshw -C network:

```
paul@taquito:~$ sudo lshw -C network
Password:
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth1
       version: 02
       serial: 00:19:d2:d1:e1:42
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.0mp firmware=14.2 1:0 () ip=192.168.1.103 latency=0 link=yes multicast=yes wireless=IEEE 802.11b
       resources: iomemory:d8000000-d8000fff irq:16
  *-network
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@05:00.0
       logical name: eth0
       version: 00
       serial: 00:1b:24:30:3d:f5
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.15-k2-NAPI firmware=0.5-1 latency=0 link=no multicast=yes port=twisted pair
       resources: iomemory:da000000-da01ffff ioport:4000-401f irq:18

```

And a portion of sudo iwlist eth1 scan:

```
          Cell 03 - Address: 00:15:05:EC:94:D5
                    ESSID:"burrito"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:3
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=84/100  Signal level=-49 dBm  Noise level=-49 dBm
                    Extra: Last beacon: 112ms ago

```

Any help would be greatly appreciated. Maybe this is just a sign that I should use WPA instead.

---

### Post by b_chris on 2007-05-15
Hey I'm havign trouble too, I get the following.... I notice where it says 'wireless' mine is unassociated where as yours is not.... how'd you do this??


*-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth1
       version: 02
       serial: 00:13:02:1f:f2:66
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.0mp firmware=14.2 1:0 () latency=0 link=no multicast=yes wireless=unassociated
       resources: iomemory:edf00000-edf00fff irq:21

---

### Post by QuartersMostly on 2007-05-15
Hmm, I wish I could tell you how I made mine say wireless 802.11b. But I really didn't do anything. If I had to guess, I would say that maybe you're missing a driver? Maybe even try doing a sudo apt-get update? Hopefully someone with some knowledge will chime in.

---

### Post by chili555 on 2007-05-15
Connecting should be as easy as:```
sudo iwconfig eth1 essid burrito
sudo iwconfig eth1 key 0123456789abcdef
sudo dhclient eth1
```Sometimes the WEP key will connect if it followed by the word 'restricted' or 'open' after the key, thus:```
sudo iwconfig eth1 key 0123456789abcdef open
```Also, be sure you have the hex key; if you are using ASCII, prepend the key with s: like this:```
sudo iwconfig eth1 key s:mylilkey
```Finally, *iwconfig* seems to want lower case letters and not caps.

---

### Post by QuartersMostly on 2007-05-15
Aha! Thanks Chili! I'll have to try this as soon as I get home from work. I've read a bunch of your posts before, and even tried exactly what you have above based on your previous recommendation. But I used caps in my key when I tried it. I did try using lower case letters when I was using Knetworkmanager, but I've read that there are a bunch of problems with that app. I'll let you know how it goes...

---

### Post by b_chris on 2007-05-15
What do you type to generate the WEP key??

---

### Post by chili555 on 2007-05-15
> What do you type to generate the WEP key??Generally, on the administration page of your router, you may see a place to type in your choice of a passphrase, such as 'ilovecoldbeer' or 'mysecretkey' and a proper WEP key will be generated. Attached is an example.

---

### Post by b_chris on 2007-05-15
Ok Chilli, I did what you wrote and got this.......

There is already a pid file /var/run/dhclient.pid with pid 9818
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:13:02:1f:f2:66
Sending on   LPF/eth1/00:13:02:1f:f2:66
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.



I obtained my WEP key from [HERE]("http://www.andrewscompanies.com/tools/wep.asp")

---

### Post by chili555 on 2007-05-15
b_chris-
You are quite certain you have the exact same key in your router as what you typed into *iwconfig?* You double-checked?

---

### Post by NilsE on 2007-05-15
The best way to generate a key is to type something like your password into the pass phrase box on the router and then take the hex key it generates in the router and use that as the key in the Ubuntu wireless config. Typing the same pass phrase in both places does not work since the algorithm is different.

---

### Post by b_chris on 2007-05-15
Hey,

Just did it again as ASCII:

chris@chris-laptop:~$ sudo iwconfig eth1 essid ****
chris@chris-laptop:~$ sudo iwconfig eth1 key s:ASCII Password
chris@chris-laptop:~$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 16791
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:13:02:1f:f2:66
Sending on   LPF/eth1/00:13:02:1f:f2:66
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


Same result....  Still no go.

---

### Post by b_chris on 2007-05-15
One more thing, the IT guys said it needs to be set to shared, not opwn.

---

### Post by chili555 on 2007-05-15
If you are using shared key in your router, then you must add the suffix 'restricted' thus:```
sudo iwconfig eth1 key 0123456789abcdef restricted
```Also, the key in your router is either hex or ASCII, it isn't both. That's why I asked:> You are quite certain you have the exact same key in your router as what you typed into iwconfig?

---

### Post by b_chris on 2007-05-15
The IT guy said I could enter either the password or a hex version of it, either would work.

---

### Post by b_chris on 2007-05-15
Chili555, you are GOLD, after I put restricted at the end....  ALL systems are GO!!

---

### Post by NilsE on 2007-05-16
> **b_chris said:**
> Hey,

Just did it again as ASCII:


No DHCPOFFERS received.
No working leases in persistent database - sleeping.


Same result....  Still no go.
No DHCPOFFERS was because you did not authenticate. This will make you look like you are connected but you are only loosely associated. 

You need to use the hex password generated at the router and use that as the hex password in Ubuntu.  Also make sure the key size (64, 128, etc) generated at the router matches the input size.

---

### Post by QuartersMostly on 2007-05-16
I only tried for a minute last night, but I didn't have any luck. But I still think what Chili and others have written is correct and I'm just misunderstanding my router's interface or something. I'll try it out again tonight.

---

### Post by QuartersMostly on 2007-05-16
It looks like everything is working now. I modified the /etc/network/interface file and did a sudo bash /etc/init.d/networking restart and it seemed to work.

I just wanted to add that Knetworkmanager is an awful, awful program. When I connected to a neighbor's router, I was not able to disconnect through the app. And after I messed around with the manual configuration mode there was no way to swtich back to the regular mode. Not to mention the fact that it didn't work at all. I hope someone retools it a bit soon.

---

