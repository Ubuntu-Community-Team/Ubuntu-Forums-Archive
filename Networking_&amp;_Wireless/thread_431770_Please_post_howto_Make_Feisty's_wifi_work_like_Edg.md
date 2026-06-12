---
title: "Please post howto: Make Feisty's wifi work like Edgy's"
date: 2007-05-03
forum: Networking &amp; Wireless
---

### Post by spectro on 2007-05-03
I have a desktop for guests at home with a wifi usb adapter. When I installed edgy it was up and browsing internet pages in like 5 minutes. Just configured ID and key and it was working. It liked to crash with heavy traffic, thought (usb webcam uploads would freeze the machine after a few minutes)

Yesterday I installed Feisty and that damn Network Manager showed up. After a few hours I got it to connect but that damn keyring password keeps popping up. I applied the patch to prevent that but I have that desktop set to auto-login to a guest account and it asks for it again. I would also need to setup that damn ID, key and keyring thing for each damn user I add to that machine.

In Edgy, I configured wifi ONCE and it worked from startup for ANY USER, can somebody please post a little walkthrough to make Feisty do the same?. I would go back to Edgy but so far Feisty's wifi drivers seem more stable (usb webcam survived overnight)

This maybe as easy as disabling network manager and modifying a couple of config files, I just can't seem to find the key information anywhere.

---

### Post by chili555 on 2007-05-03
I think it's as simple as:```
sudo apt-get remove network-manager network-manager-gnome
```Then go in to System -> Administration -> Networking and re-configure your wireless interface. You may need to tweak your */etc/network/interfaces* a bit if it doesn't start on boot. Please post back if you get stuck.

---

