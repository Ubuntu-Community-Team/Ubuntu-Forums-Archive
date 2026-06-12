---
title: "Network Manager not connecting"
date: 2007-02-12
forum: Networking &amp; Wireless
---

### Post by Graham1 on 2007-02-12
I can't figure out why Network Manager isn't accepting my WPA key. I've selected the correct settings within the GUI but for some reason, it doesn't fully connect. By fully, I mean that the bottom "dot" is green but then it returns me back to the connection dialog box. What am I doing wrong? Please help.

:)

Edit: I should note that I'm using a static IP.

---

### Post by spd106 on 2007-02-12
You can't use a Network Manager with static addresses, at least not yet. You will have to use the /etc/network/interfaces file and wpa_supplicant. See the WPA sticky for more details.

---

### Post by Graham1 on 2007-02-13
Thanks for your reply :). Currently connected using the method mentioned. Are static IP's not supported due to the version (0.63) as this setup works in openSUSE 10.2 and Fedora Core 6? 

:)

Edit: Btw, how is the Feisty Fawn testing coming along?

---

### Post by spd106 on 2007-02-13
I can't really comment on other distros since I haven't used them for a while now. However I from what I have read they all use a separate backend utility to manage static addresses at the moment. This is what Ubuntu does now in Edgy with the network-admin capplet and will do in Feisty, only NM is installed by default.

It works well if you only connect to one network at a time and only use DHCP to manage addresses, which is probably the vast majority of users. The new avahi-autoip is included as well, but I can only get it working on wired interfaces.

Static addressed networks work less well, I can't find a way to do it on wifi w/ WPA without disabling NM and falling back to wpa_supplicant again.

The best news for Atheros users is that the madwif-tools package from Debian testing has been added to the universe repo. At last monitor/adhoc modes without having to build the tools separately.

Herd 4 should be out by the end of the week, feel free to help out with testing if you can.

---

### Post by Graham1 on 2007-02-13
The only difference with Ubuntu was that I had to install network-manager and network-manager-gnome manually. Maybe extra packages are required for Ubuntu though. However, NM is storing my IP address somewhere (by right-clicking on NM applet, it shows my static IP) but the other info, i.e gateway, subnet mask, etc are left blank. Maybe (and I'm guessing) if I could add the gateway address, it may be able to autheticate with my AP. Any ideas where NM saves it's settings?

:)

---

### Post by spd106 on 2007-02-13
I'm afraid this web page is my primary source of information [http://live.gnome.org/DarrenAlbers/NetworkManagerFAQ](http://live.gnome.org/DarrenAlbers/NetworkManagerFAQ)

The only place NM stores information is the system/networking/wireless/network key in gconf. It also takes control of the /etc/resolv.conf as well, but not for interactive editing.

---

### Post by Graham1 on 2007-02-13
I'll dig around in gconf and see what I can find ;). Thanks for your help and the link (will come in handy).

:)

---

