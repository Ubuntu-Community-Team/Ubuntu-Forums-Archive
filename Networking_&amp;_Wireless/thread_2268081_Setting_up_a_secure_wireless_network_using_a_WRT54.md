---
title: "Setting up a secure wireless network using a WRT54GL router and dd-wrt"
date: 2015-03-06
forum: Networking &amp; Wireless
---

### Post by cscj01 on 2015-03-06
I am running Ubuntu 14.04.1 x64 with a wired NFS home network using a WRT54GL Version 1.1 router with dd-wrt version 24-sp2 (08/12/10) std. I recently purchased a Samsung Tab 4 and decided to set up security for my wireless network. I used the instructions here: [http://www.tomschaefer.org/how-to-setup-a-secure-wireless-network-dd-wrt/]("http://www.tomschaefer.org/how-to-setup-a-secure-wireless-network-dd-wrt/"). However, when I look at the Wi-Fi networks available from my Tab 4, mine always shows as Open while most of the others show as Secure. I have secured the Wireless part in the router per the instructions referenced above.  Do I have to setup a separate wireless network in Ubuntut in addition to my existing wired network?  If so, the only option I get when I try to add a network is VPN.  What am I doing wrong?

---

### Post by TheFu on 2015-03-06
Not broadcasting the SSID doesn't provide any more real security and could make the network slower.  It is similar to MAC filtering - keeps honest people honest, but doesn't add to security in any real way.
[http://blog.jdpfu.com/pages/wifi-security](http://blog.jdpfu.com/pages/wifi-security) - my checklist for wifi router security.

---

### Post by cscj01 on 2015-03-10
It seems my issue of the network showing as > Openwas because I had not re-booted the router.  After re-booting, the network requires login credentials.  Ah, sometimes the things not mentioned are somewhat like > The Road Not Taken.

---

### Post by cscj01 on 2015-03-10
It seems my issue of the network showing as > Openwas because I had not re-booted the router.  After re-booting, the network requires login credentials.  Ah, sometimes the things not mentioned are somewhat like > The Road Not Taken.

---

### Post by cscj01 on 2015-03-10
It seems my issue of the network showing as > Openwas because I had not re-booted the router.  After re-booting, the network requires login credentials.  Ah, sometimes the things not mentioned are somewhat like > The Road Not Taken.
Sorry about the multiple posts.  I kept getting Server Time Out messages, and when I paged back to the thread, only my original response showed, and it was not posted.

---

