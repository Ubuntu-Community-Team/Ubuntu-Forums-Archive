---
title: "How can you connect to vpn when connected via dialup / gprs"
date: 2008-01-05
forum: Networking &amp; Wireless
---

### Post by zonky on 2008-01-05
access vpn when using internet via dialup/gprs
I use a bluetooth connection and gprs/3g data occasionally to connect to my work vpn. (pptn).

I have VPN connection manager installed (PPP Generic) and i can access my vpn via the network applet when connected to a wireless or wired network.

When i'm on my dialup / bluetooth phone connection (using pon/poff), as far as the vpn connection is concerned, i'm not connected to the 'net and can't access my vpn profile (it is greyed out).

Is there another way i can enable the vpn connection?

I figured that i can add to my /etc/network/interfaces a section:


```
iface ppp0 inet ppp
provider vodanz

```
This allows me to connect via my mobile to the internet via network manager, but the vpn is still greyed out!

Looking at the advanced options for the vpn instance config, there is a greyed out checked box called 'require network connection'.

Obviously, i need this unchecked, but you can't.

Really, this is a silly, silly flaw in design and i can't believe all i can find on the forums by searching is other people in the same boat- connection via dialup / mobile and unable to use vpn.

Please, please, someone tell me how you solved this.

---

### Post by zonky on 2008-01-08
I have figured out using pptpconfig is a way around the issue- if i could make it work. I suppose there is no way around the Network Manager issue- perhaps creating a virtual network interface which loops traffic via the ppp path?

---

