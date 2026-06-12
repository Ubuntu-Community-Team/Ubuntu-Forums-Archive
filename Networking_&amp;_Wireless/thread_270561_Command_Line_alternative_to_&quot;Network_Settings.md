---
title: "Command Line alternative to &quot;Network Settings&quot;?"
date: 2006-10-03
forum: Networking &amp; Wireless
---

### Post by scratched on 2006-10-03
I was hoping someone could tell me a command line alternative to the Network Settings and Connection Settings GUI programs so that I can try to write a small shell script to automatically go through the motions I have to do whenever I connect to a network.

The way everything's set up right now, if I want to switch between my wired and wireless home network, I have to open up Network Settings switch my location (which is painfully slow sometimes) and then select the essid of my network, run dhclient from the command line, and then select my wireless card in connection settings. I've reached the point where it really gets on my nerves to have to do this over and over.](*,) 

At school it takes even more time because I have to start up the cisco VPN for my school in addition to doing the above.

---

### Post by merkur2k on 2006-10-03
the following commands should do what you need, in various configurations:
ifconfig, iwconfig, route.

---

