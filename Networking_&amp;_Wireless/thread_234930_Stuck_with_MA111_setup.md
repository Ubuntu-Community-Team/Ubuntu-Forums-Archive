---
title: "Stuck with MA111 setup"
date: 2006-08-12
forum: Networking &amp; Wireless
---

### Post by MatBi on 2006-08-12
I did everything explained in the wiki page
[https://help.ubuntu.com/community/WifiDocs/Device/NetgearMA111](https://help.ubuntu.com/community/WifiDocs/Device/NetgearMA111)
The module "ieee80211" is not there, looks like it's not required by prism2_usb; the file /etc/modprobe.d/wlan was not there, i had to create it.

when i start the interface, i get:
# ifup wlan0
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Operation not supported.
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Operation not supported.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Operation not supported.

I also tried to modprobe ieee80211 but nothing changed.
Looks like something is missing, can anyone help me?
Thanks,
MatBi

---

### Post by az on 2006-08-12
Are you sure it's a prism2_usb device?

When you plug it in, what modules are loaded?  

lsmod

---

### Post by MatBi on 2006-08-16
Sorry for the delay.
Here's the syslog snippet:
Aug 16 00:42:05 localhost kernel: [17236923.800000] usb 3-1: new full speed USB device using uhci_hcd and address 3
Aug 16 00:42:07 localhost kernel: [17236925.388000] ident: nic h/w: id=0x8026 1.0.0
Aug 16 00:42:07 localhost kernel: [17236925.388000] ident: pri f/w: id=0x15 1.1.4
Aug 16 00:42:07 localhost kernel: [17236925.388000] ident: sta f/w: id=0x1f 1.7.0
Aug 16 00:42:07 localhost kernel: [17236925.392000] MFI:SUP:role=0x00:id=0x01:var=0x01:b/t=1/1
Aug 16 00:42:07 localhost kernel: [17236925.392000] CFI:SUP:role=0x00:id=0x02:var=0x02:b/t=1/1
Aug 16 00:42:07 localhost kernel: [17236925.392000] PRI:SUP:role=0x00:id=0x03:var=0x01:b/t=1/4
Aug 16 00:42:07 localhost kernel: [17236925.392000] STA:SUP:role=0x00:id=0x04:var=0x01:b/t=1/12
Aug 16 00:42:07 localhost kernel: [17236925.396000] PRI-CFI:ACT:role=0x01:id=0x02:var=0x02:b/t=1/1
Aug 16 00:42:07 localhost kernel: [17236925.396000] STA-CFI:ACT:role=0x01:id=0x02:var=0x02:b/t=1/1
Aug 16 00:42:07 localhost kernel: [17236925.396000] STA-MFI:ACT:role=0x01:id=0x01:var=0x01:b/t=1/1
Aug 16 00:42:07 localhost kernel: [17236925.400000] Prism2 card SN: \x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00

lsusb gives:
Bus 003 Device 003: ID 0846:4110 NetGear, Inc. MA111 WiFi (v1)

and lshw:
*-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:09:5b:b2:09:27
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=p80211_prism2_usb driverversion=0.2.2 link=no multicast=yes wireless=IEEE 802.11-DS

and lsmod | grep prism
prism2_usb             77060  0
usbcore               130692  7 prism2_usb,ohci_hcd,uhci_hcd,ehci_hcd,usbhid,usb_storage

Thanks

---

### Post by az on 2006-08-16
Looks like everything is working fine?  Ignore that part about the ieee module.

You can't connect?

---

### Post by MatBi on 2006-08-16
> **azz said:**
> Looks like everything is working fine?  Ignore that part about the ieee module.
You can't connect?
As stated in the first post, i get this bunch of errors; "ifconfig wlan0" gives no ip info => no connection.
Is the "*-network DISABLED" a good thing?

---

### Post by az on 2006-08-17
> **MatBi said:**
> As stated in the first post, i get this bunch of errors; "ifconfig wlan0" gives no ip info => no connection.
Is the "*-network DISABLED" a good thing?

I don't know if that just means you have not configured it properly in /etc/network/interfaces.  Maybe itM's because linux-wlan-ng doesn't use the same config?

I don't know if that is a bad thing from a hardware point of view.

---

### Post by tormod on 2006-08-29
> **MatBi said:**
> 
when i start the interface, i get:
# ifup wlan0
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Operation not supported.
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Operation not supported.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Operation not supported.


These messages are normal, nothing to worry about. Can you tell us what you have in /etc/network/interfaces ?

---

### Post by MatBi on 2006-08-31
> **tormod said:**
> These messages are normal, nothing to worry about. Can you tell us what you have in /etc/network/interfaces ?
Here's the snippet relative to the wlan interface:

 iface wlan0 inet dhcp
 wireless_mode managed
 wireless_essid wasabi
 wireless_enc on
 wlan_ng_key0 63:79:73:70:61
 wlan_ng_authtype opensystem

Is there something missing? It's meant to use 64(40) bits WEP with fixed key.

---

### Post by tormod on 2006-08-31
Depending on your network, you may not need "wlan_ng_authtype opensystem".

I haven't seen "*-network DISABLED" before, it it possible you have a hardware button to turn off wireless (the "kill switch") ? Many laptops have one of these buttons, and a LED to see if it's on or not.

See also [https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb](https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb)

---

### Post by MatBi on 2006-08-31
> **tormod said:**
> Depending on your network, you may not need "wlan_ng_authtype opensystem".

I haven't seen "*-network DISABLED" before, it it possible you have a hardware button to turn off wireless (the "kill switch") ? Many laptops have one of these buttons, and a LED to see if it's on or not.

See also [https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb](https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb)

It's an USB device, so no switch. To install I followed that doc and others. 
Well, I'll check everything step by step this weekend; i'll also try the card under windows, to exclude hardware issues.
Thanks so far.

---

