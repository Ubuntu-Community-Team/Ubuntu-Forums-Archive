---
title: "Need help with my Atheros chipset"
date: 2008-05-16
forum: Networking &amp; Wireless
---

### Post by TobbeQ on 2008-05-16
Hi, need help getting my wireless card to work. I've got an Atheros 5006x chipset in it.

I've tried madwifi but it didnt work. Maybe i did it in a wrong way.
I've also tried ndiswrapper, and no success there either.

Anyone with an idea?

thx in advance

---

### Post by Snappo on 2008-05-16
> **TobbeQ said:**
> Hi, need help getting my wireless card to work. I've got an Atheros 5006x chipset in it.

I've tried madwifi but it didnt work. Maybe i did it in a wrong way.
I've also tried ndiswrapper, and no success there either.

Anyone with an idea?

thx in advance

I'm on the same boat as you. I have been searching for three weeks now with no luck, what is your computer model?

---

### Post by simmcrd on 2008-05-16
This is a buggy workaround, but it gets my Compaq Presario F700 series up (Hardy/Heron):

[LIST=1]
[*]System->Administraion->HardwareDrivers
[LIST]
[*]"Atheros Hardware Access Layer (HAL)" is probably ENABLED but NOT IN USE. leave it alone.
[*]"Support for Atheros 802.11 wireless LAN cards" is probably ENABLED but NOT IN USE. Click in the box to DISABLE it, then click it again to ENABLE it.
[*]Now both "Support for Atheros 802.11 wireless LAN cards" and "Atheros Hardware Access Layer (HAL)" are both ENABLED and IN USE.
[/LIST]

[*]/etc/init.d/networking restart
[*]SUSPEND thru the GUI icon.
[*]RESUME. You now should be magically on line. (I do not know why yet, but you have to SUSPEND/RESTORE in order for the bogus wlan0:avahi interface to disappear and to bring the valid wlan0 interface up in its stead.
[/LIST]

Notes:
[LIST=a]
[*]This change is only temporary, it has to be repeated for each reboot. [*]A caveat is that my GUI (kde) hangs on boot if it cannot find a connection to the internet. I have to plug a UTP ethernet cable into my RJ-45 port on reboots.
[*]I'm brand new to Ubuntu and its variants (i.e. Kubuntu) but am well experienced with other distributions. I haven't had the time to parce my logs yet. I believe that possibly an applet might be hanging the boot. I will post more detailed results after I complete my work project.
[*]I am unable to "cafe" because I need a copper connection on bootstrap.
[/LIST]

I do hope this helps you somewhat.

---

