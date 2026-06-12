---
title: "Dell XPS 13 9343 - WiFi connection not persistent across reboots, or longer than ~20m"
date: 2021-04-13
forum: Networking &amp; Wireless
---

### Post by Volume on 2021-04-13
Hi everyone. I decided to put Ubuntu 20.04.2 on my XPS 13 9343. I am able to connect to wifi via the toolbar in the top right of the desktop, by supplying my credentials and SSID. The connection works fine while it is connected.

On rebooting, the wifi does not automatically reconnect to the same SSID, even though when I go back into the toolbar settings, the credentials are saved - I have to manually click connect. This same thing happens after ~20 minutes or so of wifi, it will disconnect, and I have to manually reconnect.

Strangely, I was using an older release of 20.04 on this same laptop without issue. Only when I decided today to install 20.04.2 (from a fresh install, not an upgrade) did I see this problem.

I have attached the output of the wireless-info script as requested in the sticky. I have only changed the wifi.powersave parameter from its default of 3 to 2 (it made no difference that I can tell, even after restarting the network manager service)

[ATTACH]288304[/ATTACH]

---

### Post by Volume on 2021-04-14
Update: I solved this problem by upgrading to 20.10. No idea what has changed. Would be curious if anyone knows what caused it.

---

