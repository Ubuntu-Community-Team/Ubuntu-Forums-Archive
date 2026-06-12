---
title: "Multiple wireless networks problem"
date: 2007-03-09
forum: Networking &amp; Wireless
---

### Post by Mets on 2007-03-09
I recently encountered a small problem on Ubuntu with wireless networking.  I installed Ubuntu at school, and so when I was setting up the networking most of the settings were for that network.  I just plugged in the ethernet adapter and it worked.  I plugged in the wireless card and it recognized it, and I typed in the network name, and it worked.

I just got back to my house though, which has a wireless network but obviously has a different name and different settings, and wifi no longer works!  I went into System-Administration-Networking on the main menu and I see my three adapters - Wifi, ethernet, and modem.  My wifi card is enabled, but the lights on the card aren't on.

I found that if I went to properties on the wireless adapter and changed the settings, including network name, my card lit up and I could  get myself on my home network (and write this post).  However, that is really not a good solution, because now whenever I switch networks I'm dead.  I couldn't get wifi working in the airport, and I'm assuming this is the reason.  On windows, it just recognizes the new network and connects to it.  Is there anyway to make Ubuntu do the same?    I don't have the name of every wireless network I'll ever be on.  I have no idea what the network name at either airport I was at today was, yet from the way I am doing it right now, I have to give the card a specific network name and password, otherwise it won't even turn on.  Can somebody help me simplify this?

---

### Post by andreas64 on 2007-03-09
HI,

if you often connect to different WLAN-Networks, you should use network-manager to handle it.

Andreas

---

### Post by Mets on 2007-03-09
Cool, what's that and how do I make it work?

---

