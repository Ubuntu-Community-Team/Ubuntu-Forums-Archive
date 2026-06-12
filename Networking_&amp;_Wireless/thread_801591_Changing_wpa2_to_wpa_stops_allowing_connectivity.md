---
title: "Changing wpa2 to wpa stops allowing connectivity"
date: 2008-05-20
forum: Networking &amp; Wireless
---

### Post by disasm on 2008-05-20
I have a linksys wrt54gl router running openwrt. I had it using wpa2 passkey, but a friend came over that didn't support wpa2, so I changed it to wpa1.

Then my ubuntu wireless laptop was unable to connect. Network Manager has the spinning circle thing. I can manually set the connection and it works fine. I also have multiple other networks I connect to that work fine.

Any ideas as to how to reset all the NetworkManager data?

I've tried apt-get --purge remove network-manager network-manager-gnome wpasupplicant, and adding them back to no avail. Where does network manager and wpasupplicant store it's network keys?

Sam

---

