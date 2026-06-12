---
title: "Wireless card wond configure"
date: 2006-10-28
forum: Networking &amp; Wireless
---

### Post by TTL on 2006-10-28
Hello,
I am trying to get a Z-com XI-325 wireless card working.
However, every time I insert the card I get in dmesg:
```

[17181184.852000] pccard: PCMCIA card inserted into slot 1
[17181184.852000] pcmcia: registering new device pcmcia1.0
[17181184.852000] hostap_cs: setting Vcc=33 (constant)
[17181184.852000] hostap_cs: CS_EVENT_CARD_INSERTION
[17181184.852000] hostap_cs: setting Vcc=50 (from config)
[17181184.852000] Checking CFTABLE_ENTRY 0x01 (default 0x01)
[17181184.852000]   Vcc mismatch - skipping this entry
[17181184.852000] 1.0: GetNextTuple: No more items
[17181184.852000] prism2_config() failed


```

pccardctl info returns:
```

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255
PRODID_1=""
PRODID_2="IEEE 802.11 Wireless LAN/PC Card"
PRODID_3=""
PRODID_4=""
MANFID=d601,0005
FUNCID=6

```

pccardctl status returns:
```

Socket 0:
  no card
Socket 1:
  5.0V 16-bit PC Card
  Subdevice 0 (function 0) bound to driver "hostap_cs"

```

I am using Kubuntu 6.06

unamr -r returns:
```

2.6.15-26-386

```

The wireless card is a PCMCIA one. The PCMCIA socket uses the RL5c476 II (rev ac) controller.

Has anyone an idea?

Moreover I am a little confused. According to some sites I should use the orinoco driver and according to others I should use the drivers von wlan-ng with this card.

Thanks in advanced.

---

### Post by TTL on 2006-10-28
Looks like I have solved the problem.
First I prevented the orinoco, orinoco_cs and hermes modules from loading by renaming them.
Then I loaded the module hostap_cs with the option ignore_cis_vcc=1
before inserting the card.
After inserting the card I got a wlan0 device :-)

---

