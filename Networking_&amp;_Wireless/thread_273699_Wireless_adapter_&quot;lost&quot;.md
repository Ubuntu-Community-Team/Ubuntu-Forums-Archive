---
title: "Wireless adapter &quot;lost&quot;"
date: 2006-10-08
forum: Networking &amp; Wireless
---

### Post by m.musashi on 2006-10-08
I have been trying to get beryl installed on my laptop and in the process of doing some upgrades and installs the wireless adapter "disappeared". It no longer shows up in Network Setting. I was not doing anything related to networking so I am unsure why my wireless adapter would vanish. I did remove and reinstall the nvidia drivers and part of that involved downloading kernel headers and such. I don't remember exactly when it stopped working. It works in Windows fine so I don't think it's hardware related.

Any ideas? How do you reinstall a network adapter? I'm not using ndiswrapper. My card was recognized and set up by default on install.

Thanks.

---

### Post by spd106 on 2006-10-09
If your card uses a driver from the linux-restricted-modules package ie Madwifi for atheros based cards, then this may have been removed. Try re-installing it. Alternatively you could try building the latest driver instead, you may already have most of the required packages: kernel headers, gcc etc. [https://help.ubuntu.com/community/WifiDocs/Driver/Madwifi](https://help.ubuntu.com/community/WifiDocs/Driver/Madwifi)

---

