---
title: "How do I access disk plugged into USB port of my router"
date: 2020-08-21
forum: Networking &amp; Wireless
---

### Post by desconocido on 2020-08-21
I have recently added an Orange Livebox ADSL router to my LAN as an additional WiFi Access Point and also as a network disk server.

This is an Arcadyan router rebadged by Orange for the Spanish market.

The Wifi works fine (connected by Ethernet to the rest of my existing network).

The router admin pages recognise the device plugged into its USB port as a FAT32 device and says that > In order to access your USB disks from the LAN it is enough you enter the following URL on your Browser: \\Livebox

That does not work (sounds a bit like Windows to me) and there is no more help available.

Any idea how I can access the disk from Ubuntu?

---

### Post by chili555 on 2020-08-21
Open Files > Other Locations and enter in the Connect to Server box:

```
smb://192.168.x.y
```Of course, subsitute the actual IP address of your router.

[https://websiteforstudents.com/wp-content/uploads/2017/11/ubuntu_network_shares-1.png](https://websiteforstudents.com/wp-content/uploads/2017/11/ubuntu_network_shares-1.png)

---

### Post by ajgreeny on 2020-08-21
There may also be a setting in the router setup windows which enable or disable file sharing via the USB on the router itself; there certainly is on mine so have a look around yours.

---

### Post by desconocido on 2020-08-22
> smb://192.168.x.y

Thanks, that works a treat.

---

### Post by desconocido on 2020-08-22
> **ajgreeny said:**
> There may also be a setting in the router setup windows which enable or disable file sharing via the USB on the router itself; there certainly is on mine so have a look around yours.

Thanks, I had already checked the router setting.

---

