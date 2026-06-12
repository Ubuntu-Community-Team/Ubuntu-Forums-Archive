---
title: "Xubuntu 14.04 problems with wireless card, shutting down and rebooting"
date: 2014-09-27
forum: Networking &amp; Wireless
---

### Post by argonvegell on 2014-09-27
My wireless card doesn't show up on Network Connections, and I typed this command on the terminal, "type lshw -C network" to see what my card model was, which is "BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller", I installed the driver with "Additional drivers', this is what was installed:

libfakeroot
fakeroot
bcmwl-kernel-source
dkms
removed - linux-generic

but my card wasn't detected still, and what's more, it seems to have hung my shut down and reboot options, I turned off the computer manually instead, I was able to regain my shut down and reboot by uninstalling the following above and reinstalling "linux-generic".

I believe I'm experiencing this bug: [https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1304532](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1304532)

I do not know what to do, I'm now afraid to even install my wireless driver, of fear of losing the option to shutdown and/or reboot my PC.

And also I noticed that whenever I shut down my PC, my LAN card is still activated, and it only shuts down when I physically unplug my computer from the power outlet.

---

### Post by jeremy31 on 2014-09-27
Follow the instructions here to install the correct drivers/firmware

[http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by Hadaka on 2014-09-27
Hi, please do the exact same commands as i suggest here
[http://ubuntuforums.org/showthread.php?t=2245919](http://ubuntuforums.org/showthread.php?t=2245919)
thanks.

---

### Post by argonvegell on 2014-09-27
> **jeremy31 said:**
> Follow the instructions here to install the correct drivers/firmware  [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)  Thanks, that worked, I followed the instructions to the teeth, thank you.  But what caused my issues to begin with anyway?

---

