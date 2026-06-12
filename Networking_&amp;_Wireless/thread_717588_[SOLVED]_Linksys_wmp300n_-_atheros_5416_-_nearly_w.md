---
title: "[SOLVED] Linksys wmp300n - atheros 5416 - nearly works but not quite"
date: 2008-03-07
forum: Networking &amp; Wireless
---

### Post by dredwerker on 2008-03-07
I am using kubuntu gutsy - fyi.

There are similar threads on this but I am not sure that I haven't broken something along the way.

I have used ndiswrapper against the inf and sys files copied into my home from the cd. Seemed to work.

I even got it to appear in the knetwork manager at one point but it wouldn't connect.

I tried this - to no avail from this link.
[http://ubuntuforums.org/showthread.php?t=684495]("http://ubuntuforums.org/showthread.php?t=684495")

Manual networking
---------------
lshw -C network

shows:

description: Wireless interface
       product: AR5416 802.11a/b/g/n Wireless PCI Adapter
       vendor: Atheros Communications, Inc.
       physical id: 6
       bus info: pci@0000:05:06.0
       logical name: wlan0
       version: 01
       serial: 00:18:39:0f:a5:20
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5416 driverversion=1.45+Linksys, A Division of Cisc latency=128 module=ndiswrapper multicast=yes wireless=IEEE 802.11b


logical name was wlan0 - that is the interface name



sudo apt-get install wpasupplicant
sudo nano /etc/wpa_supplicant.conf

for wpa2 I put this in the above conf file
  GNU nano 2.0.6                                          File: /etc/wpa_supplicant.conf



ctrl_interface=/var/run/wpa_supplicant

network={
        ssid="pioneer3"
        psk="mypass"
        key_mgmt=WPA-PSK
        proto=RSN
        pairwise=CCMP
}


ifconfig wlan0 down
-- this worked or seemed to


sudo dhclient -r wlan0


Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:18:39:0f:a5:20
Sending on   LPF/wlan0/00:18:39:0f:a5:20
Sending on   Socket/fallback


sudo wpa_supplicant -w -D wext -i wlan0 -c/etc/wpa_supplicant.conf -dd 

lots of output came out - don't know what it meant.

New shell :

sudo ifconfig wlan0 up
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0

Output:
Output:
rogerhi@orwell:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:18:39:0f:a5:20
Sending on   LPF/wlan0/00:18:39:0f:a5:20
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

------------------

So near yet so far.

tia dred

---

### Post by dredwerker on 2008-03-12
I have solved it partially but I still dont really understand what I am doing.

I understand a lot more now.

I have installed wicd as I thought that might help but to no avail. It seems better than network-manager and is worth a try. I am also using the ndiswrapper installation gui tool. Available in a repository near you if its not already installed.

I have found that I can connect without any encryption but with wpa1/wpa2/wep I can't get it to connect.

Any ideas?

---

### Post by dredwerker on 2008-03-28
Solved by another thread using madwifi.

Requires a make etc.. Instructions are clear though thanks to this poster.

[http://ubuntuforums.org/showthread.php?t=718244&highlight=5416]("http://ubuntuforums.org/showthread.php?t=718244&highlight=5416")

---

