---
title: "pre working wireless not working"
date: 2014-09-08
forum: Networking &amp; Wireless
---

### Post by basuprasen on 2014-09-08
Hello all!!. My wireless networks had been working nice previously. Frequenty a message came showing wireless network avialable/not available/ connecting etc. Some how I disabled the message permanently, because I was working at that time using wired network. Now I am not able to get it back. No trace in System->settings->network or nothing is coming by giving lspci command. I need it ugently. please help. Thanks you in advance

---

### Post by sheldon-corey on 2014-09-09
> **basuprasen said:**
> Hello all!!. My wireless networks had been working nice previously. Frequenty a message came showing wireless network avialable/not available/ connecting etc. Some how I disabled the message permanently, because I was working at that time using wired network. Now I am not able to get it back. No trace in System->settings->network or nothing is coming by giving lspci command. I need it ugently. please help. Thanks you in advance

Rather vague post very difficult to help diagnose.



Some helpful info to provide would include: outputs from the following commands (install the pkgs inxi lshw vnstat if needed first)


inxi -MnS


vnstat -i wlan0 -l  (average or value from a successful sudo apt-get update && sudo apt-get upgrade )

---

