---
title: "Share XPs Internet with Ubuntu"
date: 2006-10-19
forum: Networking &amp; Wireless
---

### Post by tbar3 on 2006-10-19
ok, here's the deal: I have a wireless connection that i'm getting from my landlord's business. i have a wireless nic set up on my XP box. i have ubuntu installed on a Mac G3. i want to connect my G3 to my XP box using a crossover cable and share my internet connection. As of right now, i can't even get the 2 machines to see each other at all (still shows the Network cable is unplugged). the way it's set up is:
Wireless router -> Wireless NIC (XP) NIC -(crossover cable)-> G3 NIC

any ideas how to get the two to play nice? please?? :(

---

### Post by tbar3 on 2006-10-20
bump

---

### Post by zytsef on 2006-10-20
In Windows: go to control panel --> network connections/network and internet connections (the former if you're using the classic view; latter if you use the new and 'improved' view. from the new interface you have to do an extra step and click on network connections) --> Right-click the wireless adapter --> Advanced tab. Make sure the 'share this connection with network users' box is checked.  

You may or may not have to set static IPs on both the linux and windows ethernet adapters, I don't really recall how well the windows xp pro dhcp server works with linux

---

