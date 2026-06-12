---
title: "RT61 problems with Knetwork manager"
date: 2007-10-20
forum: Networking &amp; Wireless
---

### Post by mike00 on 2007-10-20
I started using ubuntu/kubuntu with Dapper and I seem to have encountered various problems before with wireless network with WPA. I had everything running OK on Feisty with the following in my /etc/network/interfaces:
```

auto ra0
iface ra0 inet static
address 192.168.1.50
netmask 255.255.255.0
gateway 192.168.1.1
post-up route add default gw 192.168.1.1
wireless-essid linksysnetwork
dns-nameservers *******************
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=TKIP
pre-up iwconfig ra0 essid ********
pre-up iwpriv ra0 set WPAPSK="********"

```

My pci card:
lspci | grep Ra
01:0a.0 Network controller: RaLink RT2561/RT61 802.11g PCI

I am currently using knetworkmanager (with dhcp) to connect, but it keeps disconnecting and not finding the access point. - I sometimes need a reboot to get a connection. I remember giving up with knetworkmanager before because I seemed to have fewer problems with just putting my settings into /etc/network/interfaces.

Is there a way that i could set it up to work like this in Gutsy?  - I don't seem to be able to use commands such as "iwpriv ra0 set AuthMode=WPAPSK" because I now get "Invalid command : set"
Note: the interface has changed from ra0 to wlan0 whan I installed 7.10 (I am using Kubuntu AMD 64)

I would really like to get a reliable internet connection up and running. Any help much appreciated!

---

### Post by mike00 on 2007-10-21
I have managed to get it working by using the driver from serialmonkey. Then blacklisting the rt61pci driver.

My etc/network/interfaces looks like this:
```
auto wlan0
iface wlan0 inet static
address 192.168.1.50
netmask 255.255.255.0
wireless-essid xxxxxxxxx
gateway 192.168.1.1
post-up route add default gw 192.168.1.1

dns-nameservers xxxxxxxxxxxx
pre-up ifconfig wlan0 up
pre-up iwpriv wlan0 set AuthMode=WPAPSK

pre-up iwpriv wlan0 set EncrypType=TKIP
pre-up iwconfig wlan0 essid xxxxxxxxxxxxx
pre-up iwpriv wlan0 set WPAPSK="xxxxxxxxxxxx"
```
(Maybe this will be helpful for someone else)

It's still not starting automatically at boot though, But if I run sudo /etc/init.d/networking restart things usually work out OK. I have also tried the RutilT tool, which seems to be better than Knetworkmanager so far.

---

