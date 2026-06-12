---
title: "Intel 7260ac hardware disabled without hw wifi buttons"
date: 2016-02-11
forum: Networking &amp; Wireless
---

### Post by Poldone on 2016-02-11
I bought a Intel7260ac to change my old atheros, to add ac functionality to my Sony Vaio SVE1513.
I installed the card, but always airplane mode, so on intel forum I found a hint to tape the pin #20 and #51, and now the BT works and no airplane mode, but the wireless is rfkill hardblocked.
The pc doesn't have a hardware button to enable wifi.

I have some days to return to amazon the card, but I would try to make it work.

Thank You in advance

Here the wireless-info
[ATTACH]267231[/ATTACH]

---

### Post by Hadaka on 2016-02-11
Hi, you should not have to put tape anywhere to get a new wifi card to work.
you run the risk of destroying the card or your computer.
please see this link for the possible location of your **WIFI** **SWITCH** and how to make
bluetooth function correctly
[https://docs.sony.com/release/VPCEA2_series.pdf](https://docs.sony.com/release/VPCEA2_series.pdf)
pages  14..18..and 67..68
and also do..
```
sudo rfkill unblock all
```
report back your findings
thanks.

---

