---
title: "Ubuntu 24.04 hotspot"
date: 2024-07-15
forum: Networking &amp; Wireless
---

### Post by gian2 on 2024-07-15
Hello All,

I would like this Ubuntu instance to work as a bridged hot spot.
I am using a Dlink USB radio, which is correctly detected with lsusb:

Bus 001 Device 002: ID 2001:3d04 D-Link Corp. 802.11 n WLAN

However, when I open the wireless setup, the hotspot option is greyed out, which makes me think that the OS thinks it's not capable, bridged or not.
This is not true, because I have two other Raspberry Pi working as AP on Debian, with the same hardware...

Any idea?

Thanks for your advice,

-Gian

---

### Post by gian2 on 2024-07-15
Investigating the differences between the Raspi and this Ubuntu 24.04 station, I see that iw list returns ...

this for the Raspi
    Supported interface modes:
         * IBSS
         * managed
         * AP
         * AP/VLAN
         * monitor
         * mesh point

this for Ubuntu 24.04
    Supported interface modes:
         * managed
         * monitor

So the same USB is read in a different way.

---

### Post by currentshaft on 2024-07-15
"iw reg get" will show you wireless card capabilities

---

### Post by gian2 on 2024-07-15
Raspi iw reg get

global
country IT: DFS-ETSI
    (2402 - 2482 @ 40), (N/A, 20), (N/A)
    (5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW
    (5490 - 5710 @ 160), (N/A, 27), (0 ms), DFS
    (57000 - 66000 @ 2160), (N/A, 40), (N/A)

Ubuntu 24.04 iw reg get

global
country 00: DFS-UNSET
    (755 - 928 @ 2), (N/A, 20), (N/A), PASSIVE-SCAN
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 20), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW, PASSIVE-SCAN
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (N/A, 20), (N/A), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

---

### Post by currentshaft on 2024-07-15
Are you in Italy? If so "iw reg set it" to set the appropriate regulatory domain and try again.

---

### Post by gian2 on 2024-07-15
Thanks. 

Yes, I was looking for a setting menu but there is no way to enter that on the desktop.

I have no problem on the command line but, as I installed the desktop I kind of expected to be able to do it from there.

---

### Post by gian2 on 2024-07-15
now it is :

global
country IT: DFS-ETSI
    (2400 - 2483 @ 40), (N/A, 20), (N/A)
    (5150 - 5250 @ 80), (N/A, 23), (N/A), NO-OUTDOOR, AUTO-BW
    (5250 - 5350 @ 80), (N/A, 20), (0 ms), NO-OUTDOOR, DFS, AUTO-BW
    (5470 - 5725 @ 160), (N/A, 26), (0 ms), DFS
    (5725 - 5875 @ 80), (N/A, 13), (N/A)
    (5945 - 6425 @ 160), (N/A, 23), (N/A), NO-OUTDOOR
    (57000 - 66000 @ 2160), (N/A, 40), (N/A)

---

