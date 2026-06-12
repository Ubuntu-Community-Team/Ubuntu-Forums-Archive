---
title: "Verify wirlelss encryption from cli?"
date: 2006-10-23
forum: Networking &amp; Wireless
---

### Post by squibT on 2006-10-23
Is there a way to tell the wireless encryption/security you are using from the cli? 

TIA,

squibt

---

### Post by mahy on 2006-10-23
> **squibT said:**
> Is there a way to tell the wireless encryption/security you are using from the cli? 

TIA,

squibt

sudo iwconfig ;)

It displays the correct encryption settings most of the time.

---

### Post by squibT on 2006-10-23
Iwconfig displays Security Mode: Open...I am using WPA...there has to be some cli to verify security...anyone?

---

### Post by squibT on 2006-10-24
"iwlist eth0 scanning" reports the stats/signal comming from the AP and reports CCMP (AES) correctly but how to do I get stats from the NIC (wpc54gs) and how can I configure settings like Bit Rate?

---

