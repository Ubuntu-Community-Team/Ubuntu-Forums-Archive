---
title: "broadband router hangs when downloading torrent?"
date: 2007-11-05
forum: Networking &amp; Wireless
---

### Post by afeasfaerw23231233 on 2007-11-05
when utorrent starts downloading files, the speed increase gradually to my maximum bandwidth (10Mbps), then after 30 minutes or so, there is a dramatic decrease in speed ''gradually'' from 10Mbps to ~50K and then stop decreasing. if browse the net at this time, ff would say ''cannont be connected''. it seems that my router (dlink 524) is hanged (but it isn't hanged at all). then i need to reboot my router and it returns to normal and then sucks up around 30 min later. if i connect my box directly to the net, it doesn't happen. i want to know if there's any problem of my router (it is newly bought) so that it'd hang up when i use utorrent? but the router seems to work very well under any situation excent downloading torrent (i tried to download a 4.3 G file at my maximum bandwidth without any problem). i search the net and some articles say some routers cannot handle connection with too many ''ports'' open by torrents so it hangs. i have no idea what does it mean and i want to know if there's any solution to evade this problem. any advice will be appreciated (but don't ask me to buy another router). thanks!

---

### Post by sonofusion82 on 2007-11-05
yes, my friends also complained about his dlink router with problems similar to yours. you can probably try reducing the number to connections per torrent and global connection limit. this usually doesn't affect the download speed but will be more selective when choosing peers.
also, he said that disabling the router's firewall could improve the situation, but you will need to shield up your machine.

---

### Post by smurphy_it on 2007-11-05
It means you have to change your "Maximum connections" in your router or change your MTU value.  It would depend upon what firmware you are running on your router "Stock firmware, Open-Wrt, DD-WRT, etc".

---

### Post by afeasfaerw23231233 on 2007-11-05
It means you have to change your "Maximum connections" in your router or change your MTU value. It would depend upon what firmware you are running on your router "Stock firmware, Open-Wrt, DD-WRT, etc". : 
my MTU is 1500. what value should be set?
i cannot find the ''max. connections'' you're referring to.

yes, my friends also complained about his dlink router with problems similar to yours. you can probably try reducing the number to connections per torrent and global connection limit. this usually doesn't affect the download speed but will be more selective when choosing peers.:
my global connection limit is 200 and connections per torrent is 50. what value should i set?

---

