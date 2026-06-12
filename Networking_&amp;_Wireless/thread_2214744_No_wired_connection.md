---
title: "No wired connection"
date: 2014-04-02
forum: Networking &amp; Wireless
---

### Post by Mike_Lavender on 2014-04-02
I have installed Ubuntu 12.04 LTS along side my Windows7 as I am getting a message telling me my windows 7 is not authenticated. I installed it (windows 7) on a new desktop machine I built. Anyway, it seems when I initially installed and started Ubuntu the wired connection connected to the internet then it disconnected and I am not able to get a stable internet connection at all. 

Please help... everything else works, except, when I have tried to load drivers from a disk, like my Gigabyte mother board utility and drivers, and a wireless card driver from Asus. I get an error message that says "can't find autorun program".

---

### Post by apohal9 on 2014-04-03
Would you mind to please provide the output of the following commands?

```

lspci -nnk
dmesg
ip addr
ip route
nm-tool
```

---

