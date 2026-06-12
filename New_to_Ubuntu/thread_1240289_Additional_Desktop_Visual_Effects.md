---
title: "Additional Desktop Visual Effects"
date: 2009-08-14
forum: New to Ubuntu
---

### Post by VelkoMK on 2009-08-14
Once Installed, In The Appearance Prefrences in the tab Visual Effects there's the mode of makin' think all wobbly and stuff. On Youtube I saw different modes with fire and all. Where do I enable that? Is there something else that needs installing? And what's it called? Compiz, Beryl?

---

### Post by fooman on 2009-08-14
its compiz.

you need to install the compizconfig settings manager,  which will give you a gui program to apply the different effects that are available.  you can install it using synaptic (system > administration > synaptic package manager) or just type/copy/paste the following into a terminal:

```
sudo apt-get install compizconfig-settings-manager
```after it installs,  find it in system > preferences > compizconfig settings manager.

hope that helps.

---

### Post by VelkoMK on 2009-08-14
Thanks! That did the Trick. Can you please redirect me to a place so I can see how to Configure it :)?

---

### Post by fooman on 2009-08-14
maybe this will help:

[http://wiki.compiz-fusion.org/CCSM](http://wiki.compiz-fusion.org/CCSM)

i forgot,  there is a simpler app for compiz config called,  strangely enough: *simple*-compizconfig settings manager...you can install that one with this command:

```
sudo apt-get install simple-ccsm
```after installing,  find it in: system > preferences > simple comizconfig settings manager.  here is a guide for using it:

[http://enli.co.cc/customization/functional-eye-candy-for-ubuntu-within-5-minutes-using-simple-ccsm/](http://enli.co.cc/customization/functional-eye-candy-for-ubuntu-within-5-minutes-using-simple-ccsm/)

hope that helps.

---

### Post by VelkoMK on 2009-08-14
The simple one did the Trick :)
Thanks a lot!

---

