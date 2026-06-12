---
title: "Easytether for Ubuntu having issues"
date: 2017-09-17
forum: Networking &amp; Wireless
---

### Post by tranquilburrito on 2017-09-17
Hello all! I'm new here and rather new to ubuntu, but I feel like I've got a semi-corporeal grasp on the concepts of the OS.


Anyways, I work in the field a ton and I rely heavily upon my ability to tether. Recently my phone and laptop busted and I've had to resort to another, but unfortunately this phone doesn't have the tethering capability my other did (EasyTether still works on Windows), even though it's on my plan, and my laptop has Ubuntu 16.04. My solution was to resort to an application that would facilitate a network connection regardless, but I'm having issues connecting to the easytether service.

I've gotten the application installed but for some reason, even though it says it is connected, I'm not getting any packet flow and the network manager isn't detecting it. I added in the line of code to the /etc/network/interfaces file that the makers of EasyTether told me to add and the network manager begun detecting a wired network, but even when easytether says it is connected, I still am not getting packet flow. 

From what I've seen online it's apparently because of something with the network manager and dhclient. At this point I've exhausted my options and I haven't a clue as to how to proceed. 

Do you guys have any ideas?

---

