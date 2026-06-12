---
title: "Traffic forwading and Internet sharing"
date: 2008-02-14
forum: Networking &amp; Wireless
---

### Post by tetralis on 2008-02-14
I will start with a long description before the questions :popcorn:

I have managed to share my mobile Internet conenction in the follwing way:

Internet :::::3G USB modem ---- Computer 1 (Ubuntu) ....WLAN router/AP ..... Computer 2 (Win 2000)

::::: = Air interface (WCDMA 3G)
----- = USB cable
..... = Air interface (WLAN)
My WLAN router/AP is Speedtouch 716 WL

In order to get this to work I have to:
1. Forward the Internet traffic between ppp0 (the USB dail up connection) and wlan0 (the wireless card) on Computer 1.
2. Start DHCP-server on Computer 1
3. Set up the WLAN router/AP to use the DHCP on Computer 1

So Computer 1 and 2 will connect to the AP and get there ip-config through the DHCP server on Computer 1. Now I can have access the Internet both computers. I assume that other computers can connect have Internet access in the same manner as long as they are connected to the WLAN router/AP.

This works nice except for the follwing limitations:
1. Some times I need to get the wlan0 interface down and up before it clicks.
2. I can't ping computer 1 and computer 2 with thier internal ip-addresses (the ones that the dhcp-server assigns 192.168.0.X) from each others.

To my questions :)
I would like to skip step 2 and 3 above and instead start the DHCP server on the WLAN router AP. When I do so computer 2 can't access the Internet anymore! 
I assume that because I need to forward the traffic between the two IP-addresses that are assigned to computer 1 and 2 in the AP. Am I correct? Anyway what is missing? Should my routing table in the WLAN router/AP look in a certain way or do I need to do something else? What?

---

