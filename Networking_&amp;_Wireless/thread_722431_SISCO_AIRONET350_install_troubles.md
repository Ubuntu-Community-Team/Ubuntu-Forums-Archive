---
title: "SISCO AIRONET350 install troubles"
date: 2008-03-12
forum: Networking &amp; Wireless
---

### Post by Deffe on 2008-03-12
Hi

I freshly installed Ubuntu_7.10 on my Dell Lattitude C840 laptop.
I'm trying to make the SISCO AIRONET-350 card work with WPA-personal.
I already did what's suggested in a lot of threads.
    - install network-manager
    - install wpasupplicant
     ---> for both the system reports that the latest version is already installed.
     ----> so I didn't do anything.

Under system - administration - network the card is found.
   It is reported with two entires
            - wifi0 (default set on roaming)
            - eth1 (default set on roaming)
In the taskbar icon for the network I can see networks (with variable reception strength).
also the network I want to connect to (I'm already connected to it with a Windows PC).

Now comes the issue:
  -- When changing the Properties in the Network Settings pop-up window I can select WPA-personal and enter various options as SSID, password, and configuration (DHCP).
  - When clicking the taskbar icon and selecting the network I want to connect to a pop-up window opens with as only wireless security option LEAP.
  - When in the same icon selecting "Connect to other wireless network" or "Create new wireless network" I don't find WPA in the Wireless Security pull down list (Only different form of WEP are available).

The manual option from the icon is identical to opening the Network Settings under system administration.

I tried to set both interfaces (wifi0 and eth1) to WPA and DHCP but without any luck.
I tried also what people are suggesting in different threads about manual configuration of wireless cards without success.

maybe somebody can give me a good hint,

Thanks,

Marc

---

