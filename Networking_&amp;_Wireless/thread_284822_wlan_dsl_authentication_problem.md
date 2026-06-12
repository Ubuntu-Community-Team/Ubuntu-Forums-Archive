---
title: "wlan dsl authentication problem"
date: 2006-10-26
forum: Networking &amp; Wireless
---

### Post by whizbaby on 2006-10-26
**Problem:** I installed ubuntu 6.06 to my brother's computer which has following network setup

(rt2500 Wlan)......(access point)_____(sphairon turbolink iad crippled router)________|(jack-in-a-wall)

the main problem is that the router belongs to the ISP, the IP and username/password of the router cannot be obtained legally, so no letting the router handle pppoe (ISP says we have to buy the crap if we change settings on router). The access point is only what its name says, no more functionality here. I managed to setup the wireless with iwconfig (first time I have to use wireless though I'm no linux noob), but now I have to login to the ISP some way so I get an IP and have dsl. Is there a way to do pppoe over wlan (windoze does it, that means that when booting w$ndows there's no problem giving username and pass for the ISP over above structure, but I want to swipe the dozer) or is there any other tool I should use for that? 
(dhclient keeps dhcprequest-ing (no wonder if not authenticated))
Allthough I know it's not built for that I tried pppoeconf, pon dsl-provider then fails with *unknown option: nic-ra0* (/dev/ra0 is the wireless card), a line just added to /etc/ppp/peers/dsl-provider by pppoeconf (didn't expect this to work). What can I do? I just cant find any useful information on the net, that's why posting here.

---

### Post by whizbaby on 2006-10-26
O.k. so I got a percussion drill and made a hole in the wall to try it with a 15 meters LAN cable (otherwise it would be 25 or more).

(Ethernet card)______(crippled router)______|(jack-in-a-wall)

Now when *sudo pppoeconf* has finished and I do *pon dsl-provider* I get the error:
...**unknown option nic-eth0**

nic-eth0 is a line pppoeconf added in /etc/ppp/peers/dsl-provider 
.
.
.
rp-pppoeconf (or similar)
nic-eth0
username#####
.
.

(this is NOT copy-pasted)

Any idea?

EDIT:
Oh, and sure I set the card up with ifconfig without errors...

---

### Post by whizbaby on 2006-10-27
O.k. here's the cure (though I don't know the cause yet) for the wlan problem:
getting raling-conf_some_version_number.deb to configure the device AND installing freshly released edgy eft did it. In rutilt (the raling conf utility) I setup the connection and then did pppoeconf.
(only for those who are interested)

---

