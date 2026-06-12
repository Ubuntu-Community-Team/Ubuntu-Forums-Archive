---
title: "wireless network ceased working"
date: 2008-08-12
forum: Networking &amp; Wireless
---

### Post by 3nt on 2008-08-12
I have a Dell Inspiron 9400 using an Intel 3945ABG wireless card. It has worked fine under Hardy until recently. The only change I can connect it to is the last kernel upgrade. If I turn WEP 128 on then I get the "AP denied association (code=18)" error found in beta. If I turn WEP off then I get "authentication with AP 00:11:50:22:a8:b4 timed out.

I have tried using wicd instead of nm but without success. I tried but was unable to get nm 0.7 to fully install (I think) so couldn't test with that (although it did show that "resolvconf" was missing and that at least meant the card was always recognised without manual intervention).

the lshw -C network is attached (I haven't worked out how to get it in the boxes everyone else uses). the only oddity I see is that the card has a logical name of wmaster0 and not eth1 as before.

---

### Post by Crafty Kisses on 2008-08-12
That's weird, try posting the following output:
```
iwconfig
```

---

### Post by 3nt on 2008-08-12
iwconfig with security off (as I don't particularly want to posty my WEP key!)

I have temporarily re-installed the Gutsy kernel and now get Access point: 001:11:50:22:A8:B4 showing in iwconfig, but still don't seem to connect outside my LAN using wireless (works OK within my LAN). I will try checking the hardware and post again if I can get wireless to connect outside my LAN.

---

### Post by 3nt on 2008-08-12
I think I now have nm 0.7 installed but still no wireless connections. Attached are what I believe are the relevant sections of dmesg at boot. Is the mac80211 a dpendency of nm0.7 that I haven't got right yet?
Even though the wirless is currently set to no authentication, once the connection has been rejected it doesn't seem to re-authenticate.
I have soft re-booted the wireless huband my router to try and remove possible hardware issues

---

