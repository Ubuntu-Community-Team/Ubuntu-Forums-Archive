---
title: "Netgear MA401 card not working with HostAP driver"
date: 2007-03-25
forum: Networking &amp; Wireless
---

### Post by apu95 on 2007-03-25
I want to get my MA401 card (PCMCIA) running with the hostAP driver. When Ubuntu loads up, it gives a bunch of error messages regarding the hostAP driver. This is what dmesg outputs:

```

[17179589.128000] orinoco 0.15rc3 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[17179589.128000] orinoco_cs 0.15rc3 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[17179589.364000] eth2: Hardware identity 800c:0000:0001:0000
[17179589.364000] eth2: Station identity  001f:0006:0001:0003
[17179589.364000] eth2: Firmware determined as Intersil 1.3.6
[17179589.364000] eth2: Ad-hoc demo mode supported
[17179589.364000] eth2: IEEE standard IBSS ad-hoc mode supported
[17179589.364000] eth2: WEP supported, 104-bit key
[17179589.364000] eth2: MAC address 00:09:5B:24:0D:E2
[17179589.368000] eth2: Station name "Prism  I"
[17179589.368000] eth2: ready
[17179589.368000] eth2: index 0x01: , irq 3, io 0x3100-0x313f
[17179589.380000] hostap: disagrees about version of symbol ieee80211_get_crypto_ops
[17179589.380000] hostap: Unknown symbol ieee80211_get_crypto_ops
[17179589.392000] hostap_cs: Unknown symbol prism2_update_comms_qual
[17179589.392000] hostap_cs: Unknown symbol hostap_set_hostapd
[17179589.392000] hostap_cs: Unknown symbol hostap_set_encryption
[17179589.392000] hostap_cs: Unknown symbol hostap_remove_proc
[17179589.392000] hostap_cs: Unknown symbol hostap_set_auth_algs
[17179589.392000] hostap_cs: Unknown symbol hostap_80211_get_hdrlen
[17179589.392000] hostap_cs: Unknown symbol hostap_set_multicast_list_queue
[17179589.392000] hostap_cs: Unknown symbol hostap_get_stats
[17179589.392000] hostap_cs: Unknown symbol hostap_add_interface
[17179589.392000] hostap_cs: Unknown symbol hostap_free_data
[17179589.392000] hostap_cs: Unknown symbol hostap_set_word
[17179589.392000] hostap_cs: Unknown symbol hostap_info_process
[17179589.396000] hostap_cs: Unknown symbol hostap_set_string
[17179589.396000] hostap_cs: Unknown symbol hostap_set_antsel
[17179589.396000] hostap_cs: Unknown symbol hostap_remove_interface
[17179589.396000] hostap_cs: Unknown symbol hostap_setup_dev
[17179589.396000] hostap_cs: Unknown symbol hostap_dump_rx_header
[17179589.396000] hostap_cs: Unknown symbol hostap_init_data
[17179589.396000] hostap_cs: Unknown symbol hostap_80211_header_parse
[17179589.396000] hostap_cs: Unknown symbol hostap_init_ap_proc
[17179589.396000] hostap_cs: Unknown symbol hostap_set_hostapd_sta
[17179589.396000] hostap_cs: Unknown symbol hostap_init_proc
[17179589.396000] hostap_cs: Unknown symbol hostap_dump_tx_header
[17179589.396000] hostap_cs: Unknown symbol hostap_check_sta_fw_version
[17179589.396000] hostap_cs: Unknown symbol hostap_get_porttype
[17179589.396000] hostap_cs: Unknown symbol hostap_80211_rx
[17179589.396000] hostap_cs: Unknown symbol hostap_set_roaming
[17179589.396000] hostap_cs: Unknown symbol hostap_handle_sta_tx_exc
[17179589.396000] hostap_cs: Unknown symbol hostap_info_init
[17179589.396000] hostap_cs: Unknown symbol hostap_master_start_xmit

```

It then keeps loading as usual (the card inside my laptop is the ipw2200, which works great to browse and monitor packets), and once I can access the device manager, the card is using the orinoco_cs driver instead.

Is there any way I can fix this? I suspect that the ieee80211 error might be related to me updating the ieee80211 subsystem to the latest one (which I did when I updated the ipw2200 drivers).

Thanks!
Apu

---

### Post by chili555 on 2007-03-25
I would try blacklisting the offenders: sudo gedit /etc/modprobe.d/blacklist and add the following```
blacklist  hostap
blacklist  hostap_cs
blacklist  orinoco
blacklist  orinoco_cs
```It will probably take a reboot to see.

---

### Post by apu95 on 2007-03-25
Okay, I blacklisted those and rebooted but now there's no error at all. The device manager still shows the card, and it's identified as "NETGEAR MA401RA Wireless PC" but dmesg shows nothing out of the ordinary. It loads up ipw2200 perfectly and there aren't ieee80211 errors.

---

