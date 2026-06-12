---
title: "Wireless With Static IP"
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by plk on 2008-05-29
Hey All, 
I'm having some trouble with my wireless connection at the moment. The problem is that i used to connect to my belkin router using DHCP since my ISP would provide me an IP address.

I have now moved from the flat and there is an access point which I can connect to but I have been told to use a static IP (which I have been given).

My problem is that when I configure my network card to use a static IP for my connection (giving the ip, dns, gw, essid), Network manager doesnt see any wireless ap's no more and tells me that the configuration is manual. I'm like OK, as long as I can connect to the web, but obviously, I can't !

If I try to use dhcp for my card, network manager sees all the access points, I can connect to the one Im interested in but no luck, cannot connect to the web.

Everything works fine under XP when configure the TCP/IP protocol for my wireless card. But obviously, Id rather be on ubuntu, thats why im seeking help.

Hopefully I explained my issue well.

Thanks in Advance!
plk

---

### Post by superprash2003 on 2008-05-29
are you able to ping the AP? please post ifconfig output

---

### Post by jimv on 2008-05-29
Try using WICD ([http://wicd.sourceforge.net](http://wicd.sourceforge.net)) instead of Network Manager.  It has a spot where you can set the IP address for your wireless.  Here's a screenshot of the WICD configuration:

[IMG]http://www.jimvernon.com/WICD.png[/IMG]

---

### Post by plk on 2008-06-01
Ill post the ifconfig output tomorrow as Im going to bed. Do I need to uninstall network manager before installing wicd?

cheers

ps. ive read that wicd is much better at handling static ip and dns so fingers crossed :-)

plk

---

### Post by plk on 2008-06-02
Thanks jimv, 
wicd made it really easy to connect with a static IP :-)

Thanks Again !!

plk

---

