---
title: "Wireless connection stalls/freezes, ath9k driver"
date: 2008-11-05
forum: Networking &amp; Wireless
---

### Post by nabahr on 2008-11-05
The problem that I am having is my wireless connection will freeze up when in heavy use. 

I have a wireless-n setup with a DWA-556 card and the DIR-655 wireless router. I am using ubuntu 8.10 with the ath9k driver in the kernel. 

It appears that the connection will hold fine when not in use and it will hold fine under normal web browsing, but when I try to stream video or to copy files across the network, it will freeze and the entire connection will be gone until I reset it. The router and computer still register the connection but there is no connectivity. I tried a different card that is 802.11g and it works just fine so I tried the DWA-556 card at 802.11g and it still had the same problems. It seems like to me that it is a problem in the driver but I thought I would see if any one on here had any similar problems or possible fixes.

Thanks in advance!

---

### Post by pheckel on 2008-11-06
nabahr,

Same problem here.  I've only just begun to investigate/research/troubleshoot.  I was elated when I found out Intrepid would have the .27 kernel because of ath9k.  I am pleased the connection is mostly usable for normal browsing...this is a major improvement for me over madwifi and ndiswrapper with the dlink dwa-552 on Hardy.  That config just irritated the crap out of me.  Hopefully someone has some helpful info or the issue will be resolved in a later release.

---

### Post by nabahr on 2008-11-07
Yes, I was quite happy to find out that the card would be supported out of the box but, like anything brand new, there are still some problems. I have been unable to find any sort of solution yet, infact, I found the problem to be even worse. Last night I had the connection freeze while downloading updates and also while watching videos on youtube. Since this is in my mythtv box I ended up having to pull the card until I can find a solution.

---

### Post by pheckel on 2008-11-10
Hey nabahr,

I surfed around for some potential fixes/workarounds today.  Someone recommended switching from using the default network manager in gnome to using WICD, a different network management client.  Perhaps you are familiar.  I tried it out and the stalling/freezing problem appears to disappear.  Not exactly sure why, but it seems to work for me.  Hope this helps.

Download the .deb from [here]("http://sourceforge.net/project/showfiles.php?group_id=194573&package_id=229460&release_id=629280").  Uninstall network manager (you will become disconnected).  Install WICD from the .deb.  Configure it for your router/access point.

---

### Post by nabahr on 2008-11-10
Thanks,
I will give that a try tomorrow and post back with the results. Hopefully that will fix the problem.

---

### Post by pheckel on 2008-11-10
FWIW, I never had any connectivity problems with heavy streaming or massive file transfers on my LAN.  I only experienced trouble when transferring mucho data to/from the public Internet.  Youtube videos, etc appear to be working fine now.  Best of luck!

---

### Post by nabahr on 2008-11-11
Well, I got WICD installed and I really like it. Unfortunately though it only solved 90% of the problem for me. I can stream video online, download, and stream mp3's over the network but it still stalled up when trying to copy a large video over the network. My apartment here has a hideous amount of interference, I wonder if that is causing the problem. I discounted that earlier because my little usb adapter works just fine but I have noticed that my usb adapter picks up a stronger signal from my router.

---

### Post by gmatt on 2009-03-09
Please confirm me what your system RAM is. Is it more than 4gb? I suspect more than 4gb of ram is the issue.

---

### Post by nabahr on 2009-03-09
No, I still haven't figure out this problem. I have resorted to just using an 802.11g usb adapter that has been proven to be reliable.

I do have 4GB of ram in my system. I tried taking out one stick leaving me with 2GB total but it didn't help at all.

---

