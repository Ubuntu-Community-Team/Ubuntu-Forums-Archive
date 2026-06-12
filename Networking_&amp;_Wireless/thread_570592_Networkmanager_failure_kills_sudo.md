---
title: "Networkmanager failure kills sudo"
date: 2007-10-08
forum: Networking &amp; Wireless
---

### Post by tribaal on 2007-10-08
Hi all,

Something weird is happening to my otherwise flawless feisty laptop:

My school uses a WPA wireless network (with TLS/TKIP certificates based authentification). The handshake and connection itself work fine, however sometimes (could not isolate any specific triggers), NetworkManager crashes (the applet shows "connected to unknown" with empty signal bars).

I wouldn't mind it crashing, as a simple "sudo /etc/init.d/networking restart" would probably help it restart, but it breaks sudo (!!) when it crashes! So I cannot even turn the computer off properly, and have to hard reboot it (pulling the batteries out basically)...

My wildest guess is that it somehow crashes when roaming from one access point to the other, but unfortunately I couldn't really test this, nor find a way to disable access point roaming...

Since some googling couldn't find a related bug, maybe someone has an idea?

Thanks a lot for your help!

- Trib'

Specs:

Ubuntu Feisty amd64

NetworkManager 0.6.4

HP Pavillon dv6000 core2  T7200 - 2Gb RAM

Relevant lspci:
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

Relevant lsmod:
ipw3945               128544  1

---

