---
title: "Netgear WG511T not reconnecting after resuming from standby"
date: 2007-12-29
forum: Networking &amp; Wireless
---

### Post by fcosentino on 2007-12-29
Hi folks,

I installed Ubuntu 7.10 on a Sony Vaio PCG-R505CT, which is using a PCMCIA Netgear WG511T (Atheros chipset).

I installed the MadWifi latest driver and wpa_supplicant. The network works fine, I can browse using Firefox.

The issue is when resuming from standby - it does not reconnect automatically. Also,same issue when rebooting. What do I do?

---

### Post by fcosentino on 2007-12-30
I am completely lost on this. I tried the following:

1. Compiled and installed latest versions of madwifi and wpa_supplicant;
2. Uninstalled network manager and installed Wicd;
3. Tried various workarounds on this forum - no change.

In essence, I want to understand if it is normal for Ubuntu to behave like this. After rebooting / resuming from hibernate / waking up after sleep mode and so forth, the network disconnects ans it does not reconnect automatically.

Restarting the entire networking (or, in Wicd, disconnecting / reconnecting a couple of times) restores connectivity, but this is ridiculous, especially for a card that is supposed to be fully supported.

If that's the case, Ubuntu has a long, long way before being able to challenge Windows seriously. It takes 5 seconds to reconnect under Windows XP - 2-3 minutes of fiddling around in Ubuntu.

---

### Post by fcosentino on 2008-01-01
I installed Xubuntu - and the problems disappeared.

Performances of networking are still poor, however it reconnects automatically.

---

