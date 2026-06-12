---
title: "New ethernet card not seen as it should"
date: 2007-07-30
forum: Networking &amp; Wireless
---

### Post by carontis on 2007-07-30
I'm using Ubuntu 6.06 updated 6.0.6.1. I had a ethr0 card that was working fine till last night, when I found it was broken. It's a Skintek 1Gbit pci. I chnged the broken one with a classic 3com and quickly this last was seen as eth1. I thought it was  done to something in relation to the old card, but I think I'm wrong...

This morning I finally changed the card (warranty)  and after I've had the new one (again a Skintek 1 Gbit) I chnaged it again. With surprise I found that this one too is keeping thew eth1 and doesn't want recognize the old eth0 even if it is the only card on my pc. I can't understand what happened, also 'cause I'm using the same slot with the same ethernet card.

Does abyone knows how to bring it to the eth0 position? I've also deleted all writings in /etc(netrwork/interfaces, but nothing to do; always it shows an eth1 and not anymore eth0. Is there something I can do to fix this? Thanks to all.

---

### Post by carontis on 2007-07-30
up :(

---

### Post by carontis on 2007-07-31
Just for knowledge:
I tried to use a live cd to check if can be done to some hardware or some software. With the live cd it connects normally with eth0 and no trace is about eth1. So the error is in my system, probably something that has to do with interrupts.
The irsta card I had (exactly same to this one) was broken 2 nights ago; only after that accident my pc began to give me this kind of result. How can I fix it? It's anormal desktop pc, no wireless and no second eth card. What happened? The installed card is a RTL8169 100/1000. Now also with other cards it does the same.

---

### Post by carontis on 2007-07-31
Well, I was waiting for some help, and in meantime I tried to do by myself and finally I found the solution.

Go to file /etc/iftab and change the old MAC with the new one writing in it also the number of the eth card (etho, eth1 etc). Reboot your pc and go to connections to put all datas you need.
Everything now it's okl.

Hope it will helpful for others.

---

