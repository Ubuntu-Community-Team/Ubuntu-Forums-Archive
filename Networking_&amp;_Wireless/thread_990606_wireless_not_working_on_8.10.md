---
title: "wireless not working on 8.10"
date: 2008-11-22
forum: Networking &amp; Wireless
---

### Post by cuberoot on 2008-11-22
Hi, I'd appreciate getting help getting my wireless connection up on 8.10. I recently upgraded to 8.10 from an old 7.04 (actually 3 back-to-back upgrades). Wireless used to work quite well for me on 7.04, but not so on 8.10.

This is my wireless card:

04:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

At boot, I had no wireless connectivity, so when I tried sudo /etc/init.d/networking restart

I got this:


 * Reconfiguring network interfaces...                                                                      ath0: ERROR while getting interface flags: No such device
wpa_supplicant: "madwifi" wpa-driver is unsupported
wpa_supplicant: using "wext" wpa-driver instead ...
ioctl[SIOCGIFFLAGS]: No such device
Could not get interface 'ath0' flags
ioctl[SIOCSIWPMKSA]: No such device
ioctl[SIOCSIWMODE]: No such device
Could not configure driver to use managed mode
ioctl[SIOCGIWRANGE]: No such device
ioctl[SIOCGIFINDEX]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODE]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODE]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODE]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODE]: No such device
ioctl[SIOCSIWAP]: No such device
ioctl[SIOCGIFFLAGS]: No such device
wpa_supplicant: /sbin/wpa_supplicant daemon failed to start
run-parts: /etc/network/if-pre-up.d/wpasupplicant exited with return code 1
SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
ath0: ERROR while getting interface flags: No such device
Failed to bring up ath0.
Ignoring unknown interface eth1=eth1.
Ignoring unknown interface eth2=eth2.
Ignoring unknown interface wifi0=wifi0.
Ignoring unknown interface eth0=eth0.

---

### Post by Olivier2371 on 2008-11-22
You might want to check the following links.

[http://linuxwireless.org/en/users/Drivers/ath5k]("http://linuxwireless.org/en/users/Drivers/ath5k")

[http://linuxwireless.org/en/users/Drivers/ath9k]("http://linuxwireless.org/en/users/Drivers/ath9k")

I hope this will help.

---

