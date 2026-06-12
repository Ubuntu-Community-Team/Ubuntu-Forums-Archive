---
title: "Ad-Hoc network, bridge Ethernet connection?"
date: 2008-01-23
forum: Networking &amp; Wireless
---

### Post by FuturePilot on 2008-01-23
I'm trying to Ad-Hoc two computers together. One has an ethernet connection and I would like to be able to share that connection over the Ad-Hoc network. I've gotten to the point where the two computers can see each other and I can have them ping each other. The problem I'm having is getting them to share the ethernet connection. I can't get out to the internet on the computer with only the wireless. I think what I need to do is bridge the ethernet and the wireless connections together, and I can successfully do that with the bridge-utils package, however once I do that I can't ping the other computer anymore.
This is what I've done
```
sudo brctl addbr br0
sudo brctl addif br0 eth0
sudo brctl addif br0 eth1
```
and then when I bring the bridge up I loose the connection. Is there something I'm not doing right?
Both computers are running Gutsy by the way.

---

