---
title: "Lost Wireless after Install"
date: 2006-11-11
forum: Networking &amp; Wireless
---

### Post by g_mclinux on 2006-11-11
Hello,

I just installed Xubuntu alternate 6.10 and everything went fine, including my wireless card (DWL-G650) which was successfully detected and used during the install (ath0).

However after the post-install reboot, my wireless seemed to disappear.  It is not listed by "Network Manager" and the ath0 device seems to be gone.

I'm just going thru the re-install now, but I expect the same thing to happen.  Has anyone else run across this problem?

Thanks!

---

### Post by g_mclinux on 2006-11-11
I just finished the re-install and the same thing happened.  The wireless PCMCIA card was detected and used during the install, but disappeared after the reboot.

---

### Post by sjnovick on 2006-11-11
My wireless card changed from wlan0 to eth1.  Try running iwconfig and iwlist scan as sudo.  This will show you which wireless cards are available.

---

### Post by g_mclinux on 2006-11-11
iwconfig gives the following:

lo   no wireless extensions

eth0 no wireless extensions

- - -

It's as if ath0 has disappeared.  How do I add it back?  Thanks!

---

### Post by g_mclinux on 2006-11-11
FIXED!

FYI, I used Synaptic to search for madwifi, which showed a linux restricted modules package.  I installed the package (had to connect my wired network - and NOT use the install CD).  After a reboot all was well!  I just enabled the wireless network and voila.

Don't ask me why I had to do this.  I'm guess for legal reasons Xubuntu only installs certain modules.

---

