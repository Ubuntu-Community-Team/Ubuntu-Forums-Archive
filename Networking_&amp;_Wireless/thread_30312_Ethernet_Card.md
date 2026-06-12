---
title: "Ethernet Card"
date: 2005-04-28
forum: Networking &amp; Wireless
---

### Post by larry on 2005-04-28
Dear all,
I am a newbie. Yesterday I physically added an ethernet card  (intellinet realtek chipset).
I am going to try using it with a router I will be delivered in a couple of days'.
Now, the card seem to be detected (in the hardware  detection the device and vendor are correct, on the status line I simply read "status". The bus type is PCI, but the following devices vendor and capabilities lines read unknown).
The card has a couple of leds which should blink, flicker, do something...but they remain dead.
The real test will be when I get the router and I can test if I can put my Pc online, but I would like to know if all this is normal and if somebody can help me out with this.
Cheers
Larry

---

### Post by drummer on 2005-04-28
[QUOTE=larry]Dear all,
I am a newbie. Yesterday I physically added an ethernet card  (intellinet realtek chipset).
I am going to try using it with a router I will be delivered in a couple of days'.
Now, the card seem to be detected (in the hardware  detection the device and vendor are correct, on the status line I simply read "status". The bus type is PCI, but the following devices vendor and capabilities lines read unknown).
The card has a couple of leds which should blink, flicker, do something...but they remain dead.
The real test will be when I get the router and I can test if I can put my Pc online, but I would like to know if all this is normal and if somebody can help me out with this.
Cheers
Larry[/QUOTE]
 Most wired network cards should work out of the box and it's a good sign that its info is correct in the device manager. As for the lights, from my experience, the lights on my NIC only light up when a cable is connected to it and to a router/other NIC.. so i wouldn't worry about that. Just wait and see when the router arrives (unless someone else knows of any issues with the realtek chipset).

---

### Post by heimo on 2005-04-28
Sounds quite normal. I may have realtek integrated card on my machine, too. Ethernet cards are so painless to install in Linux, support has been good for a long time. I'd only avoid cards which name matches pattern *win*
 
On terminal window you can run *ifconfig *or *ifconfig eth0 *and you should see eth0 listed (with lots of information you don't need to worry about). If you can configure IP for that device (for example 192.168.0.1) and ping it using *ping 192.168.0.1 *and if you see replies, it's 99.99% sure to be healthy. (I don't know about the graphical admin tool, but if it asks for subnet mask, try 255.255.255.0 with this example). Of course you need to configure it back to what you need it to be - perhaps DHCP (dynamic configuration, no need to enter values).
 
Hopefully this helps.
 
Oh, one more piece of information. You can check the configuration in /etc/network/interfaces file.

---

### Post by larry on 2005-04-28
Thanks to both of you. I will try your suggestions and let you know as soon as I receive the router.
Larry

---

### Post by heimo on 2005-04-28
Oh. My simple test (not in any way comprehensive) was meant to test the card before connecting to router (if it can be configured, it most probably is ok). Of course you don't need to do that beforehand - my point here is just to warn that the factory default for your routers IP may very well be that 192.168.0.1, so check the manual what to do. :) If it speaks about DHCP, use DHCP... (Oh my, not my best day...) and if it gives specific network settings, use those instead*.


*) These all depend lot on your setup / possibly ISP.

---

