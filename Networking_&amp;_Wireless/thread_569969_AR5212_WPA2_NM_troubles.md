---
title: "AR5212 WPA2 NM troubles"
date: 2007-10-07
forum: Networking &amp; Wireless
---

### Post by pvangarde on 2007-10-07
$ lspci | grep Atheros
07:00.0 Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)

I have an Ubiquity Atheros card and I'm having trouble with the schools WPA2 network. It is an MSCHAPV2, AES network, and Network Manager connects fine. However, if I am not playing internet radio, it times out quickly. This means that it looks like its connected but I wait for ages before I can open a page again. The second thing is the bandwidth. It is horribly slow, although NM shows 54 M connection I maybe can download with 50 kb/s (as opposed to 500 in windows). I'm using ubuntu 7.10 beta.

In wpa_supplicant there is a fast reconnect option, I wonder if that's enabled. I don't know why i'm not getting the right bandwidth.

I have 4 of these messages in /var/log/messages:
dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.host_name

(Oh, this card connects fine to WEP networks).

---

