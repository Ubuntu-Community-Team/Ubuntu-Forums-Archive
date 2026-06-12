---
title: "NDISWrapper + Kubuntu"
date: 2005-12-01
forum: Networking &amp; Wireless
---

### Post by markr on 2005-12-01
I've installed ndiswrapper and it seems to be okay (it detects my hardware).

However I can't connect to the internet :-(

I've done this in Gnome and it took about 5 minutes to setup, KDE seems to be giving me some serious grief though.

1. I need to do a "modprobe ndiswrapper" everytime I reboot in order to get my wirelss card activated; how do I get it starting automatically, I remember reading somewhere about a file that I can stick "ndiswrapper" in to force it to start at boot time?

2.  The network and wireless apps in KDE do not seem to configure my card correctly;  can anyone provide details on doing it from command line (I know I need to change /etc/network/interfaces)?

Thanks for any advice.

Mark.

---

### Post by orbinick on 2005-12-01
What wireless card do you use?

---

### Post by markr on 2005-12-02
It's a Belkin F5D7010 PCMCIA Card.

Interestling, I booted up last night and for the first time the light came on the card during the boot process.

I've tried to amend my /etc/network/interfaces based on various posts on this site so when I get back home I'll give it a try.

Mark

---

