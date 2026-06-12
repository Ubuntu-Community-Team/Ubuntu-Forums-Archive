---
title: "Help with DWL-520 card setup"
date: 2004-11-04
forum: Networking &amp; Wireless
---

### Post by ThePoisonNinja on 2004-11-04
I have a D-Link 520 wireless network card I am trying to install but Ubuntu doesn't seem to even detect it. I am trying to install this card  in an older machine. Is that the problem or is it something else. Any help would be great.

---

### Post by az on 2004-11-06
There are probably linux drivers available.  Go here.

[http://support.dlink.com/faq/view.asp?prod_id=357&question=linux](http://support.dlink.com/faq/view.asp?prod_id=357&question=linux)

Go to the above page and see what revision you have.  Then look at the appropriate link.  If you have trouble finding or installing the driver, come back.

Also, give ndiswrapper a shot.

---

### Post by Silwenae on 2004-11-07
I have a number of D-Link wireless cards at home that work quite well.  Like the previous poster said, check the revision of the card, and the chipset.  If they're Atheros, madwifi has worked great for me in the past, though on my laptop, Ubuntu automatically installed the Atheros drivers for me.

---

### Post by kingnubian on 2004-11-14
After some research I decided to purchase a D-Link DWL-G520 Revision B. This card comes with an Atheros chipset. During the install of Warty I got the error message "No network cards detected" but I continued the install knowing that the Atheros chipset is kernel supported. After Ubuntu was running I went to the Gnome network configuration aplet to setup a wireless connection. ath0 (Wireless card) was listed and after entering DHCP as my preference and giving my ssid and wep key I was up and off to the races. The moto of the story is to do your homework and get a card with a chipset that has mature native support like that from cards with the Atheros and Intersil Prism line.

---

### Post by Razvan on 2004-11-14
funny...my card was never detected...alltough it has an atheros (Dlink Dwl-g650 rev b) do you guys know what to do?

---

### Post by bribera on 2004-11-21
[QUOTE=kingnubian]After Ubuntu was running I went to the Gnome network configuration aplet to setup a wireless connection. ath0 (Wireless card) was listed and after entering DHCP as my preference and giving my ssid and wep key I was up and off to the races.[/QUOTE]
I entered my ssid and wep key, and the applet froze.  Now my wireless monitor picks up signal strength, but the network config applet says the card isn't active, and can't activate it.  I can't get online through it... so what's up?

---

### Post by tcaptain on 2004-12-06
[QUOTE=bribera]I entered my ssid and wep key, and the applet froze.  Now my wireless monitor picks up signal strength, but the network config applet says the card isn't active, and can't activate it.  I can't get online through it... so what's up?[/QUOTE]


I have the exact same problem.  the network config applet won't let the card stay checked and then it freezes.

Ifconfig, iwconfig, cardctl ident all seem to id the card correctly....

do you get an 'IRQ 11: Nobody cares!' message on bootup too?

---

