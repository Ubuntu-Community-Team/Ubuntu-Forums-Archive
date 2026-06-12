---
title: "Have to set ap auto for atheros card"
date: 2007-09-23
forum: Networking &amp; Wireless
---

### Post by jemmyw on 2007-09-23
Hi. I've got an atheros pci wireless card. The card works fine, but every time I boot I have to run the following on the command line, or it says it can't find the access point:

iwconfig ath0 ap auto
dhclient ath0

Before it starts working. Here is my interfaces file:

auto lo
iface lo inet loopback

iface ath0 inet dhcp
wireless-essid NETNAME
wireless-key s:***********

auto ath0

Can I put something in there to make it work automatically?

---

### Post by noob12 on 2007-09-23
Try adding it in a pre-up line to your entry.  I don't know if **wireless-ap auto** works, but you could try that instead as well.  If it idoes it is equivalent.

```

auto ath0
iface ath0 inet dhcp
pre-up iwconfig ath0 ap auto
wireless-essid NETNAME
wireless-key s:***********

```

I moved the **auto ath0** line up with the rest of the stanza, but that's not significant.

---

