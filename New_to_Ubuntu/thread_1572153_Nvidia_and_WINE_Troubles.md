---
title: "Nvidia and WINE Troubles"
date: 2010-09-10
forum: New to Ubuntu
---

### Post by Zachmarius on 2010-09-10
Ok Hello all,

I'm new to Ubuntu and after a very interesting installation system I actually have it running. I've installed some updates as well as Flash and XBMC but am having problems installing WINE.

When I go to the webpage [www.winehq.org](www.winehq.org) then I select Download. I then select ubuntu. At this point the screen goes black then after a while the screen creates this weird funkadelic color image on the screen that I can't do anything with. It's essentially crashed my machine. The only fix is to reboot. I'd love to run WINE and play steam and others but this is bugging me. Is there a way to install and run without crashing my system?

Secondly I found that it was my graphics card that was causing the problem when I boot up into Ubuntu I have an NVIDIA 6200 graphics card that I want to use but an error code pops up every time I try to boot the machine with the card in. It's a PCI card and I've seen and tried other options of deleteing and installing drivers but none have fixed the problem.

Any and all help is appreciated. I can give logs if needed. Just need to tell me how to do it. I've also done very minor terminal work as long as the commands are given as well.

Thanks!

---

### Post by LowSky on 2010-09-13
open a terminal and type

sudo apt-get install wine

---

### Post by sikander3786 on 2010-09-13
Always try to install software from repositories. Most of the software is available there. You can use Software Center, Synaptic or apt-get as mentioned by LowSky for installation from repositories. Install wine as suggested above.

Also, are the proprietary drivers installed for your graphics card? Check in System >>> Administration >>> Hardware Drivers and let us know which version is activated.

---

