---
title: "Trying to enable wowlan using iw but I get:Operation not supported (-95)"
date: 2014-03-31
forum: Networking &amp; Wireless
---

### Post by den_tha_to_matheis on 2014-03-31
Hello i am trying to enable the wake on wireless lan feature in my Toshiba satellite a100 laptop with Intel PRO/Wireless 3945ABG network interface.

I found on the official pdf document (you can find it searching the following string "intel pro wireless 3945abg wake on wireless lan") for this network interface that wowlan is supported and it should work under windows operating system. actually there is a guide how to enable it there, but i cant manage to do it in ubuntu using the iw command as I found after a lot of searching ..

Has anybody managed to make wake on wireless lan (wowlan) work ?

input: sudo iw phy0 wowlan show
output: Operation not supported (-95)

or

input: sudo iw phy0 wowlan enable magic-packet
output: Operation not supported (-95)

please give some feedback i don't know what is wrong and the documentation about this is really poor

PS: I have managed to get wol feature working when connected with a eth port and Bios wake on lan feature is enabled (although this has nothing to do with wowlan)

thanks

---

