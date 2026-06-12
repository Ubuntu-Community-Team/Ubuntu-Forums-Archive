---
title: "wi-fi on dell latitude d-400"
date: 2010-12-18
forum: New to Ubuntu
---

### Post by geek-at-heart on 2010-12-18
I just installed Ubuntu 10.10 on my Dell latitude D-400. I can get internet access with an ethernet cable but my wi-fi won't work. It says dissabled when I type sudo lshw -c network. I installed the ndisgtk package but when I go to install the driver I can't find it. Any help would be really appreciated. By the way I'm running a dual boot with windows xp. My wi-fi card is a Dell wireless 1450 Dual Band WLAN Mini-Pci card.

---

### Post by 12apennachi on 2010-12-18
type in lspci in a terminal and see if it has a line for wireless or wlan or network
or
lspci | grep Network

---

### Post by geek-at-heart on 2010-12-18
I've got a line for PCI BRIDGE:intel corporation 82801 Mobil PCI Bridge (rev 81)  and Network Controller:Broadcom corporation BCM4309 802.11a/b/g (rev 03)     I hope this helps

---

### Post by 12apennachi on 2010-12-18
The classic Broadcom drivers.... I guessed that.  ndiswrapper might work but that's dirty. Go to system-> Admin-> Hardware drivers, and see if you've got something there

EDIT: I just realized that proprietary drivers aren't available until the first update (just installed 10.04 on my parents laptop with a Broadcom bcm4322) Did you update yet?

---

### Post by geek-at-heart on 2010-12-18
I've got "additional drivers" broadcom B43 wireless driver not activated. I've also got "Windows wireless drivers" I've tried to install that but when it asks where to find it, I can't find the windows.inf file.

edit: I done a full update right after install. 200mb

---

### Post by 12apennachi on 2010-12-18
> **geek-at-heart said:**
> I've got "additional drivers" broadcom B43 wireless driver not activated. I've also got "Windows wireless drivers" I've tried to install that but when it asks where to find it, I can't find the windows.inf file.

edit: I done a full update right after install. 200mb

Dont't wan't to be a smart@$$, but did you hit activate?

And by the way, just so you know, Windows Wireless Drivers is ndiswrapper, it's a workaround, I don't like to suggest it unless it is a last resort.

---

### Post by geek-at-heart on 2010-12-18
A light bulb just lit up: I didn't have the ethernet cable pluged in when I tryed to activate the "additional driver". It said it could'nt fetch the file from the website. should I plug in and try it?

---

### Post by 12apennachi on 2010-12-18
> **geek-at-heart said:**
> A light bulb just lit up: I didn't have the ethernet cable pluged in when I tryed to activate the "additional driver". It said it could'nt fetch the file from the website. should I plug in and try it?

Now there's your problem. Yes.

---

### Post by geek-at-heart on 2010-12-18
Your a genius!!! I pluged in my ethernet cable and activated that driver and everything worked. I unpluged and it reconized my wireless network, typed in the key and went on-line. Thank you so much for your help.  Problem solved!!!!!!!!!!!!!!!

---

### Post by 12apennachi on 2010-12-18
No problem! I do it for the compliments :)

---

