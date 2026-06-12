---
title: "Loss of connection speed through Firestarter"
date: 2008-02-02
forum: Networking &amp; Wireless
---

### Post by niplfsh on 2008-02-02
Here's the situation:
I have a fairly large network in my house.  3 MB/s DSL line, running through a modem/router/wap combo, which has 3 wired and one wireless connection to it.  Then a Linksys WRT54GL router connected to this and acting as an access point, with 3 more wireless connections to it. 

 The connection in question is my Ubuntu box, recently upgraded to the latest kernel.  It is connected wirelessly to the Linksys router via a Linksys WMP54G PCI card.  It then uses Firestarter to share that connection over ethernet with two other machines in the room.  Now, since I upgraded the kernel I have noticed that after a while, seemingly randomly, my download bandwidth is cut to about 1/3 of its maximum.  Note that it ONLY affects download speed, not upload.  I have run bandwidth tests on several machines (thanks to speedtest.net): machines connected directly to the DSL modem, as well as machines connected to the Linksys wireless router (but not routed through the Ubuntu machine).  So I have eliminated everything but the Ubuntu machine itself as the source of the problem.

This did not happen prior to the kernel upgrade.  The only difference I have noticed is the addition of a "wmaster0" network interface (which according to Firestarter does not receive any data, only sends).  It is fixed by simply restarting the wireless interface, so it's not so much a major problem as an annoyance.  ](*,)

Strange problem but if anyone has any idea what's going on, I'd appreciate any info!
Thanks
JW

---

