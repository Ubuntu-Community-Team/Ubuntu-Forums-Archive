---
title: "Reinstalling my wireless NIC"
date: 2007-05-05
forum: Networking &amp; Wireless
---

### Post by pwykersotz on 2007-05-05
I recently bought a Netgear WPN824 wireless router and installed an old AT&T 6500G wireless card with and Atheros chipset in Feisty.  The two worked decently together, but I couldn't take full advantage of my router's capabilities.  Thus, I bought the WPN311NA NIC to go with it and replaced the AT&T card.

I immediately noticed that I had absolutely no change in my wireless signal.  Upon inspection, I noticed that KNetworkManager identifies my card as an Atheros Communications, INC. AR5212 802.11abg NIC.

Seeing as how this isn't my WPN card and I haven't read anywhere that Kubuntu auto-detects your NIC on swap and reinstalls the proper drivers, I assume I have to do it manually.  The trouble is, I don't know how.

I know this card is supported natively in Feisty, can anyone give me a hand?

---

### Post by chili555 on 2007-05-05
> I haven't read anywhere that Kubuntu auto-detects your NIC on swap and reinstalls the proper driversNow you *have* read it; it does. However, as you may read on these forums, it doesn't always do a perfect job, but no operating system is perfect.

In this case, I think Kubuntu is doing it's job properly. Here: [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear) it states the WPN311 uses the Atheros 5212 chipset.

I notice this card has 802.11g capabilities. When you are close to the router, does iwconfig show a bit rate at or close to 54Mb/s? If not, you might open a terminal and do:```
sudo iwconfig ath0 rate auto
```

---

