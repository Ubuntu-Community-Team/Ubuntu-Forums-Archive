---
title: "Problem with wireless"
date: 2008-06-26
forum: Networking &amp; Wireless
---

### Post by Mav7rick on 2008-06-26
I just installed Ubuntu and encountered a problem with wireless. It seems like Ubuntu doesnt support my wireless adapter, then I tried to follow this guide [https://help.ubuntu.com/community/Wi...er/Ndiswrapper](https://help.ubuntu.com/community/Wi...er/Ndiswrapper) but after i downloaded the windows driver files for my wireless adapter, i couldn't open or unpack it, it's an exe file, but when i use ethernet instead, it's ok, no problem anymore.
And this is my wireless adapter information
> Atheros Communications Inc. AR5418 802.11abgn Wireless PCI Express Adapter
Please help me, thank you very much :lolflag:

---

### Post by caljohnsmith on 2008-06-26
> **Mav7rick said:**
> I just installed Ubuntu and encountered a problem with wireless. It seems like Ubuntu doesnt support my wireless adapter, then I tried to follow this guide [https://help.ubuntu.com/community/Wi...er/Ndiswrapper](https://help.ubuntu.com/community/Wi...er/Ndiswrapper) but after i downloaded the windows driver files for my wireless adapter, i couldn't open or unpack it, it's an exe file, but when i use ethernet instead, it's ok, no problem anymore.
And this is my wireless adapter information

Please help me, thank you very much :lolflag:

Have you researched whether madwifi supports your chipset? In general madwifi supports most Atheros chipsets, but I don't exactly which ones are the exceptions. But if you know for sure you have to go the ndiswrapper route, you could maybe run that drivers exe file you downloaded under Wine to get it to extract. Ultimately what you are after is the .inf and .sys files for the driver, which you need for ndiswrapper.

---

