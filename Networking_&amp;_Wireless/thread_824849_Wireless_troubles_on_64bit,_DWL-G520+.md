---
title: "Wireless troubles on 64bit, DWL-G520+"
date: 2008-06-10
forum: Networking &amp; Wireless
---

### Post by Warpedflash on 2008-06-10
Ok so today i upgraded my desktop to have the following spec
mobo: Asus P5K
ram: 3 gig
cpu: intel core 2 quad @ 2.4GHz
graphics: nvidea geforce 7900GS
wireless: DWL-520+ PCI Adapter

before the upgrade my computer was a standard dell dimension (so not rely an upgrade im just to cheap to buy new graphics/wireless card/ram etc as well) and ran Ubuntu rely rather well using the standard wireless drivers.

Now of course i did a fresh install of ubuntu and while using the live cd i was able to select what network i wanted to connect to in the drop down in the top right but not to connect (could not get the network key or something), i have this problem on my laptop which i solve by running the following script on startup
```
ifconfig wlan0 down
dhclient -r wlan0
ifconfig wlan0 up
iwconfig wlan0 essid "*network name*"
iwconfig wlan0 key *key*
iwconfig wlan0 mode Managed
dhclient wlan0
```
so i figured that this would not be a problem.

When i install ubuntu everything went smoothly as far as i could see no errors, standard install with /, /home and /opt each having their own partitions.
Now after the installation there are no networks listed in the dropdown and my little script does nothing...
If i go to network tools and select Wireless Interface (wlan0) from the list all the hardware information is not available...

Does anyone have any ideas on how to solve this? i thought it might be a hardware problem but it was detected and worked on live cd...

Edit: Im on 64 bit

---

