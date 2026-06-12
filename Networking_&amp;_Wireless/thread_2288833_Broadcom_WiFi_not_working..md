---
title: "Broadcom WiFi not working."
date: 2015-07-30
forum: Networking &amp; Wireless
---

### Post by andrew251 on 2015-07-30
Hey guys, I've purchased a new laptop and it has a broadcom WiFi card.  
When I boot into Ubuntu, the WiFi card isn't detected so I go into drivers and enable the proprietary drivers but after doing that, because I'm on a live CD I lose my changes if I restart so I can't check the WiFi works? Will I have to take my chances and install Ubuntu because I want to replace Windows with it?

---

### Post by kc1di on 2015-07-30
Hi andrew251 and welcome to Ubuntu,

Broadcom cards are pretty well supported so it should not be a problem.
only thing is there are two different drives.  and it depends upon which card is in your machine which one will work best.
[See here]("http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers") for help:

You are correct that you'll loose all setting if you reboot live cd.  You don't have to reboot however to try out your card.

you should be able to start the driver with this command in a terminal.

```
modprobe wl 
``` (if it's ths bcmwl driver) or
```
modprobe b43
``` (if it's the b43xx driver)

wait a minute and see if your card is working.

good luck :)

---

### Post by cardy_c on 2015-07-30
You should be able to get it working after you install. 
I would suggest  doing a side by side install allowing you boot into Windows or Ubuntu at least until you are sure everything is working in your Ubuntu.

Here are some links that helped me get my Broadcom WLan figured out on several laptops.



[http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers](http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers)
[http://askubuntu.com/questions/461384/how-to-connect-to-wifi-from-lubuntu](http://askubuntu.com/questions/461384/how-to-connect-to-wifi-from-lubuntu)
[http://askubuntu.com/questions/322861/how-to-connect-to-wireless-network-in-lubuntu](http://askubuntu.com/questions/322861/how-to-connect-to-wireless-network-in-lubuntu)

---

### Post by andrew251 on 2015-08-19
Sorry for the delay in getting back to you.
After I installed Ubuntu using an ethernet cable for updates, I just enabled the drivers in _Additional Drivers_, rebooted and everything is good. :D

---

