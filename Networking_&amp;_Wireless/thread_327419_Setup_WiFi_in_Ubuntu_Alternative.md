---
title: "Setup WiFi in Ubuntu Alternative"
date: 2006-12-29
forum: Networking &amp; Wireless
---

### Post by cendant on 2006-12-29
In my notebook I have AMBIT Prism 2.5 Wavelan wireless card.

If I install Ubuntu from LiveCD, I see this
[IMG]http://www.siberian.ws/uploads/posts/1167392741_1.jpg[/IMG]

and in Properties of Wireless connection this

[IMG]http://www.siberian.ws/uploads/posts/1167392825_2.jpg[/IMG]

When I install from Alternative Ubuntu CD, the wireless card is definetely set up by the system, but I do not see the part surrounded by black

Without I cannot setup SSID and WEP password. Can you help me with your kind advice?!

---

### Post by teaker1s on 2006-12-29
guessing that there is no firmware to load, try looking at [this]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper") and substitute the bcmwl5.inf with the correct one form your windows driver cd

---

### Post by tturrisi on 2006-12-29
> **teaker1s said:**
> guessing that there is no firmware to load, try looking at [this]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper") and substitute the bcmwl5.inf with the correct one form your windows driver cd
The above is inapplicable, his card does not have a broadcom chipset, it has a prism chipset, whick is well supported by linux.  

cendant
Are you saying that you do not have the "Settings for interface" window at all?  Can you type the ssid and passkey?

---

