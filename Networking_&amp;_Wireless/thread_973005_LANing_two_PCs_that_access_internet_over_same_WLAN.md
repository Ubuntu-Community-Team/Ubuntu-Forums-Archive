---
title: "LANing two PCs that access internet over same WLAN-AP wihtout using VPN+dyndns?"
date: 2008-11-06
forum: Networking &amp; Wireless
---

### Post by dreamer84 on 2008-11-06
hello,
sorry if it's already been asked, but I don't know how to ask more specifically:

I have two PCs with WLAN-access to the internet using the same AP. Is there any way to let them share files without them having static IPs? My current solution is openvpn + dyndns, but that of course only works if the internet connection is not interrupted. Can I make them connect using their MACs?

thanks,
tobias

---

### Post by superprash2003 on 2008-11-06
if they are connected from the same AP.. then why cant you share files via LAN..

---

### Post by dreamer84 on 2008-11-06
because they get their IPs via DHCP from the broadband modem, so I can't have them automatically know each others IP. or can I?
A related problem is that the AP (old D-Link) only forwards the modems DHCP which is configured by my provider so I can't change it and I therefore cannot use the AP whithout internet (I have a flatrate, so that's usually no problem here, but still, sometimes the internet is down, and using dyndns to let one PC know the others IP is definitely an unnecessary risk)

or can each PCs single WLAN-adapter connect to both the AP for internet and directly to the other PC?

---

### Post by superprash2003 on 2008-11-10
it should work using the local hostnames of the pcs

---

