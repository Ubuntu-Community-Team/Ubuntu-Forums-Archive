---
title: "Need help for drivers - Asus PCE N53"
date: 2018-10-27
forum: Networking &amp; Wireless
---

### Post by jopidia on 2018-10-27
Hello! As the title states, I have an Asus PCE N53 (Ralink corp. RT5592 PCIe) Wireless Network Adapter in my **desktop computer**. This is not (currently) supported by the Linux kernel, and I'm having trouble installing drivers. Here is some information on my system and network adapter:

The pastebinit as described in the "Before You Post" thread: [http://paste.ubuntu.com/p/PrtWDjGPMF/](http://paste.ubuntu.com/p/PrtWDjGPMF/)
```

04:00.0 Network controller: Ralink corp. RT5592 PCIe Wireless Network Adapter

joseph@joseph-pc:~$ uname -a
Linux joseph-pc 4.18.0-10-generic #11-Ubuntu SMP Thu Oct 11 15:13:55 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

joseph@joseph-pc:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 18.10
Release:        18.10
Codename:       cosmic

```

Here are some things I have tried:
1. The driver files from the Asus Website (this is only supported as of 2.6.x) [https://www.asus.com/us/Networking/PCEN53/HelpDesk_Download/](https://www.asus.com/us/Networking/PCEN53/HelpDesk_Download/)
2. The driver files from [https://github.com/mareksuscak/asus-pce-n53-linux](https://github.com/mareksuscak/asus-pce-n53-linux) (actually a bit surprised this didn't work).
3. The driver files from [https://github.com/unused/patched-Asus-PCE-N53-linux-driver ]("https://github.com/unused/patched-Asus-PCE-N53-linux-driver")

Things that I have yet to try:
1. Ndiswrapper (and I'd strongly prefer not to use it)
2. Buy a different wireless network adapter (strongly considering this option, unfortunately)

Thanks for any assistance you may provide!

---

### Post by jopidia on 2018-10-27
bump

---

### Post by jopidia on 2018-10-28
bump #2

---

### Post by chili555 on 2018-10-29
I know of nothing that changes my previous opinion: [https://askubuntu.com/questions/1010751/need-help-with-installing-driver-for-asus-pce-n53-11n-n600-pci-e-adapter](https://askubuntu.com/questions/1010751/need-help-with-installing-driver-for-asus-pce-n53-11n-n600-pci-e-adapter)

> Buy a different wireless network adapter (strongly considering this option, unfortunately)PCIe or USB? Let's get started.

---

### Post by jopidia on 2018-10-30
Thanks for replying! I hadn't come across that askubuntu post. Answers my question (unfortunately) perfectly.

> **chili555 said:**
> PCIe or USB? Let's get started.

Probably PCIe, but I should be able to tackle it from here ;)

**EDIT:**
On second thought, some ideas would be very helpful!

---

### Post by chili555 on 2018-10-30
> On second thought, some ideas would be very helpful!
Find out from Dr. Google if your laptop manufacturer whitelists the wireless devices that may be installed. Some do; most do not.

This should give you some idea as to the whitelist process: [https://joshuawise.com/wireless-whitelist](https://joshuawise.com/wireless-whitelist)

Next, cards come in several form factors. Most recent cards are PCIe. [http://www.machinaelectronics.com/blog/a-guide-to-mini-pci-laptop-wireless-cards/](http://www.machinaelectronics.com/blog/a-guide-to-mini-pci-laptop-wireless-cards/)

I have great luck with Intel cards. I use a 7260 AC model. [https://www.amazon.com/Intel-Dual-Band-Wireless-Ac-Hmc/dp/B00DMCVKMU/ref=sr_1_4?ie=UTF8&qid=1540905884&sr=8-4&keywords=intel+7260+ac](https://www.amazon.com/Intel-Dual-Band-Wireless-Ac-Hmc/dp/B00DMCVKMU/ref=sr_1_4?ie=UTF8&qid=1540905884&sr=8-4&keywords=intel+7260+ac)

Most laptops have either a little door on the bottom where the card is accessable or else the entire bottom panel is removable. You can probably look up the service manual for your specific laptop to find the access method. Here is an example: [https://www.tcscolumbus.com/wp-content/uploads/TCS-Wireless.jpg](https://www.tcscolumbus.com/wp-content/uploads/TCS-Wireless.jpg)

If you have further questions, please post back.

---

### Post by vidtek on 2018-10-30
Jopidia-

Before you get too involved with ndis drivers, download a live Ultimate Edition.  That has native support for many esoteric and newer wireless adaptors and ndis support built-in.

You have nothing to lose by trying it.

Cheers, Tony.

---

### Post by jopidia on 2018-10-30
Thanks for the resources! I'm actually using a desktop computer, but I should find some of your resources helpful despite!

---

### Post by jopidia on 2018-10-30
> **vidtek said:**
> You have nothing to lose by trying it.

I suppose the only thing I have to lose is time!

I made a promise to myself that I wouldn't use any of the more obscure distros - whether or not you consider Ultimate Edition a distro and whether or not you consider it obscure, I haven't heard of it before, so I think I will pass at this point in time!

---

### Post by chili555 on 2018-10-30
> **jopidia said:**
> I suppose the only thing I have to lose is time!

I made a promise to myself that I wouldn't use any of the more obscure distros - whether or not you consider Ultimate Edition a distro and whether or not you consider it obscure, I haven't heard of it before, so I think I will pass at this point in time!I haven't seen ndiswrapper work properly in several years. It's a dead end.

---

### Post by vidtek on 2018-10-31
> **jopidia said:**
> I suppose the only thing I have to lose is time!

I made a promise to myself that I wouldn't use any of the more obscure distros - whether or not you consider Ultimate Edition a distro and whether or not you consider it obscure, I haven't heard of it before, so I think I will pass at this point in time!

Jodidia-

When it all boils down to it, time is the only real currency any of us have.  You decide how to spend it, but my suggestion could save you a lot of it.  Why stuff around scouring the net for drivers, upgrading kernels, compiling all sorts of stuff when you could just d/l a distro and test if it works out of the box like it did for me and my new wireless network card.

It's up to you, that is the beauty of open source.

Best of luck, Tony.

---

### Post by sydclu on 2019-03-09
I was in a similar situation earlier today, Ubuntu 18.04 with kernal 4.18. 

Just sorted it out with both 2.4Ghz and 5Ghz with some decent speed. The updated package can be used just needing a little more steps.
 
[https://github.com/mareksuscak/asus-pce-n53-linux/issues/2](https://github.com/mareksuscak/asus-pce-n53-linux/issues/2)

---

