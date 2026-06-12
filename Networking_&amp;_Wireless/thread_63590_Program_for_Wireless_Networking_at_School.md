---
title: "Program for Wireless Networking at School?"
date: 2005-09-08
forum: Networking &amp; Wireless
---

### Post by Heavenly Evil on 2005-09-08
[COLOR=Indigo]In order to access the wireless network at school (while using Windows XP) I had to purchase a software license for Funk Software's Odyssey Client. From what I can tell, this was because it could automatically detect the WEP key of whichever access point I was near, and then used my Novell username and password to let me on the network.

Does anyone know of a program I can use in Ubuntu that will do the same thing?[/COLOR]

---

### Post by numberexhaust on 2005-09-08
:smile:

---

### Post by Strider on 2005-09-08
[QUOTE=Heavenly Evil][COLOR=Indigo]In order to access the wireless network at school (while using Windows XP) I had to purchase a software license for Funk Software's Odyssey Client. From what I can tell, this was because it could automatically detect the WEP key of whichever access point I was near, and then used my Novell username and password to let me on the network.

Does anyone know of a program I can use in Ubuntu that will do the same thing?[/COLOR][/QUOTE]

Odyssey Client gives your more than WEP encryption.  What you probably have setup is PEAP/EAP, which uses rotating WEP keys.  Odyssey client can be configured to use a username/password, which authicates to the LDAP (backend server) and if you're a valid user, it lets you access the wireless network.

I haven't come across much for getting PEAP/EAP working in linux... but search the forums.  Also, find out more about your WLAN network at school.  They may even have some recommendations/configurations for using Linux.  Can't hurt to try.

---

### Post by Heavenly Evil on 2005-09-08
[QUOTE=Strider]Odyssey Client gives your more than WEP encryption.  What you probably have setup is PEAP/EAP, which uses rotating WEP keys.  Odyssey client can be configured to use a username/password, which authicates to the LDAP (backend server) and if you're a valid user, it lets you access the wireless network.

I haven't come across much for getting PEAP/EAP working in linux... but search the forums.  Also, find out more about your WLAN network at school.  They may even have some recommendations/configurations for using Linux.  Can't hurt to try.[/QUOTE]
 Thanks for the heads-up. I figured it was more complicated than it looked. I'll ask them on Monday and let you guys know what they say.

---

### Post by Heavenly Evil on 2005-11-29
[color=Purple]I know this is months after the fact (my motherboard died and Windows broke), but it still applies. I'm no longer dual-booting so I really need some help with this. When I asked the IT people they wouldn't tell me anything useful. Just that they thought it couldn't work on Linux and to reinstall Windows. I'm starting to suspect they know nothing but Windows.[/color]

---

### Post by peterbrowne on 2006-02-26
same at my school, our wifi network GGWIREless was replaced with PDSBUser on Friday - requiring Odyssey to use EAP-TTLS or LEAP.  Through extensive googling, I found open1x - which is in the Ubuntu repositories.  Trying it on my friends Gentoo notebook on monday - while my Acer notebook (Ubuntu) needs a new power cord :(

---

### Post by Heavenly Evil on 2006-02-26
[COLOR="Indigo"]Thanks so much. I'll give this a try tomorrow when I'm on campus. :mrgreen: 

I've actually had to reinstall everything yet again (new HD) so I've got a clean install of Ubuntu to work with.[/COLOR]

---

