---
title: "I can't share my Internet connection."
date: 2010-01-19
forum: New to Ubuntu
---

### Post by ndrea on 2010-01-19
Hello! I am running Ubuntu v9.10 and need to have my Internet connection shared over the mainly XP windows operated network. I would like the machine running Ubuntu 9.10 to act as my Internet server or simply distribute Internet to the rest of the machines running XP. I have not yet installed a firewall neither coz am not sure how to. I am new to this but it is very urgent because i run an Internet cafe. 
Can i strictly do this using the graphical interface without the command line too? GUI is preferred at the moment as i explore more into the command line interface. I am at the moment reading a Ubuntu pocket guide for more exposure.
Please help.

---

### Post by inobe on 2010-01-19
sure you could, simply right click your connection icon and hit edit connections, choose the tab of the device you wish to use that will connect to your router/ switch, edit it, click ipv4 tab, in the drop down menu' change from dhcp to "shared to other computers.

note: it must be a free ethenet, most newer computers are equipped with two ethernet devices, also with some wireless routers the ethernet cable must be plugged into the lan connection, file sharing will not be possible with this configuration, a reboot is needed.

---

