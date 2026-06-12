---
title: "/etc/network/interfaces not working ?"
date: 2008-11-05
forum: Networking &amp; Wireless
---

### Post by Tex-Twil on 2008-11-05
Hello,

somehow I'm not getting a ip form my dhcp server when I restart the network. I have this in my /etc/network/interfaces:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

```

But no IP assigned. When I run 

```

dhcpclient eth0

```

I get the IP correctly.

Any ideas ?

Thanks,
Tex

---

### Post by dmizer on 2008-11-05
You may have to diasable NetworkManager: [https://help.ubuntu.com/community/NetworkManager#Disabling%20NetworkManager](https://help.ubuntu.com/community/NetworkManager#Disabling%20NetworkManager)

---

### Post by Tex-Twil on 2008-11-06
> **dmizer said:**
> You may have to diasable NetworkManager: [https://help.ubuntu.com/community/NetworkManager#Disabling%20NetworkManager](https://help.ubuntu.com/community/NetworkManager#Disabling%20NetworkManager)
Hi,
I tried this but it doesn't seem to work. Still no IP when I reload the network.

Thanks,
Tex

---

### Post by dmizer on 2008-11-06
You say that you do not get an IP when you reload the network. Do you get an IP when the system starts?

---

### Post by Tex-Twil on 2008-11-06
> **dmizer said:**
> Do you get an IP when the system starts?
Nope. That's the problem. My HOME is on a NFS so I have to log in as root first, run **dhcpclient eth0** to get an IP, then remount my home.

---

### Post by dmizer on 2008-11-06
Please post the output of:
```
lshw -C network
```

---

### Post by Tex-Twil on 2008-11-06
```
~ $ sudo lshw -C network

  *-network
       description: Ethernet interface
       product: NetXtreme BCM5754 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1a:a0:c5:0c:1c
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full firmware=5754-v3.15 ip=192.168.0.56 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s

```

Here it is ;)

---

### Post by dmizer on 2008-11-06
This is from Dapper, but here's hoping: [http://ubuntuforums.org/showthread.php?t=323667](http://ubuntuforums.org/showthread.php?t=323667)

It's the best I could dig up.

---

