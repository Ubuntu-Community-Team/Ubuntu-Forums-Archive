---
title: "Still have some wireless issues."
date: 2009-01-11
forum: New to Ubuntu
---

### Post by cptrohn on 2009-01-11
Ok, I succesfully installed the  ndiswrapper package and also the drivers for my internal wireless on my laptop.. and now the machine recognizes the wireless card and shows wireless in the connection manager icon in the upper right hand corner.  But it does not show any bars at all for WiFi signal strength..

Is there something else I need to do that I am missing here?

---

### Post by hotweiss on 2009-01-11
> **cptrohn said:**
> Ok, I succesfully installed the  ndiswrapper package and also the drivers for my internal wireless on my laptop.. and now the machine recognizes the wireless card and shows wireless in the connection manager icon in the upper right hand corner.  But it does not show any bars at all for WiFi signal strength..

Is there something else I need to do that I am missing here?

Try opening the router up, ndiswrapper doesn't like encryption too much and then go from there...

---

### Post by cptrohn on 2009-01-11
> **hotweiss said:**
> Try opening the router up, ndiswrapper doesn't like encryption too much and then go from there...

shouldn't it show the available networks though?

---

### Post by cptrohn on 2009-01-11
When I run iwconfig 

it shows

lo no wireless extensions
eth0 no wireless extensions
wlan0 IEEE 802.11g ESSID: off/any
      Mode:Managed Freduency: 2.412 GHz Access Point: Not-Associated
      But Rate: 54 Mb/s
      Power Management: off

---

### Post by hotweiss on 2009-01-11
> **cptrohn said:**
> shouldn't it show the available networks though?

It should. So a left-click displays nothing?

---

### Post by cptrohn on 2009-01-11
> **hotweiss said:**
> It should. So a left-click displays nothing?

A left click does diplay some things like enable networking and that sort of thing... and when I disconnect the ethernet it shows the same thing.

---

### Post by hotweiss on 2009-01-11
> **cptrohn said:**
> A left click does diplay some things like enable networking and that sort of thing... and when I disconnect the ethernet it shows the same thing.

What wireless card are you using?

> lspci

will show it

---

### Post by cptrohn on 2009-01-11
my card is the ar242x..

I've made progress though... before the card wasn't even recognized by the system... not it is....

LOL I'm close, very, very close.

---

### Post by hotweiss on 2009-01-12
> **cptrohn said:**
> my card is the ar242x..

I've made progress though... before the card wasn't even recognized by the system... not it is....

LOL I'm close, very, very close.

Hmm, I think you have to forget about ndiswrapper:

[http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html)

---

