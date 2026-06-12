---
title: "LNE100TX and Tulip Driver *no internet* in 8.04.1"
date: 2008-07-13
forum: Networking &amp; Wireless
---

### Post by inspired7 on 2008-07-13
Hi I am experiencing problems with my wired nic saying it does not exist.  I can not get an internet connection and would like some help resolving the issue.

Here are the details of my configuration:

2.6.24-19-generic
Ubuntu 8.04.1

I have two Linksys LNE100TX nics in my system. Here is the ifconfig output:

eth0 Link encap:Ethernet HWaddr 00:a0:cc:32:06:ff
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:50 dropped:0 overruns:0 carrier:50
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt: 11 Base address:0xd400

eth1 Link encap:Ethernet HWaddr 00:a0:cc:32:07:1a
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:149 errors:58 dropped:0 overruns:0 carrier:72
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:12953 (12.6 KB)
Interrupt: 5 Base address:0xd800

eth1:avahi Link encap:Ethernet HWaddr 00:a0:cc:32:07:1a
inet addr:169.254.3.109 Bcast 169.254.255.255 Mask 255.255.0.0
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
Interrupt: 11 Base address:0xd400

...

Running lshw -C network returns all the specs of my 2 network cards being a LNE100TX on eth0 and eth1 and also says I am using tulip as my driver with driver version=1.1.15

I have been searching for answers and have tried many things and have just reinstalled and still have the same problem. I am also dual booting with windows xp and it runs both network cards with no problems. Thanks in advance for any help.

---

### Post by chili555 on 2008-07-13
It looks like eth1 is the interface that has the wire connected right now. Please let us see:```
sudo dhclient eth1
sudo ethtool eth1
```Thanks.

---

### Post by inspired7 on 2008-07-13
sudo dhclient eth1 returns:

Listening on LPF/eth1/00:a0:cc:32:07:1a
Sending on LPF/eth1/00:a0:cc:32:07:1a
Sending on Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received
No working leases in persistent database - sleeping.

and 

sudo ethtool eth1 returns:

Settings for eth1:
No data available

Currently I have both nics plugged into my router and have tried only having one of the two plugged in for both cards but no luck.  
Any suggestions?

---

### Post by inspired7 on 2008-07-14
bump

---

### Post by chili555 on 2008-07-14
May we please see:```
dmesg | grep eth
```Also, please make sure 'Plug and Play OS' is marked 'No' in the computer's BIOS.

Thanks.

---

### Post by inspired7 on 2008-07-14
dmesg | grep eth returns:

[   41.642039] eth0: Lite-on PNIC-II rev 37 at Port 0xd400, 00:a0:cc:32:06:ff IRQ 11
[   41.954629] eth1: Lite-on PNIC-II rev 37 at Port 0xd800, 00:a0:cc:32:07:1a IRQ 5
[   46.973973] Driver 'sd' needs updating - please use bus_type methods
[   46.984867] sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   105.468260] eth0: Autonegotiation failed, using 10baseT, link beat status 10ce

[   160.667281] eth0: no IPv6 routers present
[   160.707273] NETDEV WATCHDOG: eth1: transmit timed out
[   160.707301] eth1: PNIC2 transmit timed out, status e4000000, CSR6/7 e1000200  /  effffbff CSR12 000010ce, resetting...

it repeats the last block for eth1 aswell and also repeats for eth1 saying Out-of-sync dirty pointer, 24 vs 57 instead of the no IPv6 routers present.

Thanks

---

### Post by inspired7 on 2008-07-15
bump

---

### Post by inspired7 on 2008-07-15
anyone?

---

### Post by Shinto314 on 2009-10-01
I know this is an old thread and the original author has likely moved on to a different/better network card, but here is what I did to get my Lite-on PNIC-II rev 37 working under Ubuntu (5.04 Hoary).  Maybe someone will find it helpful.

```
sudo rmmod tulip
sudo modprobe tulip options=5
```

The link autodetection was failing, so "options=5" forces it to 100baseTx-FD.  I could then run 'dhclient eth0' to get my IP.

The full list of possible options= values with the tulip driver are:
 	0 Auto-select (default to the 10baseT link)
	1 10base2
	2 AUI
	3 100baseTx
	4 10baseT-FD
	5 100baseTx-FD
	6 100baseT4
	7 100baseFx
 	8 100baseFx-FD
	9 MII 10baseT
	10 MII 10baseT-FD
	11 MII (autoselect)
	12  10baseT (no autoselect), v0.69 and later only
	13 MII 100baseTx
	14 MII 100baseTx-FD
	15 MII 100baseT4

To make the change permanent, I created a modprobe.d file:

```
echo 'options tulip options=5' |sudo tee /etc/modprobe.d/tulip.modprobe
```

---

