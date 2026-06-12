---
title: "Accessing WEP network"
date: 2007-05-21
forum: Networking &amp; Wireless
---

### Post by Vonagio on 2007-05-21
I have a USB 11g Cable & Wireless card connected to an EiSystem/PC World laptop. The card is found by Feisty fine and is identified in the network connection applet as a wireless card. I can connect to my AP when WEP is disabled, but when it is on it doesn't get past
```
"waiting for network key for the wireless network 'my_essid' ..."
```
After about 2 minutes it connects back to the wired network (or attempts to connect to the wired network if its disconnected).

My WEP key is correct and works on other (XP and mac) machines. I have not installed any software or drivers for the card.

Thanks, Von

Edit: Looking at /etc/network/interfaces shows:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```

My USB WLAN card is eth1, but it isn't shown here...It is in the network manager applet though...

ifconfig: (eth1)
```
Link encap:Ethernet   HWaddr ADAPTER_MAC_ADDRESS
UP BROADCAST MULTICAST   MTU:1500   Metric:1
RX/TX (All packets are 0 as it hasn't connected)

```

---

### Post by tturrisi on 2007-05-21
add this to interfaces:

sudo gedit /etc/network/interfaces

iface eth1 inet dhcp
wireless-essid YOURSSID
wireless-key YOUR-WEPK-EY #try a hyphen after every 4 characters
auto eth1

---

### Post by Vonagio on 2007-06-15
I've tried adding that to the interfaces file with and without the hyphens but it still requests the key when I select the wireless network.

Thanks, Von

---

