---
title: "Very new to Linux - PCMCIA WiFi problem"
date: 2005-10-26
forum: Networking &amp; Wireless
---

### Post by karlharratt on 2005-10-26
I am very new to Linux and am very impressed with Ubuntu 5.04 with the Gnome desktop.
I have just installed it on an Acer Travelmate 521TEV and it is running fine but I can't get the wireless network card to work.
It is a PCMCIA Linksys WCP11 version 4 card.

As I said above I am very new to Linux and I will require very detailed step by step instructions.

I hope you can help, thank you.

---

### Post by karlharratt on 2005-10-26
I located information about <modprobe ndiswrapper> on another post, I tried it and the lights have come on on the card.
BUT ... when I do an ifconfig there is no information for the WiFi card.

Also ... will I have to do the ndiswrapper everytime I start the computer?
Is there a way to make it start up automatically?

---

### Post by DrMoxie on 2005-10-26
To make a symbolic link so that ndis is called when the card is detected at the command line type: sudo ndiswrapper -m

Since your card is lit up you just need to go to the network manager under the system menu and activate it.  After that you should be all set!

---

### Post by karlharratt on 2005-10-27
All my thanks goes to Dr Moxie and anyone who has posted similar answers on other posts.
Everything is now working perfectly.

I feel confident in my move from M$ with your help.

Thank you.

---

