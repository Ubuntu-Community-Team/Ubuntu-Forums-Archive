---
title: "WPA problems"
date: 2005-11-13
forum: Networking &amp; Wireless
---

### Post by kch_86 on 2005-11-13
Ok i followed this guide:  [https://wiki.ubuntu.com/forum/hardware/ndiswrapperWithWPA]("https://wiki.ubuntu.com/forum/hardware/ndiswrapperWithWPA")

to try and set up wpa w/ ndiswrapper

but when I run the command:  sudo ifconfig wlan0 up && sudo /usr/sbin/wpa_supplicant -w -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf -dd

I get an error saying this: Initializing interface 'ath0' conf '/etc/wpa_supplicant.conf' driver 'ndiswrapper'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
eapol_version=1
ap_scan=1
fast_reauth=1
Line: 15 - start of a new network block
ssid - hexdump_ascii(len=6):
     50 55 52 44 55 45                                 PURDUE
key_mgmt: 0x2
proto: 0x1
[B]Line 20: WPA-PSK accepted for key management, but no PSK configured.
Line 20: failed to parse network block.[/B]
Failed to read configuration file '/etc/wpa_supplicant.conf'.

My router is set up for wpa-psk and i'm sure that i have the right psk. Anyone have any ideas?

---

### Post by firecat53 on 2005-11-13
Ok...couple of questions:

1. Does your connection work properly without WPA?
2. Can you show us your wpa_supplicant.conf file? Mine doesn't have any of the fast_reauth, eapol, ap_scan, etc... before the network block.
3. Don't think this is it, but check the permissions of the .conf file.

It will work!  I've got working automatically on boot by adding to the /etc/network/interfaces file.

good luck!
Scott

---

### Post by kch_86 on 2005-11-13
ok...
1. Yes my connection works fine w/out WPA.
2.

 Minimal /etc/wpa_supplicant.conf to associate with open
#  access points. Please see 
#  /usr/share/doc/wpasupplicant/wpa_supplicant.conf.gz for #more complete
#  configuration parameters.

#ctrl_interface=/var/run/wpa_supplicant
#ctrl_interface_group=0

eapol_version=1
ap_scan=1
fast_reauth=1

### Associate with any open access point
###  Scans/ESSID changes can be done with wpa_cli
network={
        ssid="PURDUE"
#psk="khayward"							psk=54bc6b9c3188d1241c8a204c4e1e42cf786e8d50f22cc7b8444ce9308b5be629
	key_mgmt=WPA-PSK
        proto=WPA
}

I have tried edditng out the eapol, apscan, and fastreauth, but still doesnt work.

---

### Post by kch_86 on 2005-11-14
would it matter that my wireless card is not called wlan0? In network ui its called ath0. But i did use the commands i stated in my first post adjusted for the different name.

---

### Post by kch_86 on 2005-11-15
i have a netgear 311t and i have read a couple of threads about madwifi. Should I use this? If so do i have to uninstall ndiswrapper? How do I uninstall it?

---

