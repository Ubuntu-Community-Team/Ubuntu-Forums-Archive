---
title: "Throttling: Tether Ubuntu Laptop to T-Mobile Samsung Galaxy Phone (throttle)"
date: 2024-02-01
forum: Networking &amp; Wireless
---

### Post by webmanoffesto on 2024-02-01
Update: I'm making progress. I have a connection. My laptop appears to be connected to my phone via NetShare. But when I go to my laptop's browser I still don't have internet. What could the problem be?

Ubuntu Laptop
In "Settings / WiFI" Under Visible Networks I see "Direct-NS-HotTubHotSpot". I selected it and it says "connected"
- Network / Network Proxy
- Manual 192.168.49.1 ... 8282

Android Phone
In NetShare I see "Connected Devices" 192.168.49.36. I guess that's my laptop.

--------------
I want to avoid T-Mobile throttling of tethered devices. I'm trying to use NetShare on a Samsung Galaxy to tether my Ubuntu 22 laptop to it. I think the problem I've run into now is that either NetShare doesn't have an Ubuntu client or I just don't know the correct way to connect my laptop to my phone. I'm using a USB cable. How can I do this?

When I plug in the USB cable I get "Allow Access to Phone Data? Y or N". Should I click "Yes"?
Should I have Data Transfer

In the notifications at the top of my monitor, under the WiFi I see "Galaxy S21 5G". I click "Connect to Network" and I get "Activation of Network Failed". 
When I go to "Settings / Network" I see "Galaxy S21 5G". When I move the toggle to "on", it moves itself back to "off".

On my phone sometimes I get a message "Network Name Exceeds 32 Bytes". Is that relevant to this problem? The network name is "Hotspot" and Netshare says "Network name will be preceeded by 'Direct-NS' automatically for system requirements. So it should be "Direct-NS Hotspot". In Ubuntu I see the network "Galaxy S21 5G".

NetShare provides connection instructions for all OS's except Linux. But basically they say to use a proxy server for the LAN and enter
Server: 192.168.49.1
Port: 8282
Do I enter those details under "VPN Network Proxy" or in the settings for "Other Devices / Galaxy S21 5G" where the tabs are General, BlueTooth, Proxy, IPV4, and IPV6.

Background:

[COLOR=#141618][FONT=Lato]I have a locked T-Mobile Galaxy S21 5G (SM-G991U)[/FONT][/COLOR]
[COLOR=#141618][FONT=Lato]I want to tether my Ubuntu laptop to my phone and avoid T-Mobile's crazy throttling? They give me download "speeds" of 0.05 Mbit/s and 0.1 Mbit/s.[/FONT][/COLOR]

[COLOR=#141618][FONT=Lato]Recommended solutions seem to be:[/FONT][/COLOR]
[COLOR=#141618][FONT=Lato]- [/FONT][/COLOR][NetShare]("https://play.google.com/store/apps/details?id=kha.prog.mikrotik")[COLOR=#141618][FONT=Lato] Android app, $9 for full version, or[/FONT][/COLOR]
[COLOR=#141618][FONT=Lato]- [/FONT][/COLOR][FoxFi]("https://play.google.com/store/apps/details?id=com.foxfi.key")[COLOR=#141618][FONT=Lato] ($9 for full version) with PDANet.[/FONT][/COLOR]

[COLOR=#141618][FONT=Lato]I put NetShare on my phone.[/FONT][/COLOR]
[COLOR=#141618][FONT=Lato]But I don't have it working yet.[/FONT][/COLOR]
[COLOR=#141618][FONT=Lato]I put NetShare on my phone and I'm trying to connect my laptop to it, via USB or BlueTooth. But It says "Please open NetShare+ and tap on 'WPS' in the phone you want it to connect to." and just hangs there with a spinning icon.[/FONT][/COLOR]

[COLOR=#141618][FONT=Lato]Will this work with an Ubuntu laptop. Netshare's "Help: Connection instructions" list every OS except Linux.[/FONT][/COLOR]

[COLOR=#141618][FONT=Lato]The data service on the phone is fine, but occasionally I need to use my laptop where the provided WiFi is not an option.[/FONT][/COLOR]

[COLOR=#141618][FONT=Lato]In some forums people say that just using a VPN will avoid the trottling. That is not what my tests revealed.[/FONT][/COLOR]

[COLOR=#141618][FONT=Lato]Tests Run[/FONT][/COLOR]
[COLOR=#141618][FONT=Lato]Galaxy Phone DL 419.00 UL 17.90 No VPN Phone Speedtest App[/FONT][/COLOR]
[COLOR=#141618][FONT=Lato]Phone using PIA VPN DL 304.00 UL 21.10 PIA VPN, NY Phone Speedtest App[/FONT][/COLOR]
[COLOR=#141618][FONT=Lato]Laptop, Bluetooth tethered to phone: DL 0.05 UL 0.54 PIA VPN, NY Laptop, Bluetooth tether to phone using PIA VPN NY, phone has "mobile hotspot" and "Bluetooth tether" turned on.[/FONT][/COLOR]
[COLOR=#141618][FONT=Lato]Laptop, USB tether to phone DL 0.10 UL 0.46 PIA VPN, NY Laptop, USB tether to phone using PIA VPN NY, phone has "USB tethering" turned on.[/FONT][/COLOR]

---

