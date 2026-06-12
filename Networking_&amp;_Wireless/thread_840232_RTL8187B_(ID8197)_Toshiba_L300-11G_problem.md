---
title: "RTL8187B (ID:8197) Toshiba L300-11G problem"
date: 2008-06-25
forum: Networking &amp; Wireless
---

### Post by mirkoslav on 2008-06-25
Hi!

I tried to get this card working using tutorials and instructions on this forum but no luck. Ndiswrapper installs correctly after changing the id in the INF file and reports the hardware present and working, but iwlist scanning sees no networks. I tried blacklisting rtl8187 driver as advised, no difference. I also tried the patched cuervo drivers on 2.6.24-19 kernel which compile and insert correctly, but the kernel crashes when I try to connect to a WEP network and caps lock just blinks. 

Can anybody please give me any advice, I read somewhere that Toshiba laptops (mostly RTL8187B ID:8197) are most problematic, so please if anybody has any advice, I would be most grateful. Ndiswrapper would be a good solution for me, but it doesn't work. I tried Win98 driver and XP driver with it, with no different outcome ... no errors reported, but no networks are found and I can't connect anywhere... my laptop is Toshiba L300-11G and everything else works perfectly, but I need the wlan to dump XP completely. Please help!

Thanks in advance!

---

### Post by mbarvian on 2008-06-25
Hi, I have a Toshiba laptop with the same card.  Unfortunately, they are problematic, but I wrote a guide [here]("https://help.ubuntu.com/community/ToshibaSatelliteA215S7422Guide?highlight=(a215)") to help people set up their Toshiba A215-S7422 (the model I have).  I know you have a different model, but please click the link above and look at the first section, which is a step-by-step tutorial on how to get the wireless working. However, I don't know if it works with WEP, but it works great with unsecured networks.

BTW, I have also tried ndiswrapper with no luck :(

---

### Post by MasterSander on 2008-06-25
I have the same card. [http://ubuntuforums.org/showthread.php?t=765671](http://ubuntuforums.org/showthread.php?t=765671) This should work, som people have luck using ndiswrapper but I use the patched version.

---

### Post by foreilly on 2008-12-27
FYI ... If you're running intrepid ibex on your Toshiba L300, an option is to upgrade to the new kernel 2.6.28, and wireless should just work out of the box for you, no ndiswrapper needed.

---

