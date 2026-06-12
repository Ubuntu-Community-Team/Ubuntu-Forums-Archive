---
title: "How can I get my XD card reader to work?"
date: 2010-04-22
forum: New to Ubuntu
---

### Post by ambient007 on 2010-04-22
I have an Acer Aspire 3680 with a cardreader that I often use for my camera's Olympus XD Picture Card.

Since I replaced XP with karmic, nothing happens when I put the card in the slot.

Has anyone got any tips as to how I can get it working? - The Mrs is nagging me to upload some photos to facebook. :)

---

### Post by nothingspecial on 2010-04-22
Different model, but if you insert the card before you boot it might work. It does with my wifes.

---

### Post by ambient007 on 2010-04-22
> **nothingspecial said:**
> Different model, but if you insert the card before you boot it might work. It does with my wifes.

I'll give it a try, but I'm sure I've had it in while booting before.

Be back in a minute ):P

---

### Post by ambient007 on 2010-04-22
no joy :neutral:

---

### Post by nothingspecial on 2010-04-22
Ok,

Take it out then type 

```
tail -f /var/log/messages
```

Keep that terminal open then plug it in again

Does it say anything?

---

### Post by ambient007 on 2010-04-22
So I get this when I type that command:

Apr 22 23:46:46 daniel-laptop kernel: [ 3317.113001] ata1: soft resetting link
Apr 22 23:46:46 daniel-laptop kernel: [ 3317.388646] ata1.00: configured for UDMA/100
Apr 22 23:46:47 daniel-laptop kernel: [ 3317.420404] ata1.01: configured for UDMA/33
Apr 22 23:46:47 daniel-laptop kernel: [ 3317.432836] ata1: EH complete
Apr 22 23:47:17 daniel-laptop kernel: [ 3348.000587] ata1: lost interrupt (Status 0x58)
Apr 22 23:47:17 daniel-laptop kernel: [ 3348.112994] ata1: soft resetting link
Apr 22 23:47:17 daniel-laptop kernel: [ 3348.356646] ata1.00: configured for UDMA/100
Apr 22 23:47:17 daniel-laptop kernel: [ 3348.388392] ata1.01: configured for UDMA/33
Apr 22 23:47:17 daniel-laptop kernel: [ 3348.400826] ata1: EH complete
Apr 22 23:49:15 daniel-laptop kernel: [ 3465.553630] tifm0 : demand removing card from socket 0:0



And this when I push the card in:

Apr 22 23:50:36 daniel-laptop kernel: [ 3547.280099] tifm_core: SmartMedia/xD card detected in socket 0:0


at least it knows it's there I guess...not that I have a clue what any of this means.

---

### Post by ambient007 on 2010-04-22
Bump, seems like 'nothing special' may have had an idea what was happening :-k

---

### Post by ambient007 on 2010-04-23
bump again...I really wanna get this going.

---

