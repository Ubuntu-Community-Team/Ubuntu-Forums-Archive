---
title: "Mac Address keeps changing"
date: 2008-09-18
forum: Networking &amp; Wireless
---

### Post by redroast on 2008-09-18
Hi Everyone,

First I've been using Ubuntu for 2 years and this is the most frustrating issue I have ever dealt with. 

So the Mac Address keeps changing everytime I boot up. I have a HP Pavilion 9000 AMDx2 64bit running Hardy with an NVIDA Ethernet card. This is an issue since I use a network that requires me to have a  registered hardware address. 

So I searched for this problem and found these links
 
[http://ubuntuforums.org/showthread.php?t=619483](http://ubuntuforums.org/showthread.php?t=619483) 

[http://www.nvnews.net/vbulletin/showthread.php?t=79306&page=2](http://www.nvnews.net/vbulletin/showthread.php?t=79306&page=2)

[http://ubuntuforums.org/showthread.php?t=745293](http://ubuntuforums.org/showthread.php?t=745293)

So it looks as if the forcedeth driver is misreporting the hardware address. This seems to be causing the ethX to go up by 1 on each boot up. The wireless seems to work fine, but I dont have wireless at work.

I have done every combination of changing the /etc/network/interfaces or /etc/udev/rules.d/70-persistent-net.rules but I still can seem to get the hardware address not to change. 

Although, this may seem obvious the only thing I havent done is put in the actual hardware address per the above links. This is because I dont know how to find it. If type ifconfig, the HWaddress for eth0 changes every bootup. I've looked in /var/log for something, but I cant find anything. 

I dont seem to get the error messages that is reported in the above links, whereby upon booting it says "Invalid Mac address detected: af:52:de:7d:1d:00 switching to a random mac"

Anyway, this has started up about 3 weeks ago. It worked fine on Hardy, Gutsy and Fiesty in the past. This is the part that is annoying me the most...I have no idea why it just stopped working. 

Any help would be greatly appreciated

---

### Post by ModelM on 2008-09-19
Have a look at [ _this thread](http://ubuntuforums.org/showthread.php?t=702116)_.

---

