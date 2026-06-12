---
title: "Broadcom wireless help"
date: 2008-08-28
forum: Networking &amp; Wireless
---

### Post by TheSaxon on 2008-08-28
Hi there.  I'm a relative noob to linux and while I have managed to explore and learn quite a bit, I still don't understand much of the under-pinnings.  

Anyway I have a fresh upgrade to Hardy on this box from a fresh install of Feisty.  I activated the b43-fwcutter package through the Restricted Hardware/Driver Manager, which caused the light on my laptop that indicates Wi-Fi activity to light up, but no connections could be achieved.  I looked around all over the internet to try and find solutions to this problem, but couldn't find any that seemed to work.  Eventually I just did a manual removal of the package with the --purge flag:

sudo apt-get remove b43-fwcutter --purge

and then reinstalled it with:

sudo apt-get install b43-fwcutter.

Upon restart everything worked (albeit at 1Mbps - seen in iwconfig)


Everything was great until today when everything stopped working again - for reasons unknown to me.  I tried manually uninstalling and reinstalling the package again to no avail.

I've read a lot, but can't seem to find a definite solution and I'm too worried about messing up my machine even further to try solutions tailored to other people's slightly differing experiences.

Can someone please tell me what packages I need to get, what commands to use, and what these commands are doing (so that I can learn some linux in the process)

The broadcom device I have is the BCM4311

Thanks a lot.

---

