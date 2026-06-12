---
title: "nforce2 ethernet not working"
date: 2006-10-03
forum: Networking &amp; Wireless
---

### Post by drummer4lifex on 2006-10-03
Hello,

After searching for about 2 hours, trying to figure out how to get my friend's homebrew computer to work (Asus M7NCD) I've given up and started a thread. The first things I need to resolve are the internet:

nforce2 ethernet does not work (pretty sure it's not even detected)

Texas Instruments AC111 Wireless PCI card does not work. The weird thing is that it's detected, it says it's activated, but it just doesn't detect any networks. Also, it says in dmesg that the "link is not ready" for this device. 

Also, if there is an onboard sound fix for the nforce2 that might be included with the ethernet, that doesn't work either....

Thanks!

---

### Post by spd106 on 2006-10-04
The nforce2 chipset is supported by the forcedeth driver, so check that it's being loaded (**lsmod | grep force**).

When you say it's not being detected do you mean it doesn't show up in the network-admin gui or that it isn't found in **lspci**? If it's the latter then you may have hardware trouble.

For the sound issue I have found sometimes that it has been muted. Don't ask me how or why. To unmute I use **alsamixer** to check each of the output levels. I forget which one it is that's usually been muted. This guide has a few more ideas [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

