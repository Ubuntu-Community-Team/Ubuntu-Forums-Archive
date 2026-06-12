---
title: "Routing Problem with on-board NIC and Wireless"
date: 2008-01-17
forum: Networking &amp; Wireless
---

### Post by DantePasquale on 2008-01-17
Hi,

I'm running 7.10 on my laptop and have everything working thanks to great posts on this forum. But I have a strange problem with routing. I have the following in my /etc/network/interfaces file:
```

auto lo
iface lo inet loopback

iface wlan0 inet static
address 74.110.146.173
netmask 255.255.255.240
gateway 74.110.146.161
wpa-psk "<what my mask is>"
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA2
wpa-ssid my-ssid

auto wlan0
#auto eth0

#iface eth0 inet dhcp
```

When I boot up the laptop, there seems to be a residual address on eth0 (on-board NIC) of 74.110.146.172, but the interface is not running:

When I first logon, I can't ping the router and when I trace what's going on, the ping is being sent through eth0 which is not running. Then I run /etc/init.d/networking restart and everything is fine. eth0 shows all 0's and routing is fine.

Question: How can I figure out where the residual information is being set?
Why is the ping routed through an interface that is configured, but not running? - Same result if I run ifdown eth0.

I am also running nm-applet 0.6.5 - could this be interfering? But I need it for dhcp wireless in coffee houses :guitar: and diners :)

 No good information in logs or dmesg.

---

### Post by DantePasquale on 2008-02-08
If no one from this forum can help, I'm going to open a bug as this sounds like a bug to me.

---

