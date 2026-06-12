---
title: "Network card picks up router's external IP address"
date: 2008-07-23
forum: Networking &amp; Wireless
---

### Post by j.mills on 2008-07-23
I've just had broadband activated and the ISP (Force9, ie. PlusNet) sent me a D-Link DSL-320B router. I'm on Edgy Eft Ubuntu and I think it's a RealTek network interface.

The router uses DHCP and supplies a local IP address to my network card (eg. 192.168.1.3), all fine. (I'm checking this through System / Admin / Network Tools.) Then I attach the router to the ADSL line and it clearly connects to the ISP - the router's DSL light comes on and its status page shows that it has picked up an external IP address from the ISP, along with DNS servers.

As soon as that happens, my network card acquires the same network address as the router just picked up - 87.something. I can no longer even connect to the router at that point, and have to put the PC on a static 192. address to do so. I can't get to any web pages.

I've tried with and without static address and DHCP, and also twiddled the DNS entries (System / Admin / Networking) and the proxy info in Firefox, to no effect. I spoke to the ISP and they reckoned the router should not be providing the external address to my network card, so they sent me a new router - which does exactly the same. I'm going to try a Windows laptop tonight to see if it works for Windows.

Ideas welcomed, bearing in mind that I know next to nothing about Ubuntu/Linux at the command line.

---

### Post by dmizer on 2008-07-23
your problem is with the router settings, not with ubuntu.  your computer will never see the external address unless your router allows it to.

---

### Post by j.mills on 2008-07-23
That's what I hoped! I still don't know how to fix it, but at least I can refer it to the ISP, especially if it turns out that the Windows machine won't work with it either.

Thanks for that.

---

### Post by eentonig on 2008-07-23
Problem is indeed with the telco equipment. Make sure they confirm you that their service includes a router or not? 

Did you receive loging credentials for the router (which actually acts as a bridge for the moment)?

---

### Post by eentonig on 2008-07-23
Problem is indeed with the telco equipment. Make sure they confirm you that their service includes a router or not? 

Did you receive loging credentials for the router (which actually acts as a bridge for the moment)?

---

### Post by j.mills on 2008-07-23
Yes, the Internet provider supplied the router (and its replacement, same model) along with the login details. I'll take the problem back to them when I've tried the Windows PC. (Naturally they don't guarantee to support any other OS!:))

---

### Post by clarkkillick on 2008-08-09
Hello,

I've been having the same problem with a DSL-320b (which D-Link describe as an ethernet modem rather than a router) from Plusnet, but not with Ubuntu.

Firsly, what was successful.  The network card for this was a Netgear FA311 (version 1):

I started Ubuntu 8.04 "live" from the CD, and opened Firefox, but when I tried to browse, Firefox couldn't connect.  I right-clicked the network icon near the top-right of the screen, and clicked "Manual Configuration".  In the window that opened, I clicked the "Wired Connection", and then un-ticked "Roaming Mode".  In the "Configuration" window I selected "DHCP" and then OK (or something like this; I'm in Windows now, writing from what I remember).  Ubuntu took a few seconds before reporting success, after which Firefox could browse the Web.

I've tried to connect in Puppy Linux 4.00, Knoppix 4 and 5.1.1, and DSL (all running "Live" from CD) and have had the problem described.  I can connect to the DSL-320B by entering 192.168.1.1 in the address bar of any browser, I can log on to the modem's setup pages (and I've successfully configured it in Knoppix and Puppy), but only until it connects to my ISP.  After that, configuration utilities show 87.112.something.something as the IP address (which I think is the external address), and browsers no longer reach 192.168.1.1.

I've had the same problem with a US Robotics router with a Netgear FA310TX network card, ADSL24 as an ISP, running Puppy 4.00 live.  There's a firmware update for the DSL-320B, but so far I'm too scared to try it...  The DSL-320B seems OK with Windows XP SP2 and Windows 98SE.

I realise that I'm not reporting a problem with Ubuntu here, but perhaps this will help j.mills, and I'd appreciate any help getting my other "live" CDs to connect.

Regards,
Clark

---

### Post by chili555 on 2008-08-09
I have seen this before. After an hour of hair-pulling and cursing with a buddy on IM, it turned out he had his router connected improperly.

Please be sure the DSL line connects to the DSL modem; then the DSL modem connects to the **WAN** port on the back of the router and all computers connect either wirelessly or to **LAN **ports on the back of the router. All cable switching should be done with the router and DSL modem turned off. Power up the DSL modem first and let it stabilize, the power up the router and then power up the computer(s). Do your symptoms disappear?

---

### Post by push1n420 on 2008-10-17
this is buggin the heck outta me, i'm using a netgear FA311 on an old Celeron 633 thats running Ubuntu's Hardy Haron rather poorly. I just dl'd Puppy and booted from a live cd. in Ubuntu i have no problem connecting except from the fact i have unplug and plug back into the router every time i reboot. Puppy finds a live network no problem. the router finds my pc as Puppypc, but i cannot surf the web or detect other pc's on the network. plus Puppy is showing my IP address as something i know it is not. should i try a different network card??

---

### Post by tousman on 2009-04-02
In my case my wireless card (intel 3945 abg on lenovo T61) was picking up an external ip with puppy until I established a wired connection to my router.
I experienced the same problem under XP SP2. 
Hopes that help somes.
Manu

---

