---
title: "Bridging two Nics"
date: 2007-11-04
forum: Networking &amp; Wireless
---

### Post by kapellen421 on 2007-11-04
I have a server box that I recently purchased two identical nics for . I want to bridge this connection as follows. Modem > Server > Switch. I have read a lot of posts here but none have what I really want. All you advice and help is really appreciated in advanced.

---

### Post by SpiritIsReality on 2007-11-04
howdy
I think this is what you're lookin' for pardner
[https://help.ubuntu.com/community/InternetConnectionSharing](https://help.ubuntu.com/community/InternetConnectionSharing)
trails

[https://help.ubuntu.com/community/InternetHowto](https://help.ubuntu.com/community/InternetHowto)
[http://ohioloco.ubuntuforums.org/showthread.php?t=91370](http://ohioloco.ubuntuforums.org/showthread.php?t=91370)

[http://aboutdebian.com/network.htm](http://aboutdebian.com/network.htm)
I'm workin' on 2 nic cards on a server too. 
aboutdebian mentions that linux will see the top card as eth0, the line to the modem. choose this as the primary network interface when installing.
the bottom card (closest to the edge of the motherboard, will be the eth1, the line to the switch.
see heading "At Home" about 1/3 to 1/2 way down the page.
firestarter
[http://ubuntuforums.org/showthread.php?t=542756&highlight=firestarter](http://ubuntuforums.org/showthread.php?t=542756&highlight=firestarter)
[http://ubuntuforums.org/showthread.php?t=253174&highlight=firestarter](http://ubuntuforums.org/showthread.php?t=253174&highlight=firestarter)

---

### Post by kungphukenobi on 2007-11-04
I had a similar situation, i needed to go   xbox360 > PC > switch so the xbox could access the internet through the wireless nic on the PC

I used firestarter to do it, it worked really well and is easy to configure.

---

### Post by kapellen421 on 2007-12-02
Thanks for the advice, but i have a small problem. I  have three nics. One is my on board and the other two are identical PCI, Is there and easy network gui configuratior that will allow me to do this?i don't want to use fire starter at all.

---

