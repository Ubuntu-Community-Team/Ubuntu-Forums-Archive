---
title: "Internet not stable"
date: 2007-10-24
forum: Networking &amp; Wireless
---

### Post by mk04 on 2007-10-24
Made a fresh install with Ubuntu Gutsy. I have a WG511v1 PC Card for my Laptop. I got NDISWrapper installed with the correct drivers. The problem I'm having is my Internet is not stable. Sometimes it goes fast, sometimes its slow, and sometimes it just doesn't work at all. Any ideas? 

BTW, I do have a separate partition of Ubuntu Edgy and Windows XP, and the Internet work constantly, no problems (same card).

---

### Post by tl3000 on 2007-10-24
There are still problems with the native Prism54 drivers in Gutsy for the WG511v1.  However, Network Manager is at least working now  The card is constantly active with the native drivers--the amber LED flashes wildly--even when the connection should be at idle with no activity.  However, these extraneous transmissions do not seem to affect my connection's performance too much.  Anyway, I took the following steps to use the original Netgear Windows drivers that came with the card.

Steps taken to enable an 802.11g WPA wireless connection via WG511v1 on Ubuntu Gutsy:
[probably not the most efficient or proper approach but it worked for me]

-- Install NDISwrapper (ndiswrapper-utils-1.9 & ndiswrapper-common packages)
via Synaptic Package Manager

-- Disable the native Prism54 drivers:

sudo modprobe -r prism54
sudo modprobe -r p54pci
sudo modprobe -r p54common
sudo gedit /etc/modprobe.d/blacklist

add the following 3 lines to the end and save:

blacklist prism54
blacklist p54pci
blacklist p54common

-- Install the WG511v1 Windows driver:
[download or copy the netwg511.inf & WG511ICB.sys files to the Home Folder]

sudo ndiswrapper-1.9 -i netwg511.inf
sudo modprobe ndiswrapper
sudo ndiswrapper -m
sudo gedit /etc/modules

add the following line to the end and save:

ndiswrapper

---

