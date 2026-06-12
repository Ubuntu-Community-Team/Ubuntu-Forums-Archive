---
title: "Roaming mode in Network Manager"
date: 2007-12-19
forum: Networking &amp; Wireless
---

### Post by Matthai on 2007-12-19
Hi,

what is "roaming mode" in Network Manager? It can be set if you go to "Manual configuration" at nm-applet, and choose properties of ethernet device. Then you can set dynamic or static IP address, or switch to roaming mode.

However - in roaming mode, my eth0 connection is not working. But if I do not have roaming mode enabled, I do not se VPN connections...

---

### Post by Edho on 2007-12-19
As i understand...

In Roaming the networkmanager takes by itself the best way of connection with te network.
No need for action by the user, when he puts a wire in the ethernet-connection.
Then NM will switch to wired. (= the best connection)

Thats the theory.
I don't tryed it yet.

---

### Post by BluePlum on 2007-12-19
Roming mode is awsome, you can see all networs with one click, and See signal strengh

---

### Post by Matthai on 2007-12-19
OK, I must be stupid or something, but...

I have wired connection, and I have fixed IP address. 

I unplug ethernet cable.

I go to manual configuration and set "roaming mode" for eth0.

Then I plug ethernet cable in. At nm-applet I see "wired connection" selected.

But internet is not working. Taht is logic, because I need to set up my fixed IP address. 

If I switch "roaming mode" off and manually set IP address, internet starts working, BUT when I click to nm-applet, I do not see option for VPN connection.

How to solve this?

---

### Post by trobbins on 2007-12-19
I use two wired NICs and I had to disable roaming mode for DHCP to work correctly.  I tried manually renewing my lease with dhclient but it failed to work.  I had to reboot my PC, but now, with roaming mode disabled, DHCP on my wired NICs works as expected.

---

### Post by Matthai on 2007-12-19
Well, the problem is that if roaming mode is disabled, I cannot see VPN connections...

---

