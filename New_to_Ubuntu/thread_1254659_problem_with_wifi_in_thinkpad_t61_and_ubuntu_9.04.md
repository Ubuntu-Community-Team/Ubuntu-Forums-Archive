---
title: "problem with wifi in thinkpad t61 and ubuntu 9.04"
date: 2009-08-31
forum: New to Ubuntu
---

### Post by kvorion on 2009-08-31
I was using LinuxMint Elyssa for a year on my thinkpad t61. Sudddenly my wireless stopped working in school (but worked elsewhere). The connection would simply not get established with the discovered wifi networks.

Now I installed Ubuntu 9.04. The school wireless networks were detected and worked perfectly well with the LIVE CD. Assuming that it would work fine, I installed the system. Now when I boot up, it does not show ANY NETWORKS.

I don't know what to do. Kindly help.

---

### Post by kvorion on 2009-08-31
PS:

Originally I could not see the wifi adapter listed as a result of ifconfig.

I activated the alternate atheros madwifi driver and now I can see the wifi0-00 adapter, but still am not able to see any wireless networks.

Also,
wifi0-00 shows Interrupt:17 in the ifconfig output. Is that a problem?

```
sudo iwconfig
```

resulted in a lot of information under ath0, while the others show no wireless extensions.

```
sudo iwlist ath0 scan
``` 
resulted in:

ath0  No scan results

---

