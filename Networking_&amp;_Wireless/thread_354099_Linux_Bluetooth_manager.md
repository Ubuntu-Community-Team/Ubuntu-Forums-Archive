---
title: "Linux Bluetooth manager?"
date: 2007-02-05
forum: Networking &amp; Wireless
---

### Post by SnowPunk98 on 2007-02-05
I'm a Windows guy so I don't know much and am still learning so please forgive me. I would like to get Bluetooth working on my Dell E1705 laptop so I can sync contacts with my phone. 

If you could also suggest what I could use to sync my contacts from my Samsung T619 that would be great.

---

### Post by SnowPunk98 on 2007-02-12
bump

---

### Post by SnowPunk98 on 2007-02-13
bump

---

### Post by SnowPunk98 on 2007-02-22
Anything good?

---

### Post by SnowPunk98 on 2007-03-12
Last bump

---

### Post by GabrielDunn on 2007-09-05
Hey, Sorry you haven't gotten any responses.  I have the same issue, same laptop.  My bluetooth light isn't lit, and I have tried using the synaptic package manager to find something.  And I have installed a few apps, but no luck.  How would I know if my bluetooth was even on beside the light?

---

### Post by Siph0n on 2007-09-05
if your phone has bluetooth, and its discoverable (my phone only stays discoverable for 3minutes after i make it discoverable), try typing:

hcitool scan

This is what I do to check if mine is working :)

---

### Post by GabrielDunn on 2007-09-05
root@gabriel-laptop:/home/gabriel# hcitool scan
Device is not available: No such device
root@gabriel-laptop:/home/gabriel# 


is the output I get with that..does that mean my bluetooth isnt working or there is no discoverable device?  Im so new to bluetooth.  I apologize.  I am taking a linux class, but it's all about admin and not fixing these bugs.  It took me ages to get ndiswrapper to work for my wireless.

---

### Post by Siph0n on 2007-09-05
Im actually really new to, with linux and bluetooth, but yea I think that means your bluetooth isnt working. If it was working and didnt find anything it would still tell you its Scanning, and than bring you back to the prompt after it found or didn't find something

---

### Post by d_taslim on 2007-09-06
Gabriel, what laptop do you have ?

Try to type **sudo lshw** and see if you got your bluetooth listed there. I got something like this:

description: Bluetooth wireless interface
physical id: 2
bus info: usb@5:2
version: 24.22
capabilities: bluetooth usb-2.00
configuration: driver=hci_usb maxpower=0mA speed=12.0MB/s

This is on a Dell Inspiron 6400/E1505, with the assumption that if you have a hardware key to enable/disable Bluetooth, you set it to on already (if its set to off, it won't be listed)

---

