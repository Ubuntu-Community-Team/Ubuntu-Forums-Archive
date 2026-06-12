---
title: "&quot;sudo apt-get upgrade&quot; is &quot;holding back&quot; certain updates"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by diablo75 on 2009-12-11
I have a server setup at home that I SSH into and often times I'll apply some updates while I'm connected just to get them out of the way.  I'll VNC into the server as well and apply them, but it's a little more tedious because of low bandwidth and slow screen refresh.

Anyway, I typically type into the terminal:

```
sudo apt-get upgrade
```

And most recently, it spit this out:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  bind9-host dnsutils libbind9-40 libdns45 libisc45 libisccc40 libisccfg40
  liblwres40 linux-generic linux-headers-generic linux-image-generic
  linux-restricted-modules-generic
The following packages will be upgraded:
  kdelibs-data kdelibs4c2a


I let the updates it wanted to apply go through and tried the same command again, but it kept the same packages back so nothing really happened.  I'm pretty sure if I did this through the GUI, it would work.  Is there a better command to type instead of apt-get upgrade?

---

### Post by philinux on 2009-12-11
Yes in this situation use dist-upgrade.

Just be careful using this especially if it wants to remove loads of packages. In a stable release it should be fine. People run into trouble using dist-upgrade with development releases.

---

### Post by diablo75 on 2009-12-11
> **philinux said:**
> Yes in this situation use dist-upgrade.

Just be careful using this especially if it wants to remove loads of packages. In a stable release it should be fine. People run into trouble using dist-upgrade with development releases.

That did the trick.  Didn't need to remove anything either.  Thanks!

---

### Post by LowSky on 2009-12-11
this should do it too

```
sudo apt-get update && sudo apt-get upgrade
```

If not it could be because a dependency isn't available yet, it happens from time to time, especially if you use non-Ubuntu repos

---

