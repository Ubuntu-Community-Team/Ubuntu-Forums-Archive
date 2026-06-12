---
title: "Network unavailible"
date: 2005-05-30
forum: Networking &amp; Wireless
---

### Post by nirk on 2005-05-30
Everything worked just fine i Warty. I wanted Hoary and did a dist-upgrade with Synaptic, but it failed to complete. When I restarted, X wouldn't start and some packages were conflicting so a friend ssh'ed me and fixed it. I used irssi and it worked fine. I completed the dist-upgrade from shell, but after restart, the network was unavailible. I tried every imaginable combination of settings in the router and interfaces; DHCP, static, NAT and bridge, but it never worked. Also, KDE was the only thing that worked.

I downloaded Hoary-boot.iso and reinstalled everything, and now Gnome runs nicely, but I still have no net at all, and this makes me feel kind of cut-off. So now I'm stuck i Windows.

I can't imagine that the reason is incompatibility or lack of drivers for the network card, which is "CNet PRO200WL PCI Fast Ethernet Adapter", as it worked just fine in Warty.

Thanks in advance for any help.

Ola

---

### Post by fdoving on 2005-05-31
[QUOTE=nirk]Everything worked just fine i Warty. I wanted Hoary and did a dist-upgrade with Synaptic, but it failed to complete. When I restarted, X wouldn't start and some packages were conflicting so a friend ssh'ed me and fixed it. I used irssi and it worked fine. I completed the dist-upgrade from shell, but after restart, the network was unavailible. I tried every imaginable combination of settings in the router and interfaces; DHCP, static, NAT and bridge, but it never worked. Also, KDE was the only thing that worked.

I downloaded Hoary-boot.iso and reinstalled everything, and now Gnome runs nicely, but I still have no net at all, and this makes me feel kind of cut-off. So now I'm stuck i Windows.

I can't imagine that the reason is incompatibility or lack of drivers for the network card, which is "CNet PRO200WL PCI Fast Ethernet Adapter", as it worked just fine in Warty.

Thanks in advance for any help.

Ola[/QUOTE]
 Try this:
```

sudo rmmod tulip
sudo modprobe dmfe
sudo invoke-rc.d neworking restart

```
If this works, add 'dmfe' to /etc/modules.

If that doesn't work, you can try:
```

sudo rmmod dmfe
sudo modprobe tulip
sudo invoke-rc.d networking restart

```

If this works add 'tulip' to /etc/modules file.

---

### Post by nirk on 2005-05-31
Thanks, I've now tried it but with no luck. Changes occur in network-admin though - eth0 disappears when i probe dmfe. networking restart says ok with tulip, but hangs with dmfe. And the network is unavailible at any time.

Any suggestions is appreciated.

Ola

---

