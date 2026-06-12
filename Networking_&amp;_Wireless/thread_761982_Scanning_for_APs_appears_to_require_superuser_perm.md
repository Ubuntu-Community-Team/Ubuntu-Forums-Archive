---
title: "Scanning for APs appears to require superuser permission in Hardy"
date: 2008-04-21
forum: Networking &amp; Wireless
---

### Post by SGC_Sculler on 2008-04-21
I recently upgraded to Hardy Heron Beta 5 and have had some issues with connecting to a wireless network. At home everything carried on working normally, but at university 'iwlist scan' at the terminal produces no results and setting up the card in Network Manager (having double-checked settings etc.) doesn't make it connect. The drop-down list of networks to connect to in Network Manager is also empty.
However, 'sudo iwlist scan' gives results as normal. Additionally, if I do this immediately before using network manager to try to set up my card then I do see networks in the drop-down box and am able to successfully connect. After connecting it works until the computer is restarted, when I need to repeat this procedure.
Before upgrading I didn't need to use 'sudo iwlist scan' to force the card to look for access points. Is there anything that has changed that might cause this, and how can I change it back?

Please let me know if there's any results of commands you want posted. I believe the chipset is an Intel Pro Wireless 3945.

Thanks,
Ben

---

