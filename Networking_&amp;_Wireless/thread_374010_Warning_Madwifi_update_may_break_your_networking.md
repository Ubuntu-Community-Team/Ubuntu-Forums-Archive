---
title: "Warning: Madwifi update may break your networking"
date: 2007-03-01
forum: Networking &amp; Wireless
---

### Post by silid on 2007-03-01
a recent update in the repositories for:

linux-restricted-modules-2.6.17-11-generic

caused my atheros wifi card to stop initialising - it gave ther following errors in the kernel log

```
kernel: [17179886.552000] ath_rate_sample: disagrees about version of symbol ieee80211_iterate_nodes
kernel: [17179886.552000] ath_rate_sample: Unknown symbol ieee80211_iterate_nodes
kernel: [17179886.552000] ath_rate_sample: disagrees about version of symbol ieee80211_proc_vcreate
kernel: [17179886.552000] ath_rate_sample: Unknown symbol ieee80211_proc_vcreate
kernel: [17179886.556000] ath_pci: Unknown symbol ath_rate_tx_complete
kernel: [17179886.556000] ath_pci: disagrees about version of symbol ieee80211_encap
kernel: [17179886.556000] ath_pci: Unknown symbol ieee80211_encap
kernel: [17179886.556000] ath_pci: disagrees about version of symbol ieee80211_input
kernel: [17179886.556000] ath_pci: Unknown symbol ieee80211_input

```

software updates installed subrelease .2 which broke it

i reverted back to .1 and it now works again. i am sure there is a way of fixing .2 but i couldn't find it at this time in the morning.

i hope that this helps someone.

si

---

