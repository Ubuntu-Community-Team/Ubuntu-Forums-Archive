---
title: "Intel 2200bg: How can I change the country code?"
date: 2006-12-10
forum: Networking &amp; Wireless
---

### Post by HerrBert on 2006-12-10
Hello,

I am using the "Edgy Eft" on my Toshiba Centrino laptop (Intel 2200bg WLAN chip). Standard installation, only added the "Network Manager".  

Here is my problem:

When I failed trying to connect to a WLAN (802.11g) broadcasting on channel 12, I found (via "iwlist eth1 channel") that I could not use channel 12 with my Intel 2200bg card.  
This came somewhat unexpected, since I bought and operate my laptop in Europe, where channels 1-13 are allowed for WLAN. I found out, Toshiba sells their notebooks with a special country code hardcoded into the WLAN-chip that only allows channels 1-11.

I stumbled upon a workaround for this:

[http://www.thinkwiki.org/index.php?title=Ipw2200&printable=yes#Changing_the_enabled_channels]("http://www.thinkwiki.org/index.php?title=Ipw2200&printable=yes#Changing_the_enabled_channels")

My method of choice would be patching the driver, but I have no clue how to do this, since I am completely new to the Linux world.  Could you give me step by step instructions?

Thank you very much!

HerrBert

---

