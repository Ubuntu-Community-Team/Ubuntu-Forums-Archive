---
title: "Turning off wireless radio on a macbook?"
date: 2009-07-26
forum: New to Ubuntu
---

### Post by confused_person on 2009-07-26
I'm new to linux, very recently installed Jaunty on my macbook, which does not have a wireless on/off switch. Is there a way to do this via gui or terminal?

I ask because my wireless card [broadcom bcm4328] is apparently not recognized by default, but in order to correct that I need to be able to turn the wireless switch on/off ([https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/365857](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/365857)) Thanks!

---

### Post by Liolikas on 2009-07-26
if you see it in:
sudo ifconfig -a
So you can turn it off:
sudo ifconfig name down
And on:
sudo ifconfig name up

But basically if you see it in ifconfig already so it means it works.

double check what card you have with: lspci
If no swich so maybe other?

---

### Post by confused_person on 2009-07-26
> **Liolikas said:**
> if you see it in:
sudo ifconfig -a
So you can turn it off:
sudo ifconfig name down
And on:
sudo ifconfig name up

But basically if you see it in ifconfig already so it means it works.

double check what card you have with: lspci
If no swich so maybe other?

"it" being the broadcom card? Yup, that shows up in ifconfig under Network Controller. Dumb question, but I'm new at this and don't want to screw anything up- how much of the name do I put in the terminal command? Do I put the whole thing, which is "Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)"? Thanks for your help!

---

### Post by Liolikas on 2009-07-26
No that part on side only something like eth1.
But if you see it it means it is recognized by default.
Try to do simple scan:
sudo iwlist scan

---

