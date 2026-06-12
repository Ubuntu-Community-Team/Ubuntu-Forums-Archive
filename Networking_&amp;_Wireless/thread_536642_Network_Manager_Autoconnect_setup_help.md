---
title: "Network Manager Autoconnect setup help"
date: 2007-08-28
forum: Networking &amp; Wireless
---

### Post by Eupham on 2007-08-28
I just moved into an apartment and got my own internet setup with a wireless router.  During the time without internet I would connect to a random unsecured network for internet (I know I'm horrible).  Now when I startup my computer network manager will auto-connect to that network instead of my own.  How do you set priority over different networks or delete the settings all together?

---

### Post by mentalpuff on 2008-03-05
im having the same issue. bump for possible answer. 
my problem is that my laptop autoconnects to my neighbors wireless rather than my own. is there a config file somewhere to set it to connect to the strongest available connection?

---

### Post by Brucevdk on 2008-04-27
> **Eupham said:**
> or delete the settings all together?

I knew this is a late response, but I stumbled upon this thread while researching the issue. I haven't yet managed to find out how to prevent NetworkManager from autoconnecting or as you state set the priorities of networks.

If all you want to do is remove the network configuration simply remove the folder matching the SSID from ~/.gconf/system/networking/wireless/networks

---

