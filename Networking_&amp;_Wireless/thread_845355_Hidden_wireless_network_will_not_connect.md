---
title: "Hidden wireless network will not connect"
date: 2008-06-30
forum: Networking &amp; Wireless
---

### Post by azizzle on 2008-06-30
Recently I decided to reconfigure my wireless router, and set the network to hidden. It worked fine with my windows box. The issues with ubuntu went like this:

I select "connect to other networ" and put my settings in. It connects, for about 30 seconds and then disconnects. wtf?

I create a new network, and put the ssid and wpa1 in and it connects and stays connected for a couple days. Then, when I updated to the latest kernel and now I can't connect no matter what I do. 

What should I do? I've been pouring over all of the other hidden wireless threads but it seems as though nobody has had this happen to them. Any suggestions?

---

### Post by caljohnsmith on 2008-06-30
Have you looked hard through the system log with "dmesg" for anything suspicious or something to give you clues to your problem? Unless you know you need some special functionality of the new kernel, why not just stick with the older one for now if it was working fine with your wireless? Regardless, it sounds like you should file a bug report at bugs.launchpad.net. You might be able to resolve it there.

---

