---
title: "more than one card in a laptop - WPA connection problems"
date: 2008-09-25
forum: Networking &amp; Wireless
---

### Post by neill on 2008-09-25
Hi

I've got a laptop with both an inbuilt wireless card (intel using iwl 4965 driver) and a PCMCIA card (with an atheros chip)

8.04 identifies the PCMCIA card as ath0 and the intel as wlan0

I have 2 WPA networks at home which I originally connected to using the ath0 card - this is fine and indeed still works fine

When I try and connect using wlan0 though it fails

I think it's an authentication issue as Wicd manager goes through most of the process then borks at the authentication stage

I'm guessing that somewhere there's a config file or somesuch that is set for the ath0 card and chokes n wlan0

Can anyone help ?

Also which logs should I be looking at to troubleshoot this and how can I confirm which driver the intel card is using ?

Thanks

/neill

---

