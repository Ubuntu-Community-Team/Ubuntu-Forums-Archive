---
title: "Ubuntu 24.04 weak signal on Wifi"
date: 2024-10-11
forum: Networking &amp; Wireless
---

### Post by knori on 2024-10-11
I searched the forum but I cannot find any answer on latest Ubuntu versions.

Suddenly, some days ago the intensity of wifi signal received by my laptop (an old Lenovo G50-80) has dropped.
At home I have to go very near to AP.
At work, where I connected with no problem, now my laptop even do not see any WiFi network, so that I have to use my smartphone as a Hotspot, and sometimes I lose my connection, even if it is very near to the PC.


This is the result of lshw -c network
(Italian)
```

descrizione: Interfaccia Wireless
       prodotto: Wireless 3160
       fornitore: Intel Corporation
       id fisico: 0
       bus info: pci@0000:03:00.0
       nome logico: wlp3s0
       versione: 93
       seriale: b4:6d:83:1b:fa:21
       larghezza: 64 bits
       orologio: 33MHz
       capacità: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configurazione: broadcast=yes driver=iwlwifi driverversion=6.8.0-45-generic firmware=17.3216344376.0 3160-17.ucode ip=192.168.14.218 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       risorse: irq:53 memoria:c1000000-c1001fff

```

lspci
```

03:00.0 Network controller: Intel Corporation Wireless 3160 (rev 93)

```

THanks in advance

---

