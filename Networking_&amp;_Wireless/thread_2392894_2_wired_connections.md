---
title: "2 wired connections"
date: 2018-05-26
forum: Networking &amp; Wireless
---

### Post by jgw on 2018-05-26
I am running with 18.04

I just checked my network and noticed that I now seem to have 2 wired connections (shown in settings/network)   One is enp1s0 and the other wired connection which is checked.  The other is not.  The strange thing is that they seem to be swapping back and forth.  Sometimes I check and the enp1s0 has its description up and sometimes the other.  I have no idea what is going on but I do know that the network has been acting oddly - sometimes it will work, sometimes not but settings and the thing on the top bar things it is working (but ping does nothing)

At the same time my vpn seems to stop and then I restart.

I also have 2 icons that deal with the network, sound, something with a gear that I have no idea about.  1 icon is the three things and the other looks like a lock on a pedestal.

---

### Post by SeijiSensei on 2018-05-27
You could uncheck the box to start the second adapter on boot in the Network Manager. 

However, do you have both adapters plugged into your router?  If so, disconnect one of them, and your problems will disappear.

There is no performance benefit to having both adapters connected unless you use "[bonding]("https://help.ubuntu.com/community/UbuntuBonding")."  Otherwise having two connections can lead to routing problems and the appearance of disconnects.

---

### Post by jgw on 2018-05-27
thank you for the reply

I have 2 connections wired and the other.  apparently its using the wired and not the other.  I do, however, have three icons on the top bar, next to each other, which do, exactly the same things.  One is the three little connected things, the lock on a pedestal, and the speaker thing.  That is particularly odd.

---

### Post by jgw on 2018-05-27
I think I am going to get rid of the enp1s0 wired connection.  I don't know where it came from or whY so I think I will go with the wired connection 1 instead of the wired connection enp1s0 .  I only have one adaptor, not 2 (sorry, not paying attention).  It gets even better.  I now have 2 enp1s0 connections.  I have unchecked it to boot but that doesn't seem to make any difference as the network keeps on rewarding me with this connection.  I have no idea where it came from or what it means, only that it makes no sense to me.

When I goto settings it sometimes shows one emp1s0 and other times 2.  In the icons, however (I have 3 icons which shows me a sound slider, another semi gear slider (have no idea what that may be but maybe for a microphone that doesn't exist), the wired connection(when clicked it shows two enp1s0, wired connection 1, on/off, and wired settings (takes me to settings/network), the vpn (connected to or not connected toggle), and me (log out and account settings).  I have no idea why I have three icons to tell me this, network, vpn, volume. However, if the wired connection goes off there is 1 icon (the speaker icon), if wired is connected and vpn is not then the vpn icon gets a question mark and  if the network is not connected that icon goes away.  This system of icons tell me, therefore, if the network is connected, and if the network is connected.  If the network and the vpn are not connected then I still have the volume icon to open and re-connect.

The growing number of enp1s0 connections are of concern.  I actually tried to disable but it made no difference and it came back.

Thoughts?

---

### Post by jgw on 2018-06-01
I am going to set this one as solved.  There is a problem but it keeps on changing so I am waiting for it to settle in a bit and then repost on this one.  I, for instance, actually had 4 enp1s0 connections plus one wired connection 1.  I then went to network connections in settings and found that 3 of the onp1s0 connections were at the top of my vpn connections.  A couple of other things also happened so I just re-booted.  now I just have a wired connection and no enp1s0 connections.   All of this seems to be happening automatically so I am going to give it some time, take another look, and just post what is going on instead of messing with it.

---

