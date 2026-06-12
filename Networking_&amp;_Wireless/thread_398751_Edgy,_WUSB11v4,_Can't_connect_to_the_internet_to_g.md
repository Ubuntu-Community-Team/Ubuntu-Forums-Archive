---
title: "Edgy, WUSB11v4, Can't connect to the internet to get dependencies"
date: 2007-04-01
forum: Networking &amp; Wireless
---

### Post by nescontroller on 2007-04-01
Hi I have looked at all the pervious threads concerning how to install the WUSB11v4 with ndiswrapper, however I cannot physically connect my computer to the internet, I must use wireless. Is there anyway for me to install this card? I tried to download all the .debs required to build ndiswrapper from source, burn them onto a cd, and then install but I keep getting errors. Can anybody help me?

---

### Post by Floppyjoe on 2007-04-01
> **nescontroller said:**
> Hi I have looked at all the pervious threads concerning how to install the WUSB11v4 with ndiswrapper, however I cannot physically connect my computer to the internet, I must use wireless. Is there anyway for me to install this card? I tried to download all the .debs required to build ndiswrapper from source, burn them onto a cd, and then install but I keep getting errors. Can anybody help me?

You can use your Ubuntu Install disk as a repository to install ndiswrapper by clicking on System/Administration/Synaptic Package Manager.
Then click on Edit/Add CDrom and follow the directions.
Then click reload.
Then search for ndiswrapper and install ndiswrapper-utils-1.8 and ndiswrapper-common.

---

### Post by nescontroller on 2007-04-01
Thank you, but based on the threads I have read I have to uninstall the version of ndiswrapper I can get with edgy and build from source. Do you have any suggestions or tips for this? Or do you know if it will work right out of the box(ndiswrapper I mean)?

---

### Post by Floppyjoe on 2007-04-01
You can use the method i described to get "build-essential" and "linux-headers-`uname -r`" onto your system. You can enter the command uname -r into a terminal and search for linux-headers with your kernel type in synaptic. These are prerequisites for compiling ndiswrapper.

---

