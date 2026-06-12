---
title: "Reconfiguring eth0"
date: 2007-11-09
forum: Networking &amp; Wireless
---

### Post by bobthebullet990 on 2007-11-09
Right... I've now calmed down a little from my last post which sorry, but was a bit of a rant and a rave with steam comming outta my ears!

My landlord is developer for the RAF, and when I moved into the house, I wired up the Linux box to the router [eth0 direct connection], I saw that I was getting a strange result in that no webpages could be displayed through my browser [firefox]. I checked the connection by doing a quick connect to an ftp server which worked no problems!

I was in a rush, so changed the root password and user password as he had the day off work, I said if you have a chance, you could have a look [being a developer for 20yrs or, thought he may have an idea]! Turns out... he'd not a clue about Linux and never used it!

This wasn't too much of a problem as work gave me a laptop, which I have been using to access the net, but just now, wanted to see if I could get the Linux box onto the net to do some web development [I have a local webserver running for testing etc.]

However, I turned my machine on, and saw he'd installed galleon web browser [which I'm not familiar with], and he'd said it'd come up with some pages [by this I think he means the default galleon pages being a webpage of some sort locally stored on the machine] - to install this from the package manager, an internet connection must have been alive otherwise the thing woodn't have downloaded!

Right... So now I decide to check the results of ifconfig, and get a result with no IP or broadcast address, i'm thinking wot the hell has he done here? I can't think of what it could be to fix this, but now I can't even reach the local network let alone an ftp location!

How can I reset eth0 [bearing in mind I have no network connection on the machine, so it has all got to be done without any files requiering to be downloaded!


Morale of the story here is never ever ever let anyone touch your Linux box who has never used linux before because that simply spells trouble right from the get-go!

thanks for any pointers!

---

### Post by bobthebullet990 on 2007-11-09
I will copy the results of ifconfig from the linux screen....

```

eth0:
Link encap:Ethernet HWaddr 00:0F:EA:E5:85:18
inet6 addr: fe80::20f:eaff:fee5:8518/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:281 errors:0 dropped:0 overruns:0 frame:0
TX packets:33 errors:0 dropped:0 overruns:0 frame:0
collisions:0 txqueuelen:1000
RX bytes:42990 (41.9KiB) TX bytes:9702 (9.4KiB)
Interrupt:217 Base address:0xa800

```

---

