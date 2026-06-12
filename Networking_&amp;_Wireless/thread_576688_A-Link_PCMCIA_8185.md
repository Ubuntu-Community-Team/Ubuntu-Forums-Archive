---
title: "A-Link PCMCIA 8185"
date: 2007-10-15
forum: Networking &amp; Wireless
---

### Post by Snaggo on 2007-10-15
First of all, sorry for making yet another post, but I'm getting frustrated. Also note; not really an eperienced linux user talking here.
Okay now, my basic question is: how the hell can I make this WLAN-card work on Xubuntu on this laptop? We're talking about an A-Link 54m pcmcia card. I guess it runs on the rtl-8185 chipset.
I've tried doing it via ndiswrapper. here's what i get:
```
net8185 : invalid driver!

```

that's after going trough some of the steps mentioned on ndiswrapper's installation instructions. there wasn't actually any windows drivers available for this card on their list, so I tried doing it with the ones that came on the cd.

lspci says

```
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)

```
..if that's any help.

There are also some linux drivers on the little cd that came with the card, but their installation instructions are total gibberish to me.

I would appreciate a lot if someone could point me to some foolproof installation guide. Or even better, tell me here how to do it and use it after that.

---

