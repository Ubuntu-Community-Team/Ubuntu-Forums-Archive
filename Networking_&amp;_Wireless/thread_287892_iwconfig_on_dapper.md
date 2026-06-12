---
title: "iwconfig on dapper"
date: 2006-10-29
forum: Networking &amp; Wireless
---

### Post by livestockPimp on 2006-10-29
hi,
i have been trying to set up my wifi on my laptop, i am running dapper ubuntu with a linksys wifi card and when i use iwconfig to configure my key to restricted my machine locks up... i cant sem to work it out, iwlist can see my ap and everything else seems fine.. any ideas will be appreciated..
thanks.

---

### Post by livestockPimp on 2006-10-29
i also have the realtek chipset if that helps...

---

### Post by Zlika on 2006-10-29
I have got exactly the same problem.
I've got a Realtek RTL8187, and when I type: "sudo iwconfig wlan0 key restricted *****" => the computer hangs.

If I have in /etc/network/interfaces :
wireless-key restricted *****

=> kernel panic at startup.

Help!!!

---

