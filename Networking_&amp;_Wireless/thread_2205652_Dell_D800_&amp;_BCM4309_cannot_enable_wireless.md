---
title: "Dell D800 &amp; BCM4309: cannot enable wireless"
date: 2014-02-15
forum: Networking &amp; Wireless
---

### Post by mattmoose1969 on 2014-02-15
Struggling with this one... 

In the BIOS, wireless is definitely enabled. 

issuing 'lspci | grep Network' reports: 
'02:03.0 Network controller: Broadcom Corporation BCM4309 802.11abg Wireless Network Controller (rev 03)'

I've tried installing b43-fwcutter, which reportedly has helped others, but not in this case. Not obvious what to try next.

Also:
 wireless networking does not appear as an option when I click on the networking icon in the system tray;
network-manager-gnome is installed;
going to 'edit connections' gives a wireless tab, but lists no available stations
fn+F2 (enable wireless) does nothing

HELP! Thanks.

---

### Post by chili555 on 2014-02-15
May we please instead see:```
lspci -nn | grep 0280
dmesg | grep b43
lsb_release -d
```Thanks.

---

