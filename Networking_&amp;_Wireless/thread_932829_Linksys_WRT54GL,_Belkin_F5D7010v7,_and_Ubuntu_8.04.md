---
title: "Linksys WRT54GL, Belkin F5D7010v7, and Ubuntu 8.04"
date: 2008-09-28
forum: Networking &amp; Wireless
---

### Post by DavidWilliams on 2008-09-28
So I'm new to Ubuntu, Installed it several days ago.

I'm trying to get the Belkin F5D7010v7 on Ubuntu 8.04 to connect to my Linksys WRT54GL which is running WPA Personal security with the TKIP algorithm.

I followed the steps [here]("http://ubuntuforums.org/showthread.php?t=820646&highlight=f5d7010") and the network shows up and I entered all my information correctly, however I can't connect to the internet but I can see other computers on the network.

Any advice and please, I'm like a total newb so try and dumb it down for me...

David

---

### Post by kevdog on 2008-09-28
Sounds like either a gateway problem or a name resolution problem (dns problem).  What does ifconfig show?

---

### Post by DavidWilliams on 2008-09-29
I don't know what to look for so here...

---

### Post by kevdog on 2008-09-29
Are you sure in that link you posted you have an IP address?  When I see avahi listed, its usually not good.  What I would do for now is to run the router with no wireless security to see if everything is up and running first.  Then add the security back in later.  Stick with DHCP right now (no static IP addresses).

---

### Post by DavidWilliams on 2008-09-29
I have no problem connection with this computer. Its running Vista and using the same settings as Ubuntu...

So its not the router... Unless there is something wrong with it but I doubt that...

*** Update ***

So somehow yesterday when I plugged into my router to download ndisgtk, ndiswrapper-common, ndiswrapper-utils-1.9, it registered on the router with the wired connection's mac address.

I cleared the DHCP list on the router and it worked fine...

When I restarted my computer, the wireless internet wouldn't work again...

David

---

### Post by praelster on 2009-09-14
I have the same card and i found drivers only for Belkin F5D7010v7 its working fine with windows XP here is the link [http://www.belkin.com/uk/support/article/?lid=enu&pid=F5D7010uk&aid=6129&scid=0](http://www.belkin.com/uk/support/article/?lid=enu&pid=F5D7010uk&aid=6129&scid=0)

---

