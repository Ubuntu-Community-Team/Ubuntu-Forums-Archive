---
title: "Unchecking &quot;Network Manager&quot; in &quot;Startup Applications&quot;..."
date: 2009-05-18
forum: New to Ubuntu
---

### Post by DonaldJ on 2009-05-18
If I uncheck "Network Manager" in "Startup Applications", to speed-up boot, given that I'm not on a network, will it cause any problems, or open any security holes in Ubuntu-904..?

---

### Post by cariboo on 2009-05-18
If you are connecting to the internet from the same computer you still need network manager.

---

### Post by Alterax on 2009-05-19
Well, you'll need to set up your networking manually.  I don't use network-manager on my desktops (since they don't really change addresses), but for the laptop, it's indispensible.

You'll need to set up /etc/network/interfaces and /etc/resolv.conf to handle the network settings.  This should get you through with little (if any) modification.

/etc/network/interfaces
```
auto eth0
iface eth0 inet dhcp

```

/etc/resolv.conf
```
domain home.local
search home.local
nameserver 208.67.222.222

```

Then just restart the networking services with:
```
sudo /etc/init.d/networking restart
```

---

