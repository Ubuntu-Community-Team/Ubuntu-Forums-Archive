---
title: "WiFi Problem Weak signal (Broadcom BCM43142)"
date: 2014-09-30
forum: Networking &amp; Wireless
---

### Post by MiroslavMilosevic on 2014-09-30
Hi to all,
I have problem with driver for my Wireless card in my new ASUS notebook F555LN series.
I have installed drivers for my Broadcom BCM43142 wifi card. After that i was able to enable wireless network, but i have another problem, i have very weak signal from my wireless router (just to mention that router is 2 meters away from my pc) and i get only signal level of -85dBm. With router is everything ok.
Do you guys have an idea how to solve this problem?
I was read a lot of topics on forums but nothing was helpfull :( :(

---

### Post by MiroslavMilosevic on 2014-10-01
I forgot to mention that i have installed Ubuntu 14.04.1 x64.

Any idea?

---

### Post by davit2 on 2014-10-01
In this case there is a need to install appropriate wireless module. Find out your wireless hardware device name, download the module for that device, install it and wireless will turn on. I have done it once.
OR 
install update in order to get new kernel, which, maybe will have the module you need.

---

### Post by MiroslavMilosevic on 2014-10-01
Thanks for answer anyway. I have already installed driver and wireless device works, but problem was very weak signal. That problem may produce only bad driver or some hardware problem :\

---

### Post by tgalati4 on 2014-10-01
Pull the cover panel on the bottom of the laptop and reseat the wireless card and reseat the 2 antenna connections.  Be careful, the wires are thin.  The gold connectors pop straight off.  It's possible that one of your antenna wires has shorted.  They are routed through the hinge into the top of the screen.  Do you have a loose hinge?

If you suspect a shorted antenna, disconnect one and test, then disconnect the other.  The dual antennas give you better range, but if one is shorted, that will cause a problem.

I'm running a BMC4311 and I am getting -40dBm at 6 feet away from the router.

---

### Post by MiroslavMilosevic on 2014-10-31
I have tested WiFi on windows, and it works as well. That mean that problem is driver, or i installed it on wrong way :)

---

### Post by Benjamn_S. on 2014-12-10
I have the same problem with my notebook (ASUS X455LD-WX032D / Broadcom BCM43142 ). 
The signal is really weak, even when i'm beside the router.  

Please help! :mad:

---

### Post by ferpensado on 2015-01-07
HI men! Have you solved your problem? Cause I get the same laptop 10 days ago and I have the same problem with wifi conection

---

### Post by ferpensado on 2015-01-07
HI men! Have you solved your problem? Cause I get the same laptop 10 days ago and I have the same problem with wifi conection

---

### Post by ferpensado on 2015-01-16
Di muchas vueltas hasta q por fin logre solucionar el problema con la placa Broadcom BCM43142. Me fue imposible en ubuntu 14.04 pero cuando probe con [**ubuntu 14.10**]("http://releases.ubuntu.com/14.10/ubuntu-14.10-desktop-amd64.iso") en su version live me levanto el 100 % de señal, asi q lo instale y anda a la perfeccion. 
Espero les sirva. 
Saludos

---

### Post by Moius on 2015-02-28
Had a problem with weak and unstable wifi signal on my Asus K555LN using Broadcom 43142 card.
It appears to be fixed by just running this command:

# (sudo rmmod b43 ; sudo rmmod bcma ; sudo rmmod wl ; sudo modprobe wl ; sudo modprobe lib80211_crypt_tkip)

Hope this helps.

---

### Post by akhil6 on 2015-07-31
hi guys,
Iam too facing the same problem  WiFi Problem Weak signal (Broadcom BCM43142) asusx555l

---

