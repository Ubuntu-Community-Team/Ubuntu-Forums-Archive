---
title: "wifi troubles"
date: 2007-01-19
forum: Networking &amp; Wireless
---

### Post by dimothy10 on 2007-01-19
Dear All,

i have recently run in to some troubles with my wifi under ubuntu (latest release as far as i am aware).  

From the off the card was recognised by ubuntu and worked fairly well.  I then followed the tutorial here ([https://help.ubuntu.com/community/CrackingWEP](https://help.ubuntu.com/community/CrackingWEP)) to help me install the MadWiFi drivers.  No problems so far.

I then followed a wiki helping me to install my ati x850xt card (or the drivers for it).  unfortunately i cannot find the wiki page that i used but it was an ubuntu page i seemed to go to.  Since installing the driver though, which appears to have been successful, I have lost my wifi card!

Under iwconfig the card used to appear under ath0.  i now no longer see ath0 when i run iwconfig.  it is list when i use lspci though which i suppose is some kind of blessing.

I decide to try and uninstall the madwifi drivers and start again but upon running the mad ./madwifi-unload.bash
./find-madwifi-modules.sh /lib/modules/
commands i get the following message:
FATAL: Error removing ath_pci (/lib/modules/2.6.17-10-generic/net/ath_pci.ko): Operation not permitted
FATAL: Module ath_rate_onoe is in use.
FATAL: Module ath_hal is in use.
FATAL: Module wlan is in use.

Have i accidentally disabled the driver from loading somehow as from what i glean from the error message is that it is in use somehow but commands such as iwconfig ath0 down say that the designation doesn't exist.

apologise that this has rambled on but i am fairly new to linux but desperate to learn and hoping someone out there can help me out.

Cheers

Tim

---

### Post by x64Jimbo on 2007-01-19
"operation not permitted" errors most often occur when a command requiring super user credentials is run without them. Try putting sudo before the command you're running.

---

### Post by dimothy10 on 2007-01-19
thanks very much.  feel like a muppet now.  thought i had tried it but obviously hadnt.  thanks again

---

