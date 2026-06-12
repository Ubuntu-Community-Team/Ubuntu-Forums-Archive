---
title: "linksys network problem"
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by andrude27 on 2008-05-04
I'm having problems with a linksys lne100tx pci network card. I tested the card in a compaq box and auto detected it fine. I put the card in my amd athlon 900mz and it won't work. The module I need according to all the docs I can find is tulip. I have tulip mod loaded. Ifconfig ,no network. lspci shows the card but says unclaimed device. I don't understand why it detected fine in the compaq but not in my amd. I know the amd works as I had been using a broadcom 4306 wireless before I lost that in an upgrade to 8.04. I have since reinstalled back to 7.10. I have a clean install and even tried running from the cd. I would put the wireless card back in but it's a little slow and I just spent the time and money to go hard wired. I have a feeling that the solution is something simple I'm overlooking. Also I tested the cables with a working box and even in the amd I have link light. What can I do?

---

### Post by andrude27 on 2008-05-05
hey it's me again. Never mind tying to help with the linksys problem. I loaded up open suse 10.3 and the card works fine. I've given up on ubuntu on that box as it seems to always have trouble networking. There must be some different module or kernel that allows open suse to see and configure my card . I was able to see and use the card on a compaq with ubuntu running an intel p2 233 chip but not with my amd athlon 900 chip. Somehow the different chipsets confuse ubuntu but not open suse. I just mention this for those of you that are working on bug fixes. I hope this added info helps with the debugging. I don't need further help with this issue. Thanks anyway.

---

