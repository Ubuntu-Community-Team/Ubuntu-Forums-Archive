---
title: "Wireless card unable to connect some times"
date: 2007-06-25
forum: Networking &amp; Wireless
---

### Post by Trynemjoel on 2007-06-25
Hi

I have a little problem concirning my Laptop computer's wireless card. An Intel Pro Wireless 2200BG.

Some times when booted up, it will be unable to connect to a wireless connection, it will quite simply stop trying to receive IP and such. I then  right click the Network Connection applet in the corner of the taskbar, selecting the connection I want to connect to, for a split second it turns in to the "connecting..." icon, 2 dots with some blue thing running through, then straight back to the 2 computers and the X indicating no connection.

This can usually be all fixed by a simple reboot of the computer, then it will connect just fine, but at some boots this is not the case, and i will have to reboot, costing me some time and a bit of frustration.

Does anybody here have experience with this problem and/or have a fix for it?

Please respond if you can help or need more information to do so.

---

### Post by roar on 2007-06-25
I had the same behaviour on my system, which has the 2200 bg, when network was encrypted wpa. With wep, things are stabile. What encryption are you using?

---

### Post by walkerk on 2007-06-25
i don't have the same wlan nic but i was having similar problems while using network-manager and wpa..

i uninstalled network-manager and switched to wifi-radar using wpa_supplicant. worked great..

just recently i switched to wicd. great connection and easy wpa1/2 etc

---

### Post by Trynemjoel on 2007-06-25
Well we're using MAC-filter here at home, no encryption. At Uni there is an open network, but with login for usage of the network

---

### Post by floke on 2007-06-25
sudo apt-get install wifi-radar

Sometimes this won't work if network-manager craplet is trying to connect - so you might have to disable wireless in network manager first

---

### Post by Trynemjoel on 2007-06-25
Does wifi-radar have an applet similar to that of network-manager or will i have to start it up from the commandline to see signal, networks and connect to them?

---

