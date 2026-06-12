---
title: "Link aggregation (IEEE 802.3ad) between NAS and computer"
date: 2013-11-21
forum: Networking &amp; Wireless
---

### Post by zee on 2013-11-21
Hello,
  I have a Synology DS1511+ NAS that is connected directly to a workstation. The workstation mounts the the NAS drive via iSCSI. Since the workstation has two ethernet ports I was thinking of agreggating both links into one thus improving the performance.

  Main question: Can it be done by skipping the switch part (i.e. via direct connection between NAS and the relevant computer)? All the tutorials I could find involved using a (smart enough) switch.

Thanks in advance,
zee

---

### Post by bab1 on 2013-11-21
> **zee said:**
> Hello,
  I have a Synology DS1511+ NAS that is connected directly to a workstation. The workstation mounts the the NAS drive via iSCSI. Since the workstation has two ethernet ports I was thinking of agreggating both links into one thus improving the performance.

  Main question: Can it be done by skipping the switch part (i.e. via direct connection between NAS and the relevant computer)? All the tutorials I could find involved using a (smart enough) switch.

Thanks in advance,
zee

I believe that both devices must support LACP to be directly connected together.  The switch becomes one of those endpoints (if one host or the other doesn't support LACP).  I doubt whether either host  (your NAS or the workstation) support LACP in the first place, so the point appears moot.

---

### Post by zee on 2013-11-21
Thanks BAB1 for your reply.

The NAS offers the option of setting link aggregation according to the 802.3ad standard. For the workstation part I was thinking of using bonding mode 4, which enables link aggregation according to the very same standard.

Would that work?

---

### Post by bab1 on 2013-11-21
> **zee said:**
> Thanks BAB1 for your reply.

The NAS offers the option of setting link aggregation according to the 802.3ad standard. For the workstation part I was thinking of using bonding mode 4, which enables link aggregation according to the very same standard.

Would that work?

We won't know until you try it.  I say go for it!

---

