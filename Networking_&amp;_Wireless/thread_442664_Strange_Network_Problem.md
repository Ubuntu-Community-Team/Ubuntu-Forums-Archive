---
title: "Strange Network Problem"
date: 2007-05-13
forum: Networking &amp; Wireless
---

### Post by mos942 on 2007-05-13
Im running Ubuntu Feisty on my dell latitude d510. I use a LAN connection inside my university network and wireless at my home. When at home or other wireless location, I can connect to internet fine and access any page, but I cant access any of my university web pages. These pages all start with the same IP as my static LAN address when im inside uni  network. I think this is possible whats causing problems.

It is not a problem at the university end as my friends can access the pages on their windows and mac machines, and I used to be able to before my switch to ubuntu. It also isn't my browser (firefox) as i tried a different browser and it had the same problem. Also tried clearing private data in browser.

Anybody any ideas? I hate the thought of windows machines working better than mine.

---

### Post by [S|G] on 2007-05-13
Do you access the webpages using their IP directly? If that's the case, the IP addresses could be from a private range and only accessible from inside the university. If the adresses look something like 172.xxx.xxx.xxx, 192.xxx.xxx.xxx or 10.xxx.xxx.xxx, there are good chances they are private IP adresses.

Do your friends access the webpages using the IP number as well when they're outside?

---

### Post by mos942 on 2007-05-14
Thanks, i think I've fixed it. I think it was a Ivp6 problem, its working for now anyway

---

