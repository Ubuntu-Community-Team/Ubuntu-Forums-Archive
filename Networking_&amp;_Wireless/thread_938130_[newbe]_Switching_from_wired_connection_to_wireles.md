---
title: "[newbe] Switching from wired connection to wireless"
date: 2008-10-04
forum: Networking &amp; Wireless
---

### Post by Jangalian on 2008-10-04
Hi!
 As the subjects suggest when I switch from a wired connection to a wireless one, ubuntu connects to the AP, wlan0 interface takes the IP from the AP itself as expected, but I'm not able to surf the internet. Pinging the AP revealed that the origin of the connection is not from the wireless interface IP, but from the standard (unplugged) eth0 interface.
To solve the problem I do a 'sudo ifdown eth0', I've tried to set different profiles with no result...
What I'm doing wrong? 
Thanks in advance!

---

