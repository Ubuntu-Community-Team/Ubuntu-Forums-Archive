---
title: "Change default gateway on vpn connection"
date: 2007-11-08
forum: Networking &amp; Wireless
---

### Post by Barleyman on 2007-11-08
Hi,

I am connecting to a company PPTP VPN interface via networkmanager.  Everything works fine, but I need to change my default gateway to another ip on the VPN network.  

Any ideas on how I can do this?

---

### Post by niobos on 2007-11-08
I'd suppose the PPTP connection should set this for you, but you can always set it manually via the terminal.```
sudo route del default
sudo route add default gw 1.2.3.4
```
Of course, change 1.2.3.4 by the IP you want
You can also use the more recent "ip" command to do the exact same thing:```
sudo ip route change default via 1.2.3.4
```

---

