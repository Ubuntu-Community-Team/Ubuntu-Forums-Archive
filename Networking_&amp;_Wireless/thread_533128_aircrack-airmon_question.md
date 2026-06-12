---
title: "aircrack-airmon question"
date: 2007-08-23
forum: Networking &amp; Wireless
---

### Post by danzinger on 2007-08-23
Hi

Ive reading some interesting posts here about cracking wep, but i am not able to get my realtek 8187 working in Feisty.

I got aircrack-ng, and ive followed the patching steps for my wireless card, [here]("http://aircrack-ng.org/doku.php?id=r8187")

I can put my wireless interface in Monitor mode, with this command:

iwconfig wlan0 mode monitor channel X

And i get mode:monitor in my wlan0 iwconfig.

But whenever i issue the airmon command, i get no results

airmon-ng start wlan0 1

usage: airmon-ng <start|stop> <interface> [channel]

Interface Chipset Driver

And no results here...  (same with airmon stop)

Anybody has any idea of what ive missed out?

Thank you so much!

---

### Post by markeee on 2007-11-23
have you tried following one of the tutorials? sorry i cant be of more specific help

---

