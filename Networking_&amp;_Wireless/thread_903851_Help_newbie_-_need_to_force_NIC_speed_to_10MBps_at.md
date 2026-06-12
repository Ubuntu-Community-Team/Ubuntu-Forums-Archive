---
title: "Help newbie - need to force NIC speed to 10MBps at startup"
date: 2008-08-28
forum: Networking &amp; Wireless
---

### Post by mark_pdx on 2008-08-28
Hi folks, a battle-scarred Windows victim, new to Linux, needing a tip:

Installed Xubuntu 8.0.4 on an old Dell PII laptop 333MHz / 128k RAM.  My wife was using this under WinXP as her music player and (dumb) me told her Linux was way better so let's give it a try. Installed Xubuntu, but I've been stuck for days with a NIC issue and am getting in domestic trouble for killing her music!

Note: this laptop is at the end of a long underground Ethernet cable from house to barn.  Under Windows it was fine as long as I kept the NIC -- a PCMCIA 3Com 3C574 -- set to 10MBps.  Autonegotiation would come up with 100MBps but service was erratic that way.  Speed was easy to set manually in Windows device manager, and network service was reliable.

Trying to accomplish that in Xubuntu now.  Here's where I am:
1. I can manually set speed from the Terminal using:
sudo mii-tool -F 10BaseT-FD

2. To make automatic at startup I created file:
/etc/init.d/setethspeed10

3. Contents of script file:
#! some comments here
/sbin/mii-tool -F 10BaseT-FD

4. then I did: chmod +x /etc/init.d/setethspeed10 

5. then I did: sudo update-rc.d setethspeed10 defaults
and I got back the expected confirmations.

Now when I boot the system, I can see the ethernet card go to 10MBps via an LED indicator during the bootup, but just before the graphical interface loads, it goes back to 100 MBps, and of course that doesn't work reliably on my LAN.

Is there something else I need to change, or a different place to execute the script??  I really appreciate any help you can give this beginner.  Thanks!

---

