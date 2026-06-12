---
title: "Cant connect to WPA2 -network"
date: 2008-10-16
forum: Networking &amp; Wireless
---

### Post by userkwokcmscv on 2008-10-16
I can see WLAN-networks in the upper-right corner menu.
I cant connect when I try to type password for WPA2-protected network.

Help!

Do I have to install some WPA-modules?

---

### Post by itsjareds on 2008-10-16
What wireless card are you using? I had trouble connecting my WPN111 to WPA2.

The newer versions of Ubuntu should come with wpa_supplicant, so that's not an issue, but if your wireless card came with drivers for Windows you'll need to install them on Ubuntu. Try installing ndiswrapper.

---

### Post by userkwokcmscv on 2008-10-16
> **itsjareds said:**
> What wireless card are you using? I had trouble connecting my WPN111 to WPA2.

The newer versions of Ubuntu should come with wpa_supplicant, so that's not an issue, but if your wireless card came with drivers for Windows you'll need to install them on Ubuntu. Try installing ndiswrapper.

Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

Ubuntu one is 8.04

I am USING ndiswrapper with windows drivers but I cant CONNECT to WPA2-network!

---

### Post by itsjareds on 2008-10-16
I couldn't (and still cannot) connect to my WPA2-encrypted network with NetworkManager. One of the Ubuntu locals told me to try out Wicd, an alternative network manager.

If you can, [download Wicd]("http://wicd.sourceforge.net/download.php") and install it on Ubuntu. This will require removing the _network-manager_ package first. Just go to Synaptic (System > Admin. > Synaptic Package Manager) and search for "networkmanager". Should find it for you.

After you've uninstalled it and installed Wicd, try connecting through that.

---

### Post by userkwokcmscv on 2008-10-17
> **itsjareds said:**
> 
After you've uninstalled it and installed Wicd, try connecting through that.

I installed Wicd, but cant connect.

New ideas?

---

### Post by userkwokcmscv on 2008-10-19
Anyone help, please

---

