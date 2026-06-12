---
title: "pppoe connection problem"
date: 2008-09-28
forum: Networking &amp; Wireless
---

### Post by PeterP24 on 2008-09-28
Hi! My problem is that the pppoe connection fails (the network disconnects) after some time (after 20 minutes more or less - I didn't recorded) and I am forced to do :
> # sudo poff dsl-provider
# sudo pon dsl-provider 
to activate it again. I am sure this is related to my hardware or my network settings because my coleague doesn't have this problem (he uses the same connection). I am using hardy heron for amd64. My computer is a Dell Inspiron 1501 laptop. 

I connect myself to the network through my network card (this is a LAN with a decent traffic speed).

The lspci | grep eth* command returns the following:
> 05:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
with the mention that the wireless connection works for a connection provided by another internet provider (not pppoe). 

I need help to fix this problem, since it is really frustrating to experience this especially in the middle of my favorite internet show.

Best regards 

Peter

---

### Post by d.marcu on 2008-09-29
are you using a usb network adapter? if so you may need a powered usb hub. I had similar problems with my wifi usb adapter. internet disconnects and i have to eject/reinsert the adapter and reconnect.

---

### Post by PeterP24 on 2008-09-29
I am using the laptop integrated ethernet network card (BCM4401-B0 100Base-TX from Broadcom). 

Best regards,

Peter

---

