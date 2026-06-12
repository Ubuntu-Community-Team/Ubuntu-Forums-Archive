---
title: "Stuck with Gutsy networking woes"
date: 2007-10-09
forum: Networking &amp; Wireless
---

### Post by caled on 2007-10-09
Hi all

Ok, I'm having an issue connecting my freshly installed copy of gutsy on to the internet.
The connection is wired, firefox can get to the router's homepage (192.168.1.1) and can log on to that, and just to confuse me a bit more, I can ping [www.ubuntuforums.org](www.ubuntuforums.org) and get a response.
But I can not get firefox or pidgin or anything to connect to the internet so I can browse pages.

The network is set to DHCP, the router can see the wired desktop and the desktop is receiving an IP address.

Anyone any ideas? Are there any particular logs which anyone would like to see?

Thanks in advance for any help posted

---

### Post by jnorthr on 2007-10-09
could you please post the content of the command
dmesg

there is a network service called avahi that some people report as causing difficulties. It generates an IP address for networks that do not have DHCP servers to generate the address. If it is running on your system you could try to kill it then do 
[COLOR="Red"]/etc/init.d/networking restart[/COLOR]
just to test

---

### Post by caled on 2007-10-09
Thanks for the quick response.
I've managed to get the desktop computer (running gutsy) on to the wired network, for some reason the internet wouldn't work due to DNS issues, I've set the network tools to use the OpenDNS servers and hey presto, internet! I've seen another thread in another forum that seems to mention that DHCP doesn't seem to work with the brand of router that I have (safecom), although don't know whether this is right or not ?

Another query that I have though is that after a reboot, the network manager reverts back to a default location, which has my router set as the DNS server, is there anyway to have a specific network location set as default, so that the OpenDNS servers are used automatically at start up?

thanks for your help

---

### Post by noob12 on 2007-10-09
For that last question you can use this thread: [http://ubuntuforums.org/showthread.php?t=543659](http://ubuntuforums.org/showthread.php?t=543659)
The first section tells you what to do for your case.

---

### Post by Mal1024 on 2007-10-18
I'm having the same problem, can anyone tell me how to set up OpenDNS in the Network Tools?

---

