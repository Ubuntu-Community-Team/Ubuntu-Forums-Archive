---
title: "Wifi-Radar and hidden networks"
date: 2007-02-15
forum: Networking &amp; Wireless
---

### Post by AusIV4 on 2007-02-15
I have two laptops. The first has been running Kubuntu for about 3 months now. On this computer, I use wifi-radar to connect to my preferred networks on startup. All of the networks I generally connect to have hidden SSIDs, but on my older computer, wifi-radar connects just fine.

On Monday, I got a new System76 Gazelle Value, and I have been trying to get wifi-radar to work the same way. On my Gazelle, however, wifi-radar can't find hidden networks in daemon mode. It connects to them just fine if I use the graphical interface, but the daemonized mode acts like it can't find the hidden networks.

When I run iwlist eth1 scan, it lists the network as hidden (I identify it by MAC address), so I know it's finding a signal, but it's not connecting.

Anyone have any idea why it would work on one computer but not another? (I even ran a diff to make sure the wifi-radar files were identical).

---

### Post by AusIV4 on 2007-02-15
On a whim, I decided to uninstall wifi-radar from the first laptop and see what happened. At this point, I wasn't too surprised when my laptop automatically connected to the wireless network. This means wifi-radar wasn't responsible for the connections in the first place.

The thing is, I have no idea what I have installed that is automatically connecting me to my wifi. Any ideas on how I might be able to track that?

---

