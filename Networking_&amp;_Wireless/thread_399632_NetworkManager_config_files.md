---
title: "NetworkManager config files?"
date: 2007-04-02
forum: Networking &amp; Wireless
---

### Post by mweichert on 2007-04-02
Hello,

I'm deploying Ubuntu at all of our retail stores as POS terminals. I'm using a kickstart config file to automate the installations, however I cannot auto-configure my wireless nic. I have to manually do that with NetworkManager.

So, I want to configure the wireless settings with NetworkManager on a preinstalled system, copy my "NetworkManager Configuration files" to a network share, and have a post installation script run to copy the configuration files over.

What are the NetworkManager configuration files? Or are there command-line tools to configure NetworkManager?

Thanks,
Mike

---

### Post by spd106 on 2007-04-02
Network Manager uses gconf for settings and the gnome keyring for password/encryption keys.

This FAQ is useful [http://live.gnome.org/DarrenAlbers/NetworkManagerFAQ](http://live.gnome.org/DarrenAlbers/NetworkManagerFAQ)

---

