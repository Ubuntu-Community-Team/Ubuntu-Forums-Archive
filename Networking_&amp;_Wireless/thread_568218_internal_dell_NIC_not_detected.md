---
title: "internal dell NIC not detected"
date: 2007-10-05
forum: Networking &amp; Wireless
---

### Post by abalgach on 2007-10-05
Greetings all 

I have a weird question.  I recently purchased [as in 2 weeks ago] an "Open source" desktop from dell.  Great machine, dual core, lots of ram, etc.  The only downside is that I can't get ubuntu [Fiesty]  However the internal NIC which dell lists as "item 430-0412	Integrated NIC card"  doesn't really help me determine which chipset i should be running.  I read somewhere that the e9000 is the correct chipset [its a dimension 530e]  but that seemed to be a dead end.  a great linux box with no internet is terrible.  im toying with the notion of just buying another card to get the thing running, but i feel like the internal network card should just be recognized.  any advice on how to a. figure out which card it is. and or b. install the drivers and get this thing working?  have never once had a linux install NOT detect the network card.

thanks,
a.

---

### Post by kevdog on 2007-10-05
can you list 

lshw -C network
lspci -nn

That will give us a good starting place to troubleshoot!

---

