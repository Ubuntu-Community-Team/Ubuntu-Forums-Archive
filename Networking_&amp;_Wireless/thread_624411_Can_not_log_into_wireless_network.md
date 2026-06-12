---
title: "Can not log into wireless network"
date: 2007-11-26
forum: Networking &amp; Wireless
---

### Post by lucid_dream on 2007-11-26
I just installed 7.10 and am having trouble connecting to my wireless. Ubuntu recognizes my wireless adapter just fine. But i am unsure how to connect to the network. I tried to enter the SSID through the network manager but that didn't seem to do the trick

---

### Post by ryanVickers on 2007-11-27
you'll need to enter the name, key, and anything else it needs in "Network" under System Administration

Then, run the iwconfig command setting the key once more, the channel if it's not 6, and the ap possibly...

---

### Post by lucid_dream on 2007-11-27
There is no name or key. When I set up the router I never set up that information.

---

### Post by ryanVickers on 2007-11-27
well, there IS a name, whether you know it or not.  If you haven;t changed anything, chances are all you need to do is tell Ubuntu what the name is (on a linksys, it defaults to "wireless")

---

### Post by lucid_dream on 2007-11-28
Ok I logged into my router via XP and found the current name for my network. I entered the network name , turned on DHCP and tried to connect. It now shows the network but there is no activity and can not get an ip address.  I am not familiar with the iwconfig command you referenced. Is there are way that I could  release/renew the ip as I do in XP?

---

