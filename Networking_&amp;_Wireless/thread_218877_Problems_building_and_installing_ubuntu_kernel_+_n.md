---
title: "Problems building and installing ubuntu kernel + ndiswrapper 1.8-0"
date: 2006-07-19
forum: Networking &amp; Wireless
---

### Post by SoftGround on 2006-07-19
I built downloaded and built the standard linux-source kernel (2.6.15-26.44).  I also downloaded and built ndiswrapper-source (1.8-0ubuntu4).

When I came to install the compiled ndiswrapper module (after the kernel) I got the following error.

```
root@Ubuntu:/usr/src# dpkg -i ndiswrapper-modules-2.6.15.7-ubuntu1-khz_1.8-0ubuntu2+10.00.Custom_i386.deb
Selecting previously deselected package ndiswrapper-modules-2.6.15.7-ubuntu1-khz.
(Reading database ... 143031 files and directories currently installed.)
Unpacking ndiswrapper-modules-2.6.15.7-ubuntu1-khz (from ndiswrapper-modules-2.6.15.7-ubuntu1-khz_1.8-0ubuntu2+10.00.Custom_i386.deb) ...
dpkg: dependency problems prevent configuration of ndiswrapper-modules-2.6.15.7-ubuntu1-khz:
 ndiswrapper-modules-2.6.15.7-ubuntu1-khz depends on ndiswrapper-utils (>= 1.8-1); however:
  Version of ndiswrapper-utils on system is 1.8-0ubuntu2.
dpkg: error processing ndiswrapper-modules-2.6.15.7-ubuntu1-khz (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ndiswrapper-modules-2.6.15.7-ubuntu1-khz
```

I have the latest version available of ndiswrapper-utils installed (1.8-0) and I cannot find a later version.

The only change to the kernel was to set the processor type to k7 and the clock frequency to 1000hz.

[I]I previously posted this on the Repository Forum but got no response.
[/I]

It now turns out I do not need ndiswrapper (I mistakenly thought it was part of the standard kernel), but I am still concerned that I could not install it, as everything seemed standard.

Thanks
Soft Ground

---

