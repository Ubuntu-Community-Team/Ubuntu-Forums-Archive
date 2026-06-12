---
title: "How to go on broadband"
date: 2005-04-13
forum: Networking &amp; Wireless
---

### Post by deltablaze on 2005-04-13
Hi, Im new to linux and I was wondering how the hell I use my modem with it. Im on dsl connected through a usb to the modem. Please someone help giving me a step by step guide im lost! [-o<

---

### Post by philipacamaniac on 2005-04-13
Er, hmm. Although you are currently connected via USB to the modem, I highly doubt the modem drivers exist in Linux. Almost all DSL modems (which, to use the name modem in this case, is a misnomer) have an Ethernet jack. My advice would be to go get an Ethernet patch cable and plug it in.

If that is simply not an option, you'll have to provide the manufacture and model of your DSL modem, so someone can tell you whether drivers exist or not. 

Oh, and if you're not behind a router, which you're not, then you'll definitly want to install firestarter or some kind of Firewall tool. Search for firewall in synaptic.

---

### Post by deltablaze on 2005-04-14
Its a Zyxel Prestige 600, if you could see whether it exists for drivers thanks
EDIT:I went to the computer icon at the top and then device hardware or something like that, many of my things came up including my processor etc...there was a usb interface thing I clicked on that and it said Zyxel in the window to the right. So linux seems to be knowing my modem but my modem not knowing my linux. Can anyone help?

---

### Post by philipacamaniac on 2005-04-14
Here is the driver for the Zyxel Prestige 630: [http://sourceforge.net/projects/zyxel630-11](http://sourceforge.net/projects/zyxel630-11)  which according to a Google search works with the 600. The sourceforge driver offers some instructions. You'd have to compile it because only the source code is provided. 

Also check out [http://usuarios.lycos.es/amedyn/uniwaka/wakka.php?wakka=Amedyn](http://usuarios.lycos.es/amedyn/uniwaka/wakka.php?wakka=Amedyn)
 because it appears to be a HowTo on using the Zyxel Prestige in Debian, but it doesn't seem to be complete. You're in luck, because after Googling, I noticed that a lot of people are using the device in Linux, albeit with setup frustrations.

---

### Post by deltablaze on 2005-04-16
Thanks a million

---

