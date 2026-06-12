---
title: "Wont recognize wireless card(noob)"
date: 2007-03-22
forum: Networking &amp; Wireless
---

### Post by JakeSteelXD on 2007-03-22
I have recently installed Ubuntu 6.10 and have a problem connecting to my wireless network. My wireless card is supported, but when i go to the connections it does not show up as a choice. How do I make Ubuntu recognize my wireless card?

---

### Post by cyberdork33 on 2007-03-22
What IS the wireless card...

---

### Post by JakeSteelXD on 2007-03-22
Wireless 802.11b MiniPCI Adapter

---

### Post by Mooie on 2007-03-22
anybody know anything about his ibm thinkpad r31?

---

### Post by Mooie on 2007-03-22
oops, the info in this post was wrong I just deleted it

---

### Post by Mooie on 2007-03-22
I just read this, so it turns out it doesnt use an intel wireless card.

[http://learn.clemsonlinux.org/wiki/Laptops:IBM_Thinkpad_R31](http://learn.clemsonlinux.org/wiki/Laptops:IBM_Thinkpad_R31)
> Wireless

This is a miniPCI version of the common Intersil Prism 2.5 Wavelan chipset. It is supported by both the Wavelan drivers and the Orinoco drivers. The Orinoco drivers are, IMHO, easier to use along with the Wireless Tools, and the Wireless Page can help you out with all of that. Just make sure you have the drivers hermes, orinoco and orinoco_pci compiled as modules.

Unlike some of its descendants in the Thinkpad line, this machine does not have a wireless network usage light. You can Google a little and find a program called netled which displays network traffic using one of your keyboard LED's. This isn't entirely useful, but sometimes fun. 

---

### Post by Mooie on 2007-03-27
what I know so far:

a) IBM thinkpad r31
b) miniPCI Prism 2.5 Wavelan chipset
c) behind a router, and using roadrunner cable
d) it wont get online even using an ethernet cord
e) no network devices are detected/work

he is a friend of mine, and wants to convert from windows to linux (it runs a lot faster on his laptop) He really needs to get online, and wants to reinstall windows until i figure out what the problem is, he will probably do this tomorrow some time (thats what he told me anyway).  I really dont want to see him go back to windows, so could you please help him!

thanks :-D

---

### Post by Mooie on 2007-03-29
After installing the hostap-source package, it still doesnt connect via eth1 or wlan0

---

