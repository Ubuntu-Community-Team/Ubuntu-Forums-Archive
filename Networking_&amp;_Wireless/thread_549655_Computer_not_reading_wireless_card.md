---
title: "Computer not reading wireless card"
date: 2007-09-12
forum: Networking &amp; Wireless
---

### Post by killerabbit on 2007-09-12
i have a netgear wg511 v2 pci card. My laptop is rather old (a dell latitude) and won't recognize the card. I know the interface is right, but am i missing a crucial step? should i be telling my computer to read the card? i am a first time ubuntu user. xubuntu to be exact, if that helps. Thank you

---

### Post by jimrz on 2007-09-12
> **killerabbit said:**
> i have a netgear wg511 v2 pci card. My laptop is rather old (a dell latitude) and won't recognize the card. I know the interface is right, but am i missing a crucial step? should i be telling my computer to read the card? i am a first time ubuntu user. xubuntu to be exact, if that helps. Thank you

Welcome

a quick search and I found [[COLOR="Sienna"]**_this thread_**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=74591&highlight=wg511+v2") indicating that you should download the windows driver for your card from the Netgear site and use it with ndiswrapper in order to get the card working and gives instructions on how to complete the process. remember...search is your friend

---

### Post by kevdog on 2007-09-12
if you check
lspci -nn
lshw -C network

You should see that indeed the card is being seen but the driver probably isnt installed correctly.  As the above poster recommended ndiswrapper is an option depending on your chipset, which I dont know (but with the output of the above commands I would :))

---

### Post by killerabbit on 2007-09-13
sorry, forgot to say that ndiswrapper is installed and the driver is too, and is working fine. I diagnosed the problem, my laptop just isnt reading the slots themselves.

---

