---
title: "[SOLVED] Wireless Dell Inspiron 6000"
date: 2008-03-04
forum: Networking &amp; Wireless
---

### Post by munozm on 2008-03-04
I'm just posting this to hopefully help people who do a search.

Basically my problem was that my wireless suddenly stopped working.  I spent some time restarting the network ( sudo /etc/init.d/networking restart ), shutting down the interface through the gui and the cli but nothing worked.  

I finally ran iwconfig and found: 

eth1      radio off  ESSID:""  

I realized the radio was shut off.  I don't know how to enable this through the gui or cli, but I pushed the function key ( fn ) and F2 (key with the wireless symbol) and the iwconfig didn't show the radio off anymore.  To be honest, I should have remembered this from a while ago but I don't recall shutting it off.  

eth1      unassociated  ESSID:""

This is still unregistered, but the wireless started working again where I could select my ssid through the gui.  Just to show you a registered connection for reference:

eth1      IEEE 802.11g  ESSID:"prorouting"

Hope it helps someone.
Mike

---

