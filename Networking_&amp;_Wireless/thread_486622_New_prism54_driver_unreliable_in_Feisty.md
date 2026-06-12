---
title: "New prism54 driver unreliable in Feisty"
date: 2007-06-28
forum: Networking &amp; Wireless
---

### Post by pureblood on 2007-06-28
Since I upgraded my machine to Feisty I experienced repeated losses of connections with my Netgear WG511 wireless card (ISL3890 chipset). I didn't bother to try to understand what was going on since my card always run flawlessly before.
Then, when I tried to put the card in monitor mode, I realized that this wasn't possible anymore. Apparently the prism54 project is going through a serious redesign and the module that was once called prism54 is now called prism54common and prism54pci.
These new modules not only do not support monitor mode but they are also very unreliable (I experienced also a complete crash trying to remove one).
I am very happy that this new redesign will be able to support more cards with less proprietary software but right now I would have rather sticked with the old perfectly working driver.
I don't know if this change was a choice of the people from the kernel or a choice in the people from Ubuntu but it is just causing problems to me and to other people writing on different forums.
Does anybody know how to switch back to the old driver? I tried to compile it but it seems that it doesn't compile with the new kernel source anymore without some hack.

---

### Post by chili555 on 2007-06-28
I had trouble with my WG511 just about from the start. I researched a lot of stuff, and finally, in desperation, installed ndiswrapper. I also had to blacklist the current driver, which you can find with *lsmod | grep prism54.*

After I installed ndiswrapper, my problems ended.

---

### Post by t4thfavor on 2007-06-28
Same problem, same chipset, different card. I use an senao 200mw card, which I used to use for wireless surveys at work. Now the card is busted while using feisty. I also tried to compile the older drivers to no avail. 

I am sort of upset with this since I really liked that card :( One good thing did come of it though, I got a new Cisco card out of the deal. 

My thoughts are either see if you can downgrade your kernel to one without the new prism driver, or find a cheap temporary replacement card to use until they get the code working correctly. 

FYI My "dmesg" tells me that the driver could not read the eeprom, Is that whats going on with you?


EDIT:Ndiswrapper is a great solution, if you don't need to use monitor mode. Though it will get you connected if you don't have access to another card.
Though it is curious why the Ubuntu developers decided to include the new slightly less than functional drivers instead of the older stye ones.

---

### Post by SethD on 2007-06-30
I was fooling around with my WG511 PCMCIA card today and realized that it no longer supported monitor mode on Feisty. Just found this thread and I'm wondering if there's any way to use old modules? Does anybody know anything about that? I'm not to up on kernel mods, but would it be possible to take the old modules from Edgy and use them in Feisty?

Thanks,
Seth

---

### Post by t4thfavor on 2007-07-05
I have the same problem with one of my favorite cards. sl3054CB-plus using the isl3890 chipset. 

i get the:
[ 1221.180000] p54: LM86 firmware
[ 1223.364000] 0000:03:00.0 (prism54pci): Cannot read eeprom!
[ 1223.364000] ACPI: PCI interrupt for device 0000:03:00.0 disabled
[ 1223.364000] prism54pci: probe of 0000:03:00.0 failed with error -22

Wish I could get it working again.

---

