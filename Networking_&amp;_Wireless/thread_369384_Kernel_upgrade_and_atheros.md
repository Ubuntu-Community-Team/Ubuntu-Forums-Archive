---
title: "Kernel upgrade and atheros"
date: 2007-02-24
forum: Networking &amp; Wireless
---

### Post by john36 on 2007-02-24
I have a Thinkpad X60s and I have been running Dapper on it.
It's an intel dual core and it uses the 686 kernel.

I just upgraded from 2.6.15-27-686 to 2.6.15-28-686 and my wireless stopped working.

My wireless is an atheros
Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

I have the ath_pci module loaded but under the Menu System, Networking
my wireless doesn't appear (just eth0 and the modem)

Any ideas.  I have gone back to using the old kernel.

---

### Post by spd106 on 2007-02-24
Please check that you have the 'linux-restricted-modules' package installed as the new kernel needs updated modules.

---

### Post by john36 on 2007-02-24
> Please check that you have the 'linux-restricted-modules' package installed as the new kernel needs updated modules

I had already installed those.

---

### Post by john36 on 2007-02-24
**SOLVED**

I built my own modules as described in this thread
[http://www.ubuntuforums.org/showthread.php?t=212600&page=2](http://www.ubuntuforums.org/showthread.php?t=212600&page=2)

From 20,000 feet the steps are
removed restricted modules package
rmmod a few of the atheros modules
make sure you have kernel headers downloaded
download the madwifi package from 
[http://snapshots.madwifi.org/madwifi-ng/](http://snapshots.madwifi.org/madwifi-ng/)
Build your modules
load 'em up

More details are described in the thread above.

Would be nice if I didn't have to jump through these hoops and Ubuntu did it directly.
Oh well.

---

### Post by spd106 on 2007-02-25
So you're saying that the linux-restricted-modules-2.6.15-28-686 package doesn't work for the new kernel?

I haven't updated since the 2.6.15-27 kernel on my old partition, so I'll give it go and see.

---

### Post by spd106 on 2007-02-25
Okay I've updated the kernel to 2.6.15-28-686 and my Atheros card works fine with WPA-PSK (CCMP) through Network Manager. 

In fact it works better than it ever did with the old kernel. I also tried the 386 kernel as well and it produced the same results.

It still doesn't do background scanning properly, but since it's using madwifi-old I can't complain. If I was still using Dapper (rather than Edgy/Feisty) I would still probably build madwifi-ng as mentioned above.

---

