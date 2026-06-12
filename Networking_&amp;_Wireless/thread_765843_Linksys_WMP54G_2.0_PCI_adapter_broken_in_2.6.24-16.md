---
title: "Linksys WMP54G 2.0 PCI adapter broken in 2.6.24-16-generic"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by ekravche on 2008-04-24
There is a kernel issue with 2.6.24-16-generic. Wireless seems to be broken for me. I have a PC with a Linksys WMP54G 2.0 PCI adapter (RaLink RT2500 802.11g ). I'm booting 2.6.22-14-generic and wireless runs smoothly, but when I switch to 2.6.24-16-generic wireless runs but with tons of errors, and as a result wireless speed drops.

Also when I play tremulous, I get the following error (see attachment)

This started to happen after I upgraded to Hardy 8.04

---

### Post by ekravche on 2008-04-25
I've filed a bug here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/222034](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/222034) .

---

### Post by ekravche on 2008-05-08
The same bug filed earlier, with several work arounds can be found here [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/190515](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/190515)

---

