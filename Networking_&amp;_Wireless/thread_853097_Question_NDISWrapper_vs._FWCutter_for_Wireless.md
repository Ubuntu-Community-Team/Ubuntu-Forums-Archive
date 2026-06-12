---
title: "Question: NDISWrapper vs. FWCutter for Wireless"
date: 2008-07-08
forum: Networking &amp; Wireless
---

### Post by edwardLS on 2008-07-08
Is there a strong opinion in the community of wireless experts about which method is preferable for setting up wireless networks using the Broadcom 4306 adapter?  
I have had Feisty working with FWCutter, and Hardy working with NDISWrapper.  As happy as I was to have wireless, I had some minor problems with each in terms of dropped connections and sometimes unable to make the connection.

System: Dell Inspiron 9100 with a Broadcom 4306 rev 3.

---

### Post by r4wMUnt34q on 2008-07-08
I dont know an answer to your question, but may I ask you how you fixed the droping and inability to connect problems?

---

### Post by Ayuthia on 2008-07-08
I don't really know if one is really better than another.  It all depends on the card.  For me, I have a 4311 Rev 01 card that works well with the b43 module and the ndiswrapper module.  However, it is not as happy with the bcm43xx (the depreciated module).  I use the b43 module most of the time but sometimes I will switch to ndiswrapper when I can't quite grab the signal (due to interference in the air).

I also have a 4306 rev 03 card and it works fine with the b43 driver.  I am sure that I have used ndiswrapper on it also and had no problems.  When I have more time, I am going to test them with encryption to see how the three modules fare out.

The best way to see is to try it for yourself.  However, if you are happy with what you have, there really is no need.    If you want to play around with things like aircrack, then you would need to use the b43 drivers.  Some people like ndiswrapper because it uses the Windows driver and they feel that it connects better.  I have not seen a real difference with the 4306 rev 03 card though.

---

### Post by edwardLS on 2008-07-08
For r4wMUnt34q:

I only solved the problem with Hardy using ndiswrapper.  Gleaning some information from:

[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

I set out to solve the problem for all my wireless uses.  I use it at work with WEP/DHCP, at home with Open/Static IP, and on the road with Open/DHCP.  I wrote some shell scripts which basically turn the wireless network off, and then manually re-configures it based upon which script I run and turn the network back on.  So far, I have been using the scripts about 3 weeks, this has not failed to get my wireless back up and useable.  I am not sure this is the "guru-approved" method since I certainly am not a guru, but I also am not afraid to play around with things.  Hope this helps.

---

