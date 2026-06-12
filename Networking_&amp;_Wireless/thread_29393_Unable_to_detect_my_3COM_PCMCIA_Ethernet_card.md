---
title: "Unable to detect my 3COM PCMCIA Ethernet card"
date: 2005-04-24
forum: Networking &amp; Wireless
---

### Post by gugus on 2005-04-24
Hello all,
I have a problem for using my 3com Pcmcia ethernet card "3cxfe575bt".
I tested this card under Damn Small Linux, and it works.

Here is the output:

**sudo lspci -v**

0000:03:00.0 Ethernet controller: 3Com Corporation: Unknown device 0000 (rev 01)        Flags: medium devsel, IRQ 11
        I/O ports at 4000 [disabled] [size=128]
        Memory at 20800000 (32-bit, non-prefetchable) [disabled] [size=128]
        Memory at 20800080 (32-bit, non-prefetchable) [disabled] [size=128]
        I/O ports at <ignored> [disabled]
        I/O ports at <ignored> [disabled]
        I/O ports at <ignored> [disabled]
        Expansion ROM at 20400000 [disabled] [size=128K]
        Capabilities: [50] Power Management version 1

**sudo cardctl status**: 
Socket 0:
  3.3V CardBus card
  function 0: [ready]
Socket 1:
  no card

**sudo cardctl ident:**
Socket 0:
  no product info available
Socket 1:
  no product info available

**sudo cardctl info:**
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

What can I do ?

Thanks,

---

### Post by exzantia on 2005-04-26
I am also having the same problem with my 3com card... model 3crshpw196

I would really appricate any thoughs anyone has on solving this problem...

---

### Post by gugus on 2005-04-30
This CardBus Ethernet card use the PCMCIA module "3c575_cb".
But when I use this command:
modprobe 3c575_cb

I have this error message:
FATAL: Module 3c575_cb not found.

How could I install this missing module ?

---

### Post by gugus on 2005-05-24
After some test this card seem to be not compatible with my IBM thinkpad T41:
I remove the Damn Small Linux on my old thinkpad 380X and replace it with Ubuntu.. And Ubuntu works perfectly with this card on the thinkpad 380x.

---

### Post by deorca on 2005-05-24
[QUOTE=exzantia]I am also having the same problem with my 3com card... model 3crshpw196

I would really appricate any thoughs anyone has on solving this problem...[/QUOTE]

I have same card (3CRSHPW196) and same problem. Am now discovering levels of frustration I never knew existed.

---

