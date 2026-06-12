---
title: "Connecting to college network"
date: 2007-02-03
forum: Networking &amp; Wireless
---

### Post by ainsworth on 2007-02-03
Just installed version 6.06 but can't connect to the LAN, the network settings bit says there is an ethernet card there (on-board MSI, don't know the model off hand but I could find it) and I've filled in all DNS servers, gateway etc... but I can't even ping other computers on the network. (The connection is also activated, in the network tools area there is a steady stream of packets arriving, just none going out)

Am I missing something obvious, do I need to configure something in Samba?

Thanks

---

### Post by finer recliner on 2007-02-03
my university has a very powerful firewall (called ResNet) in place.

it doesnt work so well with linux. i had to apply a patch to one of my config files.

i suggest calling your CIT help desk or something and seeing if they have a work around.

---

### Post by ainsworth on 2007-02-03
I'll pop in and see them on Monday, In the meantime I'll give it a go on my friends laptop. see if its my computer or the network.

---

### Post by ainsworth on 2007-02-03
got it!! I'm online on my own computer! 
The first two numbers of my ip address were different to the network servers etc... so I tried having them the same and all is perfect now. This hadn't ever been a problem under windows so not sure why ubuntu had a problem.

---

