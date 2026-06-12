---
title: "[Solved] Wifi connection finicky under ubuntu 16.04 only connects every other time."
date: 2016-06-13
forum: Networking &amp; Wireless
---

### Post by Karl_Hungus on 2016-06-13
Yeah, I am having issues with a consistent Wifi connection under Ubuntu 16.04

I ran many distributions based off 14.04 and 14.04 as well and never ran into this issue. 

Sometimes it boots and Wifi comes on perfectly, sometimes it boots with all networking and Wifi disabled.

No idea why so far I have tried toggling networking and wifi on and off and that is the extent of my troubleshooting.


Kinda a semi experienced Noob at a loss.


Thanks in advance,

---

### Post by Karl_Hungus on 2016-06-15
Problem persists even after a number of updates.

---

### Post by jeremy31 on 2016-06-15
*Thread moved to **Networking & Wireless**.*

You can start by checking out the wireless script link in my signature and post the results using code tags

---

### Post by Karl_Hungus on 2016-06-16
The problem persists and sometimes the wifi thinks its a Lan network occasionally wifi but still works.

When I run iwconfig I get under these circumstances I get the following: 


lo        no wireless extensions.

enp3s0    no wireless extensions.


I feel funny running somebodies random script and then publicly posting the output.
Nothing personal but Ill try and debug this another way. I realize the code is on github so I feel pretty safe about that but I don't want to post the output if it can be traced back to this machine.

---

### Post by jeremy31 on 2016-06-17
Since it sometimes sees wifi as Ethernet you may have to
```
systemctl restart NetworkManager.service
```
when it happens

---

### Post by Karl_Hungus on 2016-06-20
Thank you I will give this a shot and report back.

yeah, sudo service network-manager restart has no use in 16.04



systemctl restart NetworkManager.service    -Great solution to reset connection quickly, This quickly reset my connection and problem was resolved.

Thank you Jeremy31 for the tip!




(networking issue seems to have worked its kinks out for now)

Thanks to Debian and Ubuntu team for updates on software.

---

