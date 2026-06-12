---
title: "network menu and adapter presence"
date: 2017-10-07
forum: Networking &amp; Wireless
---

### Post by Nick Levinson on 2017-10-07
This is mainly at one location and with one network. I have a USB Wi-Fi adapter (NIC) that is Linux-compatible, including with Ubuntu 16.04.2 desktop amd64 on HDD, and it works in various locations and with various network. The NIC is Trendnet via ThinkPenguin. For this network, I plug the NIC in, wait for its LED to light up (usually it blinks, too), and wait a little longer until Ubuntu has had the normal time for connecting to a network. No connection happens. Seeing only an empty triangle icon on the top panel in Gnome, I open that icon's menu. Enable Wi-Fi is checkmarked but there's no list of networks. I can get around that by selecting Connect to Hidden Wi-Fi Network even though the network I want is not hidden, but that menu item is not visible, not even as dimmed. So, instead, I have to repeatedly click the VPN Connections menu item, maybe 20 times, because the menu item for hidden networks will likely turn up in that spot in the menu for a small fraction of a second a few times, so one of my dozens of clicks will accidentally select it, which is what I want. Then I get a dialog where I select the network I want (title bar "Connect to Hidden Wi-Fi Network", body ". . ."/"Enter the name and security details of the hidden Wi-Fi network . . . ."/"Connection: . . ."/"Network name: . . ."/"Wi-Fi security: . . .", buttons "Cancel" & "Connect") (the network I usually use here doesn't need a password), it selects the device and the  network connection entry (I have one for every device/network pair and I've used them before) and I click the Connect button. Then I get an alert that no device was found (title bar "Connection failure", body "Failed to activate connection"/"(3) Device not found", & only button "Close"). (One variation is when a connection was established without that dialog and I used the dialog anyway, immediately getting the "(3) Device not found" alert despite already having a network coonnection.) Then, in the usual case, after the alert, I wait and the computer connects to the network I selected ("Connection Established"/"You are now connected to the Wi-Fi network '. . . [network name]'"). Then, if I look, the panel menu lists several networks in addition to the one I'm on. The connection is generally stable.

1. How do I get the menu to list the non-hidden networks right away and before I click on the menu?

2. How do I get the menu item for hidden networks to appear in the menu and stay up steadily so a single click is enough to select it?

3. How do I get the system to recognize that the adapter is present, not just eventually but by the time I'm trying to select a network?

---

