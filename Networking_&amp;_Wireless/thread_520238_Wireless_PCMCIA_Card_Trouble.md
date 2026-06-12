---
title: "Wireless PCMCIA Card Trouble"
date: 2007-08-07
forum: Networking &amp; Wireless
---

### Post by m-enterprise on 2007-08-07
I'm using an old laptop that has Ubuntu 7.04 installed and my PCMCIA wireless card isn't working. It's a D-Link DWL-G630. I've installed ndiswrapper and it recognizes the card, the lights flash on the card, and I can see my network but when I try to access the internet nothing is displayed. Any suggestions?

---

### Post by kevdog on 2007-08-07
Can you post the following so I can get up to speed with your system?:

iwlist scan
lshw -C network
modinfo ndiswrapper
ndiswrapper -l

Thanks

---

### Post by m-enterprise on 2007-08-07
Sorry I'm a new user, can you tell me how to get all that information. Or point me to a link that shows me how to get it. Do I just type it into the terminal?

---

### Post by kevdog on 2007-08-07
Type it into the terminal, (hopefully you have a wired internet connection so you can cut and paste the output.  If not you could paste it into a text file and then transfer it via USb stick to a different computer with an internet connection.)

---

### Post by m-enterprise on 2007-08-07
Well I'm at work right now but I will get it back to you as soon as I get back home, which unfortunately won't be until 7 tommorow morning. Thank you for you help.

---

