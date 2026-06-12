---
title: "Getting Wireless Working"
date: 2007-12-22
forum: Networking &amp; Wireless
---

### Post by ShutItDown on 2007-12-22
I have a HP ze4900 laptop and have a Linksys N router. I could not get the N card to work on my laptop with 7.1 so i took it out. How can i just connect to it with the built in network card? Please help.

---

### Post by ijason on 2007-12-22
you removed the network card from your laptop? it has built-in wi/fi as well? i need some more information :)

---

### Post by ShutItDown on 2007-12-22
when i had XP i was using a N card in the slot but now that i have 7.1 it wont work so i took it out and now would like to just connect with the built in one.

---

### Post by ijason on 2007-12-22
ok. 

most likely, ubuntu was able to recognize the built in wireless device in your laptop, it may just not be enabled. 

go to System > Admin > Network Tools, from the start menu, and under the Devices tab, there should be a list of the current network devices ubuntu sees on your laptop. mine has Loopback Interface, Eth0, and Eth1 for  example. 

if you see such eth0 or eth1 then it's almost certain your ubuntu can use the built in device. then you'll go to System >Admin > Network, and you should have "Wireless connection" as one of the listed connections. you just click on it and in the properties for it i believe you can set it to enabled. it should pop up a list of visible networks! :)

---

### Post by ShutItDown on 2008-01-09
i need the firmware for Broadcom 43xx chipset family. anyone know where to get that?

---

