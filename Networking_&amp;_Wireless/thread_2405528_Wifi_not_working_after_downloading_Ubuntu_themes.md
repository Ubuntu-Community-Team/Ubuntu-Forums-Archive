---
title: "Wifi not working after downloading Ubuntu themes"
date: 2018-11-07
forum: Networking &amp; Wireless
---

### Post by pandaemonium2 on 2018-11-07
Ubuntu Community,

This is my first post. I recently downloaded some Ubuntu themes such as  Arc, Pop, and Paper on my 2014/15 Lenovo Yoga 2. My WiFi access works well at home but does not connect when I'm at a local hospital. I noticed that it connected at my hospital with a fresh install of Ubuntu 18.04 without adding and changing themes in the Tweaks tool. But after I downloaded some of the themes listed above it no longer connects. My wireless card can "see" the WiFi signal and attempts to connect to the hospital's WiFi but without success. Is this an issue with some of the themes I downloaded causing a disruption in the way my computer connects a hospital's wireless internet? How would I troubleshoot and find out the source of the problem? 

Thanks in advance!

---

### Post by mitesh.agrwl on 2018-11-09
Hi,

As it is mentioned here > WiFi access works well at home but does not connect when I'm at a local  hospital. I noticed that it connected at my hospital with a fresh  install of Ubuntu 18.04 without adding and changing themes in the Tweaks  tool
it shows that the wireless adaptor is working and it dos not have any issues. But after downloading and activating the new themes it can not connect to local hospital wifi there are chances that the security policy at local hospital might be preventing it to connect. One can define such security rules for Bring Your Own Device (BYOD), although the chances of such security are minimal, but still possible.

One possible way to troubleshoot is by capturing the traffic on the wireless adaptor using Wireshark.

```
~$ sudo apt-get install wireshark
```

Once the traffic is captured, it can be analyzed to pin point the issue.

Regards,
Mitesh

---

