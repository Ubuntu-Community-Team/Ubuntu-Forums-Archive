---
title: "Have to mess around with network settings every bootup"
date: 2008-03-30
forum: Networking &amp; Wireless
---

### Post by Miles111 on 2008-03-30
Hello,
Whenever I restart or switch on my PC and go into ubuntu, it does not connect to the internet, and to get online I have to mess around, reentering data and disabling and reenabling my wireless network card to get it to connect. Is there a way past this irritating routine? It tends to take a good 5 minutes, which I would rather avoid, as it frustrates me.

---

### Post by kutjara on 2008-03-30
> **Miles111 said:**
> Hello,
Whenever I restart or switch on my PC and go into ubuntu, it does not connect to the internet, and to get online I have to mess around, reentering data and disabling and reenabling my wireless network card to get it to connect. Is there a way past this irritating routine? It tends to take a good 5 minutes, which I would rather avoid, as it frustrates me.

It might not be the same problem, but my wireless card wouldn't work at bootup unless I manually typed the "modprobe" command for the card each time. While this worked, it was a bit of a bore having to reenable the damned card after every shutdown, sleep, or hibernate.

Finally, I found an unrelated thread that gave me the clue I needed: I had to edit the modules file to include a line pointing to my card. In my case, because my laptop uses an Atheros chipset, I had to insert "ath-pci." I did this by typing:

sudo gedit /etc/modules

and then entering:

ath-pci

on its own line at the end of the text already present.

Now, my wireless card comes up properly everytime I boot.

Clearly, what you have to type into the modules file will depend on what modprobe command you need to enable the card.

I hope this helps.

---

