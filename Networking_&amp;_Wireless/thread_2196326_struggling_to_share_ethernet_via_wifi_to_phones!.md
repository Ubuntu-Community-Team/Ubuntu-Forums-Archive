---
title: "struggling to share ethernet via wifi to phones!"
date: 2013-12-28
forum: Networking &amp; Wireless
---

### Post by joshuaos on 2013-12-28
Hello!  I am attempting to share my ethernet connection out via wifi in "access point mode" (on a fresh install of ubuntu 13.10 x64) so that phones and such can access the internet!

I followed this guide:
[http://forum.xda-developers.com/showthread.php?t=2009381](http://forum.xda-developers.com/showthread.php?t=2009381)

It fails with the following:

```

 * Restarting DNS forwarder and DHCP server configuration syntax check                                       [fail] 
net.ipv4.ip_forward = 1
Configuration file: /etc/hostapd.conf
Failed to create interface mon.wlan0: -23 (Too many open files in system)
Try to remove and re-create mon.wlan0
Failed to update rate sets in kernel module
Using interface wlan0 with hwaddr 00:0d:f0:ac:6b:80 and ssid 'babybird'
net.ipv4.ip_forward = 0
 * Stopping DNS forwarder and DHCP server dnsmasq                                                                    * (not running)

```

My network device as listed with lspci -v is:

```

04:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723AE PCIe Wireless Network Adapter
	Subsystem: Realtek Semiconductor Co., Ltd. RTL8723AE PCIe Wireless Network Adapter
	Flags: bus master, fast devsel, latency 0, IRQ 17
	I/O ports at 3000 [size=256]
	Memory at e0500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: rtl8723ae

```

Please, any help would be so vastly appreciated.  It's amazing to me there isn't a nice graphical way to do this yet!

Thanks!
Joshua

---

### Post by ian-weisser on 2013-12-29
> **joshuaos said:**
> ```

 * Restarting DNS forwarder and DHCP server configuration syntax check                                       [fail] 
net.ipv4.ip_forward = 1
Configuration file: /etc/hostapd.conf
[COLOR=#ff0000]Failed to create interface mon.wlan0: -23 (Too many open files in system)
Try to remove and re-create mon.wlan0[/COLOR]
Failed to update rate sets in kernel module
Using interface wlan0 with hwaddr 00:0d:f0:ac:6b:80 and ssid 'babybird'
net.ipv4.ip_forward = 0
 * Stopping DNS forwarder and DHCP server dnsmasq                                                                    * (not running)

```

Did you check to see if mon.wlan0 is already created?
If so, did you remove it?

---

