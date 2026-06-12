---
title: "Broadcomm wireless does not work :-("
date: 2006-11-13
forum: Networking &amp; Wireless
---

### Post by Timokl on 2006-11-13
Hi, 

my wireless is screwed up after upgrading from Dapper (where everything worked with Ndiswrapper) to Edgy.

I gave the bcm43xx module a shot, but it never worked with my card (Broadcom 4318) which is known to make probs with this module, when I booted up.

So, I decided to go back to Ndiswrapper. I followed these instructions for my Acer notebook: [https://help.ubuntu.com/community/WifiDocs/Acer5021WLMi_Amd64]("https://help.ubuntu.com/community/WifiDocs/Acer5021WLMi_Amd64")

All the instructions work up to this point:

```
root@aristoteles:~/Desktop/80211g# modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

```

What could be the problem?

Thanks for any help!

Timo

BTW: Although my notebook has an AMD64 cpu, I run Edgy 32bit with the standard kernel.

---

