---
title: "AP-hotspot how to NAT/Bridge the connection"
date: 2013-10-31
forum: Networking &amp; Wireless
---

### Post by Azyx on 2013-10-31
I have set up a Hi-Fi Hotspot, with help of web upd8:s ppa and following the guide here: [http://www.webupd8.org/2013/06/how-to-set-up-wireless-hotspot-access.html](http://www.webupd8.org/2013/06/how-to-set-up-wireless-hotspot-access.html). I use an old eee PC 900 with lubuntu 13.10. As I understand i have installed *hostapd* and *dnsmasq, a*nd configure it as a wifi-hotspot with a NAT with one subnet for wifi (Wlan0) 192.168.150.0 and another for (eth0) 192.168.0.0

I get here an ip-adress 192.168.150.1 for the wifi-connection on wlan0 and eth0 get the ip-adress 192.168.0.5 from my dhcp-server in the broadband-'router'.

It work perfect to get an internet connection. I have also find a config file called **hostapd-hotspot.conf** in /etc, that describe how i configured during 'sudo ap-hotspot configure'

```
# WiFi Hotspot
interface=wlan0
driver=nl80211
#Access Point
ssid=[COLOR=#0000ff]Skynet[/COLOR]
hw_mode=g
# WiFi Channel:
channel=1
macaddr_acl=0
auth_algs=1
ignore_broadcast_ssid=0
wpa=3
wpa_passphrase=password
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP
rsn_pairwise=CCMP
```

there i have change SSID to [COLOR=#0000ff]Skynet[/COLOR] and have here in post, change paraphrase to [COLOR=#0000ff]password.[/COLOR]


**Which security do my hot-spot have?**

I wonder what kind of encryptation this link have? Is it WPA-PSK, WPA2 or? As I have understand it, WPA are quite easy to bruteforce, compared to WPA2, who change the transmitted paraphrase more often, I think?

**How-to forward or brige the wlan0 to eth0?**

Ho do I make a forward with some ports or how do I make a bridge, so I can connect to my local lan true the wifi-hotspot on a quite secure way?

Before 2006 used Firestarter as a GUI to manage the firewall/router, but it has now stopped develope and I think I will use gUWF or something. I am not found of CLI, cos I'm a little dyslectic and often type spell errors^^. Maybe some kind of web inteface that only may be configured from eth0?

Cheers

---

### Post by alivema4ever on 2013-10-31
That's as simple as setting up NAT. You can masquerade from wlan0 to eth0.
Fire up a terminal, type this command to allow masquerading.

```
sudo iptables -t nat -A POSTROUTING -s 192.168.1.0/24 -o eth0 -j MASQUERADE
```

Assign a static ip address on wlan0 interface
Configuration file /etc/network/interfaces
```
iface wlan0 inet static
address 192.168.1.1
netmask 255.255.255.0
broadcast 192.168.1.255
pre-up hostapd -B /etc/hostapd/hostapd.conf
post-up service dnsmasq restart
post-down killall hostapd


```

Make sure  you've configured dnsmasq correctly to serve DNS and DHCP so that clients connected via wireless get functional ip address.

Configuration file /etc/dnsmasq.conf
```
# DHCP addresses to assign
dhcp-range=wlan0,192.168.1.150,192.168.1.160,2h
# DNS servers to forward dns request (Google DNS)
server=8.8.8.8
server=8.8.4.4
```

Customize those to fit your needs.

---

### Post by Azyx on 2013-11-01
Thanks. I have had little more to fix in irl and have just studied and try to understand what you have shown. :)

What does this do? Do it change 192.168.150.0 to 192.168.1.0 on the eth0-device? 
```
sudo iptables -t nat -A POSTROUTING -s 192.168.1.0/24 -o eth0 -j MASQUERADE
```

My lan is 192.168.0.0/24 so in the above I should change to 192.168.0.0/24 ?

I also wonder if this above is permantent? If it disappear how to make it permanent?

If MASQUERADE give my wifi-devise an IP-adress in 192.168.0.0/24 how does it prevent that it does not have the same a another machine in the local network?

I have studied my interfaces and dnsmasq.conf

```
File: /etc/network/interfaces                         

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
```

and:

```
File: /etc/dnsmasq.conf                             

#A lot of #-text about dns and dhpc...
.
# Bind to only one interface
bind-interfaces
# Choose interface for binding
interface=wlan0
# Specify range of IP addresses for DHCP leasses
dhcp-range=192.168.150.2,192.168.150.10,12h
#INTERFACE_NET=eth0
```

This seems to give the wlan-devices a ip between 192..168.150.2 - 192.168.150.10 in a lease for 12 hours... 

In my existens dnsmasq.conf there are a bind-interfaces, should I remove that in another dnsmasq.conf???

My broadband-router (NEATGEAR)  do have also assigned DNS-servers and forward them to the local net.

---

