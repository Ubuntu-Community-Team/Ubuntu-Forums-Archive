---
title: "Update killed wireless"
date: 2007-04-06
forum: Networking &amp; Wireless
---

### Post by greglcarter on 2007-04-06
Hi Folks from a newbie...
I have an IBM T30 that I just upgraded to Ubuntu 6.10. Was running Xbuntu. The upgrade found my wireless and it was working fine as eth1. I just installed a bunch of updates (162 or so) and in the network settings list I now only have wired connections as wlan0 and eth0. When I run the iwconfig list, the eth1 does not show up. I have read some forum messages that suggest I'm not the first to have this happen. Unfortunately I don't understand some of the sugested solutions...something about restricted kernels missing in the update, but one post indicates restricted kernels are available for download...? Or going back to the old kernel will work. Sounds good to me but being real new here I have no idea what that means or how to implement it. 

The eht1 network connection is still showing up in the top screen menu bar but is not working. Is there a simple way to get that eht1 back in working order...? Help

Thanks much in advance.

---

### Post by cryptonic on 2007-04-08
i have the same prob m8, its a problem with the kernal update. Im looking for a fix atm but not looking so good. the bug was filled in 2005 and still nothing has been done. Personally i doubt this will get addressed considering the age of the hardware and the potentially low percentage of ubuntu users with the problem. Its a pity though as i cannot get it to work with my usb dongle either. Id say your best bet if you wanted an up to date linux os on the ibm t30 with working networking is to use fedora or open suse. I love ubuntu but im sick of these type of issues. feisty fawns intention was to increase compatibility with wireless cards yet to do that they break compatibility with older cards, truly sad.

---

### Post by HumbleGod on 2007-04-09
> **greglcarter said:**
> Hi Folks from a newbie...
[...] I just installed a bunch of updates (162 or so) and in the network settings list I now only have wired connections as wlan0 and eth0. When I run the iwconfig list, the eth1 does not show up. I have read some forum messages that suggest I'm not the first to have this happen. Unfortunately I don't understand some of the sugested solutions...something about restricted kernels missing in the update, but one post indicates restricted kernels are available for download...? Or going back to the old kernel will work. Sounds good to me but being real new here I have no idea what that means or how to implement it.

The same happened to me when I updated the kernel after installing Edgy and (finally) getting wireless to work. Using the original kernel works fine for me; I just select the old one from GRUB when the computer boots. Give that a shot and see what happens.

I'd love to know that if/when I upgrade to Feisty (after the official launch) the same thing won't happen, but I'm afraid to find out!

---

### Post by donstefano on 2007-04-09
Same problem here, after updating kernel my hifi network is not available. Hope it'll be fixed soon!

---

