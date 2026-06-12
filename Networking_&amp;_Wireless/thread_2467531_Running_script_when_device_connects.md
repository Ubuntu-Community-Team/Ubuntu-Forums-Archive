---
title: "Running script when device connects"
date: 2021-09-29
forum: Networking &amp; Wireless
---

### Post by Cos_Marchy on 2021-09-29
Hi, 

I'm looking for a solution which will run a script when a specific device connects to a wifi network.
                                 
I have a mobile wifi device which is connected to a battery with a limited run time. When the mobile device is in range of my network, I need to trigger a  script to download the information from that device to a NAS. The question is more to do with how to trigger the script rather than what the script will do.

 Since I cannot see any way of triggering an event on my router when  the mobile device connects to it, I was wondering whether this is possible  by using a device such as a RaspberryPI as a hotspot, which the mobile device would connect to,  thus triggering a script and triggering the download.  

Whilst a RaspberryPi is not the only hardware which can be used a hotspot, I'm guessing that if this is possible, it is more of a software or rather Linux question than it is a hardware problem as Linux will run on multiple platforms...

 I cannot rely on a polling type setup, where the hotspot device polls  for the mobile device at set intervals, as the mobile device comes in to range of the  wifi and connects as different times of the day and I need to trigger the download  as soon as possible after connecting to ensure the download completes  before the battery runs out...

 Is this possible to do this?

Thanks

---

### Post by TheFu on 2021-09-30
In the old days, before netplan, we'd use **post-up** scripts in the /etc/network/interfaces file. From the interfaces manpage:
```
       post-up command
              Run  command after bringing the interface up.  If this command
              fails then ifup aborts, refraining from marking the  interface
              as  configured  (even  though  it has really been configured),
              prints an error message, and exits with status 0.  This behav&#8208;
              ior may change in the future.
```

I don't know how to accomplish the same thing with netplan. Sorry.  Google found this:
[https://netplan.io/faq/#use-pre-up%2C-post-up%2C-etc.-hook-scripts](https://netplan.io/faq/#use-pre-up%2C-post-up%2C-etc.-hook-scripts)
They have example scripts.  I've not used it, so don't know if or how well it works.

---

