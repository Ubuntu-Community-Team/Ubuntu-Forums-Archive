---
title: "Linksys WMP54G Wireless adapter"
date: 2007-05-05
forum: Networking &amp; Wireless
---

### Post by SamsLembas on 2007-05-05
I have recently purchased and installed a WMP54G wireless adapter for a Feisty Fawn running PC. The adapter seems to be recognized, but when I try to connect to one of the networks on the list, it stalls at the connecting stage for a while before just going back to having no network connected. I have done quite a bit of Googling without finding anything useful. Anyone have any suggestions? Should I just return this adapter and get a different one? If so, what adapters work well with Linux?


I am fairly new to Linux, though I have limited command line experience from Mac. Also, I have no internet going dirrectly into my computer, but I can transfer files to it from a different one.

---

### Post by MeneM on 2007-05-06
Hi,

It sounds as though you have the Broadcom chipset version of that card. My answer is [this]("http://ubuntuforums.org/showthread.php?t=403229") would apply here as well.

I'm fond of Linksys but am sad to see them using broadcom chipsets. Those things just plain suck...

Anyway, back to your question: If you are using Edgy follow this guide: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy)

In any case, also post the output of "lspci" here is this thread. Just to see if it really is a broadcom card ;-)

---

