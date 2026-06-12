---
title: "Problemas wirh WiFi"
date: 2010-10-09
forum: New to Ubuntu
---

### Post by stpgqe2010 on 2010-10-09
[B]Hi all there, I'm new to Ubuntu and Linux. I download the ubuntu-10.04.1-desktop-amd64 version and installed it correctly, but my wifi connection does not work.

I google about it, and get to "ndiswrapper-1.56", It' supposed that this software will resolve my problem with a windows driver of my wifi card.

The thing is that I can't install this [/B][B]ndiswrapper, I only have this:
"$ sudo aptitude install ndiswrapper-common ndiswrapper-modules-1.9 ndiswrapper-utils-1.9 " <--- I don't get it, It seems I don't have those files or packages.

Does anyone have any [/B][B]ndiswrapper for dummies guide?? I just want to try Ubuntu with a Wifi experience.

Thanks in advanced
[/B]

---

### Post by Quackers on 2010-10-09
Does it work with an ethernet cable plugged in?
Have you looked in System > Admin. > Hardware drivers? What is your wi-fi card?

---

### Post by irv on 2010-10-09
So far every laptop I have installed Ubuntu on I had to be hooked up to a network with the wire, then after installing had to go to System>Administration> Hardware drivers and install the driver for the wifi card. It always finds the right one and installs it. After that you can unplug the cable and the wireless should work.

---

