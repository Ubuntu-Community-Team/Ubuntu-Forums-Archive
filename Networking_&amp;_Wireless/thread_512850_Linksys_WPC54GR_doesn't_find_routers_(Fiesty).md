---
title: "Linksys WPC54GR doesn't find routers (Fiesty)"
date: 2007-07-29
forum: Networking &amp; Wireless
---

### Post by Kulgan on 2007-07-29
I got a random wireless card (gift... WPC54GR) for my laptop, and the computer seems to be recognising it. 

From /var/log/syslog:
```

Jul 29 14:48:06 ubuntu NetworkManager: <information>^Ira0: Device is fully-supported using driver 'rt61'. 
Jul 29 14:48:06 ubuntu NetworkManager: <information>^Inm_device_init(): waiting for device's worker thread to start 
Jul 29 14:48:06 ubuntu NetworkManager: <information>^Inm_device_init(): device's worker thread started, continuing. 
Jul 29 14:48:06 ubuntu NetworkManager: <information>^INow managing wireless (802.11) device 'ra0'. 
Jul 29 14:48:06 ubuntu NetworkManager: <information>^IDeactivating device ra0. 

```

That looks good enough, I would suspect - it finds the device, finds a working driver, starts it, takes control of the network - and then deactivates it? Makes no sense. 

The network manager doesn't list any wireless networks, though I know there are several in the neighbourhood, and my router is beside me and working perfectly. 

It should have started a device called "ra0", so....

dmesg | grep "ra0"
```

[   99.230000] ra0: no IPv6 routers present
[ 1910.310000] ra0: no IPv6 routers present
[ 1970.950000] ADDRCONF(NETDEV_CHANGE): ra0: link becomes ready
[ 1981.830000] ra0: no IPv6 routers present

```

ifup ra0 and ifdown ra0 both fail, presumably because it is not in /etc/network/interfaces yet, but I don't think I should add it manually (correct me?)

The power indicator on the card is on, and the activity light is flashing rapidly, as if I were downloading something - yet ping doesn't work.

What more can I do to find the source of the issue?

Thanks,
-K

---

### Post by Kulgan on 2007-08-02
Well, I don't know what went wrong, but it's working. Apparently I had to add it as a wireless interface in /etc/network/interfaces :

```

auto ra0
iface ra0 inet dhcp
wireless-essid home
wireless-key A35D521C0AE4F8D33D210EEDC2

```

then 

```

ifdown -a
ifup ra0

```

And it connected. So I was wrong in my assumption.


Gotta love writing for the record.
-K

---

