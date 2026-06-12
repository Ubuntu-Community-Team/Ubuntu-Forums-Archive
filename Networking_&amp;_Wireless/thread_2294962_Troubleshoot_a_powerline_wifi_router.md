---
title: "Troubleshoot a powerline wifi router"
date: 2015-09-15
forum: Networking &amp; Wireless
---

### Post by coldraven on 2015-09-15
My local pub has this powerline wifi router [http://www.addon-tech.com/new_/product/html/?99.html](http://www.addon-tech.com/new_/product/html/?99.html)
One unit is connected to the BT Home Hub, the other is in the bar so that us customers can get some wifi. It was working but now on my Android phone I get full signal strength but with an exclamation mark next to it and no internet connection. The guy that installed it has moved away and I'm the next in line to be "computer nerd fixit man" :)
I downloaded the user manual and had browse but a lot of it did not seem to apply to its current use. I don't think we need WAN for example.

The user manual says that you connect to the configuration panel at [http://192.168.99.1/](http://192.168.99.1/)  so could this be a DHCP conflict with the BT hub? If so how do I assign it a fixed IP?
Any tips on troubleshooting this gadget would be welcome plus any info  on BT Home Hubs as I have never had one. (I believe that this is the  newest version)
 For it's portability I plan on using my Xubuntu 14.04 notebook and I don't mind installing and running any CLI tools. TIA

---

### Post by coldraven on 2015-09-30
The problem was that the network connection ports of the BT Home Hub are broken so the powerline adaptor was not getting an internet connection.
Now waiting for a new Hub from BT.

---

