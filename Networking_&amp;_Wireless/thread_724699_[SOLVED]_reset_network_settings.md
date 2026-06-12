---
title: "[SOLVED] reset network settings"
date: 2008-03-14
forum: Networking &amp; Wireless
---

### Post by Rytron on 2008-03-14
Hi,
After reading great things about WiFi radar I am going to use this to try and sort out my unstable wireless connection.

How can I safely reset my network settings (including removing the WEP from keyring).?

---

### Post by Paris Heng on 2008-03-14
If using the conventional way, just copy back the original (Backup) network configuration file into the current one.

---

### Post by Rytron on 2008-03-15
> **Paris Heng said:**
> If using the conventional way, just copy back the original (Backup) network configuration file into the current one.

How is this done?

Are there some terminal commands that can quickly reset all network settings?

---

### Post by Nythain on 2008-03-15
almost all networking device info is stored in a file called "interfaces" thats locate at /etc/network

you could check for a .bak or whatever of your original interfaces file, then just
sudo cp /etc/network/interfaces.bak /etc/network/interfaces

or you can just edit the interfaces file and remove any info you dont want/need
for examples on what a fresh clean unchanged interfaces file would look like, you could google it, or ask here... i dotn know atm because im at work on win98

---

### Post by Rytron on 2008-03-17
[COLOR="Red"]CAUTION!
Before you try this, be aware that execution of **sudo apt-get remove-purge network-manager net-tools**  can result in a crippled OS & a residual filesystem that can only be accessed via an external boot.[/COLOR]

I cam across this - can't remember from where:

```
sudo apt-get remove-purge network-manager net-tools
Then re-boot your system and re-install them again
sudo apt-get install network-manager net-tools
```

---

