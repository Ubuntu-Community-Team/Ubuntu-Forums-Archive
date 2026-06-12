---
title: "wireless networking help"
date: 2004-12-05
forum: Networking &amp; Wireless
---

### Post by paul.hendrick on 2004-12-05
hi all,
i'm new to networking, so i'm not sure what i'm doing right/wrong, but i've been searching around and still cant get my machines to talk to each other. I want an adhoc network between my ubuntu desktop and my fedora laptop(i cant get ubuntu on it).

System one is running ubuntu. I've installed ndiswrapper, and installed the drivers from my driver cd and the wlan0 device is created. 
Then with the networking tool, I add a new wireless device. Set the Essid to local_net, and put a 5 digit key, click next. choose automatic config (dhcp), next step. Apply and activate the connection. After that, the program hangs indefinately(no window redraw), and i have to kill it.
When the network-admin window comes back up, i've got the connection in the list, but i cant activate it. i check the box, but after a couple of seconds, it unchecks itself.
Running network-admin from the command line gives me no output at all.

Any ideas what to do next?
thanks for readin.

---

### Post by tcaptain on 2004-12-07
I have the same problem only my card doesn't need the special drivers (its supported in linux)

I get the same hang, and on either kill-restart or reboot, I can checkmark it and it stays 2 seconds and unchecks.

I checked /etc/...(not sure path)/interfaces and the ESSID and WEP key is correct.
its frustrating...it just doesn't seem to get logged in.

---

