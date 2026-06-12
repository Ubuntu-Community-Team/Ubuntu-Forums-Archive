---
title: "Computer Freezes on Wifi Authentication"
date: 2008-02-20
forum: Networking &amp; Wireless
---

### Post by elainevdw on 2008-02-20
I'm running Xubuntu 7.10 on a really old Toshiba Protege 7020CT with a Linksys PCMCIA wifi card (WPC 11 ver. 4, which worked successfully on previous versions of Xubuntu -- in fact, it worked on Edgy straight out of the box!). 

I installed Xubuntu fresh from the alt CD and it seemed to pick up the card just fine. It sees all the wifi networks in my area, at least.

However, whether I do it in the GUI or in Terminal, as soon as I enter the WEP hex code and it starts authenticating my wifi connection, the entire computer freezes up. Mouse and keyboard don't respond, and I get this blinking green light on my computer.

I tried installing the ndiswrapper and the RTL8180 driver that I've gotten this Linksys card working with on other versions of Xubuntu, but oddly enough, on two separate laptops, this combo has made Xubuntu 7.10 run about 80% slower than usual. Weird. So, I uninstalled ndiswrapper and deleted the RTL8180 driver, bringing me back to square one and the frozen computer.

Any idea what might be causing this? I don't even know where to start!

---

### Post by elainevdw on 2008-02-20
After sleeping on it, I think I decided just to downgrade to Edgy, since it worked fine with Edgy before. Maybe it will work again in a future release. :)

---

### Post by foo fah on 2008-02-20
Sounds very similar to the problem I had...I'm happy to say that a new wireless card fixed it  for me ([here's the thread]("http://ubuntuforums.org/showthread.php?t=699584")).

Although...in my case, there were no earlier versions that the card worked with previously....

Good luck!

---

### Post by nick_simon on 2008-02-27
I've got the same problem with a Netgear MA521card, also the RTL8180 chipset.  No problem until I got the wireless password right!

---

