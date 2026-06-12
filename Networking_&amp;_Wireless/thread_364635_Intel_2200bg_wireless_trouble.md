---
title: "Intel 2200bg wireless trouble"
date: 2007-02-18
forum: Networking &amp; Wireless
---

### Post by Falkon MX-5 on 2007-02-18
Not to sound like a broken record with all these other wifi problems, but I just can't get the Intel card working on my Inspiron 600m.  I have tried using every gui tool available and iwconfig with no luck.  

Background:
Router is 802.11g with WEP enabled.  
lspci recognizes card as Intel Pro/Wireless 2200bg

line from /etc/network/interfaces
```

iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid HomeTown
wireless-channel 11
wireless-key <hexwepkey>

```

When I do ```
sudo ifup eth1
``` I get a dhcp address from the router [192.168.0.1].  When I try to ping 192.168.0.1 I get "Destination Host Unreachable."

I know I put in the right WEP key.  I've tried this with wireless-assistant, network manager, and wifi-radar.  I have had zero luck getting this working.

So how can I get a DHCP offer from the router and an IP, yet can't ping the router or get out to the internet?

---

### Post by Falkon MX-5 on 2007-02-18
Okay, nevermind.  I restarted and it all came up beautifully.

---

