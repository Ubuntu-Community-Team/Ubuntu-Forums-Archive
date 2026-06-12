---
title: "Do I need to sacrifice a chicken or something? BCM4306 &amp; iBook G4"
date: 2007-05-08
forum: Networking &amp; Wireless
---

### Post by grepcomputers on 2007-05-08
I've tried about 3 or 4 different how-to guides for getting the bcm43xx kernel module working with wireless and WPA(1) encryption.

With bcm43xx-fwcutter and bcm43xx-firmware I have no trouble getting the card working well enough to scan networks and join unencrypted ones. But only *once* have I managed to get it to join a WPA encrypted network. Then I made the mistake of rebooting, and that ability went away.

I'm running Xubuntu 6.06. (Originally Feisty, but I gave up on that after hearing about all the network issues. Plus, I wanted XFCE as my window manager).

I've tried things in different orders, I've tried rebooting, I've tried using bcm43xx-fwcutter, bcm43xx-firmware, BOTH, neither obvioulsy no go there), and all sorts of different ways of getting wireless working. I've also tried using nm-manager-gnome and wifi-radar, which didn't work. (Using wpa_supplicant and wpa_supplicant.conf was what worked that one time).

Is there just some PPC incompatibility that makes this next to impossible to get working? I feel like I'm doing black magic or something.

---

### Post by dbott67 on 2007-05-08
I'm not sure about the PPC compatibility, but I've got a Dell 6400 with Broadcom 4311 and wrote up how I got it working.  Using NDISWrapper and network-manager-gnome, I am able to easily connect to WEP and WPA networks.  The write-up is here:

[http://ubuntuforums.org/showthread.php?t=274915](http://ubuntuforums.org/showthread.php?t=274915)

The key issues for me were:

1. Blacklist existing bcm* modules
2. Compiling NDISwrapper from source
3. Installing network-manager-gnome, which handles all types of encryption (WPA1&2, WEP, etc.)

You may need to comment out any WPA lines in your /etc/network/interfaces file, as network-manager will handle all the gory details.

```
sudo apt-get install network-manager-gnome
```After installation, restart you computer. A "Network Manager" icon should appear along the top that you can click on to configure:

[IMG]http://www.gnome.org/projects/NetworkManager/images/wireless-at-tealuxe.png[/IMG]

Details are here:

[http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)

-Dave

---

