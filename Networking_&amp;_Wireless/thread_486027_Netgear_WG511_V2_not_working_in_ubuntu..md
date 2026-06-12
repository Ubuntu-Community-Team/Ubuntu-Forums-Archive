---
title: "Netgear WG511 V2 not working in ubuntu."
date: 2007-06-27
forum: Networking &amp; Wireless
---

### Post by Antonio44 on 2007-06-27
I am new to the Ubuntu family here so I am a bit lost. A couple of weeks ago I managed to install my BCM4318 with the help of a wonderful person named Compwiz 18 and his how to script guide. I was hoping that someone can help me install this thing. I know it may be a pain but if someone has a heart can they give me all the commands and such because outside of a GUI I am lost. When it was inserted last it read something about Marvell as the manufacturer. I have read that this is the native driver trying to work. BUt sadly it doesn't. I am told I have to use ndiswrapper which I believe I used for my broadcom card in my other computer (The one I am using now:). I really need to get this thing to work as it is not returnable and if I wasted the money it will really make me sad. lol. Please someone help!

Thanks

A.

---

### Post by kevdog on 2007-06-27
Couple of questions:

Is this device a wireless card (PCMCIA), inside computer (PCI), or a USB device?

If its a card or inside computer (basically a PCI/PCMCIA device), go to a command prompt, type the following commands, and then cut and paste the output:
lspci
lspci -n

If its a USB device
lsusb

---

### Post by Antonio44 on 2007-06-27
Okey dokey,

First question is simple to answer it is PCMCIA.

The second is a it harder for m to do considering ubuntu is installing on that computer at the moment. Also my install seems to have frozen. It does this everytime I try and put anything but Mint on it. It is a gateway 400 laptop any Ideas. I have seen many of your posts around, which leads me to believe you know what you are doing. Anything you can give me I would accept graciously. Thanks.



A.

---

