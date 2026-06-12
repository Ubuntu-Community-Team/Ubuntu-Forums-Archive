---
title: "how to get wireless working on boot"
date: 2008-07-08
forum: Networking &amp; Wireless
---

### Post by eleach on 2008-07-08
I have a Dell Inspiron. I installed the Wicd wireless manager. Wireless works fine but does not start on booting.

I'm using the Intel 945 and the ipw3945 driver that came with the laptop.

Below is my /etc/network/interfaces file. I suspect I need to change something in this file. The wireless card is eth1.

Thanks

------

auto lo
iface lo inet loopback

iface eth0 inet dhcp

iface eth1 inet dhcp
wpa-psk <long string>
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid rmrm6

auto eth1

---

