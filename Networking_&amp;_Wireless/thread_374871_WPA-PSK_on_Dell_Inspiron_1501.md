---
title: "WPA-PSK on Dell Inspiron 1501"
date: 2007-03-03
forum: Networking &amp; Wireless
---

### Post by dinkoarun on 2007-03-03
I currently got the Dell WLAN driver installed using the guide found here [http://ubuntu1501.blogspot.com/2007/01/fixing-wifi-on-dell-1501.html]("http://ubuntu1501.blogspot.com/2007/01/fixing-wifi-on-dell-1501.html")

The problem now is I am unable to configure my wireless network to connect to a WPA-PSK encrypted network. The encryption used is TEKIP. When I do  "sudo iwlist scanning" It shows that the network is encrypted with WPA, but i donot know where to enter the "passkey"

These are my setting is /etc/network/interfaces file. I currently eth1 to connect to the wireless network.

[I][B]auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp


iface eth1 inet dhcp
wireless-essid linksys
wireless-key s:

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid linksys


auto eth1
[/B][/I]

Any information would be greatly appreciated.

Thanks

---

### Post by spd106 on 2007-03-03
I suggest that you install Network Manager [https://wiki.ubuntu.com/WifiDocs/NetworkManager](https://wiki.ubuntu.com/WifiDocs/NetworkManager)

Otherwise you will have to configure wpasupplicant manually.

---

### Post by dinkoarun on 2007-03-03
Thanks for the reply.

I do have NetworkManager installed. But there is no particular place that I can enter the WPA information.

---

### Post by spd106 on 2007-03-03
Almost all configuration of Network Manager is done through the nm-applet in the notification area. N M will detect which kind of encryption the essid requires and then presents you will the right dialogue boxes.

It may be that you haven't set up the interfaces correctly post-install, see the above link for more information.

---

