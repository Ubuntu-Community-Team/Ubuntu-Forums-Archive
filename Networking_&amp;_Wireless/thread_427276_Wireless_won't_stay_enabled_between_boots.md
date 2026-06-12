---
title: "Wireless won't stay enabled between boots"
date: 2007-04-29
forum: Networking &amp; Wireless
---

### Post by Gadren on 2007-04-29
I run Feisty Fawn on a Dell Inspiron 6400/e1505, with a 1390 wireless card.  I have my wireless set up, but every time I start up, I have to run the following command to get wireless:

sudo modprobe ndiswrapper

How can I set it so I don't have to keep typing this in?

---

### Post by got_nix on 2007-04-29
yeah.. I"ve had the same problems.. I realizeds when i do ndiswrapper -l it says driver installed alternate driver bcm43xx however i did black list it.. so. .i'm not sure why its still there :s

---

