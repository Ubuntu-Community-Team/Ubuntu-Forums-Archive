---
title: "Networking suddenly stopped"
date: 2007-03-21
forum: Networking &amp; Wireless
---

### Post by Hav0ck on 2007-03-21
I just installed Xubuntu on my old IBM thinkpad 600E and everything seemed to be working just fine.
My wireless network connected fine, my wired NIC also worked fine.
I shut the machine down and the next day turned it back on and I could no longer connect to my network.
In the Gnome network manager I can not activate the wireless card (I've tried two which previously worked). I can check the activate option, fill in the static IP or leave it DHCP but when I click OK the wireless NIC does not get a check mark next to it.
The Wired card does get a check mark but it will not get an IP from my DHCP server and when I specify the IP address I cannot ping any other computer on the network, nor can the laptop be pinged.

I swear everything did work and now it doesn't. Any help would be appreciated.

---

### Post by Mr. C. on 2007-03-21
Let's see what you have:

```
sudo ifconfig -a
sudo lspci
sudo lspci -v

```
MrC

---

### Post by Hav0ck on 2007-04-03
Hey Mr. C.

Thanks for the response. Sorry it took so long my wife was in the hospital. I'll give that a try when I get home and post the results.

---

