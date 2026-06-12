---
title: "Can't connect  after USB Wireless Card's Driver Installed"
date: 2007-10-08
forum: Networking &amp; Wireless
---

### Post by flypeyton on 2007-10-08
I just used ndiswrapper to install the driver for the netgear MA111 USB wireless card. In the terminal, I ran: "ndiswrapper -l" and got the message: "netma111: driver installed  device(0846:4110) present (alternate driver: prism2_usb) But in **System->Administration->Windows Wireless Drivers**, in the "Currently Installed Windows Drivers" column, there was an icon with the sentence "Hardware present:No". This sounded contradict. Anyway, in the network setting, I can see the wireless card shows up as " Wired connection (wlan0)" (not Wireless connection)and the network card shows up as "Wired connection (eth0)". I am not sure whether this is right.

 So I chose to connect to a wireless network which I once was using in WinXP system by clicking on the network icon on the panel(NetworkManager Applet 0.6.4) and input the wireless network's name. And chose "None" for Wireless Security since the network had no password needed. But it attempted but could never connect to the wireless network. In the "Connection Information", a doubtful part:
Interface: Wireless Ethernet(wlan0)
Speed: Unknown
Driver: prism2_usb (instead of the windows driver I installed?!)
IP Address: 0.0.0.0
Broadcast Address: 0.0.0.0

I also looked into the network configuration. Instead of the automatic configuration, I tried "enable roaming" and didn't work out either. Could it be due to the weakness of the wireless signal? The wireless signal is not strong in my apartment. But it once could connect to internet with WinXP system. After trying 5 hours in it, really need help from you guys!

---

### Post by tormod on 2007-10-17
You could try linux-wlan-ng (and prism2_usb) instead of ndiswrapper if you have a prism2 USB card.

---

