---
title: "updated today and now the networking won't work"
date: 2007-12-18
forum: Networking &amp; Wireless
---

### Post by spottyrover on 2007-12-18
I have just tried to install nx from the instructions on the first page ( Installing FreeNX in Ubuntu 7.10 Gutsy )
All went well I thought as I could login to the other pc and all went well
( by the way a good article)
Until I rebooted the pc's and now I can not get them to talk to each other
I can ping the router from both pc's but they will not ping each other.
I installed guarddog and then opened up all of the settings ( including the disable firewall option) but still no change.
I rebooted a number of times and still no go.
Luckily for me I have another ubuntu install and booted into that one and they could talk to each other.

the install is an amd 64x2 3800 which was updated just before I did the nx install

I have since realised that the problem was proberly  due to the update and not the freenx install
So I thought this is the more appropiate forum (incase you noticed it in 2 places)

any help would be appreciated
Dave
__________________

---

### Post by spd106 on 2007-12-19
There was a kernel update recently so check over any drivers that you've modified in the past. For example I had to re-install ndiswrapper, because I build a newer version from source.

You'll need to be specific about what isn't working, such as the information about the network card, whether it was working in a default install, what driver it uses etc. Then we'll take it from there.

---

