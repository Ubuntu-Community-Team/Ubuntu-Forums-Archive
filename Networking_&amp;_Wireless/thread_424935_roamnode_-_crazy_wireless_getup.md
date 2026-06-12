---
title: "roamnode - crazy wireless getup"
date: 2007-04-27
forum: Networking &amp; Wireless
---

### Post by heng on 2007-04-27
I've just installed Feisty onto a laptop and, hardware wise everything appears to be functional. The wireless card is the intel 2200 and shows all the SSIDs i should be able to see.

The problem is that the method for connecting to the university network (which uses an almost homebrew system called roamnode) is strange and its not immediately obvious to me how to get it working. Essentially one sets up a PPPoE connection over the wireless link, and then opens a PPTP VPN tunnel.

Under windows, this involves letting the wireless widget try to connect to the relevant SSID, which it sort of does but only acquires a link-local IP (and complains that I may have limited or no connectivity). It seems to me that this is the standard windows way. Now I create a PPPoE link with a username and password, and then I open a PPTP connection to the relevant server, which prompts for a password. Now it works.

Now I wish to do this under Fiesty. Having read around a bit, it seems that I should be able to get a link-local ip address by setting the configuration option in networkmanager to be zeroconf. Now, the question is, should I be able to open the PPPoE connection using pppoeconf at this stage? And once this is done, can I use the PPTP VPN plugin within NetworkManager to connect to the VPN? or do I need to use an alternative VPN widget?

Also, if i fail to get network manager to acquire a link-local address, can I assign one manually/use another tool?

The problem is, obviously, that under ubuntu I don't have access to the network, and hence have some problems looking up info. Its stupid non-standard weird ways of doing things that cause problems.

I'd appreciate any advice. Thanks!

---

### Post by heng on 2007-04-27
Having tried out the changing of the wireless card properties to zeroconf, I can say that it changes nothing. Networkmanager still gives up and returns no network address.

Incidentally, I can't seem to make the zeroconf setting persistent. If I open up the wireless card settings again, it has resorted back to "roaming" mode.

---

