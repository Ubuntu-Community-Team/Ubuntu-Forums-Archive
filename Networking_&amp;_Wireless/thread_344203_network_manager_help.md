---
title: "network manager help"
date: 2007-01-22
forum: Networking &amp; Wireless
---

### Post by mmc on 2007-01-22
howdy all, quick question - i have network-manager installed (as per here -> [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)) and working hunky-dory except for two little things things

[LIST]
every time edgy boots it tries to connect to a neighboring wireless network not my own & i have to manually intercept & tell it to connect to my wireless network - how do i set the default connection?
[/LIST]
[LIST]
when using network-manager it needs to have the interfaces de-configured in /etc/network/interfaces ... this is where i used to bring in my iptables rules when my interfaces came up - where can i call iptables now (can i call it when loopback comes up)? 
[/LIST]

any punt in the right direction would be much appreciated.

ta
mmc

---

### Post by scrooge_74 on 2007-01-22
I just read another thread with the same issue, and it said this helped

[http://forums.debian.net/viewtopic.php?p=43551&sid=1348b9998746d42ce64f2fc05069c174](http://forums.debian.net/viewtopic.php?p=43551&sid=1348b9998746d42ce64f2fc05069c174)

---

### Post by mmc on 2007-01-22
thanks! that did the trick for the preferred network.

if anyone has any suggestions on how to invoke iptables with the interface that would be appreciated!

ta
mmc.

---

### Post by scrooge_74 on 2007-01-22
noop I rather use firestarter, iptables config from the command line is just to much for me at this time

---

