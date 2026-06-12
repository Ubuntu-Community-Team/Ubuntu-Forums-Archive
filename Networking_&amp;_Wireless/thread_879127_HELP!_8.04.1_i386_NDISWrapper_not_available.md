---
title: "HELP! 8.04.1 i386 NDISWrapper not available"
date: 2008-08-03
forum: Networking &amp; Wireless
---

### Post by Tornota on 2008-08-03
I am at a loss...  ](*,)

I'm trying to get my WMP300N wireless card running and I've been following every tutorial I can find but can never get past step 1, install NDISWrapper.  When I go into Synaptic Package manager to install NDISWrapper, I can't find it doing a search or manually scrolling.  Next I've tried to manually install wrapper that I've downloaded onto my laptop (what I'm using now) and transferred, but I keep getting compile errors using terminal and the Gui installer I found on SourceForge.  The weird thing is that my laptop has NDISWrapper but I never had to install it as my wireless worked from install on the laptop.  I installed 8.04.1 off of the same disk to my laptop as a dual boot just to verify that the disk was functional and working after the issues on my desktop.  My desktop is a clean install on a new hard drive on a home built computer that did run properly off of my secondary hard drive that I use to check out my hardware set up with XP as the Primary OS.

Oh yeah, and I've reinstalled HH after it didn't work the first time, and I'm running an AMD single core.

Please... Any help would be greatly appreciated!

---

### Post by cpetercarter on 2008-08-03
You need to enable the universe and multiverse repositories and install the ndisgtk package - see [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

---

