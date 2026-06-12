---
title: "Atheros 5006eg problem on acer aspire, ubuntu 7.10"
date: 2008-03-29
forum: Networking &amp; Wireless
---

### Post by JaredsaNOOB on 2008-03-29
I know a lot of people ask about this card, but no instructions have worked. I had the card working for about a week a few weeks ago, so i tried the same how to several times, as well as many other instructions, I've googled it at least 50 times, and I think maybe I have a specific problem. when I do lspci, my wireless card comes up as 03:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01) in case that helps.

---

### Post by em3raldxiii on 2008-03-29
I have much the same issue, and I haven't resolved the issue yet (because I am at work, 300km away), but apparently in some cases, your 6EG is being incorrectly reported - you may actually have the 7EG.  With that in mind, you may want to try installing a different driver snapshot.  Are you using the madwifi drivers?

---

### Post by kutjara on 2008-03-30
> **JaredsaNOOB said:**
> I know a lot of people ask about this card, but no instructions have worked. I had the card working for about a week a few weeks ago, so i tried the same how to several times, as well as many other instructions, I've googled it at least 50 times, and I think maybe I have a specific problem. when I do lspci, my wireless card comes up as 03:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01) in case that helps.

The Atheros card on my Acer notebook flaked out after several days of working fine, forcing me to re-modprobe for it every time I booted the machine. Once I'd manually modprobed for it, the card came up, but wouldn't connect to anything (even though it could see all the networks in range).

My solution was to insert a line about the card into the /etc/modules file. I typed:

sudo gedit /etc/modules

and added the following on a new line at the end of whatever text was already present:

ath-pci

I then saved the modules file and rebooted. When the machine restarted, the wireless card was up and running, with no problems connecting to any available networks. I haven't had any problems since then.

Hope it works for you.

---

