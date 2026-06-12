---
title: "Problem with wifi"
date: 2005-04-24
forum: Networking &amp; Wireless
---

### Post by Minnie000 on 2005-04-24
Trying to get my wireless network up.  Had no problems with eth0...it configured on installation.  Now I'm using ndiswrapper to get my dell truemobile 1350 wireless card up and running.  I have successfully installed ndiswrapper already...the computer knows my card is there, but I can't get a connection to the web.
When I type iwconfig beside the essid it says off/any.  The mode is managed and the channel is set correctly at 6.  I've configured it in both the network settings and manually at the prompt. Encryption is currently off as well.
I'm using a Dell Inspiron 5150.  If I need to add anything else let me know.
Any suggestions?
Thanks!

Minnie

---

### Post by crazybill on 2005-04-24
Make sure your IP settings are correct on both your Ubuntu and your wireless router. Ping to your router to make sure you get a reply. Then ping to the otherside of your router.

For example, if you are using static IP, lets say that your router is 192.168.1.1 with submask 255.255.255.0 and that it is getting its WAN side connection via DHCP. Your box should have similar settings with IP 192.168.1.2 (last digit can b e 2-254) and submasked at 255.255.255.0 and gateway set at 192.168.1.1 

If your computer is finding the router, it sounds like your problem may be the IP settings. Always start with pinging.

---

### Post by Minnie000 on 2005-04-24
Thanks for the help crazybill.  The second I configured my wlan0 to static IP and stuck in the numbers I had a signal...no web,...but I had a signal.  Unfortunately I couldn't leave it like that because when I did my wired connection didn't work either.
What do I try now?

Minnie

---

