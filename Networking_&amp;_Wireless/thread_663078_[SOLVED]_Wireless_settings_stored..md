---
title: "[SOLVED] Wireless settings stored."
date: 2008-01-09
forum: Networking &amp; Wireless
---

### Post by HighFrictionZone on 2008-01-09
Right, so. I've searched the forums and google, and haven't yet found anything. Where does Kubuntu store its network configuration settings? I ask this because KNetworkManager works and lets me connect to my wireless network when I'm running from the 7.10 livecd, but when I installed it to hard drive, it stopped even detecting the wireless networks in my area - though, oddly enough, it still recognized that I had a wireless card and even let me configure it.:confused: So I figure that perhaps I could copy the working settings from when I configure it in the LiveCD to the hard drive. I'd kinda like to get wireless working on my machine as it's a pain in the butt to run a really long cable to the router.:)

---

### Post by HighFrictionZone on 2008-01-09
Right. So, on a whim, I went and commented out all the stuff in /etc/network/interfaces that were even remotely related to my wireless card, and then I opened up KNetworkManager, and BAM! It recognized the nearby wireless networks and I connected to mine and it was working! I guess sometimes, less IS more!:grin:

---

