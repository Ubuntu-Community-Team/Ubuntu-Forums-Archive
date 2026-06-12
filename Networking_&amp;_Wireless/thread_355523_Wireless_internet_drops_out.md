---
title: "Wireless internet drops out"
date: 2007-02-07
forum: Networking &amp; Wireless
---

### Post by grsing on 2007-02-07
After a seemingly random amount of time (usually an hour or more, but sometimes 5 minutes), my wireless connection will stop working. I've tried disabling and reenabling it, but the only solution that seems to work is restarting (and restarting so often is getting to be a major pain).  I'm not exactly certain what config files and such I should post to help diagnose the problem, so ask and I'll post whatever you need. Thanks!

---

### Post by grsing on 2007-02-07
Few more details. First, this only started happening about 3 or 4 days ago, it had been working fine for a month. Second, the adaptor is a WUSB54g rev. 4, running the rt2x00 driver. I'm not using Network Manager or any applet like that (it's a desktop, so it's always on the same network, there's no need to browse for networks). Lastly, I'm checking it on Windows now, just to see if it's a problem on the router/network end, rather than my connection.

---

### Post by Nakkis on 2007-02-07
I have the same problem with Buffalo WLI-U2-KG54 USB-wireless adapter which uses the same rt2570 driver. So far I have found two ways to fix it: one  is to disable USB 2.0 support, either from bios or removing the ehci_hcd module from kernel every time I boot (sudo modprobe -r ehci_hcd) and the other is to use ndiswrapper with the windows drivers. But ndiswrapper doesn't seem to work after I reboot the computer for some reason even though it sees my card and the access points.

So I have disabled USB 2.0 support from my bios and use only USB 1.1 which is a pain in the arse sometimes.

---

### Post by grsing on 2007-02-07
Update: I've been running Windows for about 5 hours now, and no cutouts. So the problem has to be with my Ubuntu install. Any ideas?

---

### Post by grsing on 2007-02-08
No ideas? I love Ubuntu and hate using Windows, but I can't put up with restarting half a dozen times a day because my networking goes out. Would a reinstall of Ubuntu help? That's a pain, but if it would fix it, I'll deal. Thanks again.

---

### Post by Keltazz on 2007-02-08
HI - i ve had the same probelm., i think - when i  m writng a long email or posting like this, i ll finish and then the connection is gone and all my slow typing is lost - so i refresh the page every couple minutes, or write in word doc and then just paste it all in., ,  i guess i d be willing to disable the usb, but i d like to know what they have to do with eachother. also, i ve had this problem before and it has seemed to cure itself, so i wonder if it might be an internet setting on the computer, or even the server...sincerely, keltazz

---

### Post by grsing on 2007-02-11
Well, I think I've narrowed down the problem, but it also appears to have worsened. It appears that it only happens while I have a torrent downloading; however, it's now a hard freeze, rather than just the internet going out (by hard, I mean the only way to recover is with the power button on the computer, ctrl-alt-bksp and everything less has no effect). Any more ideas?

Edit: I'm going to make a new thread on it, since it's a rather different problem, so consider this closed. Thanks.

---

