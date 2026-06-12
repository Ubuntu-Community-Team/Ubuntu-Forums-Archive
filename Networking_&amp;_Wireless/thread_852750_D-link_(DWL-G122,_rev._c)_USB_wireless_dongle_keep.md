---
title: "D-link (DWL-G122, rev. c) USB wireless dongle keeps dropping."
date: 2008-07-07
forum: Networking &amp; Wireless
---

### Post by Midnightsun on 2008-07-07
Hi guys,

Am having some trouble with my newly purchased D-Link Wireless Dongle.  When I plug it into my laptop, it activates and I am able to see the wireless networks.

After selecting the network and typing in my network key it connects fine, but then completely deactivates after a couple of seconds.  If I continue unplugging and plugging it in, eventually one of the attempts will work and it will stay on, but that can sometimes take over 10-15 tries.  The messages in the system log are:

Jul  8 10:26:44 m1dn1ght-laptop kernel: [  202.469250] usb 3-5: new high speed USB device using ehci_hcd and address 5
Jul  8 10:26:44 m1dn1ght-laptop kernel: [  202.740406] usb 3-5: configuration #1 chosen from 1 choice
Jul  8 10:26:45 m1dn1ght-laptop kernel: [  203.089546] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jul  8 10:26:48 m1dn1ght-laptop kernel: [  206.681439] eth0: PHY reset until link up.
Jul  8 10:26:58 m1dn1ght-laptop kernel: [  216.442494] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jul  8 10:26:58 m1dn1ght-laptop kernel: [  216.703963] eth0: PHY reset until link up.
Jul  8 10:27:04 m1dn1ght-laptop dhcdbd: dhco_input_option: Value -1 cannot be converted to type L 
Jul  8 10:27:04 m1dn1ght-laptop dhcdbd: dhco_parse_option_settings: bad option setting: new_dhcp_lease_time = -1 
Jul  8 10:27:04 m1dn1ght-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.host_name
Jul  8 10:27:04 m1dn1ght-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_domain
Jul  8 10:27:04 m1dn1ght-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_servers
Jul  8 10:27:08 m1dn1ght-laptop kernel: [  226.726520] eth0: PHY reset until link up.
Jul  8 10:27:09 m1dn1ght-laptop kernel: [  226.992449] usb 3-5: USB disconnect, address 5

Also, not sure if it's relevant but there is one line in the system log that keeps repeating every 10 seconds 

Jul  8 10:33:40 m1dn1ght-laptop kernel: [  617.604917] eth0: PHY reset until link up.

---

Any help will be much appreciated.

---

