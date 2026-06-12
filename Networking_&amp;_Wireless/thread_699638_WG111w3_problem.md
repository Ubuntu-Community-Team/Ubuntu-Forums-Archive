---
title: "WG111w3 problem"
date: 2008-02-17
forum: Networking &amp; Wireless
---

### Post by andersw on 2008-02-17
Trying different wifi cards in my old TP 600E with ubuntu 7.10 drives me crazy....


I'm now on a Netgear WG111v3 card.

Current problem: I can't get it to register my ESSID name.
* I tried "iwconfig wlan0 essid "name""
* have tried to put it into /etc/network/interfaces
* tried the standard networkmanager tool in gnome

Despite what I try, iwconfig will report back "ESSID: off/any"
(and obviously no association)

- version 1.52 of ndiswrapper
-drivers form the net (named W111v3)

I have tried to connect to a AP with WEP turned on (64 bit key, tried both hex and ascii) and also a AP with no security.

(And the blue light on the card is blinking all the time.....)

Any suggestions?

I have of cause tried [http://ubuntuforums.org/showthread.php?t=615471](http://ubuntuforums.org/showthread.php?t=615471)
and tried [http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)
(and all other links I've found related to this topic)

Anders

---

### Post by elarella on 2008-02-17
I don't know if this will solve your problem, but I have the Netgear WG311T and I had to activate the restricted drivers under the Restricted Drivers Manager.  After I did that, Ubuntu was able to see my network card and I was able to configure my card.  

Hope that was of some help. :-?

---

### Post by andersw on 2008-02-17
> **elarella said:**
> I don't know if this will solve your problem, but I have the Netgear WG311T and I had to activate the restricted drivers under the Restricted Drivers Manager.  After I did that, Ubuntu was able to see my network card and I was able to configure my card.  

Hope that was of some help. :-?

Thanks for the suggestion, but my stick is not the T-model

Anders

---

