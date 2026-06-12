---
title: "native+ndiswrapper"
date: 2008-02-21
forum: Networking &amp; Wireless
---

### Post by archman on 2008-02-21
Hi, i have ndiswrapper 1.52 working perfectly on gutsy. But, ndis doesn't support monitoring.
My question is, how can I shutdown ndis and load bcm43xx native driver (blacklisted) when I need monitor mode and packet injection?
I want ndis to remain the default module on startup, and not to load native automatically...

tnx

---

### Post by spd106 on 2008-02-22
It's a simple matter of bringing the interface down, unloading one driver and then loading the other. If you set up the interface name in the /etc/iftab, then it will always use that name rather than switch between wlan0 and eth1 or whatever.

Basically I do this:

```
sudo ifdown eth1
sudo modprobe -r ndiswrapper
sudo modprobe bcm43xx
```

The network scripts should automatically bring the interface up and configure it correctly, unless you've modified the /etc/network/infaces file differently.

You can check which driver has control by using this command, though there are probably other ways.

```
sudo lshw -class network
```

If you are using Network Manager then there will be extra complexity. In that case it's probably better to use different interface names and use the interfaces file for the one you're going to be working with.

---

