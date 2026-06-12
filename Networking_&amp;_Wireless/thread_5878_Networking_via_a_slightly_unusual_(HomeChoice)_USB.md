---
title: "Networking via a slightly unusual (HomeChoice) USB modem"
date: 2004-11-22
forum: Networking &amp; Wireless
---

### Post by unprinted on 2004-11-22
HomeChoice is a London UK-based 'video on demand' service that also does internet connectivity for subscribers. My HC setup currently uses a HC-specific set-top box (STB) which talks to an Alcatel SpeedTouch ADSL modem. To get the internet service, a small USB box plugs into the PC and converts USB to the RS422 the STB wants to use.

Phew!

The basic guide to getting this to work under Debian is at 

[http://www.epiphany.homechoice.co.uk/HomeChoice/](http://www.epiphany.homechoice.co.uk/HomeChoice/)

Under ubuntu, I have set up /etc/ppp/peers/provider, /etc/chatscripts/provider and /etc/ppp/ppp_on_boot to use the settings there. 

On booting up, the lights on the USB box and the STB flicker happily and the light on the STB stays on - something is happening and it would appear that the STB thinks it is connected. 

However, Linux networking virgin that I am, I'm missing some important step: if I try to ping an ip address, I get a 'connect: network is unreachable' error.

What else should I be telling ubuntu about my networking (and how)?

---

