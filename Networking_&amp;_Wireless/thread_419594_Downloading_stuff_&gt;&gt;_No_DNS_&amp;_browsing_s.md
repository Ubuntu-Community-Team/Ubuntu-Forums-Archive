---
title: "Downloading stuff &gt;&gt; No DNS &amp; browsing slow"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by Lieter on 2007-04-23
Hello ubuntu community,

i've totally made the switch about a week ago, but i've got a very strange problem:
When i'm downloading stuff(with klibido(usenet) or bittorrent for instance) my browsing speed goes down the drain. My opera stops responding(which also happens when i login to a SSL secured server), the same happens with firefox. I've got no idea why this is, the problem never existed on (oh god) winXP. 

I've already disabled IPv6, and i change my MTU to 1492 manually everytime(ive put it in /etc/network/interfaces, doesnt seem to work). So ive got no idea how to fix this, but its very annoying, and i dont want to go back to windows :) .

Setup:
Asus P4P800SE Mainboard
Pentium 4 3,2 GHz.
Marvell 88E8001 Gigabit Ethernet Controller
Wired to 100 MBit switch/router
ADSL 6Mbit down, 768 KBit up

thanx for helping me in advance

---

### Post by lassegs on 2007-04-23
I've got the same NIC as you, and use klibido, azureus and firefox, but i never got this problem (except azureus strangles my internet connection.)

---

### Post by Lieter on 2007-04-23
I dont thinks its a nic problem. I think its a setting somewhere (maybe QoS, i dont know)

---

### Post by F-3582 on 2007-04-23
The problem with Azureus strangling your connection can be easily solved by setting the upload limit about ten K/sec lower than the actual upload speed your connection is capable of. That way your Ping doesn't jump into the thousands.

---

### Post by Lieter on 2007-04-23
it also happens with usenet downloads, so it isnt an upload too high problem, i'm still looking what it can be but i cant figure it out

---

### Post by Lieter on 2007-04-24
today i installed hellanzb instead of klibido, and it looked like it went better, but still the browsing is slow, but it stil annoys me XD. no-one of you guru's know why this problem exists?

---

