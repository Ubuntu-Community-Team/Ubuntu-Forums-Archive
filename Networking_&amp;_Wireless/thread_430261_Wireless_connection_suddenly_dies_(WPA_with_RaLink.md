---
title: "Wireless connection suddenly dies (WPA with RaLink RT2500)"
date: 2007-05-01
forum: Networking &amp; Wireless
---

### Post by midnightblade on 2007-05-01
I'm a complete Linux newb but I managed to figure some things out going on the forums and reading guides and what not. I spent several hours today trying to get my wireless card to play nice with my wireless network. I'm using Feisty Fawn 7.04 right now and I finally managed to get it to work by editing the /etc/network/interfaces and I have the following added:

auto ra0
iface ra0 inet dhcp
pre-up iwconfig ra0 essid "SSID HERE"
pre-up iwconfig ra0 mode managed
pre-up iwpriv ra0 set Channel=11
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=TKIP
pre-up iwpriv ra0 set WPAPSK="KEY HERE"
pre-up iwpriv ra0 set TxRate=0

Now I know this bypasses the Network Manager and the internet seems to work fine for the most part, even though I can't see that it's connected in network manager. However it seems like every few minutes the connection dies and I restart it by typing:

sudo ifdown ra0
followed by:
sudo ifup ra0

to reconnect. Could anyone help me figure out why it's dropping the connection like this or help me maybe properly configure it? Thanks in Advance.

I also know it isn't my internet crapping out because even when I do a ping 192.168.1.1 it says destination host unreachable and I don't get these problems while I'm running windows so I figure I must have configured something wrong.

---

