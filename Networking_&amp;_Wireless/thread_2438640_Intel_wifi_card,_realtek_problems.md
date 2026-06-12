---
title: "Intel wifi card, realtek problems?"
date: 2020-03-15
forum: Networking &amp; Wireless
---

### Post by inappropriate on 2020-03-15
Hello. I'm using a HP Omen laptop and tired of having wifi issues with Ubuntu. I found a backport that temporarily fixes the issue but it is unreliable. I would like to replace my wifi card to something more Linux frieldy. However, I don't understand the difference between a wifi card and a LAN card, or if they are the same thing. Realtek is the problem with my Ubuntu build. However, I noticed when I opened up the laptop it had an Intel wifi card in it. I'm assumed the wifi card related to Realtek but maybe not? Since Realtek is the issue, if I replace the wifi card would that affect the Realtek problem or no?

---

### Post by chili555 on 2020-03-15
> I don't understand the difference between a wifi card and a LAN card, or if they are the same thing. A wifi or wireless card allows us to connect to the internet without any wires, as the name wireless suggests. We can tuck our laptops under our arms and connect from the bedroom, the living room or even at the coffee shop down the road.

LAN, an abbreviation for local area network, is sometimes used as a not-quite-correct synonym for ethernet; the internet connection that requires an ethernet cable connected to the router, switch or other internet device. It is entirely possible, likely even, that your laptop has a Realtek ethernet card and a seperate, both physically and in function, Intel wireless card.> Realtek is the problem with my Ubuntu build. What is the evidence of that? What has your, we assume, Realtek ethernet device done that is troublesome?>  I would like to replace my wifi card to something more Linux frieldy. In my opinion, there is no more Linux-friendly wireless card than Intel. Replacing it would, again, in my opinion, be a step backwards.> tired of having wifi issues with Ubuntu. I suggest that we start by identifying your wifi, also known as wireless device. Please open a terminal and run:```
lspci -nnk | grep 0280 -A3
```Since it is probably an Intel device, let's also check the log for interesting messages:```
dmesg | grep -e iwl -e wlp
```Post the results and we'll continue.

---

