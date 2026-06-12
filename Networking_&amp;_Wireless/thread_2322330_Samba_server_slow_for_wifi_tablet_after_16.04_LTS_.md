---
title: "Samba server slow for wifi tablet after 16.04 LTS update, worked fine in 14.04 LTS"
date: 2016-04-27
forum: Networking &amp; Wireless
---

### Post by bastian2 on 2016-04-27
After updating to Ubuntu 16.04 LTS the wifi speed on my tablet from samba dropped from 3.5 mbyte /sec to 800 kbyte /sec which makes it impossible to stream movies from my samba server.

Using 14.04 LTS this worked well, but since 16.04 it suddenly slowed down drastically without changing any Samba config.
I did not change anything else then updating 14.04 to 16.04 LTS.

Speeds on a wired windows machine seem to be fine, although they now have a slow and unstable start, this was not the case on 14.04.
I also had the same problem on 15.04 and 15.10 (Non-LTS), at that point I returned to 14.04

I don't have any idea where to start....

server is on 1 gbit lan, the server is not using wifi.

---

### Post by bastian2 on 2016-04-27
Solution for me that works is:

Turning off: tcp-segmentation-offload: off

ethtool -k yourcard (eth0)
sudo ethtool -K eth0 tso off 

Problem solved....
Also see:
[https://bbs.archlinux.org/viewtopic.php?id=196853](https://bbs.archlinux.org/viewtopic.php?id=196853) last post...

Don't know if it survives a reboot yet.

Edit: 
this does not survive a reboot, as soon as I reboot it is gone.

Extra info:
NIC: Atheros L1E
Kernel module: atl1e

---

### Post by Metanei on 2017-04-12
You are awesome bastian2! Saved my day!! I'm going crazy searching what the hell is happening to my WiFi connection. I updated my server to 16.04LTS and not noted the problem on the WiFi transfer speed until some weeks after the update and I never realised that the problem could be this update. I started thinking on replace my router!! 
I'll try to find a solution for doing this change effective also after a reboot and post it here if I found it.

THANK YOU VERY MUCH!!

---

### Post by Metanei on 2017-04-12
I found this fix. Worked for me:

[https://forum.ivorde.com/linux-tso-tcp-segmentation-offload-what-it-means-and-how-to-enable-disable-it-t19721.html](https://forum.ivorde.com/linux-tso-tcp-segmentation-offload-what-it-means-and-how-to-enable-disable-it-t19721.html)

Thanks and regards.

---

