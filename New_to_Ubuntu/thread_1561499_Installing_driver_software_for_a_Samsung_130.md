---
title: "Installing driver software for a Samsung 130"
date: 2010-08-26
forum: New to Ubuntu
---

### Post by Cameron Murray on 2010-08-26
I am trying to install the wifi driver for my new Samsung 130. The hardware driver tool, has not flagged any drivers. So what do I do?

Also I know I need to install the video card divers, are there any other drivers I'm missing?

Sorry Ubuntu newbie here.

Much appreciated.
Cameron Murray

---

### Post by gandaran on 2010-08-26
> **Cameron Murray said:**
> I am trying to install the wifi driver for my new Samsung 130. The hardware driver tool, has not flagged any drivers. So what do I do?

Also I know I need to install the video card divers, are there any other drivers I'm missing?

Sorry Ubuntu newbie here.

Much appreciated.
Cameron Murray
if the computer is connected to the internet, have you looked in system » administration » hardware drivers ? run **sudo apt-get update** in terminal first then go look there.
if no drivers there post the output of this command 
```
lspci
```

---

### Post by oldsoundguy on 2010-08-26
Laptops!!  The bane of most.

The best way to set up a laptop is to HARD WIRE it into your network until EVERYTHING is going .. 
I even do that with Windows based laptops.  It just makes life a LOT easier as most home networks will see almost ANY network CARD or ONBOARD setup, whereas they will NOT see that Fred Flintstone Wi-Fi setup until TOLD TO.

---

