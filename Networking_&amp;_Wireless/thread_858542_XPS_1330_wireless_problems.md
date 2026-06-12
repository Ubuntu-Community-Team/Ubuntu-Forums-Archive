---
title: "XPS 1330 wireless problems"
date: 2008-07-13
forum: Networking &amp; Wireless
---

### Post by TetelestaiSCG on 2008-07-13
I have Hardy installed on my XPS 1330.  My internet has worked perfectly until last night.  I had some updates come through, but I didn't check what they were.  Anyway, my wireless isn't working and my network manager went back to the old one I hadn't seen in years.  Any ideas.  

I was using ndiswrapper because the computer wasn't showing internet otherwise.  Thanks in advance.

---

### Post by PinkFloyd102489 on 2008-07-13
Probably got a kernel upgrade, which means you'll have to reload the ndiswrapper module.

```
sudo modprobe ndiswrapper
```

I forget how to permanently load it, but that's a quickfix.

---

