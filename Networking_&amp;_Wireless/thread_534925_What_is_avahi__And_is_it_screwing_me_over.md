---
title: "What is avahi?  And is it screwing me over?"
date: 2007-08-25
forum: Networking &amp; Wireless
---

### Post by Icemanyurt on 2007-08-25
I am working on trying to get my desktop, which is running fiesty, to connect to my wi-fi network.

The connection, ssid, and WEP key all work on my laptop just fine, which is on edgy.  This card on my desktop worked just fine under edgy.  

My question is, when I was looking under settings I can across wlan0 and wlan0:avahi.  The wlan has no interface information, while avahi does...

What is going on and why can't I connect?

---

### Post by kevdog on 2007-08-25
avahi is not screwing you over, if the wireless interface is not configured properly it automatically defaults to avahi.

When you upgraded to feisty, you probably upgraded the kernel also, and within this new kernel (a separate set of files) is not contained your wireless driver.  

So what you really need to do at this point is to reinstall your wireless driver.  I would help you however you gave no details about your wireless card.

---

### Post by Icemanyurt on 2007-08-25
Under lspci  it is a realtek semicondiuctor co. Ltd. RTL-8185 IEEE 802.11a/b/g Wireless Lan Controller

---

### Post by kevdog on 2007-08-25
Im not sure how you had it last time, however I would recommend ndiswrapper + win98 driver to set it up.

---

### Post by Icemanyurt on 2007-08-29
Alright, tried ndiswrapper and win98 driver and no luck in the current kernel...

I booted into an older kernel, and it works...

---

### Post by Icemanyurt on 2007-08-31
bump

---

