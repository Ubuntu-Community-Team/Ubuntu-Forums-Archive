---
title: "Network-manager won't save passwords"
date: 2006-09-15
forum: Networking &amp; Wireless
---

### Post by fieldstone on 2006-09-15
This is only really a minor inconvenience, but it could be a real problem for me when I'm not at home and I'm using some WEP key that's a series of 20 or more letters and numbers.

I can't seem to get network-manager to save passwords for networks. When using knetworkmanager, I get the KWallet error (which I've seen documented other places) that says "There have been repeated failed attempts to access a wallet. An application may be misbehaving." As a result, I have to enter my password every time I restart.

I also tried network-manager-gnome's nm-applet program, and though it works just fine for connecting, I can't get it to save passwords either. I have gnome-keyring and gnome-keyring-manager installed, but I can't seem to get gnome-keyring-daemon to run properly at startup - every time I run gnome-keyring-manager, it says "GNOME Keyring daemon is not running". (I have Kubuntu, which doesn't come with gnome-keyring installed by default, so is there something I need to do to get it working?)

If someone can walk me through fixing whichever of these issues is easier to fix, I'd appreciate it very much. For reference, I've already installed version 0.6.4 of Network Manager... so is there some Gnome or KDE library I need to update, or a script I need to put somewhere, to get my wireless passwords to save correctly?

---

### Post by ruffneck on 2006-09-15
So you compiled NM 0.6.4 from souce or you found a .deb somewhere?

---

