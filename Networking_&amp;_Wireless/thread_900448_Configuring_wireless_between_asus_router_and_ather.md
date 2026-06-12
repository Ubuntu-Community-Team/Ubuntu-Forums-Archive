---
title: "Configuring wireless between asus router and atheros zd1112b dongle"
date: 2008-08-25
forum: Networking &amp; Wireless
---

### Post by marcomangiante on 2008-08-25
Hello to everyone,

I have kubuntu 8.04 and have an asus wl-500gp v2 connected with an huawei e220 modem to connect to internet. For my pc I acquired the Atlantis Land wireless usb adapter NetFly usb-54 that has the atheros zd1211b chipset on board (the product number of the atlantis adapted is A02-UP-W54 v1.1).

It seems that the dongle is recognized, even if it seems that it has only 1Mb capacity.

Now I want to connect my pc to the router in wireless mode so I can have the internet connection, but when I use the knetworkmanager I can't do it. I tried to configure the knetworkmanager, but I think it lacks some parameters.
I set the router with these parameters:

ssid: asusnetwork
Authentication Method: WPA2-Personal
WPA encryption: AES
WEP Encryption: WEP-128 bits

Now under knetworkmanager these parameters are not present, it seems that it is present only the WEP one, or similar.

Could please someone help me? It is possible to set all with knetworkmanager? I like it because give to me a visual feedback of the connection, if it is up or down.
I tried to install kwlan but have no luck: it tries to start wpa_applicant but I don't found the appropriate driver on the list. 

Hope someone can help me or dictate the right direction.

--
Regards,

Marco Mangiante

---

### Post by marcomangiante on 2008-08-26
Hello,

I also noticed this strange problem: after some time, if I do iwconfig, the eth1 (that is the dongle) is no more present: why?

Hope someone can help me to resolve these little problems.

--
Regards,

Marco Mangiante

---

