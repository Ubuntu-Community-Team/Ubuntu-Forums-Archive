---
title: "Network Manager - No Wireless Connection"
date: 2007-03-19
forum: Networking &amp; Wireless
---

### Post by mohit22722 on 2007-03-19
Hi,
    I installed Network Manager.  When i installed it, the manager was showing me my wireless connection and others but after trying to connect to my connection several times.  All the wireless connections disappeared.  So, now it just shows NO NETWORK CONNECTIONS.  But when i click on Firefox, i can go online.  I think it's connected to my wireless connection but it doesn't show all the wireless connections available in my area.

Is there anything i can do to get the manager to display all the wireless connections available??
I tried to reinstall the network manager but still no improvements.

Will strongly appreciate your help,
Mohit

---

### Post by jpeddicord on 2007-03-20
Go to System > Administration > Networking. Find your wireless card, and **uncheck** the box next to it. Close the window. Network Manager should now be able to use your wireless card. (Restart your PC if you need to.)

The reason it need to be unchecked is because only one service can manage the card at a time, to to use Network Manager you needed to shut it off in the system first.

Jacob

---

