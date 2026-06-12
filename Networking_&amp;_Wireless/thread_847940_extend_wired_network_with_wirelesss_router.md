---
title: "extend wired network with wirelesss router"
date: 2008-07-03
forum: Networking &amp; Wireless
---

### Post by bcn17 on 2008-07-03
I realize this is not ubuntu specific although I always seem to get such good and quick responses on these forums I thought I would give it a try!

I have a BEFSR41 linksys router v2.00.1 connected via the WAN port to a modem and that to the internet.

I am trying to plug in a linksys WRT54GL flashed with dd-wrt v23.sp2 into the router via one of it's lan ports and have wireless access with my laptop. 

BEFSR41: 192.168.1.1 -DHCP server enabled
dd-wrt: set to 192.168.1.2 DCHP server disabled. 

I plugged in the dd-wrt via it's wan port and its lan port (different attempts) to Lan port 1 of the BEFSR41 to no avail. 

I still have the internet connection on the dd-wrt set to DHCP ( i believe this is telling it that it will receive it's IP based from a DHCP server) and the BEFSR41 to automatically obtain IP which I believe is the same thing just different names. 

On the dd-wrt router their are settings for dhcp server forwarding which I have enabled and I have also tried the same above settings with that instead of disabled. 

I have also tried setting the dd-wrt to RIP2 router or OSFT router instead of gateway with the above settings. 

Please any help would be greatly appreciated! I have an 80 foot cat5 that I'm sick of winding throughout my house!

---

### Post by HalPomeranz on 2008-07-03
Hmmm, if you connect LAN ports on the BEFSR41 and WRT54GL and disable the DHCP server and WAN port on the WRT54GL then everything should work (I have a somewhat similar setup here and it works for me).  But it sounds like you tried that and it didn't work.  Where did things break down?  Were you able to associate with the WRT54GL?  Did you get a dynamic IP address?

Have you considered getting rid of the BEFSR41 completely and just do everything with the WRT54GL?  The WAN port on the WRT54GL would connect to your cable modem (or whatever) and the WRT54GL could provide DHCP service for your internal LAN and wireless networks.

---

### Post by bcn17 on 2008-07-03
I can't use just the wrt54gl (I have tried and it works great) because we have more than 4 computers on a wired connection. 

I did try this a couple different times again with the WAN port assigned to switch. I also tried combinations with BasicSetup--> Internet connection- Disabled and with Basic settings--> network connection --> dhcp serve disabled. (both, 1 or the other, and neither disabled) I have tried each of those combinations with WAN port assigned to switch and not assigned to switch and all of those with my wrt54gl pluged in from the first routers lan port into the wan port and the lan port on the wrt54gl. I have also tried these settings with RIP2 and the other option router- OS?? under advanced routing instead of gateway. I am growing tired! - I think I'm going to try reflashing to v24 of the dd-wrt but I am also beginning to suspect the first router. After I try these things I can connect to the wrt54gl at 192.168.1.2 just fine however I get no internet and I can't connect to the first router at 192.168.1.1 through the wirless. If I unplug the cord going into the wrt54gl and plug it into my computer internet is just fine. So it's as if the wrt54gl won't talk with the first router or Can't see it for some reason. AAAAHHHHH!!!! Any other ideas?

---

### Post by HalPomeranz on 2008-07-03
> **bcn17 said:**
> I can't use just the wrt54gl (I have tried and it works great) because we have more than 4 computers on a wired connection.


You could just buy a small network switch with enough ports to connect all of your wired devices.  The switch would connect to the WRT54GL via a LAN port. 

> **bcn17 said:**
> 
I did try this a couple different times again with the WAN port assigned to switch. I also tried combinations with BasicSetup--> Internet connection- Disabled and with Basic settings--> network connection --> dhcp serve disabled. (both, 1 or the other, and neither disabled) I have tried each of those combinations with WAN port assigned to switch and not assigned to switch and all of those with my wrt54gl pluged in from the first routers lan port into the wan port and the lan port on the wrt54gl. I have also tried these settings with RIP2 and the other option router- OS?? under advanced routing instead of gateway. I am growing tired! - I think I'm going to try reflashing to v24 of the dd-wrt but I am also beginning to suspect the first router. After I try these things I can connect to the wrt54gl at 192.168.1.2 just fine however I get no internet and I can't connect to the first router at 192.168.1.1 through the wirless. If I unplug the cord going into the wrt54gl and plug it into my computer internet is just fine. So it's as if the wrt54gl won't talk with the first router or Can't see it for some reason. AAAAHHHHH!!!! Any other ideas?

0) Make sure that the range of IP addresses being handed out by the DHCP server on the BEFSR41 does not include the 192.168.1.2 address you're using for the WRT54GL

1) Reset the WRT54GL to the factory defaults (go to the Administration tab and select the "Factory Defaults" sub-tab to reset everything).

2) Connect to the WRT54GL after the reset.  Go to "Setup" --> "Basic Setup":

    2.a) Under "Internet Setup", "Connection Type" should be set to "disabled"

    2.b) Under "Network Setup" set "Local IP Address" to 192.168.1.2, "Subnet Mask" to the appropriate value (you're probably using "255.255.255.0"), "Gateway" to 192.168.1.1, and "Local DNS" to whatever's appropriate

    2.c) Set "DHCP Server" to "Disable"

3) Configure the settings under the "Wireless" tab as you wish

4) Save your changes and power off the WRT54GL

5) Make sure that there is an undamaged/unkinked RJ45 cable going from one of the LAN ports on the WRT54GL to one of the LAN ports on your BEFSR41

6) Power on the WRT54GL

If you follow the above instructions and your network connection does not appear to be working, then report what happens when you try the following:

A) Connect to the wireless network being supplied by the WRT54GL.  Can you ping any of the following: the WRT54GL, the BEFSR41, an external site like [www.google.com?](www.google.com?)  Can you connect to the management interface on the WRT54GL or the BEFSR41?  Can you connect to Google?

B) Repeat the above tests with your computer plugged into one of the LAN ports on the WRT54GL.

C) Repeat the above tests with a computer plugged into one of the LAN ports on the BEFSR41.

---

### Post by kevdog on 2008-07-03
So basically you want to have your ddwrt to act as an access point -- correct?  An access point is a wireless connection point that is plugged into a wired backbone.  That is what you have. Here is a link that describes what you want to do:

[http://www.dd-wrt.com/wiki/index.php/Wireless_Access_Point](http://www.dd-wrt.com/wiki/index.php/Wireless_Access_Point)

Take note of using either a LAN or WAN port.

---

