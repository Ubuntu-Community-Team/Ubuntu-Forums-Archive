---
title: "HP Pavilion dv1000 networking issue"
date: 2010-03-04
forum: New to Ubuntu
---

### Post by Fläsh on 2010-03-04
Hello ubuntu community,

Since my laptop crashed on me and i was unable to reinstall windows xp because HP wouldn't accept the version being installed i reformatted my hard disk with Ubuntu 9.10.

Works awesome great the only thing i can't do is go wireless i get no idea of it. I had to setup wine itunes etc with a wired LAN connection through my friends house.

Any help on how to fix this issue would be greatly appreciated

---

### Post by Temposs on 2010-03-04
greetings Flash,
   You should open a terminal and type this command:

```
lspci -v | grep Network
```

and then paste the result here. This will tell us what is your wireless card, so then we can find a remedy.

---

### Post by Fläsh on 2010-03-05
[PHP]Network controller: Broadcom Corporation BCM4311  802. 11b/g WLAN (rev 01)[/PHP]

That is what the terminal spit out.

---

### Post by Temposs on 2010-03-05
OK, try typing this into the terminal:

```
sudo apt-get install b43-fwcutter
```

What this will do is supposedly install firmware for your type of wireless card. I have no direct experience with this. I suppose, after installing that, then restart the computer and see if you can connect to a wireless network. Let me know how it goes.

---

### Post by Fläsh on 2010-03-05
Noting happened installed the drivers through wired lan rebooted fired up network manager connected to my configed network noting.

---

### Post by Peter09 on 2010-03-05
Have you looked in System->Administration->Hardware for any drivers to enable?

You will find the packages you need in synaptic- do a search on BCM.

---

### Post by Temposs on 2010-03-05
Yeah, Broadcom wireless cards are a pain. I'm glad I've never had one.

OK, let's try another thing. Do this command:

```
sudo apt-get install bcmwl-kernel-source
```

Then reboot the computer and try your wireless again. Also, when you reboot, check System->Administration->Hardware Drivers and see if there is a hardware driver you can activate for your broadcom wireless card.

---

### Post by Fläsh on 2010-03-05
I downloaded the native linux drivers for my wireless card (broadcom chip) followed a guide on the internet and installed them through makefile rebooted my laptop now it lets me connect to networks but it seems to be kicking me out of the network I don´t know what type of sercuity my router has (WEP , WPA) so thats what i need help with 

PS ´In the hardware menu you told me to look in i only found one driver for the Broadcom B43 Wireless i installed that first but with no prevail so i came here´

---

### Post by Temposs on 2010-03-05
network manager will generally auto-detect the kind of security setup you have. So, if you have WEP, it'll offer to let you enter a WEP code by default. But, it depends on your router, and you'll need to get into your router settings for that. The method to do that varies from router to router.

---

### Post by Fläsh on 2010-03-05
Hmm... alright i will look in my routers settings to look that up thank you my problem has been SLOVED many thanks !
 
-Flash

---

