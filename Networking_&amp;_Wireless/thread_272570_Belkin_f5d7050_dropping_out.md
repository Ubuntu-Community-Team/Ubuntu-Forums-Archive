---
title: "Belkin f5d7050 dropping out"
date: 2006-10-06
forum: Networking &amp; Wireless
---

### Post by glaeven on 2006-10-06
I got a Belkin USB Wireless Adapter yesterday, and I finally got it installed. It took a while but it worked. I got on Firefox and it worked fine. After 5-10 minutes or so, it stops. I will try to load a page, and it wont find a connection. Any solutions?

I am using Dapper Drake on a Compaq Presario 5000 (old peice of junk...). The adapter is version 3001 (which seems to be the same as 300)

---

### Post by glaeven on 2006-10-06
please, some one help me here. its really an obnoxious probem.

---

### Post by gtrtoolman on 2006-11-12
I had the same issue with a WUSB54GV4 adapter in Dapper and Edgy until I went into /etc/network and remarked # iface eth0 in the interfaces file so it would not look for it. Has not dropped out since. Hope this helps.

gtrtoolman

---

### Post by FrodoB on 2006-11-12
Can you post more details on your F5D7050 ver3001 please. We need to see the outputs from:

lsusb

iwconfig

the contents of /etc/network/interfaces

Also what are you using for a driver? The Ralink rt73 driver or something else?

---

