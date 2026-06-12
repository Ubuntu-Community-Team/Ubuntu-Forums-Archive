---
title: "Multiple Nics, Wireless, and DHCP"
date: 2008-01-31
forum: Networking &amp; Wireless
---

### Post by abuthemagician on 2008-01-31
Ok, so i looked at other threads and couldn't find what i wanted to know so here it goes. 

I have three nics in my system that are setup as follows:

eth0 is on a 192.168.25.0 lan
eth1 is on a 10.150.2.0 lan and has my internet connection
wlan0 is used when i am not at home

All nics use DHCP for their addresses.

My problem is that I am running Vista inside of VirtualBox, and need it to have access to all three networks. When i am at my desk i want all 0.0.0.0 traffic routed through eth1 with the 192.168.25.0 traffic going through eth0, unless i am on wireless.

How would i go about solving this? I don't mind vista having a natted IP as i don't need to get to it directly. (its only running office 2k7 and other windows apps i can't live without at work) I don't mind running scripts when i switch between wireless and my desktop if someone could write them for me. I am a complete noob in linux but have many years of windows administration under my belt.

---

