---
title: "Wlan"
date: 2008-03-13
forum: Networking &amp; Wireless
---

### Post by Exsecrabilus on 2008-03-13
Just like every other person here asking for help, I can't access the Internet.

When I switched to Ubuntu, it was because my Windows computer got so messed up that everytime I turned it on, it turned off.

It's an HP laptop, and it has a button for turning WLan on, (and a light turns on signaling it's on) and that's how I get Internet, with a Linksys.

The Linksys is working fine, but I can't turn WLan on, no matter how much times I press the button.

Help?

---

### Post by chewearn on 2008-03-14
There is the network manager applet (nm-applet) in your desktop notification area.  Turn on your WiFi (forget about the light for the moment), wait a minute or so, then left click on the nm-applet.  Did a menu pop-up, with your WiFi network listed?

---

### Post by Exsecrabilus on 2008-03-14
No matter how many times I press the button for turning on WLAn it doesn't turn on and nothing happens.

Is this because before I switched to Ubuntu, in my Windows, I turned WLAN off?

---

### Post by chewearn on 2008-03-15
> **Exsecrabilus said:**
> No matter how many times I press the button for turning on WLAn it doesn't turn on and nothing happens.

Like I said, ignore the WiFi light for the moment.  DId you click on the nm-applet?  What did you get?

> 
Is this because before I switched to Ubuntu, in my Windows, I turned WLAN off?No, this is highly unlikely.

---

### Post by Exsecrabilus on 2008-03-18
I don't get it, how so I turn on my Wi-Fi?

Sorry if I'm irritating anyone, I'm not a tech person.

---

### Post by lavinog on 2008-03-18
i have a compaq laptop (made by hp) that uses a broadcom chipset...the only way i was able to get it to work was to use the ndiswrapper.

the first step to fixing your problem is to find the exact name of your wireless chipset.
is this an amd based laptop or intel?

try this in a terminal:
```
lspci | grep -i wireless 
```
post what it says

---

### Post by Eiríkr on 2008-03-18
> **Exsecrabilus said:**
> I don't get it, how so I turn on my Wi-Fi?

Sorry if I'm irritating anyone, I'm not a tech person.

Fair enough, Exsecrabilus, we all start somewhere.  :)  However, it seems we have a basic failure to communicate here.  AstalaVista asked:

> **AstalaVista said:**
> Like I said, ignore the WiFi light for the moment.  DId you click on the nm-applet?  What did you get?

Your comments so far do not give us any indication of whether you've checked the nm-applet.  Any questions we ask here are asked in an effort to figure out your symptoms and situation, and thereby to understand what advice to give you -- but **if you don't answer them, we cannot help you.**  

If you're up to it, it would also be very helpful if you could open a terminal, type in the following commands one at a time, and post the results here in this thread.  

```
ifconfig
iwconfig
cat /etc/network/interfaces
```

Cheers,

Eiríkr

---

### Post by chewearn on 2008-03-18
> **Eiríkr said:**
> 
Your comments so far do not give us any indication of whether you've checked the nm-applet.  Any questions we ask here are asked in an effort to figure out your symptoms and situation, and thereby to understand what advice to give you -- but **if you don't answer them, we cannot help you.**  


Thanks, Eiríkr.  It seemed, I got stuck in a loop with Exsecrabilus. :mrgreen:

---

