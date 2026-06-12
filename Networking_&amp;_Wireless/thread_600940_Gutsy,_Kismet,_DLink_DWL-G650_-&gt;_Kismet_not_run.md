---
title: "Gutsy, Kismet, DLink DWL-G650 -&gt; Kismet not running"
date: 2007-11-02
forum: Networking &amp; Wireless
---

### Post by LinuxFan9 on 2007-11-02
Hi there,

My DLink DWL-G650 (Atheros Chipset) is running fine with Gutsy and WPA.
Nevertheless, starting sudo kismet
(from my kismet conf: source=madwifi_ag,wifi0,DWL-G650)
results in::

Source 0 (DWL-G650): Enabling monitor mode for madwifi_ag source interface wifi0 channel 6...
WARNING:  Found a non-master non-monitor VAP wifi0::kis1.  Madwifi-ng has historically had problems with normal-mode VAPs combined with monitor-mode VAPs.  You may need to remove them.
NOTICE:  Created Madwifi-NG RFMON VAP kis2
WARNING: wifi0 appears to be using Madwifi-NG.  Some versions of the Madwifi-NG drivers have problems in monitor mode, especially if non-monitor VAPs are active.  If you experience problems, be sure to try the latest versions of Madwifi-NG and remove other VAPs

and aborting kismet.
What does the error message mean - and what can I do?

Sincerely,
Linuxfan9

---

