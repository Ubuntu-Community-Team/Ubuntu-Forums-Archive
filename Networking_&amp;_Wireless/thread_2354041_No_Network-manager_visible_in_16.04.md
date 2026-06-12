---
title: "No Network-manager visible in 16.04"
date: 2017-02-27
forum: Networking &amp; Wireless
---

### Post by BrianV on 2017-02-27
I have tried to set up a VPN with IPVanish, following their instructions for Ubuntu OpenVPN Setup. This calls for installing network-manager-openvpn, and I have confirmed with Synaptic that I have installed:
network-manager
network-manager-gnome
network-manager-openvpn
network-manager-openvpn-gnome
network-manager-pptp
network-managerpptp-gnome

There is no network-manager icon in the system tray, nor can I find a network-manager application when searching in the dashboard.

My understanding of networks is quite limited, so I may just be doing something silly, so any advice will be helpful, either to resolve the current problem or to aid my understanding of networking.

Thank you for any help offered.

---

### Post by wildmanne39 on 2017-02-28
Please do:
```
sudo apt-get install --reinstall network-manager-gnome
```
does that add the icon to the top bar?
Thanks

---

### Post by BrianV on 2017-03-05
> **wildmanne39 said:**
> Please do:
```
sudo apt-get install --reinstall network-manager-gnome
```
does that add the icon to the top bar?
Thanks

No change, except after following the recommendations during the re-installation Synaptic reports the additional installed packages:

network-manager-vpnc
network-manager-vpnc-gnome
network-manager-openconn
network-manager-openconn-gnome
and
libproxy1-plugin-networkmanager

Thanks

---

### Post by ganesh66x on 2017-03-10
> **BrianV said:**
> I have tried to set up a VPN with IPVanish, following their instructions for Ubuntu OpenVPN Setup. This calls for installing network-manager-openvpn, and I have confirmed with Synaptic that I have installed:
network-manager
network-manager-gnome
network-manager-openvpn
network-manager-openvpn-gnome
network-manager-pptp
network-managerpptp-gnome

There is no network-manager icon in the system tray, nor can I find a network-manager application when searching in the dashboard.

My understanding of networks is quite limited, so I may just be doing something silly, so any advice will be helpful, either to resolve the current problem or to aid my understanding of networking.

Thank you for any help offered.

See my post here, this should help :

[URL="https://ubuntuforums.org/showthread.php?t=2355229"]https://ubuntuforums.org/showthread.php?t=2355229

**sudo apt-get install network-manager-openvpn network-manager-openvpn-gnome**
**y**
**sudo systemctl restart network-manager**
  [/URL]

---

### Post by BrianV on 2017-03-11
> **ganesh66x said:**
> See my post here, this should help :

[URL="https://ubuntuforums.org/showthread.php?t=2355229"]https://ubuntuforums.org/showthread.php?t=2355229

**sudo apt-get install network-manager-openvpn network-manager-openvpn-gnome**
**y**
**sudo systemctl restart network-manager**
  [/URL]

I had a look at your other post and then tried the commands you list above. The network-manager-openvpn and -openvpn-gnome are most current versions. Restart network-manager made no apparent difference. I cannot find any network-manager icon or GUI.

I had icons displayed for System Monitor, Dropbox, In Sync, and HPLib. Quitting each of them, then restarting network-manager makes no difference: I still see no network-manager.

Your IPVanish set up procedure looks good, if I can get to network-manager.

---

