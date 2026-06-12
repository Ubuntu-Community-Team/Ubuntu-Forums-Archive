---
title: "ifconfig command problem with wireless please help"
date: 2017-03-22
forum: Networking &amp; Wireless
---

### Post by liamse22 on 2017-03-22
Hello I am generally new to Linux so this might be a simple question, and please don't rain hell on me if this has been asked somewhere else because i really tried to find this issue.


So i tried to change my mac address and i was able to everything went well and when I tried to connect back to the internet i failed.
First i thought it was because the mac change but I isolated that.

Anytime I use ifconfig wlan0 down and than try to bring it again up with ifconfig wlan0 up I can't connect back to the internet.

My networkcard does menage to connect to my home network (to my AP) but no connection to internet. I tried :
service networking restart
service network-manager restart
I checked if the adapter was in monitor mode and it was not its is menaged mode, the only solution to resolving this issue is restarting my laptop. 


I would be thankful for any help, cheers ;)

---

