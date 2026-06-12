---
title: "Unable to surf web"
date: 2005-07-05
forum: Networking &amp; Wireless
---

### Post by jr0 on 2005-07-05
:)

---

### Post by codejunkie on 2005-07-05
open a terminal and type ```
sudo ifconfig
``` and post the output here also post a little more info like if your on dialup, cable ,dls using a wireless networkcard what kind of network card your using your using a router etc this would help a great deal trying to answer your question.

---

### Post by jr0 on 2005-07-05
;-)

---

### Post by codejunkie on 2005-07-05
if you don't have a router and your pc is just plugged straight into the cable modem that could be the issue it's not renewing the ip when between os reboots i've seen this happen you have to power cycle your cable modem that will fix it which can be aggriavating just to note it's not linux's fault it's the cable modem or your isp not automatically renewing the ip this also happens with dual boot setups like windows 98 and xp the best fix is buy a router this wont happen as often maybe never again and you also have that extra security with the firewall in the router but it can also happen if you do have a router and your isp has some issues with the headend like mine does and i have to set up a static ip between my pc and my router.
but truthfully it could have been caused by a number of things a like your isp having problems so now that it's working i would'nt worry about it too much unless it starts happening often, then try a using router or if you have a router setup a static ip between your pc and the router like manually set the ip to something like 192.168.0.54 for linux and manually set the ip for windows to 192.168.0.55 hope this helps.

---

### Post by jr0 on 2005-07-05
Thanks.

---

