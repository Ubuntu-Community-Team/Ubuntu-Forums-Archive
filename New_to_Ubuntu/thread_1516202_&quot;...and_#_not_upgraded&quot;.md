---
title: "&quot;...and # not upgraded&quot;"
date: 2010-06-23
forum: New to Ubuntu
---

### Post by adobrakic on 2010-06-23
When I upgrade, I get the following:

```
ado@ado-laptop:~$ sudo apt-get upgrade --yes
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  brasero libbrasero-media0 linux-generic linux-headers-generic
  linux-image-generic mozilla-plugin-vlc vlc vlc-data vlc-nox vlc-plugin-pulse
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.

```

Anyone know why they're not being upgraded?

---

### Post by snowpine on 2010-06-23
Try:

```
sudo apt-get dist-upgrade
```

dist-upgrade differs from upgrade in that it allows the upgrade of packages that would require installation/removal of other packages. Of course you should be careful and read the list before saying Yes, rather than using the --yes flag, in my opinion. :)

---

### Post by adobrakic on 2010-06-23
Ah, that fixed it right up :D thanks a lot! and yeah, i should probably read the list, but even if i didn't put --yes, i'd just blindly put 'y' and hit enter. :p i spoil ubuntu with trust

---

### Post by Paqman on 2010-06-23
You can also do the upgrade through Synaptic, rather than the command line. It's probably a bit clearer to see exactly what will be installed and removed in Synaptic.

---

