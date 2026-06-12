---
title: "How to set a static IP?"
date: 2005-04-15
forum: Networking &amp; Wireless
---

### Post by raid517 on 2005-04-15
Hi I am trying to figure out my networking issues. At the moment I can use dhcp - but this is useless for most peer to peer applications - such as amule and bittorrent.

I connect to the internet with a combo router/modem.

My router is set up so that I can contact it by typing 192.168.1.1 into a web browser. I have a dhcp server set up so that all addresses up to 192.168.1.110 are static and all addesses from 192.168.1.111 to 192.168.1.254 are automatically assigned by dhcp. Which means I have 110 static IP's.

Normally when connecting I would set my IP on my lan to 192.168.110, my netmask to 255.255.255.0 and my route to 192.168.1.1 (which is the address of my router).

This always worked in the past.

But now Kabuntu KDE control is asking me to include a braodcast address too.

I have no idea what this is, let alone how to configure it.

Can anyone advise on the best way to set a static IP address from the details I have given and have my network automatically started on boot?

I would very much appreciate any advice anyone can offer.

Best regards,

GJ

---

### Post by abhaysahai on 2005-04-15
Please select your route address as broadcast address.

Regards

---

### Post by raid517 on 2005-04-15
Hi no, unfortunately this didn't work.

I set my IP address to 192.168.1.110
I set my netmask to 255.255.255.0
I set my broadcast address to 192.168.1..255  (the 255 part was added automatically).
I set my gateway to 192.168.1.1

This always worked in the past.

I have no idea why it isn't working now.

I noticed in kcontrol that there was also another tab for 'domain name system' and 'static hosts' - but I have no idea what these are, how to configure them or even if they are configured correctly.

I would very much like to get a static IP going if at all possible, because otherwise networking isn't much use to me - at least no without my most used apps.

If anyone can offer any input at all, it would therefore be very much appreciated.

Best regards,

GJ

---

### Post by dangerous666 on 2005-04-16
[QUOTE=raid517]Hi no, unfortunately this didn't work.

I set my IP address to 192.168.1.110
I set my netmask to 255.255.255.0
I set my broadcast address to 192.168.1..255  (the 255 part was added automatically).
I set my gateway to 192.168.1.1

This always worked in the past.

I have no idea why it isn't working now.

I noticed in kcontrol that there was also another tab for 'domain name system' and 'static hosts' - but I have no idea what these are, how to configure them or even if they are configured correctly.

I would very much like to get a static IP going if at all possible, because otherwise networking isn't much use to me - at least no without my most used apps.


If anyone can offer any input at all, it would therefore be very much appreciated.

Best regards,

GJ[/QUOTE]

I have the same problem... No sucess yet... :(

---

### Post by Buffalo Soldier on 2005-04-16
[QUOTE=raid517]Hi no, unfortunately this didn't work.

I set my IP address to 192.168.1.110
I set my netmask to 255.255.255.0
I set my broadcast address to 192.168.1..255  (the 255 part was added automatically).
I set my gateway to 192.168.1.1[/QUOTE]
Guessing here. Try setting your broadcast address to 192.168.1.**255**

---

### Post by abhaysahai on 2005-05-16
Your Broadcast address has an extra "." 
As suggested by "Buffalo Soldier" Please set it to "192.168.1.255".
Do let us know of the result.
Abhay

---

