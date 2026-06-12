---
title: "wireless problem"
date: 2008-07-26
forum: Networking &amp; Wireless
---

### Post by qbox on 2008-07-26
Hi
I have Ubuntu 8.04 and 
0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
I install ndiswrapper and use windows drivers and everything work GREAT! Today when I start computer I connect to internet and surf the web but suddenly I got disconnected from the wifi AP. (AP is my own i dont use AP from another person) I use Network Manager to operate connections. After I got disconnected from the AP I cant connect again. I didnt install nothing I didnt do nothing at all. I just surf the web. When I use ifconfig command I didnt see wlan0 like before. Now I see two eth0 and eth1 controllers. I have only one before (eth0) I cant scan for networks with iwlist scan. But when I open the network manager I see diferent AP. But I cant connect to anyone.
Please HELP!!:confused:

---

### Post by qbox on 2008-07-26
Strange
I turn of and again turn on the computer. After booting I get connected automatically. But with ifconfig I didnt see wlan0 and I cant do iwlist scan. I see one eth0 who is not used and another eth1 which is connected do the internet. How can be this? What is the problem????:confused::confused::confused:
Please anyone.

---

### Post by Ayuthia on 2008-07-26
> **qbox said:**
> Strange
I turn of and again turn on the computer. After booting I get connected automatically. But with ifconfig I didnt see wlan0 and I cant do iwlist scan. I see one eth0 who is not used and another eth1 which is connected do the internet. How can be this? What is the problem????:confused::confused::confused:
Please anyone.

Sometimes the logical name of your wireless gets changed after you configure ndiswrapper.  The changes usually take place after you reboot.  So what happened here is that wlan0 was changed to eth1.  You should be able to scan wireless networks with eth1.

If you do get disconnected again, you might go to the Terminal and type dmesg.  It might provide a clue on what is happening.

---

### Post by qbox on 2008-07-26
Same problem Again

dmesg output:
```
.........
[ 1219.018724] CPU1: Temperature/speed normal
[ 1219.018739] CPU0: Temperature/speed normal
[ 1397.317640] Machine check events logged
[ 1616.448155] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 1627.409807] eth1: no IPv6 routers present

```

Now I start a game with wine. Railroad Tycoon Gold or something like that.

---

### Post by richardjennings on 2008-07-26
whilst looking for the cause of the problem, using:

```
sudo /etc/init.d/networking restart
```

may get your wireless working again without having to reboot.

---

### Post by richardjennings on 2008-07-26
can you post:

```
cat /etc/network/interfaces
```

---

### Post by qbox on 2008-07-27
To post when problem show up or when everything work fine?

When all work fine cat /etc/network/interfaces show

```
qbox@qbox:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

iface wlan0 inet dhcp
address 192.168
netmask 255.255.255.0
wireless-key s:qwasz
wireless-essid MKD

auto wlan0

qbox@qbox:~$ 

```

When problem show Up I will post again.

---

### Post by richardjennings on 2008-07-27
these lines ```
address 192.168
netmask 255.255.255.0
``` dont appear to be necessery. Comment them out with a hash (to make it easy to change back), restart networking and see if the problem is better.

to edit the file

```
sudo gedit /etc/network/interfaces
```
change:

address 192.168 
netmask 255.255.255.0

to:

#address 192.168
#netmask 255.255.255.0

save the file then:

```
sudo /etc/init.d/networking restart
```

any better?

---

### Post by darkshado on 2008-07-27
Well i have the same problem. I install my USB key with ndiswrapper (my USB key netgear WG111v3). Every think goes fine and after few minutes of surf on the web. I lost de connection and the "wlan0" just disapear.

---

### Post by richardjennings on 2008-07-27
do you use the dsl connection?

I would try changing:

auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

to:
#auto dsl-provider
#iface dsl-provider inet ppp
#pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
#provider dsl-provider


then restart networking again.

---

### Post by qbox on 2008-07-28
This line didnt help me alot...

```
qbox@qbox:~$ sudo /etc/init.d/networking restart
[sudo] password for qbox: 
 * Reconfiguring network interfaces...                                          dsl-provider: ERROR while getting interface flags: No such device
Plugin rp-pppoe.so loaded.
wlan0: ERROR while getting interface flags: No such device
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; No such device.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
 * Stopping NTP server ntpd
   ...done.
 * Starting NTP server ntpd
   ...done.
Bind socket to interface: No such device
Failed to bring up wlan0.
                                                                         [ OK ]
qbox@qbox:~$ 

```

I use wireless network so Im in wLAN and AP(rooter) and dont need to configure DSL provider. I only connect to wlan and use internet(until problem dissapear)

This lines 
```
auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider
```

are for another place where I use internet and I didnt use them now.
I use network manager now. When wifi is set in roaming mode I have the problem. I didnt try otherwise yet. And how to take back wlan0?

In System->Administration->Hardware Drivers I have One drivers who is checked and are in use. i didnt remember are they used before the problem show. How to check does my wifi work with ndiswrapper driver or maybe use another drivers?

---

### Post by qbox on 2008-08-06
Hi to all.
I think I have found the problem.
I disable the driver in the System->Administration->hardware drivers and rebooted the system. Now I run again ndiswrapper drivers and all work fine.
Ubuntu developers have make some bugs in this bcm4328 802.11a/b/g/n so wifi go down sometimes and I get disconnected And cant connect to accesspoint again. Now I have full control over wifi and I can see wlan0 with ifconfig command. I can scan for networks and everything.
Thanks.

---

