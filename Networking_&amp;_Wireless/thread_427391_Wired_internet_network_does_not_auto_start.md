---
title: "Wired internet network does not auto start"
date: 2007-04-29
forum: Networking &amp; Wireless
---

### Post by rush_ad on 2007-04-29
i am running ubuntu 7.04, connected to wired internet network using Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 31).

problem is that everytime i reboot (not many anyway), i have to manually start internet connection. what i mean is that after every reboot, i have to click on NetworkManager Applet 0.6.4 and select "Wired Network" to enable internet. once i do that (just click on Wired Network" internet works fine.

how can i make it so that internet is automatically connected?

---

### Post by Red Knuckles on 2007-04-29
This worked for me in Linux Mint Bianca KDE. The KNetworkManager icon still pops up though I'd like to figure out how to stop that. Or I'll just hide it in system tray. Here's the instructions:

Disabling network manager in your gnome session will not work as that is just the 'notification area' for the network-manager service. To disable network-manager, either uninstall it (which will break ubuntu-desktop package) or do this:

Stop network manager...

sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
sudo /etc/dbus-1/event.d/25NetworkManager stop

Create two files with only the word 'exit' in them. These files are:

/etc/default/NetworkManager
/etc/default/NetworkManagerDispatcher

Reboot.

I know he's talking about Gnome but it worked for me in KDE. 
:lolflag: :guitar:

---

