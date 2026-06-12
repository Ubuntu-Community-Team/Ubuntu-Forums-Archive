---
title: "Settings for Standard accounts' access to Internet"
date: 2021-11-30
forum: Networking &amp; Wireless
---

### Post by bcschmerker on 2021-11-30
**I've an *e*machines®/ac*e*r® EL1210-09** (Shuttle® PC6300001 PSU, Acer Computer Inc. WMCP78M (*really* a HannStar® DAO78L Boxer):  Advance Micro Devices Athlon 64® LE-1620 (P/N ADH1620IAA5DH), nVIDIA® nForce® 780a SLI&#8482; (the planar C77 64-bit geForce® GPU by-passed in favor of a PCIe x16 LP VDA), msi® N610GT-1GD3-L (nVIDIA GF119, 1 GiB GDDR3 VRAM), add-in PCIe x1 dual EIA-571) **running ubuntu® 20.04.3-LTS** (Kernel Families 5.13.0-22, 5.11.0-41, and 5.4.0-96 in order of preference)**, which I am preparing for projector duty at a house of worship,** and I can reach the Internet from the Admin account but not the standard accounts prepared for two Divisions. (I've also an OpenLP Common account, which I plan to configure for a login application of /bin/false upon completion of config; OpenLP Common may need access to an intranet for purposes of controlling an EPSON® projector, but not the Internet.)  Which preferences, permissions, &c. need I set for the standard accounts to enable Internet access?

---

### Post by Tadaen_Sylvermane on 2021-12-01
I think you can do this with iptables. I've not tested this at all and admittedly am not very good with iptables. This is what I came up with.

Put the user(s) in a group. Then put these on iptables.

```
# allow group to lan
iptables -A OUTPUT -m owner --gid-owner ${no_internet_gid_group} -d 192.168.1.0 -j ACCEPT
# drop anything not targeting lan
iptables -A OUTPUT -m owner --gid-owner ${no_internet_gid_group} -j DROP
```

Think that will allow them lan access without anything else. Change the 192.168.1.0 to whatever your lan range is. You may need to allow an ip range to target that way it skips your router / gateway.

---

### Post by bcschmerker on 2021-12-01
**I'll lift the IP tables and see what gives.**  Incidentally, the Advanced Preferences in mozilla firefox contributed to the no-connect from the Standard accounts.

---

### Post by bcschmerker on 2022-02-07
**Had to build *new Profiles* in mozilla® Firefox® for all accounts.**  IPTables yielded no abnormalities. ):P

---

