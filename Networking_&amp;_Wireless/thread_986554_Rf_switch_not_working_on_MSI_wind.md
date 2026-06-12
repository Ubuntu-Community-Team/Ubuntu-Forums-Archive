---
title: "Rf switch not working on MSI wind"
date: 2008-11-18
forum: Networking &amp; Wireless
---

### Post by sofsof on 2008-11-18
Hi all,

I have an MSI wind since 1 month using Hardy. I changed the wifi card into a Atheros GN-WI01GT which works well with madwifi. The only problem is that I have noticed that the FnF11 switch has no effect on wireless (while it switches bluetooth on and off), i.e. the wifi card is always on and connected even if the wifi led is off.

I have noticed in `dmesg` that the following line
```
[ 1669.063649] MadWifi: ath_attach: Switching rfkill capability off.
```
So I unloaded ath_pci and reloaded it using
```
# modprobe ath_pci rfkill=1
```
and I got
```
[ 5262.669013] MadWifi: ath_attach: Switching rfkill capability on.
```
but still the wifi card is on and Fn F11 has no effect on it.

Is it possible to have the rf switch working on my msi wind? It's very useful to not discharge batteries when wireless is not needed.

Thanks

---

