---
title: "[ADSL] RFC 2516 - tun0 or tap0?"
date: 2007-09-28
forum: Networking &amp; Wireless
---

### Post by merci_b on 2007-09-28
For my USB ADSL Modem, the WinXP setup says *"RFC 2516 PPPoE Encapsulation"*; For setting up the EciAdsl driver, I used *LLC_SNAP_RFC1483_BRIDGED_ETH_NO_FCS* setting, which uses a tap0 interface. When I run *eciadsl-start* usually it would give

> [EciAdsl 1/5] Setting up USB support...

Preliminary USB device filesystem is OK

[EciAdsl 2/5] Uploading firmware...

Process skipped .. no more needed
firmware loaded successfully

[EciAdsl 3/5] Synchronization...

 Please Wait.. Synchronisation in progress [|]


Whereas sometimes it says
> [EciAdsl 1/5] Setting up USB support...

Preliminary USB device filesystem is OK
[B]Loading tun/tap module...
tun loaded successfully[/B]

[EciAdsl 2/5] Uploading firmware...

Process skipped .. no more needed
firmware loaded successfully

[EciAdsl 3/5] Synchronization...

 Please Wait.. Synchronisation in progress [|]


Does this mean it uses a tun0 instead of tap0? Am I using the wrong Encapsulation type?

The available modes in EciAdsl are
[B]VCM_RFC2364
LLC_RFC2364
LLC_SNAP_RFC1483_BRIDGED_ETH_NO_FCS
VCM_RFC_1483_BRIDGED_ETH
LLC_RFC1483_ROUTED_IP
VCM_RFC1483_ROUTED_IP[/B]

---

