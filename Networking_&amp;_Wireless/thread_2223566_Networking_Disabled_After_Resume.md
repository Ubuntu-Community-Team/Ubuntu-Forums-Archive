---
title: "Networking Disabled After Resume"
date: 2014-05-11
forum: Networking &amp; Wireless
---

### Post by HDTimeshifter on 2014-05-11
My wired networking is disabled after resuming from sleep. If I select Enable Networking from the icon in the upper right, it still won't re-enable it and I have to reboot to get networking back.

I'm running Ubuntu 14.04 LTS, and have not been able to resume from sleep (mouse stopped working or couldn't log-in or screen would freeze up - can't remember exactly which) since the previous release last fall. There's some bug with nVidia (I have GeForce 9500 GT), but I just changed the driver from the default X Org to a proprietary nVidia driver (any of the 5 versions seem to work), which allows it to resume now, however I loose networking.

When I originally installed Ubuntu in 2008, I remember having problems with networking and it was something to do with the Atheros driver, but only nVidia drivers show up in Additional Drivers application.

---

### Post by HDTimeshifter on 2014-05-14
Below is my network information:

> *-network
description: Ethernet interface
product: AR8121/AR8113/AR8114 Gigabit or Fast Ethernet
vendor: Qualcomm Atheros
physical id: 0
bus info: pci@0000:02:00.0
logical name: eth0
version: b0
serial: 00:23:54:00:bf:86
size: 100Mbit/s
capacity: 1Gbit/s
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI duplex=full firmware=L1e ip=192.168.1.100 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
resources: irq:17 memory:fe9c0000-fe9fffff ioport:dc00(size=128) 

The result of "lsmod | grep atl" is:
> atl1e                  42380  0
so it doesn't appear to be the driver?

---

### Post by chili555 on 2014-05-14
Is the driver still loaded after suspend? Any clues here?```
cat /var/log/syslog | grep -e atl -e etwork | tail -n20
```

---

### Post by HDTimeshifter on 2014-05-15
Looks like it's removing the driver upon sleep and adding it back on resume, but not activating it?
> May 15 02:18:56 Main NetworkManager[878]: <info> kernel firmware directory '/lib/firmware' changed
May 15 02:40:15 Main NetworkManager[878]: <info> sleep requested (sleeping: no  enabled: yes)
May 15 02:40:15 Main NetworkManager[878]: <info> sleeping or disabling...
May 15 02:40:15 Main NetworkManager[878]: <info> (eth0): device state change: activated -> unmanaged (reason 'sleeping') [100 10 37]
May 15 02:40:15 Main NetworkManager[878]: <info> (eth0): deactivating device (reason 'sleeping') [37]
May 15 02:40:15 Main NetworkManager[878]: <info> (eth0): canceled DHCP transaction, DHCP client pid 1038
May 15 02:40:15 Main NetworkManager[878]: <warn> DNS: plugin dnsmasq update failed
May 15 02:40:15 Main NetworkManager[878]: <info> Removing DNS information from /sbin/resolvconf
May 15 02:40:15 Main NetworkManager[878]: <info> (eth0): cleaning up...
May 15 02:40:15 Main NetworkManager[878]: <info> (eth0): taking down device.
May 15 02:40:15 Main NetworkManager[878]: <info> NetworkManager state is now ASLEEP
May 15 02:40:16 Main NetworkManager[878]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:02:00.0/net/eth0, iface: eth0)
May 15 02:43:42 Main NetworkManager[878]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:02:00.0/net/eth0, iface: eth0)
May 15 02:43:42 Main NetworkManager[878]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:02:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
May 15 02:43:42 Main NetworkManager[878]: <warn> failed to allocate link cache: (-12) Object not found
May 15 02:43:42 Main NetworkManager[878]: <info> (eth0): carrier is OFF
May 15 02:43:42 Main NetworkManager[878]: <info> (eth0): new Ethernet device (driver: 'ATL1E' ifindex: 3)
May 15 02:43:42 Main NetworkManager[878]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/1


---

### Post by chili555 on 2014-05-16
That seems to point to a Network Manager issue. Does the ethernet come back if you do:```
sudo service network-manager restart
```Is this a stay at home computer so that we could eliminate NM altogether, at least experimentally?

---

### Post by HDTimeshifter on 2014-05-17
That worked!
I put "service network-manager restart" in my /etc/pm/config.d/config file and it now resumes with networking.

This is a home tower PC with only wired networking (considering adding wireless - need to do some research on combining both how to do that - if I need to replace my router or if I can add wireless capability with some add-on device).

Thanks!

---

### Post by chili555 on 2014-05-18
> **HDTimeshifter said:**
> That worked!
I put "service network-manager restart" in my /etc/pm/config.d/config file and it now resumes with networking.

This is a home tower PC with only wired networking (considering adding wireless - need to do some research on combining both how to do that - if I need to replace my router or if I can add wireless capability with some add-on device).

Thanks!Awesome! Glad it's working.

Just for the benefit of the searchers, so they can see the exact technique, please show us:```
cat /etc/pm/config.d/config
```I think a wireless 'add on device' also known as a wireless access point, is just as expensive and a whole lot less capable than a new wireless router. 

I suggest you research your wireless card carefully; some work perfectly with Ubuntu and some don't.

---

### Post by HDTimeshifter on 2014-06-21
> **chili555 said:**
> Just for the benefit of the searchers, so they can see the exact technique, please show us:```
cat /etc/pm/config.d/config
```

Exactly as I mentioned above:
```
service network-manager restart

```

By the way, I simply replaced my wired Lynksys router with a wireless-G Lynksys router that had been given to me and everything works as before, plus I now can check e-mail, etc. from my phone throughout the house and garage at 54 Mbps. I tried a couple other wireless routers that were lying around first - a D-Link MIMO, which I couldn't ping, and a Belkin G+ that had no wireless functionality, and a Belkin G single antenna which didn't have full strength throughout my house. All of these were given to me free - people just throw these things away (freecycle) - I have no need for faster Gigabite wireless since I'll just use wired connections for anything requiring faster speeds.

---

