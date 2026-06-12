---
title: "Getting Davicom ethernet card to work"
date: 2005-09-07
forum: Networking &amp; Wireless
---

### Post by paulmclaughlin on 2005-09-07
I have had trouble getting the installation of Ubuntu to recognise my network card - the live CD and various other distros work okay, and from looking on this and other forums I know various people have had problems with this card.

I finally tracked it down to the installed copy trying to use the tulip driver rather than dmfe, as the live cd correctly uses. I am able to get the network running properly by:

```
rmmod tulip
ifdown eth0
rmmod dmfe
modprobe dmfe
ifup eth0
```

Note that dmfe is already loaded at boot-up but isn't used and by watching the device manager I needed to rmmod and modprobe it back in to get the driver to update.

Obviously this is a pain to do every time I use the computer. Can I simply delete the tulip.ko driver to ensure that it doesn't get used?

---

### Post by s_p_a_r_k_y on 2005-09-07
check and see if tulip is being loaded in /etc/modules, if so comment it out, then put in your dmfe module

---

### Post by paulmclaughlin on 2005-09-07
Thanks, Sparky. That's perfect.

---

