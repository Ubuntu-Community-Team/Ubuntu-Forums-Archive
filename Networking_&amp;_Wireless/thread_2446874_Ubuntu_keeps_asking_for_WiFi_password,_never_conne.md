---
title: "Ubuntu keeps asking for WiFi password, never connects"
date: 2020-07-08
forum: Networking &amp; Wireless
---

### Post by sunblox on 2020-07-08
Laptop is an HP Elitebook 840 G5, Ubuntu 20.04.

So far this has never been a problem, but I recently switched router and now I keep getting asked for the wifi password whenever I want to connect to it. Upon entering the correct password and waiting a couple of minutes, the prompt for the wifi password comes up again and again and again, without ever establishing a connection. On all other devices (Phones and a Windows PC) in the house it works fine. 

So far my findings on the internet tell me that it might be a problem with the 802.11 settings of the router being incompatible with the ones on my computer, but I'm not sure. Here's what I get from sudo lshw -C network:

*-network
       description: Wireless interface
       product: Wireless 8265 / 8275
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlp1s0
       version: 78
       serial: 50:76:af:3b:99:bc
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=5.4.0-40-lowlatency firmware=36.77d01142.0 latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:158 memory:b6200000-b6201fff


My routers advanced wifi settings: Channel selected automatically, 802.11 mode is 802.11b/g/n, AP isolation off, Bandwidth selected automatically


Could it be that the 802.11 of my laptop is incompatible with the 802.11b/g/n of the router? If yes, how do I change it?

---

### Post by ajgreeny on 2020-07-08
You don't  mention which security settings you have on the router; WEP, WPA, WPA2?

Let us know that, as it should be WPA2, assuming it's  available.

---

### Post by sunblox on 2020-07-08
WPA & WPA2 Personal

---

### Post by sunblox on 2020-07-09
The security of the router is not the problem, I tried connecting through WPS and it didn't work, I also briefly disabled the password altogether and got a connection error. I don't think it's an issue that can even be fixed within the router's settings. Maybe the iwlwifi driver just isn't compatible with this particular router? But I honestly have a hard time imagining that.
t

---

### Post by Autodave on 2020-07-09
I have run into this twice on HP laptops.  Try this:  Open up a word or text file and type your password into the file.  When prompted for your password, copy it from the file and paste it into the box.

---

### Post by sunblox on 2020-07-09
Didn't work, it's probably not actually a problem with authentication since I still can't connect even if I disable the password for the router.

---

### Post by T6&amp;sfpER35% on 2020-07-09
look at [this](https://easylinuxtipsproject.blogspot.com/p/internet.html)

---

### Post by sunblox on 2020-07-10
Thank you for the suggestions, but even after following all of the steps of that link (including the newest of the new drivers, power management off and setting the channels and bandwidth on my router), there's still no effect.

---

