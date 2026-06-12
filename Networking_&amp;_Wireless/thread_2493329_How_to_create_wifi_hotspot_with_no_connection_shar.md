---
title: "How to create wifi hotspot with no connection sharing?"
date: 2023-12-11
forum: Networking &amp; Wireless
---

### Post by mirek on 2023-12-11
hello

for few days i am facing following problem:

on raspberry pi computer i need to create wifi hotspot, which will allow to connect the clients (iot things) with password. the raspbery pi is connected to the internet, but the connected clients will be NOT ABLE to connect to internet. they will be able to connect only to the raspberry pi and use the services, which are available in there.

i need to install more computers (raspberry pis) with such functionality so i am trying to add this configuration as part of my provisioning script. for creation i use network manager with cli tool nmcli. currently i have this:

```
nmcli connection add type wifi ifname wlan0 con-name Hotspot autoconnect no ssid "my-network"
nmcli connection modify Hotspot 802-11-wireless.mode ap 802-11-wireless.band bg ipv4.method shared
nmcli connection modify Hotspot wifi-sec.key-mgmt wpa-psk
nmcli connection modify Hotspot wifi-sec.psk "secret.password"
nmcli connection modify Hotspot ipv4.addresses 10.0.0.1/24
nmcli connection modify Hotspot ipv4.dns ""
nmcli connection modify Hotspot ipv4.gateway ""
nmcli connection up Hotspot
```

one of the ideas was to not provide dns and gateway info for the clients, but it's not working :-( and when i experiment with other modes than shared, my current skills are not sufficient to make it work at all :-(

if someone understands the problem and can help me, how to make it to work, i will be happy :-) especially with network manager, which is preinstalled on the rpi, and no hostapd, if it is possible.

thanks

bletvaska

---

### Post by SeijiSensei on 2023-12-11
The simplest solution would be a firewalling rule on the hotspot that only allows local machines to communicate among themselves.

If you have a network where some machines can have full Internet access, and others only limited access, I'd use your DHCP server to put the devices into separate subnets so I could write iptables rules like this:
```

iptables -A INPUT -s 10.1.1.0/24 -d 10.1.1.0/24 -j ACCEPT
iptables -A INPUT -s 10.1.1.0/24 -d 0/0 -j REJECT

```
The first rule allows machines with IP addresses in the 10.1.1.0/24 subnet to communicate with other machines in the same subnet. Outbound traffic will be blocked by the second rule.

You shouldn't be trying to manage this on the clients but on the firewall device itself.

---

