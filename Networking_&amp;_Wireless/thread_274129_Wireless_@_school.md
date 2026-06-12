---
title: "Wireless @ school"
date: 2006-10-09
forum: Networking &amp; Wireless
---

### Post by Mollos on 2006-10-09
Hello everyone, I've installed Ubuntu 6.06 on my laptop and I'm very satisfied with it. At home I plug in a network cable and I can use the internet as normally. But when I'm at school I want to use the internet too, so I tried to get my wireless working. My wireless card was recognized out of the box so that's no problem. Now I want to log on to the school network.

The network at my school uses MAC filtering and they added me. The name of the network is AvansWlan and I added the name to my network properties of the wireless card, that's no problem. It,s not using a WEP key so I don't have to add that. Everything should work I think but it doesn't.

I can't see if the wireless is connecting or is connected. Is there a program to look for wireless networks in the enviroment and connect to them. That would make things easier for me. Else, is there a solution for my problem?

Thanks in advance

---

### Post by spd106 on 2006-10-09
Take your pick: 

Network Manager looks great and does WPA, but not static addresses.
Wifi-Radar is generally better integrated (IMHO).
From the terminal there's **iwlist wlan0 scan** and **iwconfig**

There are others, enable universe repo in synaptic and have a look.

---

### Post by Mollos on 2006-10-09
thanks a lot. I'll try this wednesday at school.

---

