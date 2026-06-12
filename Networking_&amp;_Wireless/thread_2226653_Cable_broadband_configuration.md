---
title: "Cable broadband configuration"
date: 2014-05-28
forum: Networking &amp; Wireless
---

### Post by linuxyogi on 2014-05-28
Hi,

I have migrated from DSL to Cable broadband today.

This ISP does not offer any CPE (Customer Premises Equipment).

Its  simply a LAN cable which is connected to the onboard NIC.

They have provided me a IP, SM, DG and also a specific primary DNS server. I can use any DNS of my choice as the 2nd and 3rd.

Problem is every time I boot there is no Internet connectivity. I need to open Firefox, browse to their login page (which is on the intranet) and login.

The login page says 

> [SIZE=1][FONT=Tahoma][COLOR=#000000][B]To start surfing, Minimize this login window and open a new browser window.
 Please do not close this Window without logging out[/B][/COLOR][COLOR=#ff0000]
[/COLOR][/FONT][/SIZE]

My question is, is there a way I can configure this connection is Network Manager ?

---

### Post by vasa1 on 2014-05-28
Could you expand "They have provided me a IP, SM, DG"?

---

### Post by linuxyogi on 2014-05-28
> **vasa1 said:**
> Could you expand "They have provided me a IP, SM, DG"?

Sorry.

They gave me an IP address, subnet mask and default gateway.

In short  no dhcp.

---

### Post by oldfred on 2014-05-28
Then you should just be able to set a fixed address into Network Connections using manual instead of DHCP.

Screenshot is just setting a fixed address into my router, so it is a local IP number, but you should be able to use the addresses given and plug those in.

I might still purchase a router. Then you also could connect addition devices and have some isolation from Internet to your system. You would then configure router with fixed address and could use DHCP to router or set a fixed local address to router that is outside the auto assigned range. Or set router to only load your fixed address.

---

### Post by linuxyogi on 2014-05-28
> **oldfred said:**
> Then you should just be able to set a fixed address into Network Connections using manual instead of DHCP. Screenshot is just setting a fixed address into my router, so it is a local IP number, but you should be able to use the addresses given and plug those in. 

I have already done that part. .


> **oldfred said:**
> 

I might still purchase a router. Then you also could connect addition  devices and have some isolation from Internet to your system. You would  then configure router with fixed address and could use DHCP to router or  set a fixed local address to router that is outside the auto assigned  range. Or set router to only load your fixed address.

I have no idea about what type of router I need to buy. I have used only DSL connection so far and as you know it requires an adsl router. 

But I doubt I can use that with this type of a connection because the incoming connection is not a RJ11 but a RJ45. There is only 1 RJ45 port on my adsl router and that is for connecting the router to the PC.

I am searching for a way to make the login process automatic. Is it possible to do that from within Ubuntu ?


Frankly I dont wanna buy any hardware atm simply because I dont need to share this connection with any other device.

---

### Post by oldfred on 2014-05-28
Modem and router usually are two devices, although my new Comcast device is a modem & wireless router.

With my old Comcast system I originally directly connected to modem. But it was DHCP.
But then I added a wireless router. I even used a inexpensive $20 one that worked.

---

