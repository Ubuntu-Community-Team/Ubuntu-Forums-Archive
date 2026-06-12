---
title: "Access a 10.0.0.x network computer from 192.168.1.x"
date: 2020-11-30
forum: Networking &amp; Wireless
---

### Post by michael351 on 2020-11-30
My Internet provided modem/router hosts my 192.168.1.x network for all my connected devices.
One of these devices is a netgear wireless router which will not work properly in bridge mode without DHCP running.
So I set it up as a router (behind my ISP router) with the customary 10.0.0.x network running DHCP. Devices such as cell phones and tablets connect to this router and are assigned 10.0.0.x addresses. It has its own 192.168.1.129 address assigned to it by the main router.

Recently, I connected a network player to one of the wired ports on the back of the netgear router out of position convenience. It is assigned a 10.0.0.x address by the netgear router. I would like to access the web page of this device (control music), but I don't know how to get to it from my 192.168 network where my desktop and other devices are connected.

Would someone suggest how to do this? Thanks

---

### Post by SeijiSensei on 2020-11-30
The likely problem is that the ISP router doesn't know what to do with packets for 10/8 addresses. You would need to modify that router's set up and add a "static route" to the 10/8 network. Otherwise it will send that traffic upstream to the Internet where it will be dropped. To do this requires that you can access the configuration page in the ISP's router.

I've connected routers via a "daisy-chain," but I connected all my local network devices to my router, and none to the ISP's. Is that an option for you? If you have too many devices, buy an Ethernet switch and plug it into the LAN side of the Netgear router.

[https://www.newegg.com/Switches/SubCategory/ID-30?Order=1](https://www.newegg.com/Switches/SubCategory/ID-30?Order=1)

---

