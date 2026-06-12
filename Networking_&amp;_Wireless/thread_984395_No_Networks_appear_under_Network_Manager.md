---
title: "No Networks appear under Network Manager"
date: 2008-11-16
forum: Networking &amp; Wireless
---

### Post by KaiJordanDay on 2008-11-16
Installed all the Linux BackPorts (Generic, Intrepid etc...)

Wireless networks appeared on my Network manager, but no networks appear under them. 

Im using Atheros on my Fujitsu Siemens Amilo Li 1718.

Any Suggestions?

---

### Post by shanix on 2008-11-16
What's ur network card?

please run the following command:


lspci -vvnn | grep Wireless

And paste the output here. Also, which Ubuntu release are you using?

Not sure by any chance this will be ur solution, but, check this out:
[http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html)

---

### Post by gnusci on 2008-11-16
Could you please give more details, run this comands:

[B]$ iwconfig
$ iwlist scan[/B]

---

### Post by wyth on 2008-11-19
Having the same problem, no networks showing up.  I removed backports, but was having hard freezes/lock-ups, so I needed to put that back in.  

I'm running an Intel 3945ABG[GOLAN] wireless card. 

Running iwconfig tells me ```
lo no wireless extensions
``` and ```
eth0 no wireless extensions
```

Running iwlist just shows me the help command -- no networks are shown.

The kill switch is tripped on booting with the backports modules, so I have to turn the switch off and back on to get the light to come on.  But it seems its not coming back on.

---

### Post by KaiJordanDay on 2008-11-21
I can't even get my LED light up.

---

### Post by Snappo on 2008-11-21
> **KaiJordanDay said:**
> I can't even get my LED light up.

It would be best if you posted the following.

lspci -vvnn | grep Wireless

I have atheros on my laptop ended up there was NO support for that model and I was forced to buy a dongle.

A small investment, but it works just as well.

---

### Post by wyth on 2008-11-21
Here's what worked for me, to date:

The 2.6.27-7-generic kernel worked okay for me, but 2.6.27-8-generic was causing hard freezes.  Backports was supposed to solve that issue, but the backports screwed up wireless (no networks).  It also wouldn't bring up the wireless network automatically (i.e. no lights).

I removed all the backport stuff, but didn't purge anything.  I then commented out the 2.6.27-8-generic kernel in my /boot/grub/menu.lst, and just automatically boot into 2.6.27-7-generic.  Since I wasn't having any problems with it, I decided not to worry about what 2.6.27-8-generic could offer.  So far everything is grand.

---

