---
title: "Netlink Error when attempting to switch Ethernet setting to Full Duplex"
date: 2023-03-13
forum: Networking &amp; Wireless
---

### Post by vincent911 on 2023-03-13
I did a fresh install of Ubuntu 22.04 and noticed my wired internet speeds were about in half via speed tests.


 My ethernet runs through a Dell 3100 Docking Station via USB with updated DisplayLink drivers.

 
Details of sudo lshw-c network here:

 
  *-network
       description: Ethernet interface
       physical id: c
       bus info: usb@2:1.3
       logical name: enx0c37963ab0ab
       serial: 0c:37:96:3a:b0:ab
       size: 1Gbit/s
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=cdc_ncm driverversion=5.19.0-35-generic duplex=half firmware=CDC NCM ip=192.168.0.23 link=yes multicast=yes port=twisted pair speed=1Gbit/s

 
When I look to change the duplex setting to full using: sudo ethtool  -s enx0c37963ab0ab duplex full I receive the following error:

 netlink error: Operation not supported

 
I'm not sure what to do next. Any help is greatly appreciated.

---

### Post by vincent911 on 2023-03-13
The reencrypt feature on my load balancer wasn't allowing the Docker Container to return any usable data.

---

