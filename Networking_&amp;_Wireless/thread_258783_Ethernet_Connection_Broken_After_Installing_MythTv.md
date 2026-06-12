---
title: "Ethernet Connection Broken After Installing MythTv and its Deps"
date: 2006-09-16
forum: Networking &amp; Wireless
---

### Post by CharlieM on 2006-09-16
I installed MythTv 0.2 from source Tars after removing an old install from apt-get.

The install appeared to go well, after eventually tracking down all the dependancys it needed. After a little bit of setting up I need to reboot (can't remember why) since then my wierd ethernet network has completly stopped working.

I have checked dmesg, which shows the card to be detected and the link to be detected. If I run ifconfig I get the normal eth0 entry.

If I run /etc/init.d/networking force-reload, fails to recive a DHCP reconce. Looking closer it never manages to send the requst either. It simply shows "send_packet: Network is unreachable" twice. 

Can anyone suggest what to try next. The network it is attached to is functioning normally. So I guess it must have been something that got changed when I was installing MythTv's deps. 

Any help would be greatly appreaciated, this has beaten my modest linux talents.

Charlie

---

### Post by CharlieM on 2006-09-16
I have just found and have since been following the Wierd Networking trouble shooting guide. [http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643)

All is good up to the Testing the local link section. The first thing to try recommands typing  ifconfig eth0. This shows lots of info. Data has been sent & recived and there is no droped packets. It aslo shows an IPv6 address but on IPv4 address.

Is it possible that IPv4 has somehow got disabled or corrupt. Does anyone know how to tell if its enabled, or test its working? Its not really something people usually disable but theres probably away.

Charlie

---

### Post by CharlieM on 2006-09-16
I have been doing a little more diging. Firstly IPv4 appears to all be intact. 

I tried assigning a static IP and it worked. I can't understand why its suddenly losing the DHCP traffic to and from the router. I entered the router in as the gateway saticly and that worked fine. So there is definatlly comunication between the two.

I guess I can leave it static. Although it does seem a little odd. Most importantly I can now continue setting up MythTv.

Charlie

---

