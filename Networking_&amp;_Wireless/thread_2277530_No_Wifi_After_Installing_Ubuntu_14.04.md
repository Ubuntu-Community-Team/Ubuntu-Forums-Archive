---
title: "No Wifi After Installing Ubuntu 14.04"
date: 2015-05-09
forum: Networking &amp; Wireless
---

### Post by nicholas19 on 2015-05-09
After installing Ubuntu 14.04 I tried to get onto my Wifi. But there is no option to do that. Only ethernet cord. 
I did research and there's supposed to be options in Additional Drivers in Software & Updates. But all it says is 'No additional Drivers Available.'

I've also read in a few places that my Wifi Card might not be turned on? im just not sure what's wrong

I'm on a Lenovo Edge 15.

Any help would be much appreciated.

---

### Post by Pilot6 on 2015-05-09
Please give output of

lspci -knn | grep Net -A2
rfkill list

---

