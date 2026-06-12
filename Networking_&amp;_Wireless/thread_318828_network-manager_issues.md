---
title: "network-manager issues"
date: 2006-12-14
forum: Networking &amp; Wireless
---

### Post by David Mulligan on 2006-12-14
Network Manager sucks.  Let me reiterate... network manager has great potential but it has a lot of room for improvement.

- I do like how it picks my wires connection over my wireless one.
- I do like having wired, wireless and virtual network config and choices all in one spot.
- I wish there were a way to get debug logging like in network-manager-pptp so that I can see what is going on with NM itself.
- My Dell's wireless radio disable Fn-f2 disabled the radio but it would be nice if that also showed in the left click menu unchecking the Enable Wireless option.
- My pptp vpn tunnel times out (server gives me the boot for being idle) though network manager still shows it as connected.  It should notice and show as disconnected from the vpn
- Connection Information often fails with the error message "Error displaying connection information: Could not find some required resources (the glade file)!"
- Connection Information only displays information on the ethernet or wireless connection.  It should also show information on the vpn connection too.
- network manager seems to be involved in a bug that disables my computer.  Every once in a while, if I leave "Enable wireless" checked I will get "NETDEV WATCHDOG: eth1: transmit timed out" logged in /var/log/messages over and over.  This is being worked on by some folks at [http://lkml.org/lkml/2006/11/15/296](http://lkml.org/lkml/2006/11/15/296)
- if I click on my active wired network menu item it will reconnect.  It would be nice if the vpn connections could do that too.  It would also be nice if the other vpn connections in the connection list would allow me to switch without disconnecting.  What I really mean is that if I click on another one then it should disconnect and connect to the newly chosen one.

Where should I log my feature requests and issues?

Thanks,
David

---

### Post by rts on 2006-12-14
Sounds like it is working much better for you than for me...

If I configure my wireless via System | Administration | Network, it works great.

Using Network Manager, however, the wireless never comes up.  In /var/log/syslog I get a load of messages about wpa_supplicant failing to do various things.

And if I attempt to use Network Manager, my regular configuration is screwed until I reboot.

---

### Post by mutlu_inek on 2006-12-15
> **rts said:**
> the wireless never comes up.  In /var/log/syslog I get a load of messages about wpa_supplicant failing to do various things.
Rts, did you pull a newer version of wpa_supplicant from non-official Ubuntu repositories? Maybe Trevino's? That broke NetworkManager for me. The current version Ubuntu provides is 0.5.4-5.

If yes, clean the apt cache, comment thos repositories out, remove --purge wpa_supplicant, then reinstall wpa_supplicant and NetworkManager.

Good luck.

---

### Post by mutlu_inek on 2006-12-15
David, maybe you should sign up to this list?

[http://mail.gnome.org/mailman/listinfo/networkmanager-list](http://mail.gnome.org/mailman/listinfo/networkmanager-list)


Rts, see the thread I had opened when I had (presumably) that problem:

[http://ubuntuforums.org/showthread.php?t=305902](http://ubuntuforums.org/showthread.php?t=305902)

---

### Post by rts on 2006-12-15
> **mutlu_inek said:**
> Rts, did you pull a newer version of wpa_supplicant from non-official Ubuntu repositories? Maybe Trevino's? That broke NetworkManager for me. The current version Ubuntu provides is 0.5.4-5.



Nope.  I have

ii  wpasupplicant  0.5.4-5        Client support for WPA and WPA2 (IEEE 802.11

---

### Post by David Mulligan on 2006-12-19
I've started this thread on the Network Manager list about these issues [http://mail.gnome.org/archives/networkmanager-list/2006-December/msg00165.html](http://mail.gnome.org/archives/networkmanager-list/2006-December/msg00165.html) According to Dan Williams, the author of Netowkr Manager, it is a concurrency issue with softmac and not directly network manager.  Dan also says that there are a few driver patches that could resolve the issue.  I've also found references that say that using the devicescape 80211 stack should solve the problem.  However since softmac is part of the kernel that solution is currently above my head.

Is there any way to have a custom kernel that still gets updates?  Is there someway of compiling my own kernel that is the generic Edgy kernel just patched to use devicescape?

Also this one for my feature requests [http://mail.gnome.org/archives/networkmanager-list/2006-December/msg00164.html](http://mail.gnome.org/archives/networkmanager-list/2006-December/msg00164.html)

---

