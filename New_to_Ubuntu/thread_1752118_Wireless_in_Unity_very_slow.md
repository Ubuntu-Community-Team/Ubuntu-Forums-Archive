---
title: "Wireless in Unity very slow"
date: 2011-05-07
forum: New to Ubuntu
---

### Post by Pulka on 2011-05-07
Hi!


installed unity for a week now and my wireless internet is very, very slow. Never had any problem with the previous versions of ubuntu.

Any thoughts of what might be the problem?

---

### Post by Gone fishing on 2011-05-07
I had a weird problem with a laptop. 

I put 11.04 on and installed the proprietary driver for the Broadcom wireless it worked fine - I download 100meg through synaptic fine and then it stopped or more correctly became so slow it couldn't be used. I could ping the adsl model (through the wireless) I could ping google but not the bbc or cnn. If I connected to the modem with a cable all was fine. If I uninstalled the driver and used a usb wireless card (realtek) all was fine. But the broadcom driver worked for an hour then became so slow it couldn't be used - tried reinstalling no improvement. How weird is that? 

I have read that the free driver b43-fwcutter and firmware often works or you could get a usb dongal. 

Are you using a broadcom wireless card? (sudo lshw) to find out.

---

### Post by Pulka on 2011-05-08
it's an atheros

---

### Post by Gone fishing on 2011-05-08
OK have a look at these:

[http://ubuntuforums.org/showthread.php?t=1746326&highlight=atheros](http://ubuntuforums.org/showthread.php?t=1746326&highlight=atheros)

[http://www.ubuntusecrets.it/2011/04/hack-connessione-lenta-su-natty-forse-ho-la-soluzione-giusta-per-voi/?lang=en](http://www.ubuntusecrets.it/2011/04/hack-connessione-lenta-su-natty-forse-ho-la-soluzione-giusta-per-voi/?lang=en)
[http://ubuntuforums.org/showthread.php?t=1742274&highlight=atheros&page=3](http://ubuntuforums.org/showthread.php?t=1742274&highlight=atheros&page=3)

I think those links will solve your problem

---

### Post by Durden on 2011-05-08
All internet connections slow or just web browsing? I had to do about:config in Firefox and disable ipv6 to make things tolerable.

---

