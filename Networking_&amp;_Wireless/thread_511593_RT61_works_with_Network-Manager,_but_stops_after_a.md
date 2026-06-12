---
title: "RT61 works with Network-Manager, but stops after a few minutes"
date: 2007-07-28
forum: Networking &amp; Wireless
---

### Post by bmeyer on 2007-07-28
I'm using a Linksys PCI wireless card (RT61 chipset) with network-manager.  RT61 kernel module is blacklisted and the most recent RT61.inf is installed with ndiswrapper.

When I boot the computer up, network-manager does not initially have wireless options available.  But after I modprobe ndiswrapper, the wireless connectivity becomes available.  This is odd, since I try ndiswrapper -m and it tells me I already have the mod link set up.

Regardless, after modprobe, I'm able to connect and successfully use the internet.  But it goes down after a few minutes and won't start back up without a reboot.  The card works fine under Windows, so I don't think it's an issue with the card or router...

Any ideas what the heck would be causing this?

---

### Post by kevdog on 2007-07-28
To make the ndiswrapper module load on boot:

echo ndiswrapper | sudo tee -a /etc/modules

---

### Post by bmeyer on 2007-07-28
> **kevdog said:**
> To make the ndiswrapper module load on boot:

echo ndiswrapper | sudo tee -a /etc/modules

That worked, thanks!  However, the network connection keeps going down after a while.  Any idea why?

---

### Post by kevdog on 2007-07-28
I dont really have an answer for you on this one.  The only thing I would recommend if you want to play around is to install the serial monkey rt61 drivers.  Id use this post as a guide (its for rt73 but rt61 drivers can be installed the exact same way -- substitute 61 for 73).  If you choose to do this, make sure to blacklist the ndiswrapper module (that way in case it doesnt work, all you need to do is remove the blacklist ndiswrapper statement and you will be back to where you started).
[http://ubuntuforums.org/showthread.php?t=400236&highlight=serialmonkey](http://ubuntuforums.org/showthread.php?t=400236&highlight=serialmonkey)

---

