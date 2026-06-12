---
title: "Cannot connect to Cable Broadband via Ethernet"
date: 2007-05-08
forum: Networking &amp; Wireless
---

### Post by K_C on 2007-05-08
Hi,

I have just installed Ubuntu 7.04 Feisty Fawn desktop version and I am having problems getting connected to the Internet.

I have two netcards in my machine; one onboard and one PCI card. Ubuntu recognises them both and allows me to configure both cards. 

My Internet connect works via a crossover cable connecting my Ethernet card directly to the back of a cable modem (Motorola Surfboard 585101E) which serves as a dhcp client also.

I have tried powering down the equipment and powering up with Ubuntu and also I have tried alternately switching the Ethernet cards off and on in case that gets it to reconnect, nothing seems to work. On one of the Eth interfaces there are bytes transmitted but no connection is made. I noticed when looking at the properties of the Ethernet cards that they were setup to MTU size of 1500 and I am pretty sure my Cable modem likes 1346 could this be the problem?

Any help would be greatly appreciated as I am a Linux newbie.

TIA

---

### Post by Kobalt on 2007-05-08
Hello,
can you please post the output of the following command line ```
ifconfig
```
Have you tried this also : ```
sudo /etc/init.d/networking restart
```
Eventually, what is the output of this command line ?

---

### Post by willskills on 2007-05-08
Definition: The MTU is a limit, expressed in bytes, on the size of data sent over a network. It is the maximum size of a single unit (e.g., an Ethernet frame) of digital communications. 

Ethernet standard is 1500 I think, although this shouldn't stop you connecting.

I use Virgin as an ISP, and I know on thier network, you need to power your modem off for at least 3 minutes, for the lease to die on your present MAC address.

I think auth'ing onto thier network is done via the mac address that is connected to your modem, so if you changed cards, you would need to power off the modem (just take power cable out) for at least 3 minutes (I would leave it 5) - and reconnect, and you should be a go!

---

### Post by Lone_Banana on 2007-05-08
I'm new to Ubuntu, so please forgive me if I'm talking rubbish, but I notice you are using a crossover lead. Should that not be a straight through lead? I thought crossover was used if you are directly linking two computers without a router.

---

### Post by K_C on 2007-05-11
Hi thanks for all your replies,

IFCONFIG Command:

eth0      Link encap:Ethernet  HWaddr 00:01:02:DA:B4:7A  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0x2800 

eth1      Link encap:Ethernet  HWaddr 00:13:8F:A0:AE:79  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21 Base address:0xc800 

eth0:avah Link encap:Ethernet  HWaddr 00:01:02:DA:B4:7A  
          inet addr:169.254.7.198  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:18 Base address:0x2800 

eth1:avah Link encap:Ethernet  HWaddr 00:13:8F:A0:AE:79  
          inet addr:169.254.8.39  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:21 Base address:0xc800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:770 errors:0 dropped:0 overruns:0 frame:0
          TX packets:770 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:61604 (60.1 KiB)  TX bytes:61604 (60.1 KiB)

SUDO Command:

 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 5936
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:01:02:da:b4:7a
Sending on   LPF/eth0/00:01:02:da:b4:7a
Sending on   Socket/fallback
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth1.pid with pid 5955
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:13:8f:a0:ae:79
Sending on   LPF/eth1/00:13:8f:a0:ae:79
Sending on   Socket/fallback
eth2: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
ath0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
wlan0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:13:8f:a0:ae:79
Sending on   LPF/eth1/00:13:8f:a0:ae:79
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:01:02:da:b4:7a
Sending on   LPF/eth0/00:01:02:da:b4:7a
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ OK ]

Any thoughts or suggestions?

Thanks

---

### Post by K_C on 2007-05-11
Oops where the smileys are should be ":D" the forum has reformatted for me.

---

### Post by K_C on 2007-05-11
Arrgh it keeps formatting the text.

second time  - the smileys in the text above should be :D

---

### Post by Kindredgarou on 2007-09-24
also as another note Virgin has a 4 change limit per hour  for mac addresses so if ytou have tried mre than that ina n hour you will have no joy.

---

