---
title: "Wireless Help:06:09.0 Ethernet controller: Winbond Electronics Corp W89C33D 802.11"
date: 2007-06-03
forum: Networking &amp; Wireless
---

### Post by aholland on 2007-06-03
Alright I have a medion laptop with that wireless card in there. I have the current ubuntu installed...Umm I had an older version installed which didn't detect the card well but this new version tells me everything about the card but nothing shows up under ifconfig for the card or iwconfig. I have tried to install it with ndiswrapper but it doesn't work either. 

Here is what comes up when I do lspci:

06:09.0 Ethernet controller: Winbond Electronics Corp W89C33D 802.11 a/b/g BB/MAC

Any ideas on how I get my wireless card to work under Ubuntu?...Really don't want to go back to Windows :(

---

### Post by mattkeeble on 2007-06-09
I have the same card and the same issue. I thought I had managed to install an earlier version of Ubuntu without issue, but the latest version (7.04) is causing me issues. Haven't tried the Windows wrapper yet, but I don't want to use Windows Home (the previously installed OS) and can't be arsed to pay for XPPro.

Can anyone help? I have posted the lshw output generated with sudo lshw -C network below for convenience...

You'll notice the first line is "*-network:0 UNCLAIMED" which is ironic as this is the last mention on the troubleshooting site relating to this entry: "TODO: describe what it means when it shows *-network UNCLAIMED, and no configuration line is present" - Aaaarggh.

Bottom line is, I have about 3 days to get this sorted before I NEED to use this machine productively. If I don't get it done, I'm going to have to revert to Windows and i don't want to!

Thanks if anyone is able to help.:D

 *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: W89C33D 802.11 a/b/g BB/MAC
       vendor: Winbond Electronics Corp
       physical id: 11
       bus info: pci@00:11.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0 maxlatency=32 mingnt=64
       resources: iomemory:48021000-480211ff

---

### Post by brigden on 2008-07-06
i have the same problem with this card

---

