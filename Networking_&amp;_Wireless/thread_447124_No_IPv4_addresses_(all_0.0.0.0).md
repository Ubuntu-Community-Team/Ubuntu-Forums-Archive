---
title: "No IPv4 addresses (all 0.0.0.0)"
date: 2007-05-17
forum: Networking &amp; Wireless
---

### Post by gareththered on 2007-05-17
I've just installed Ubuntu 7.04 on a laptop just 'for fun'. Everything worked fine apart from the wireless network.
I'm trying to create an ad-hoc network with my Windows PC which is configured for Internet Sharing.  To make it simpler I'm not intially bothering with WPA or WEP.  I know that side of things works as I can boot the laptop with Windows, and the wireless card connects to the PC and Internet sharing works - I can surf from the laptop in Windows.
I've installed ndiswrapper to get my PCMCIA wireless card working, and that side of it seems OK.  I can see the Windows PC and get a reasonable signal strength (about 70%), but if I choose 'Connection Information' I get 0.0.0.0 for all the various IP addresses.
It's difficult to post all my logs, as I'd have to type them all in on my PC!!!

'ifconfig' shows wlan0 with a inet6 address and below it wlan0:ava (whatever that is!) has a locally assigned 169.x.x.x address (presumably, the latop gives up waiting for a DHCP response from the PC!)

'iwscan' shows the other PC along with it's ESSID

'iwconfig' shows the ESSID of the PC along with reasonable signal strength etc.

'dmesg' shows:-
ndiswrapper (set_essid:59): setting essid failed (C0000001)
ADDRCONF(NETDEV_UP): wlan0: link is not ready
ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
wlan0: no IPv6 routers present

To make matters worse.  I've had it work once, but only once!

Hope someone can help, and if better logs are really needed I can copy them with a USB memory stick.

---

