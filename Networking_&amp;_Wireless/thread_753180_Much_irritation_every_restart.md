---
title: "Much irritation every restart"
date: 2008-04-12
forum: Networking &amp; Wireless
---

### Post by Miles111 on 2008-04-12
Hello,
Whenever I restart Ubuntu I am not connected to my wireless network. Usually it takes a few minutes of messing around with the network settings to get online, but lately, and worst of all earlier today, I have been spending upwards of 20 minutes trying like a fool to connect to the internet. I am quite short tempered and usually by the end of the 20 minutes I'm swearing and shouting in rage. 

A few important things to say: my wireless network card is a mini-pci dell wireless 1370 (broadcom bcm43xx equivalent) and typing sudo modprobe bcm43xx into the terminal is useless.

---

### Post by shivam.seth on 2008-04-12
I think I can help you....I also have broadcom wlan card and bcm43xx drivers. I was facing similar problems with it.

try doing **echo 'alias eth1 b43' | tee /etc/modprobe.d/b43** and then restart the computer. It worked for me...I hope it works for you as well.

---

