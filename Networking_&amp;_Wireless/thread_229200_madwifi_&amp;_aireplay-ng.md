---
title: "madwifi &amp; aireplay-ng"
date: 2006-08-04
forum: Networking &amp; Wireless
---

### Post by wildseven on 2006-08-04
hello, i recently bought a wg511t and it's great, worked right out of the box literally. Well, I read on the aircrack-ng main website that for aireplay-ng to work with the atheros chipset, we need a driver update, but i tried ARP injections and it seemed to work very well. Do i still need to update drivers or am i set? What exactly is madwifi, i read it but i am still a little confused.

---

### Post by stormblue on 2006-08-04
You shouldn't fix what isn't broken.

Madwifi is a driver.

---

### Post by wildseven on 2006-08-04
haha ok, thanks, my tech teacher in 7th grade used to say that heh~

---

### Post by spd106 on 2006-08-04
Madwifi is the open source driver created for atheros chipsets. Have a look over at madwifi.org.
The madwifi-ng driver is very cool, being able to create virtual access points and stations. You can capture packets on a VAP set to monitor mode while sending/receiving on another VAP in station mode. I've not tried out the AP mode yet. Should be fun.

I'm not sure if the devs will be including the -ng driver in edgy, IMHO they should.

If anyone's had Network Manager working on madwifi-ng please let me know.

---

### Post by mcclen on 2006-08-07
I found the following which seems to work for me:

[http://www.excentral.org/archives/2006/08/03/dapper-and-madwifi/](http://www.excentral.org/archives/2006/08/03/dapper-and-madwifi/)

I have an IBM X40 with Dapper 6.06 LTS (2.6.15-26-686 #1 SMP PREEMPT), atheros 5212 (b/g). Was previously frustrated and couldn't get any stable connection. The linux2go site added new wpa* and nm-* plus I installed their madwifi-ng-default per the above link. I've been connected for 15 minutes - wow!

BTW - I cleaned out /etc/network/interfaces along the way save for the loopback interface, having eth0 and ath0 in it seemed to conflict with nm-*.

Chris

---

### Post by mcclen on 2006-08-07
Hold the phone - I'm back to a wired connection. The referenced solution held on for about 30 minutes and then went flako. Oh well ..., what did the pundit say - you don't get what you don't pay for ...

---

