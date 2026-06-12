---
title: "Assigning an &quot;Unknown Card&quot; to axnet_cs"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by fishcake007 on 2007-04-21
Hi
I need to assign my Japanese Brand network card to the axnet_cs driver. I don`t have a clue how to do this in Feisty as I was previously using cardmgr in Dapper and it was ages ago since I configured the card. I remember simply adding the card details to an config file and simply starting cardmgr. How do I do this in Feisty without installing cardmgr.

If I run pccardctl ident then the card is identified as 

Socket 0:
product info: "IO DATA", "ETXPCM","3.0","AX88190"
manfid: 0x0149, 0xclab
function: 6 

I know this card runs under axnet_cs driver , how on earth do I assign it to use this driver?

Any help would be most appreciated.

---

### Post by fishcake007 on 2007-04-21
Solution.. don't waste your time trying... Install pcmcia-cs and the the thing will work straight away.. strange...

---

