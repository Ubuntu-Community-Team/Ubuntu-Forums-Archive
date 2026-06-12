---
title: "Wireless network adapter.. fried!?"
date: 2011-07-22
forum: New to Ubuntu
---

### Post by HFriberg on 2011-07-22
Hello everyone,

I've heard that I could try Ubuntu in a "safe way" without messing with my Windows installation, and went for the newest wubi 11.04. I used a standard installation (all defaults), chose af username, restarted in ubuntu, and was delighted by what I saw and ease of installation. I was, however, not able to configure the wireless connection and thus booted back into Windows to search for help online. Then came the big shock, my wireless internet connection no longer worked in Windows! Wubi had somehow messed with my Windows installation.

I have currently tried to:
 - Uninstall wubi
 - Deactivate/activate the network adapter numerous times
 - Full system recovery

While the network adapter displays itself on the computer, it shows as "Not turned on" although I have a small LED on the frontpanel of my laptop stating otherwise. My best guess is that the network adapter have been fried by a faulty software driver. What is your guesses and do you have any suggestions for me?

Btw, the network adapter is a: Broadcom 802.11n

---

### Post by jtarin on 2011-07-22
Not possible for a software driver to fry a network adapter.Can you give us some more information about your computer? Make,model.....etc. What version of windows do you have? Check Device Manager in Windows and see if the adapter is having problems....possibly the windows driver needs to be reinstalled.

---

### Post by roger_1960 on 2011-07-22
Hi

Yes, do as jtarin suggests.

Also, perhaps try:

shut down
remove power supply
remove battery for 2 minutes
reinstall battery & reboot.

This sometimes works where hardware is "confused" about what is turned on.....

---

