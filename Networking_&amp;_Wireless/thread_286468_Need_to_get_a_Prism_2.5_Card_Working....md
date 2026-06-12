---
title: "Need to get a Prism 2.5 Card Working..."
date: 2006-10-27
forum: Networking &amp; Wireless
---

### Post by justintime32 on 2006-10-27
I'm fixing a computer for a friend, which needs a new MoBo (they've agreed to let me install Linux because they don't want to pay for Windows).

Anyway, they have a D-Link DWL-520 Rev E (A Prism 2.5 Wavelan card)

To make sure this card worked, I hooked it into my computer. It was detected as wlan0, although it couldn't do anything (scanning, etc.). I've tried a lot of things, including blacklisting modules (orinoco, orinoco_pci, hermes) although it still will not work.

Right now I'm installing linux-wlan-ng and the firmware (although for some reason the Ubuntu servers are *very* slow right now, so It may take a while.

I just need to know the easiest, cleanest way to get this card working. I'd prefer not to use ndiswrapper, but I can use it if it's the best/easiest way to do it.

---

### Post by stani on 2007-03-15
Help this bug out on Feisty, contribute by passing your details to launchpad:

[https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63989](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63989)

> Can everyone affected please attach (do not paste into comment) the output of "lspci -vv" and "lspci -vvn", make sure to name the file something like lspci-vv-<yourname>.txt

There is not much time left, please participate!

Stani

---

### Post by chili555 on 2007-03-15
The prism 2.5 is one of the easiest cards to get going. I have a pcmcia version in one of my too many laptops. Why does a sane man need three laptops and two desktop computers. Help!

I would unblacklist everything except prism2_pci. In my multi-lappy experience, orinoco and hostap will play nicely together, but not prism2. I never tried wlan-ng; never had to.

Get the ESSID and WEP set correctly and you're all set.

---

