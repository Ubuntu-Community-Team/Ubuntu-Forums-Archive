---
title: "Dual boot networking problem"
date: 2005-11-07
forum: Networking &amp; Wireless
---

### Post by Dagur on 2005-11-07
Hi,

This is more a minor annoyance than a real problem but if someone knows the answer it would be great.


So the problem I'm having is that when I reboot from windows to ubuntu It's like my router won't allow me to connect to the internet. So my only choice is to wait 10-15 minutes or restart the router. This doesn't happen when I reboot from ubuntu into windows. 
I don't know if it's relevant but i chose my own IP (i.e. I don't let my router choose one for me). 

Any ideas? Maybe this is a windows/router problem and not an ubuntu problem.

thanks to anyone replying :)

---

### Post by mlomker on 2005-11-07
Have you tried using different IP's in each?  It shouldn't be an issue since it's the same network card, but a MAC-address problem was the first thing that came to mind.

---

### Post by mips on 2005-11-08
Does Windows & Ubuntu both use the same IP address ?
If they differ then make them the same & let us know what happens then.

What Router (make&model) do you have ?

---

### Post by Dagur on 2005-11-08
I use the same ip for both, i have apache running on both sides. 

It's a "zyxel prestige 600 series" router. I don't have any access to it so I have to call my ISP every time I want to change something.

---

### Post by paddyg on 2005-11-08
i had a problem similar to that---after rebooting ubuntu didn't connect to the internet.

i've got a router and static ip for my box.

What i did was to set dns servers in network settings other than the router gateway address. Internet connection has been working fine since then.

---

### Post by Dagur on 2005-11-13
Unfortunately that didn't work for me

---

