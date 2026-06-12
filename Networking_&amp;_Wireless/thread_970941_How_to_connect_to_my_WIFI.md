---
title: "How to connect to my WIFI?"
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by Zoree on 2008-11-04
Hi.

I'm new to Ubuntu, I installed my first ubuntu dekstop for about 2 months ago now. It worked fine with Wifi.

Now i have made a upgrade from 8.04.1 to 8.10 and now i cant get my wifi connection to work.

Can someone please tell me how to set it up?

---

### Post by IndyGunFreak on 2008-11-04
Need a lot more info than that to even begin to try and help you, first, what wireless device are we talking about here?

If you don't know, and assuming this is an internal wireless device on a laptop, open a terminal and type "lspci" no quotes, hit enter, and post the output here..

IGF

---

### Post by prematurebaby on 2008-11-04
I know what your talking about. Everybody had that problem with the upgrade. This thread helped me. 
[http://ubuntuforums.org/showthread.php?t=968797]("http://ubuntuforums.org/showthread.php?t=968797")

---

### Post by Zoree on 2008-11-04
prematurebaby -> that page you linked to was a guide that shows how to allow some modules to be loaded so that the wlan card will start.

My wifi card is loaded fine if i make a ifconfig in terminale it will show my network interfaces. eth0, lo, wlan0, wlan0:avahi and wmaster0

My problem is that i dont know how to set it up to connect to my wifi.


IndyGUnFreak -> lspci tells me "0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)"

Its a DELL D520 laptop i have.

---

### Post by IndyGunFreak on 2008-11-05
> **Zoree said:**
> prematurebaby -> that page you linked to was a guide that shows how to allow some modules to be loaded so that the wlan card will start.

My wifi card is loaded fine if i make a ifconfig in terminale it will show my network interfaces. eth0, lo, wlan0, wlan0:avahi and wmaster0

My problem is that i dont know how to set it up to connect to my wifi.


IndyGUnFreak -> lspci tells me "0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)"

Its a DELL D520 laptop i have.

Well, that could be an end-user issue.. What happens when you click on nm-applet?  Do you not see your network?

1.  You need to know your ESSID/Password for your network... Is the laptop dual booting?  You might be able to get this info off of XP/Vista.

Once that is done, left click on nm-applet, choose create new wireless network, and enter the parameters for your network.

---

### Post by Zoree on 2008-11-06
arrhh... 

That was strange... 

IndyGUnFreak -> I have now inserted the ESSID and PASSWORD for my Wireless and then i connect just fine. but i didnt enter the MAC of the AP or NIC and then it workeds, before I made this thread I did enter those 2 numbers and it didnt work... But great it works now...

Thanks for your help.

---

