---
title: "Network assistance needed (assume I know NOTHING)"
date: 2009-03-20
forum: New to Ubuntu
---

### Post by Karyzma on 2009-03-20
Hello, I am a complete noob to linux and uBuntu.  I literally just installed it on my notebook today.  I need an extremely layman, easy to follow, elementary, step-by-step guide on how to get an atheros wireless card to function properly and allow me to connect wirelessly to a network.  I am aware that there are several posts on the forums regarding this issue but they all start going over my head with jargon and they became too difficult to follow.  I would appreciate any and all help that I receive

---

### Post by Kevbert on 2009-03-20
Welcome to Ubuntu.
First of all we need to know what type of Atheros card (and chipset) you are using. Please go to Applications-Accessories-Terminal and type in the following:
```
lspci > lspci.txt
iwconfig > iwconfig.txt
```
Now open a new post and add the lspci.txt and iwconfig.txt files as attachments.

---

### Post by taavikko on 2009-03-20
I'll suspect that you're using the latest release, that is 8.10
And atheros chip 500*

Then make sure you havent enabled the restricted drivers from System->Admin->Restricted drivers (or what was it called?)

Install package "linux-backports-modules-intrepid-generic"
That way you'll get the ath5k driver for atheros.

Next, make the driver load on the startup
```
echo "ath5k" |sudo tee -a /etc/modules
```
copy&paste to avoid mispelling

And restart computer (power off)

If it isn't working, paste the outputs of these two commands
```
lspci
```
```
dmesg |tail -30
```

---

### Post by Karyzma on 2009-03-20
Thank you very much  Taavikko, it worked just like you said after restart.  I appreciate it.  Does make me wonder though why there are so many more complicated fixes listed in the forums?

---

### Post by Kevbert on 2009-03-20
That's an easy fix taavikko. I'll bookmark that for future reference. Thanks.

---

