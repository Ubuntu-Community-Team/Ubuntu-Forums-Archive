---
title: "ifconfig status as well as Snort errors."
date: 2017-06-26
forum: Networking &amp; Wireless
---

### Post by 1jarwolf on 2017-06-26
Hello, I  new to linux, however, I do know that when ifconfig is typed in, you're supposed to see eth0, lo, and wlan0. However, on my  ifconfig, I am seeing completely different. I have enp3s0, lo, and wlp2s0. I have never seen these before, so how's I suppposed to know which IP address that I need. I am trying to get Snort to work, and it's just way too much **** and configuration to do. I am completely lost. I type in "Snort -vde" I get this...  "[COLOR=#ff0000]WARNING: No preprocessors configured for policy 0.[/COLOR]"

---

### Post by chili555 on 2017-06-26
Please see here: [https://askubuntu.com/questions/760196/why-is-enps-in-stead-of-eth-whats-the-meaning-of-enps/760243#760243](https://askubuntu.com/questions/760196/why-is-enps-in-stead-of-eth-whats-the-meaning-of-enps/760243#760243)> I have enp3s0, lo, and wlp2s0. I have never seen these before, so how's I suppposed to know which IP address that I need.enpxx is [COLOR="#FF0000"]e[/COLOR]ther[COLOR="#FF0000"]n[/COLOR]et protocol; wlpxx is [COLOR="#FF0000"]w[/COLOR]ire[COLOR="#FF0000"]l[/COLOR]ess.

Sorry, I know nothing about snort.

---

