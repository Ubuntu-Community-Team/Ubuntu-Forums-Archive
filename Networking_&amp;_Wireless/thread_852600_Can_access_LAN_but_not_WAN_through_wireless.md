---
title: "Can access LAN but not WAN through wireless"
date: 2008-07-07
forum: Networking &amp; Wireless
---

### Post by Shards_x on 2008-07-07
Hello everyone,

First I have to confess that I'm a Linux newbie and not that great at networking, but I've searched the internet for solutions to my strange internet access problem and found none, so here goes...

I recently installed Ubuntu Hardy on my laptop, and added Firestarter to configure the firewall.  Prior to installing Firestarter, I was able to access the internet via both wired and wireless connections.

After Firestarter was installed, I did not touch the firewall configuration (just enable/disable).  I was connected through wired at this time, and I had access to both my LAN and the internet.

Then I switched to wireless and the problems began.  I had access to my LAN, but no access to WAN.  I can RDP to my Windows PC, I can access its shares, but I could not longer reach any websites with my laptop.  The Windows PC can access the internet just fine, so it is not an ISP or router or cable modem issue.

I tried disabling the firewall in Firestarter, but to no avail. I even removed Firestarter, but that did not help.  Some people suggested that Firestarter might have added rules to the iptables, so I checked with 'iptables -L' and there is nothing, and just in case there was something hidden in there, I flushed it with 'iptables -F', but still my wireless does not allow access to the outside world.

Funny thing is, if I plug my laptop in through a wired connection, then everything works again.  Once I switch back to wireless, WAN access stops.

Does anyone have any ideas on what other things I can try?  Any help will be really appreciated.

---

### Post by The incredible bulk on 2008-07-07
I googled firestart right quick and I found it resides on IPTABLES, it's just a front end you might say.

so here's a link that might help you understand iptables,
I'm not that good with it, but you need more help e-mail me and I'll see if I can help out.

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

Before I send you on that "wild goose hunt" just open a terminal and do a 
sudo iptables -F
and see if you can surf the internet then.

TIB

---

### Post by The incredible bulk on 2008-07-07
I googled firestart right quick and I found it resides on IPTABLES, it's just a front end you might say.

so here's a link that might help you understand iptables,
I'm not that good with it, but you need more help e-mail me and I'll see if I can help out.

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

Before I send you on that "wild goose hunt" just open a terminal and do a 
sudo iptables -F
and see if you can surf the internet then.

TIB

---

