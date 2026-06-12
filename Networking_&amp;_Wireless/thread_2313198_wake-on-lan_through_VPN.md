---
title: "wake-on-lan through VPN"
date: 2016-02-10
forum: Networking &amp; Wireless
---

### Post by flucoe2 on 2016-02-10
I want to be able to turn on the desktop that I have in my office, from my house. The issue is, I need to do this through VPN to get into my office's network. If I leave the desktop on, I can ssh to it from my laptop just fine (as long as I'm connected via VPN). However, the VPN, at least in its default settings, does not allow me to do "wake-on-lan". Any suggestions on how to deal with this? I could always leave my desktop running in the office, but I'm looking for alternatives that would not require to do that. Thanks.

---

### Post by alexandari on 2016-02-12
How are you trying to use wake on lan? Which tool? What VPN is that? Is WOL enabled in the BIOS?

---

### Post by flucoe2 on 2016-02-12
It is the Cisco vpn. WOL is enabled in the BIOS. I am able to use WOL when in the same network (laptop in my office) but not when I'm outside the network. I'm using powerwake and it works perfectly fine within the network but it doesn't when using the VPN. Thanks.

---

