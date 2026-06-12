---
title: "Wireless connecting issues ip3945"
date: 2008-01-11
forum: Networking &amp; Wireless
---

### Post by Bino on 2008-01-11
I updated from Ubuntu 7.04 to 7.10 a month and a half ago and I have been tampering with it trying to get wireless operational. I tried setting it up manually, uninstalled network manager and installed wifi radar,... However,all without success. 

The fact is that I can see my network on the statusbar at the top and if I want to connect it asks me for the WEP key. I then see the connecting icon where the bottom green light lights up, however, at the end I don´t get a connection and I get asked again for the WEP key. I already checked on our router and the key I enter is correct.

I also already disabled WEP encryption and SSI but still can´t connect. 
The router is running MAC filtering on my laptop but when I look at ifconfig it is the right address.

My wireless is using the Intel(R) PRO/Wireless 3945 Network Connection driver for linux (listed as restricted driver and is enabled).

Can anybody help with getting it to work? 
Without wireless I can´t use Ubuntu and have to revert to Vista...

---

### Post by patrickfromspain on 2008-01-11
maybe you could try wicd?

wicd.sourceforge.net

---

### Post by natehall on 2008-01-11
Here's a thread with a bunch of useful information on the Intel wireless 3945.
[http://ubuntuforums.org/showthread.php?t=587576](http://ubuntuforums.org/showthread.php?t=587576)

---

### Post by Bino on 2008-01-11
Using the iwl3945 driver didnt´t seem to work.

Same goes for using wicd. I saw my hidden/protected network and filedl in everything like SSID, WEP,... however connection couldn´t be made. Following the status of the application, it looks like I have trouble "obtaining an ip adres". 

Any idea what that may be causing and how to solve it?

---

### Post by Bino on 2008-01-12
I´m starting to think that it´s not my wireless driver that is causing conneting problems but more or less the router. 

Does anyone know why I don´t get an IP assigned from the router? DHCP settings?

---

