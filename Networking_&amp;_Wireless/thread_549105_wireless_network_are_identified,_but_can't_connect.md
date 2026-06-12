---
title: "wireless network are identified, but can't connect"
date: 2007-09-12
forum: Networking &amp; Wireless
---

### Post by liorz1984 on 2007-09-12
Hello
I have an LG Laptop with fiesty fawn and INTEL 3945BG wireless card.
I can see the network list in the network manager, but for some reason i can never connect to it.
i pretty new to linux, iv'e searched through google and this forum, and nothing worked for me.
When im executing iwconfig, i get this error:
iwconfig: error while loading shared libraries: libiw.so.29: cannot open shared object file: No such file or directory

and my network listing is like that:

  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:19:db:09:a5:fa
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
(I didn't see the name of my wireless card anywhere, i called the manufacturer and asked ... maybe a driver problem?)

Furthermore, when i try to execute ipw3945d-2.6.20-16-generic, i get this error:

 ERROR: Could not find Intel PRO/Wireless 3945ABG Network Connection

Anyway, Im really desperate... Please help me :)

---

### Post by noob12 on 2007-09-12
> 
iwconfig: error while loading shared libraries: libiw.so.29: cannot open shared object file: No such file or directory


This indicates an improper installation of the wireless-tools package (which contains iwconfig, iwlist, etc.).  The version that comes with Feisty Fawn uses libiw.so.28 which is installed as part of the libiw28 package along with wireless-tools.  Did you somehow replace the wireless tool versions you had?  You might try reinstalling those from the Feisty repository.

That should let you use the tools at least.

---

