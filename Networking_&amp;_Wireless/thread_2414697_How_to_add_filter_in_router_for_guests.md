---
title: "How to add filter in router for guests"
date: 2019-03-14
forum: Networking &amp; Wireless
---

### Post by jsjpandey on 2019-03-14
I am having cafe with Tenda Router N301 which doesn't have guest mode built in. I want to share the wifi with customers but with some limits like usage or time limit. As a noob with linux I don't know how to do it.

---

### Post by wildmanne39 on 2019-03-14
*Thread moved to **Networking & Wireless a more appropriate sub-forum**.*

Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

---

### Post by TheFu on 2019-03-14
> **jsjpandey said:**
> I am having cafe with Tenda Router N301 which doesn't have guest mode built in. I want to share the wifi with customers but with some limits like usage or time limit. As a noob with linux I don't know how to do it.

In a business, please use 2 separate routers if you don't have a business-specific router with the capabilities necessary.  If improperly configured, one of your customers might be able to intercept traffic with financial data or MitM any wifi devices you use for the business.

The guest wifi setup doesn't need to be great, but it does need to be separate.  IMHO.

In my small business and home, guests are on a different subnet than business computers, separated by firewalls. The guest network is treated like it is internet traffic and only gets the same access that anyone in a different country would get to the business side of the LAN.

Also, home routers generally don't support keeping all the guest connections separate, so 1 guest can hack all the others on the same wifi. More capable routers can keep each guest separate, so they cannot attack each other over wifi.

Does Tenda run Ubuntu?  Most routers do not.  

If you are interested in setting up a router using an x64/x86 computer, then we can help. Ubuntu Server can be configured as a router and can manage multiple subnets as a business would need to safely support separate guest networks and firewalls for the business-side of the network.  You can use the Tenda on the guest-LAN as a wifi AP and get a nice Ubiquity AP for the business users. Then they'd have different SSIDs, different credentials and different subnets.

Or you could treat wifi completely as untrusted like many businesses do and require the use of a full VPN to get inside the business subnet. I do this on my home network. Last place I worked did this too. Wifi was never trusted to get direct access to the corporate LAN.

---

