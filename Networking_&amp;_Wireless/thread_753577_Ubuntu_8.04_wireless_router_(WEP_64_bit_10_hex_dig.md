---
title: "Ubuntu 8.04 wireless router (WEP 64 bit 10 hex digits key) connection problem"
date: 2008-04-12
forum: Networking &amp; Wireless
---

### Post by tuathan on 2008-04-12
Using Ubuntu 8.04.
trying to connect to a wireless router which requires a WEP 64 bit 10 hex digits key. problem is that the Ubuntu gui seems to require at least 13 digits in the key! (i can click the connect button unless i enter at least 13 digits)....

anyone know how to get around this

---

### Post by chili555 on 2008-04-12
Sure, don't use the GUI! Instead, open a terminal and do:```
sudo iwconfig eth1 essid <your_essid>
sudo iwconfig eth1 key <your_key>
sudo dhclient eth1
```Substitute your wireless interface for eth1.

---

### Post by tuathan on 2008-04-12
i tried that but got the following error:

Error for wirelss request "Set Encode" (8B2A);
SET failed on device eth1; No such device



i have used the the ethernet connection fine

---

### Post by kevdog on 2008-04-12
Is eth1 your wireless device?

You also have to bring down your wired device before bring up your wireless device which is something like
sudo dhclent -r eth0
sudo ifconfig eth0 down

---

### Post by tuathan on 2008-04-15
> **chili555 said:**
> Sure, don't use the GUI! Instead, open a terminal and do:
```
sudo iwconfig eth1 essid <your_essid>
sudo iwconfig eth1 key <your_key>
sudo dhclient eth1
```
Substitute your wireless interface for eth1.

my wireless device is wlan0.

i tried that but this happen:
```

sudo iwconfig wlan0 essid ****
sudo iwconfig wlan0 key **********
sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:90:4b:f5:6c:f8
Sending on   LPF/wlan0/00:90:4b:f5:6c:f8
Sending on   Socket/fallback
receive_packet failed on wlan0: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
send_packet: Network is down

[1]+  Stopped                 sudo dhclient wlan0

```

---

