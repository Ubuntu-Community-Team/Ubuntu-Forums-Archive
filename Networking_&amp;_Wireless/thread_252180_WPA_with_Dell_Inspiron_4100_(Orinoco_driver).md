---
title: "WPA with Dell Inspiron 4100 (Orinoco driver)"
date: 2006-09-06
forum: Networking &amp; Wireless
---

### Post by PacketPaul on 2006-09-06
Hi,

Does anyone know if it is possible to setup WPA with the Dell 4100 Inspiron.  I believe the driver I am using is the Orinoco driver.  I have installed the network-manager-gnome package and wpasupplicant.

When I follow the directions found at:
[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

I do not receive the WPA option under the network manager.  If I try to run wpa_supplicant manually I receive the following results:

-------------------------------------------------------------------
/proc# wpa_supplicant -ieth1 -c /etc/wpa_supplicant/wpa-psk-tkip.conf

ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
ioctl[SIOCSIWSCAN]: Device or resource busy
Failed to initiate AP scan.
--------------------------------------------------------------------

Suggestions?

Thanks for your help!

Paul

---

### Post by marcochs on 2007-02-08
I'm just getting started with this, but I have that same error.

I also have a Dell Inspiron 4100 (but with xubuntu 6.10) and get that same PRISM2 errors.

My card is a MSI MP54G5 which I *think* needs the rt61 driver.

Not sure if prism needs to be removed or blacklisted or what... I do see the rt61_pci module loaded...

---

