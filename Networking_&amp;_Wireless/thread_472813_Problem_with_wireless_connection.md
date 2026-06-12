---
title: "Problem with wireless connection"
date: 2007-06-13
forum: Networking &amp; Wireless
---

### Post by bellzii on 2007-06-13
hey everyone
Ive been trying to set my wireless connection , im using a DELL Laptop with Ubuntu 6.10  Edgy Eft

here is what i tried  

root@bellzii-laptop:/home/bellzii# sudo ifconfig eth1 up

root@bellzii-laptop:/home/bellzii# sudo iwconfig eth1 essid ____ key ____ channel __
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "____".

Can some1 plz help

---

### Post by chili555 on 2007-06-13
I believe "Set Encode" (8B2A) means your key is invalid in some respect. Let's troubleshoot. Is your router or access point set up with WEP or WPA? For the moment, let's assume WEP.
#40 or 64 bit ASCII WEP code has 5 characters
#40 or 64 bit HEX WEP code has 10 characters
#128 bit ASCII WEP code has 13 characters
#128 bit HEX WEP code has 26 characters 

If your key is ASCII, you must prepend it with **s:** thus:```
sudo iwconfig eth1 key s:12345
```Please check your work and post back.

---

### Post by bellzii on 2007-06-13
hey thanks alot for ur reply,
 

the code u sent me did nothing

I really dont know whether my WEP is 40/64 or 128 ..but i know its ASCII

---

### Post by chili555 on 2007-06-13
Ummmm, how many characters does it have?

---

### Post by jmbargar on 2007-06-13
Why don't you try to put your network configuration in /etc/network/interfaces? So, if you use dhcp only you have to do is editing that file and put inside something like this:

auto eth1
iface eth1 inet dhcp
wireless-essid name_of_your_network
wireless-key key_of_your_network

now save the file and type:

sudo /etc/init.d/networking restart

remember that the content of /etc/network/interfaces must be only those lines for your eth1 interface.

Best regards

---

### Post by bellzii on 2007-06-28
tried that but i got :

root@bellzii-laptop:/etc/network# sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          
/etc/network/interfaces:18: too few parameters for iface line
ifdown: couldn't read interfaces file "/etc/network/interfaces"
/etc/network/interfaces:18: too few parameters for iface line
ifup: couldn't read interfaces file "/etc/network/interfaces"
                                                                                                                                                                         [fail]

---

### Post by bellzii on 2007-06-28
I did miss adding something but after i did i got this:


root@bellzii-laptop:/etc/network# sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 6098
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:15:c5:17:59:79
Sending on   LPF/eth0/00:15:c5:17:59:79
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
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
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "coolpunk1".
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:13:02:98:b2:f2
Sending on   LPF/eth1/00:13:02:98:b2:f2
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ ok ]

---

