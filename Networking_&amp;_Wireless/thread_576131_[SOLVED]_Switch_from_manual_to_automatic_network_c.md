---
title: "[SOLVED] Switch from manual to automatic network config"
date: 2007-10-14
forum: Networking &amp; Wireless
---

### Post by Stormspireiv on 2007-10-14
I'm running Feisty with the default networking applet on a wired network.  Normally I have the applet auto-configure my IP address and other settings (DHCP), but I had to temporally set up a seperate network using a hub I had laying around.  In doing so, I requred a user-set static IP (no DHCP), so I used the manual configuration tool to set this. 
Now, when I went back to my normal network configuration, it will only allow me to do a manual configuration when I would like it to automatically configure my settings.  How would I go about doing this?

Thanks in advance.  If there's any more info you need, just ask.

---

### Post by tlie on 2007-10-14
i just had the same problem.

right click the network icon, untick "Enable Network" and tick it back.
works for me.

---

### Post by Lambert on 2007-10-14
> **Stormspireiv said:**
> I'm running Feisty with the default networking applet on a wired network.  Normally I have the applet auto-configure my IP address and other settings (DHCP), but I had to temporally set up a seperate network using a hub I had laying around.  In doing so, I requred a user-set static IP (no DHCP), so I used the manual configuration tool to set this. 
Now, when I went back to my normal network configuration, it will only allow me to do a manual configuration when I would like it to automatically configure my settings.  How would I go about doing this?

Thanks in advance.  If there's any more info you need, just ask.


post the info in your file /etc/network/interfaces

---

### Post by Stormspireiv on 2007-10-14
> **tlie said:**
> i just had the same problem.

right click the network icon, untick "Enable Network" and tick it back.
works for me.

Yep that worked just great. Thanks.

---

