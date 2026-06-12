---
title: "WPA Supplicant Stopped Working!?"
date: 2006-12-22
forum: Networking &amp; Wireless
---

### Post by Chongo on 2006-12-22
Hi,

I configured my laptop to work on two wireless networks with WPA via wpa_supplicant in July this year. In the last couple of weeks, I have been unable to connect to either network, and I don't know why. There seems to be something wrong with WPA Supplicant.

*

My /etc/network/interfaces:

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wpa-driver wext
wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf

*

My /etc/wpa_supplicant/wpa_supplicant.conf:

ctrl_interface=/var/run/wpa_supplicant

network={
ssid="Homer"
proto=WPA
pairwise=TKIP
key_mgmt=WPA-PSK
psk=Blaa Blaa
}

network={
ssid="NapAir"
proto=WPA
pairwise=TKIP
key_mgmt=IEEE8021X
eap=PEAP
phase2="auth=MSCHAPV2"
identity="Blaa Blaa"
password="Blaa Blaa"
}

network={
ssid="000D0BBCD928"
}

network={
ssid="gnerwifi"

*

I have an IBM ThinkPad T43 with the Intel 2200BG Wireless Mini PCI card, and Kubuntu 6.06 LTS with all of the updates.

*

When firing up the network connection (sudo ifup eth1) I get the following barf:

Line 24: WPA-PSK accepted for key management, but no PSK configured.
Line 24: failed to parse network block.
Line 28: WPA-PSK accepted for key management, but no PSK configured.
Line 28: failed to parse network block.
Failed to read read or parse configuration 'etc/wpa_supplicant/wpa_supplicant.conf'.
wpa_supplicant: failed to locate ctrl_interface socket, exiting
run-parts: /etc/network/if-pre-up.d/wpasupplicant exited with return code 1

(then onto DHCP, which fails to receive any offers)

*

I have not changed the configuration since it worked, and so I am not sure what to do. Has anyone got any suggestions? If so, that would be tremendously appreciated.

Best wishes,

Tom

---

### Post by wieman01 on 2006-12-23
All I can offer is the thread in my signature... It works for most of the people.

---

