---
title: "Enabling Prism2-usb wlan in Xubuntu - Help!"
date: 2006-10-05
forum: Networking &amp; Wireless
---

### Post by jarthurs on 2006-10-05
I am having trouble getting my wireless LAN up an running under Xubuntu 6.06.1 the problem is that there are so many different solutions on the forums I've no idea which way to turn!

My USB 802.11b adapter is detected OK.

jason@kobu:~$ lsusb
Bus 001 Device 005: ID 09aa:3642 Intersil Corp. Prism 2.x 802.11b Adapter
Bus 001 Device 001: ID 0000:0000

The prism2_usb module appears to be loaded...

jason@kobu:~$ lsmod | grep prism
prism2_usb             81636  0
usbcore               139172  3 prism2_usb,uhci_hcd

I've added my SSID to /etc/wlan/wlan.conf and my wlancfg-DEFAULT has my WEP key and the encryption enabled.

When I try to run sudo ifup wlan0 I get...

Failed to enable the device, resultcode= implementation_failure .
run-parts: /etc/network/if-pre-up.d/linux-wlan-ng-pre-up exited with return code 1
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Operation not supported.
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Operation not supported.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Operation not supported.

Can anyone suggest a solution for this, as being tied to a wired connection is such a PITA...

Regards,
Jason.

---

### Post by tormod on 2006-10-13
Did you read through the wiki documentation?
[https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb](https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb)

---

