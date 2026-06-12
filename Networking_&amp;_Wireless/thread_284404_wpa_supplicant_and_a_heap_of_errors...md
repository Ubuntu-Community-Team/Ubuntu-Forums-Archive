---
title: "wpa supplicant and a heap of errors.."
date: 2006-10-25
forum: Networking &amp; Wireless
---

### Post by MrJavalava on 2006-10-25
Heya..
I'm trying to use wpa_supplicant for my networking, the wpa_supplicant will run on a wired network. The .conf file looks like this:

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=network

network={
  key_mgmt=IEEE8021X
  eap=PEAP
  identitiy="my userid"
  password="my password"
  priority=10
}

I get this error message when I do:
"wpa_supplicant -i eth0 -c /etc/wpa_supplicant.conf"

ioctl[SIOCSIWMODE]: Operation not supported
Could not configure driver to use managed mode
ioctl[SIOCGIWRANGE]: Operation not supported
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: Operation not supported
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: Operation not supported
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: Operation not supported
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: Operation not supported
ioctl[SIOCSIWSCAN]: Operation not supported
Failed to initiate AP scan.
ioctl[SIOCGIWSCAN]: Operation not supported
CTRL-EVENT-TERMINATING - signal 2 received
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: Operation not supported
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: Operation not supported
Failed to disable WPA in the driver.
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: Operation not supported
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: Operation not supported
ioctl[SIOCSIWAP]: Operation not supported

---

### Post by MrJavalava on 2006-10-26
Okay... to give you more info:

I'm using an integrated network card which is in my motherboard, Asus A8NE

I have not done anything with the .configure in the kernel.

Also my /etc/network/intefaces looks like this:

auto eth0
iface eth0 inet dhcp

auto lo
etc.....

---

