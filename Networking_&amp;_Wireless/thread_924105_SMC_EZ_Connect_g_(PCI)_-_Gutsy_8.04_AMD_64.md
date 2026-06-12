---
title: "SMC EZ Connect g (PCI) - Gutsy 8.04 AMD 64"
date: 2008-09-19
forum: Networking &amp; Wireless
---

### Post by or1onas on 2008-09-19
Greetings to everybody.

I'm trying to setup a SMC EZ Connect g (PCI) card to my AMD 64 Gutsy Gibbon box.
It's using an Atheros chipset and i've not been able to understand the necessary moves i need to do in order to make it work.

'lspci' displays it as an Atheros chipset, unknown id 001d <-- these are the info displayed in short

- I've downloaded and installed:

madwifi-tools_0.9.3+dfsg-3_amd64.deb

- I've also added 'ath_pci' to /etc/modules

- I disabled Atheros HAL from the 'proprietary drivers' menu

- No change after several reboots.

- 'iwconfig' returns only 'eth0' and 'lo' as interfaces

I've also found the following package:

madwifi-0.9.4.tar.bz2

Should i also install it?
Is the driver included here? 
What about the madwifi-tools? What is their use?

Any help would be much appreciated.

Thanks in advance.

---

