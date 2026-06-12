---
title: "[ORiNOCO] Gives some weird errors."
date: 2007-05-27
forum: Networking &amp; Wireless
---

### Post by WeeJeWel on 2007-05-27
So i followed the tutorial on [http://my.opera.com/subjam/blog/show.dml/473107](http://my.opera.com/subjam/blog/show.dml/473107) to install my SpeedTouch 120. But when i make the package, i get the following error.
> make -C /usr/src/linux-headers-2.6.20-15-generic M=/home/emile/orinoco KERNELRELEASE=2.6.20-15-generic modules
make[1]: Map '/usr/src/linux-headers-2.6.20-15-generic' wordt binnengegaan
  CC [M]  /home/emile/orinoco/orinoco.o
[B]/home/emile/orinoco/orinoco.c: In functie &#8216;orinoco_get_drvinfo&#8217;:
/home/emile/orinoco/orinoco.c:4287: fout: &#8216;struct net_device&#8217; has no member named &#8216;dev&#8217;
/home/emile/orinoco/orinoco.c:4288: fout: &#8216;struct net_device&#8217; has no member named &#8216;dev&#8217;[/B]
make[2]: *** [/home/emile/orinoco/orinoco.o] Fout 1
make[1]: *** [_module_/home/emile/orinoco] Fout 2
make[1]: Map '/usr/src/linux-headers-2.6.20-15-generic' wordt verlaten
make: *** [modules] Fout 2

Anyone got a clue what my problem is? I'm really stuck at the moment :) 
I'm running Kubuntu with kernel 2.6.20-15.

Thanks in advance!

---

### Post by WeeJeWel on 2007-05-27
Anyone?

---

### Post by WeeJeWel on 2007-05-28
Sorry I have to bump, but is there no one who knows what this is? :O

---

### Post by chili555 on 2007-05-28
You might just try amending *orinoco.c* with gedit or kate to edit both lines 4287 and 4288 of orinoco.c replacing dev->dev.parent with dev->class_dev.dev. Then try *make again.*

---

