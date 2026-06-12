---
title: "Ubuntu Ultimate 1.4 &amp; Wireless Device"
date: 2007-06-18
forum: Networking &amp; Wireless
---

### Post by sidimaiga on 2007-06-18
Hi,

I just install Ubuntu Ultimate 1.4, and after following the instructions to install my Nvidia GPU and Beryl, my wireless card got disabled.

Must a removes some repo while cleaning nvida files.

Please any suggestion on how to get it up and running? Wireless is my only connection ressource on that box.


Thanks, 

PS: there is the instruction i followed to install NVIDIA drivers: [http://ubuntusoftware.info/beryl.html#nvidia](http://ubuntusoftware.info/beryl.html#nvidia)
Method 1. Thx

---

### Post by spd106 on 2007-06-20
It's likely that during the installation of the nvidia driver the linux-restricted-modules packages were removed. This package contains some wireless drivers such as the madwifi driver used with Atheros based cards.

I suggest you check which wireless card you have (lspci) and if it an Atheros card then download and the driver from [http://madwifi.org](http://madwifi.org) and build that one.

---

### Post by Raptormn on 2007-06-20
> **sidimaiga said:**
> Hi,

I just install Ubuntu Ultimate 1.4, and after following the instructions to install my Nvidia GPU and Beryl, my wireless card got disabled.

Must a removes some repo while cleaning nvida files.

Please any suggestion on how to get it up and running? Wireless is my only connection ressource on that box.


Thanks, 

PS: there is the instruction i followed to install NVIDIA drivers: [http://ubuntusoftware.info/beryl.html#nvidia](http://ubuntusoftware.info/beryl.html#nvidia)
Method 1. Thx

how did you get a copy of it? i was looking on the site but didnt see any links or torrents. i would like to try it out.

---

### Post by TheeMahn2003 on 2007-07-08
> **Raptormn said:**
> how did you get a copy of it? i was looking on the site but didnt see any links or torrents. i would like to try it out.

Actually what he had was the 1.31 beta.  1.4 has been released but currently only in cd format.  You can read more about it [here]("http://ubuntusoftware.info/Ubuntu_Ultimate_CD/").

---

