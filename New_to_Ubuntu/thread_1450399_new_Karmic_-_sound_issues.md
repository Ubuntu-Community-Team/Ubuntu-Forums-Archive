---
title: "new Karmic - sound issues"
date: 2010-04-09
forum: New to Ubuntu
---

### Post by stevek123 on 2010-04-09
I finally got my raid settings removed and Karmic installed. I got all the updates installed and a ton of apps I like. I got the nvidia drivers in and running. When I went to configure sound, I found that the onboard sound was recognized but not enabled. After a cpl hours of trying I was unable to get it going.
I am familiar with the Ubuntu Comprehensive Sound Problem Guide (I have to recompile my sound drivers every time I update my bios on my Hardy computer=irritating). When I went there to run through it for my onboard, I saw it was not listed. A Google search showed there was a reported BUG for my onboard chipset and no obvious solution. I tried to enable the entire alsa list to get it going but failed. 
OK - then I installed on old Yamaha YMF pci card identical to the one I use on my Hardy machine. I disabled the onboard in bios and went to configure this card. The alsa site says it is still supported with driver ymfpci... but when I went to compile/install, it is no longer listed in the most current alsa build. 
I've uninstlled and re-installed ubuntu soundbase alsa base and alsa utils without success. 
Now what the heck do I do? I dont have another sound card (actually I do but they have not been supported for a long time...) and no scratch for one. If I dump Karmic and replace with Jaunty, is it possible the older OS will still include my sound card in their build???
I dont know how to use backports properly. Synaptic tells me to install a metapkg that I dont see listed - and if I did I'm still not sure if that would get me the driver I want. HELP?

---

