---
title: "Can't connect to secure wireless (64-bit WEP encryption)"
date: 2007-06-02
forum: Networking &amp; Wireless
---

### Post by fifth_rune on 2007-06-02
I have a Dell Draft Wireless 1500 mini-PCI card that I got working with a How-to on Feisty. It works fine on unsecured wireless channels but I can't seem to get a connection to my WEP 64-bit encrypted network, the connection just hangs for awhile then tries to connect again after failing.  I am using a WRT54G Linksys router.  Thanks in advance for any help on this issue, I will be monitoring this thread so if you need any more information  I will try to reply promptly.

---

### Post by fifth_rune on 2007-06-02
Bump

---

### Post by Candace on 2007-06-24
Hi,

I can connect fine to unsecured wireless networks, or to networks where I have to authenticate (i.e. entering my school id and username from a terminal), but I am also unable to connect to a secure network.

I have Ubuntu 7.04 and an HP dv2020 laptop w/ Broadcom Corporation BCM4318 802.11g Wireless card
I am not sure what the encryption type here is.

Has anyone else had this problems besides fifth_rune and I?

---

### Post by Unchien on 2007-06-24
I had the same problem with a WPA2 wifi network.
network-manager kept asking for my password over and over but didn't connect.
The solution was to uninstall network manager by typing:
sudo apt-get remove network-manager
and install wicd instead. It's mentioned on this forum and there's also a guide here:
[http://wicd.sourceforge.net/wiki/doku.php?id=faq](http://wicd.sourceforge.net/wiki/doku.php?id=faq)
Then in Wicd I could type in my WPA2 password under the wifi configuration.

---

