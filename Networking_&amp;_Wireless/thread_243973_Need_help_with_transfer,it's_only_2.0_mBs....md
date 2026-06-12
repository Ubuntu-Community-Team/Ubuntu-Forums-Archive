---
title: "Need help with transfer,it's only 2.0 mB/s..."
date: 2006-08-25
forum: Networking &amp; Wireless
---

### Post by m4r3k on 2006-08-25
can somebody help me to configure the d-link (atheros) pci card to transfer more then only 2.0 mB/s??

my txpower is 13dbm,but someone say'd that i must iwconfig ath0 commit,but i get the massage that commit is a unknow wireless command??


help pls
thnx

---

### Post by AzraelUK on 2006-08-26
[FONT="Courier New"]sudo iwconfig XXXX rate XXm[/FONT]
so, for example, i would put sudo iwconfig eth0 rate 11M
hope this helps!

---

