---
title: "[SOLVED] Kubuntu's network problems, Xubuntu just fine, any ideas ?"
date: 2008-08-30
forum: Networking &amp; Wireless
---

### Post by tosszyx on 2008-08-30
Hi, I installed Xubuntu 8.04.1 some days ago and installed over it Kubuntu from repositories (I have been unable to install a working Kubuntu setup directly from CD). The network worked just fine after configuring it. When changing to Kubuntu the preexisting setup worked just fine, even the network was setup correctly, **the problems came when modifying Kubuntu's network parameters**, after that the wireless will not connect and refuse any connection no matter what information was input in the network configuration. I was able to configure everything from the terminal following the sticky in this forum, but neither Konqueror nor Amarok will connect to the network even when Firefox, Skype, Thunderbird, etc. do so. How can I fix this or at least troubleshoot it? I'm not that experienced with Linux but I can follow instructions.:) 

Regards

**Well after some more searching I found out this [page ]("https://bugs.launchpad.net/kdenetwork/+bug/86680"), were it is explained that is a bug related to the knetworkmanager. Just quitting it, solved the problem. **Hope it helps somebody else.

---

