---
title: "Cannot Connect to Wireless using Ralink rt73 chipset in Gutsy"
date: 2008-04-02
forum: Networking &amp; Wireless
---

### Post by Scorpion1031 on 2008-04-02
So here is my issue:
I am very new to Linux (Ubuntu 7.10 is the only flavor I have ever used).  I have installed the rt73 drivers from the Ralink website and have been using Rutilt to try to connect to my home network (WPA TPIK).  I can see all the networks around my house and can use airomon-ng fine.  

When I try to connect to my wireless network I keep connecting then disconnecting.  It does not connect long enough for my router to issue an IP so I can't use Firefox or Synaptec Manager or basically anything that needs a live internet connection.  I have tried wicd and wifi radar, but I have the same problem.  

If I connect to the router directly using a ethernet cable I am fine and everything works.  

Any ideas on where I should go from here to solve this issue?  

Thanks.

---

### Post by Gaute65 on 2008-04-02
I had the same problem in Hardy. 

The solution was to set the router from channel 12 to channel 6. 

Then it works.

---

### Post by Scorpion1031 on 2008-04-03
My router is on channel 6 though.

---

