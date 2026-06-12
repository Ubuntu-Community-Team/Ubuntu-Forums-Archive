---
title: "Routine update to Ubuntu 18.04 LTS broke wired networking."
date: 2021-03-11
forum: Networking &amp; Wireless
---

### Post by John Nagle on 2021-03-11
After letting the updater run, and rebooting, wired Ethernet no longer works. Can't ping 8.8.8.8 or even the local router. 

 
Suspect that NetworkManager can't talk to the device.


 
Syslog line: "device (enp3s0) state change: unmanaged->unavailable (reason 'managed', sys-iface-state: "external")

 
Old system, running for years until this update broke something.
Fortunately I have a second Ubuntu system nearby, so I can post here.

Looking for solutions, found:

[https://askubuntu.com/questions/71159/network-manager-says-device-not-managed](https://askubuntu.com/questions/71159/network-manager-says-device-not-managed)

So, checked NetworkManager.conf. No mention of Ethernet.
Checked /etc/network/interfaces. No mention of Ethernet.

It looks like the "upgrade" may have been trying to move a device to Network Manager, but didn't finish the job.

...

And now, after an hour, it's up. Huh?

---

### Post by John Nagle on 2021-03-11
So then I rebooted the system, and now networking is broken again.

---

### Post by John Nagle on 2021-03-11
Trying to restart networking from the GUI produces the syslog message:

Device (enp3s0) state change: ip-config -> failed (reason "ip-config-unavailable", sys-iface-state "managed").

---

### Post by John Nagle on 2021-03-11
/etc/netplan is an empty directory. That seems wrong.

/etc/network/interfaces has only

auto lo
iface lo inet loopback

The hardware seems to be up, though. Tried

sudo ethtool enp3s0

It finds the device, and says link detected: yes. 

sudo ethtool -S enp3s0

shows tx_packets 825, rx_packets 3647, and no errors.

So the hardware is alive, but the networking management systems are missing something.

---

### Post by germarsh on 2021-03-11
Is it a static IP address? I have no problem with DHCP addresses but as soon as I set a static address it refuses to speak to anything? I have just installed Ubuntu on an ex-windows laptop.

---

### Post by John Nagle on 2021-03-11
No, default configuration using DHCP.

All I did was let Ubuntu "update" the system.

---

### Post by John Nagle on 2021-03-11
Tried adding a default netplan, because /etc/netplan was empty.

network:
  version: 2
  renderer: NetworkManager

Netplan try accepts that, but it doesn't help.

---

### Post by John Nagle on 2021-03-11
Looking at syslog, the machine says it's sending a DHPDISCOVER request, but there's no indication of a reply.
The router (Sonic/AT&T/Nokia 1Gb/s) reports IP allocation "pending" while this is in progress, with the correct
MAC address. So desktop and router are talking in at least one direction. 

ifconfig says UP, BROADCAST, RUNNING, MULTICAST  mtu 1500.

It shows 723 packets as "dropped". No errors, just "dropped". 4073 packets received since book, 821 transmitted.

---

### Post by John Nagle on 2021-03-11
Restarted the router. After that, the machine was able to get a DHCP lease and connect.

Rebooted again, to make sure this would survive a reboot, and it connected again. 

So, DHCP bad lease release on the router side?

---

### Post by chili555 on 2021-03-11
```
So, DHCP bad lease release on the router side?
```Entirely possible. You might try flashing the latest firmware on the router. If that doesn't help, then perhaps the router is defective. If it is ISP provided, I'd call them and ask for a replacement.

---

