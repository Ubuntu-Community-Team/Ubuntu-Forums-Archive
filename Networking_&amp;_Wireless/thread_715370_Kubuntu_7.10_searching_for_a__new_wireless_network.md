---
title: "Kubuntu 7.10 searching for a  new wireless network"
date: 2008-03-04
forum: Networking &amp; Wireless
---

### Post by MonctonJohn on 2008-03-04
I recently setup this laptop with kubuntu 7.10 which has a 3com wireless card. My home network is WEP so I setup the initial connection with the SSID and the WEP key. I am at a hotel now and I had troubles finding the hotel's wireless connection. Using KNetworkManager there was nothing I could do to remove the WEP key and it would not find the hotels network. I kept getting a 169. address, which means there is no connection. After looking around in /etc I noticed the file /etc/network/interfaces so I did:

```
less /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# The primary network interface
auto eth1
iface eth1 inet dhcp
        # wireless-* options are implemented by the wireless-tools package
        wireless-mode managed
        wireless-key1 xxxxxxxxxxxxxxxxxxxxxxxxx
```

(key1 masked of course)

So this tells me this file is holding onto the WEP key I set up. Great... for when I'm home, but what if I travel.

I commented out the two lines like so:

```
#wireless-mode managed
#wireless-key1 xxxxxxxxxxxxxxxxxxxxxx
```

And boom I picked up the hotel's network. Why is this file allowed to affect wireless in such a way (in my opinion, a negative way). I understand the need to keep the WEP key stored, but it shouldn't disable searching for alternative networks, especially on a laptop which is meant to travel and connect to other networks.

Any ideas or responses are appreciated. Tell me  if I missed something or if I should RTFM, I can take it.

---

### Post by MonctonJohn on 2008-03-06
Any ideas?

Should I post a bug???

---

