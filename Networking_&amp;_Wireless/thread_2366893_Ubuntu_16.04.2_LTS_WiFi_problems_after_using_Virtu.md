---
title: "Ubuntu 16.04.2 LTS: WiFi problems after using VirtualBox"
date: 2017-07-23
forum: Networking &amp; Wireless
---

### Post by slowerphoton on 2017-07-23
I've always had problems with the internet connection in Ubuntu (other OS on the same device working fine as well as other devices). Sometimes it got randomly disconnected for no apparent reason and I had to manually reset it to make it work again. It wasn't too often though - happened at most once a day if at all.

However after playing with pfSense in VirtualBox and entering different IP addresses in Chrome it disconnected most of the time when trying to enter IP addresses like 192.168.1.1 - not immediately and I do not claim there is a link between these two things but there might well be. The problem this time was that I was not able to fix it by a manual reset - i.e. uncheck Enable Networking and after a while check it again or deleting the network from the list and then adding it again. The only thing that helps is rebooting the OS.
[URL="https://pastebin.com/raw/mAEHT1yk"]
Here I include the output of lsmod command.[/URL]

I am not too tech-savvy so if you think I should include more info about something, just tell me.

UPDATE: it seems to happen when watching videos on Chrome (something about a lot of data downloaded?). sudo service network-manager restart doesn't work at all. Yes, this seems to be the case: I tried downloading a large file and after 83,8 MB the network went off.

---

