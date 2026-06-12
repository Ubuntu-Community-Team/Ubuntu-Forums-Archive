---
title: "Simple Wifi AP without NAT"
date: 2018-03-30
forum: Networking &amp; Wireless
---

### Post by vanbynight on 2018-03-30
I just spent about an hour googling how to do this but I can't find a simple answer.

What I'm trying to accomplish is a layer 2 bridge between my wired and wireless interfaces so I can have clients connect to my wireless AP running on this box (let's call it APnode). I specifically don't want to run a DHCP and DNS forwarder on APnode and all I want it to do is have it act as an access point for my preexisting network that already has DHCP DNS NAT etc working.

I'd like to accomplish this using ```
 /etc/network/interfaces 
``` but I don't know how to configure the wireless in access point mode.

Is there an option that would look similar to this? The names are just for reference and I'd probably use a vlan interface for management on eth0

```


auto eth0
iface eth0 inet manual

#management interface
auto eth0.10
iface eth0.10 inet dhcp
vlan-raw-device eth0

#pass wireless traffic to this interface
auto eth0.20
iface eth0.20 inet manual
vlan-raw-device eth0

#Wireless interface in Access Point Mode
auto wlan0
iface wlan0 inet manual
#not sure how to set a wireless interface to act as an access point
WPA-ACCESS-POINT-SSID "My access Point"
WPA-ACCESS-POINT-PASSWORD "secret"
WPA-ACCESS-POINT-MODE "anything other than client mode"

#the bridge that pushes traffic from wlan0 to the ethernet interface
auto br0
iface br0 inet manual
bridge-ports wlan0 eth0.20

```

I don't want to have a DHCP server running on APnode and I'd prefer that it didn't do any layer 3 routing.

If using /etc/network/interfaces isn't an option I'd like to make a bash script that I can run from /etc/rc.local that adds the wireless interface to the bridge

**Bonus points if you know how to make this work with multiple access point SSID's running on the same hardware for a guest-network**

---

