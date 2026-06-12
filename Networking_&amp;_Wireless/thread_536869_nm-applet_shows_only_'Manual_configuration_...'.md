---
title: "nm-applet shows only 'Manual configuration ...'"
date: 2007-08-28
forum: Networking &amp; Wireless
---

### Post by misja on 2007-08-28
I have installed Feisty on my laptop a couple of weeks ago. I then tried to connect to my wireless network at home which has WPA security.
At first I couldn't get it to work although my network was found because there was no option in the network manager to configure my WPA settings, only WEP and such.
Then I searched the internet and found how to configure the /etc/network/interfaces file, install wpa_supplicant etc. and now WPA at my home works.

I still don't get to see any WPA option in my network manager but until recently I thought this was the only way to do it under Feisty.
However, yesterday I spoke to a colleague who has the exact same laptop. He switched to Feisty a couple of weeks ago too, just like me. He was surprised to hear of my problems because he never had any. He showed that on his laptop the network manager applet had a list of available wirelss networks, and that their signal strengths were shown as well. If you clicked on their properties you could even specify your WPA settings .. :confused:

So for the last 2 days I have been trying to get my nm-applet to behave the same as his. But whatever I do, it just behaves like it has always done: When I left-clck it it shows only 2 options, 'Wired network' and 'Manual configuration ..'. When I click 'manual configuration' I doesn't show WPA anywhere. :(
I commented out my wireless settings in the interfaces file but nothing changed. I tried installing the latest gnome-network-manager and network-manager but it says I already have them.

So how can this be? What should I do?

Any help greatly appreciated,
Misja

---

### Post by spd106 on 2007-08-28
The short answer is open System -> Admin -> Network, select your wireless interface and check the roaming mode box in the top left. 

This will activate Network Manager, which it sounds like you want. The only problem with this is that you can't set specific network settings, it only supports DHCP.

As you have found, the static mode utility (network-admin) doesn't support WPA yet, that's coming up in Gnome 2.20 and will be integrated into Ubuntu 7.10 (Gutsy). So until then you have to use roaming mode (network manager) or edit the interfaces file by hand.

---

