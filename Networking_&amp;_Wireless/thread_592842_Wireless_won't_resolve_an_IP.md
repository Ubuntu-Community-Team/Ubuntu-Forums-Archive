---
title: "Wireless won't resolve an IP"
date: 2007-10-26
forum: Networking &amp; Wireless
---

### Post by afderrick on 2007-10-26
I am brand new to linux, trying it out again from the last time I used it about 4 years ago in the Suse flavor.  My wireless USB card is working fine and I can get it to bring up networks.  If I turn off all security on my router (I use WPA encryption and MAC address filtering but I did not turn off that one) it will allow me to connect to my router.  It shows a steady connection rate of about 80% which is about right.

The problem I am having is when it tells me I am connected to my router it will not receive an IP through DHCP and I am unable to ping the router.  I have gone into terminal and done some DHCP searches to try and help resolve the IP but I still get nothing.  I have looked all over and not found anyone else with this same problem.  I have also tried to static route the IP and network when I do that I am unable to connect to the router at all.

Should I try turning off the MAC address filtering?  That is something done at the physical layer and shouldn't affect the OS.

---

### Post by scrooge_74 on 2007-10-26
The MAC filtering is done in your router so if you add your card to the router list you should not have any problems.

Try adding the router from the terminal

sudo iwconfig eth1 (or your card id by system) essid name_or_lan
sudo dhclient eth1 or sudo ifup eth1

Did you have wap supplicant installed?

---

### Post by afderrick on 2007-10-26
I do not have any wpa supplicants installed yet, I will try that as soon as I get a chance though and let you know how it went.  I was just wanting to get the internet out then I saw some tutorials on how to get WPA working correctly on Ubuntu.

---

### Post by afderrick on 2007-10-26
Craziest thing just happened, I turned everything on and it worked without a problem connecting with WPA on.  It is barely creeping along and for a second I could ping my router and got google to come up but it is very slow to respond.  Ant suggestions where to go from here?

---

