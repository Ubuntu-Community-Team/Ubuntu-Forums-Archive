---
title: "configuring netgear MA111 USB wireless adapter"
date: 2007-06-03
forum: Networking &amp; Wireless
---

### Post by Caermundh on 2007-06-03
OK, i am trying to configure the Netgear MA111 (V1) USB wireless adapter to connect to my wireless router on Ubuntu 7.04 alternate CD installation.

I know that Ubuntu "sees" the adapter... I did "lsmod | grep prism" and got the following output:

Prism2_usb     74628     0
p80211           31884     1   prism2_usb
usbcore         134280    4   prism2_usb,usbhid,uhci_hcd


I added the following lines to /etc/network/interfaces:

auto wlan0
iface wlan0 inet dhcp
wireless_mode managed
wireless_essid my_essid
wireless_enc on
wlan_ng_key0 nnnnnnnnnn
wlan_ng_authtype opensystem

I know that this is configuring the wireless adapter because before i added these lines to /etc/network/interfaces it would say "roaming mode enabled" under the connector when i went to System->Administration->Network, after adding those lines it now says "Address:dhcp". When I go to open up a web browser though, it still says page not found for every web page.

What step have I missed?

---

### Post by Caermundh on 2007-06-04
bump.....

---

