---
title: "wired highspeed ethernet connection problem"
date: 2008-07-15
forum: Networking &amp; Wireless
---

### Post by sendjy on 2008-07-15
I just installed the latest version of Ubuntu, harding, yesterday. I have been trying ever since to get the internet connected.

  I used a wired highspeed ethernet for Internet. It's the most common type of high-speed internet you get if you get high speed internet in Toronto or anywhere (I don't know the technical name for it). 

  In the network manager, it showed 3 ethernets and 1 PPoe. I'm pretty sure that eth2 should be the right one. I did not enable roaming and I set it to DHCP. All three ethernets are checked off. The computer won't let me check off the PPoe, but it doesn't matter.

  In the network tools, If I select eth2 as the network device, the data on the bottom shows that it is receiving packages (it has received 7000" , but the link speed is described as "unavailable". When I click on "configure", I was told that "the interface does not exist"..

  Also, when I tried the ping thing in network tools, it showed that no package is received.

  The thing is, isn't wired ethernet supposed to work automaticly?

   Help a beginner out?

---

### Post by NilsE on 2008-07-15
Have you tried it with DHCP and roaming turned on for all interfaces?  Try that and restart the network or reboot.  If you do not get an IP try the following in a terminal and report the results.

sudo dhclient

---

