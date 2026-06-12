---
title: "[SOLVED] setting AP mac address failed - kernel bug?"
date: 2008-09-20
forum: Networking &amp; Wireless
---

### Post by eben on 2008-09-20
hi, after a reinstall i having trouble to get my wlan working again.
i'm trying to connect to a wpa secured wlan with a zyair b-220 card. 
i'm using ndiswrapper cause the zd1201u module does not support wpa.

when i try to connect dmesg shows:

[   64.749508] ndiswrapper (iw_set_ap_address:575): setting AP mac address failed

Does anyone know a workaround for this?

Any help will be greatly appreciated.....


/etc/wpa_supplicant.conf

```
ctrl_interface=/var/run/wpa_supplicant
eapol_version=1
# 0: Der Treiber des Interfaces kümmert sich um das Scannen von Netzen und die AP-Auswahl.
#    Dieser Modus sollte benutzt werden, wenn man eine Verschlüsselung auf ein Kabelnetzwerk legt.
# 1: wpa_supplicant kümmert sich um das Scannen von Netzen und die AP-Auswahl.
# 2: Fast wie 0, es wird aber mit Hilfe von Sicherheitsrichtlinien und der SSID zu APs verbunden (BSSID wird nicht unterstützt)
#
# Normalerweise funktioniert entweder Modus 1 oder Modus 2.
ap_scan=2
network={
        ssid="SSID"
        #scan_ssid=1
        proto=WPA
        key_mgmt=WPA-PSK
        pairwise=TKIP 
        group=TKIP
        psk="PSK"
}

```

/etc/network/interfaces

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
iface wlan0 inet dhcp
 wpa-conf /etc/wpa_supplicant.conf
#auto eth0
iface eth0 inet dhcp

auto wlan0


```

```
uname -r
2.6.24-19-generic

```

[https://lists.ubuntu.com/archives/kernel-bugs/2008-March/034355.html]("https://lists.ubuntu.com/archives/kernel-bugs/2008-March/034355.html")

[http://sudan.ubuntuforums.com/showthread.php?t=770523]("http://sudan.ubuntuforums.com/showthread.php?t=770523")

---

### Post by eben on 2008-09-21
as i was thinking my problem is related to a bug 

[https://bugs.launchpad.net/ubuntu/+source/dhcdbd/+bug/205000]("https://bugs.launchpad.net/ubuntu/+source/dhcdbd/+bug/205000")

[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/194714]("https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/194714")

as the bug is related to 'linux-ubuntu-modules' my solution to the problem is to install the old gutsy linux-ubuntu-modules-2.6.22-14-generic_2.6.22-14.37_i386.deb


i'm sorry for my english

---

### Post by eben on 2008-09-21
:guitar: i finally got my wlan working again. all you have to do when you get this "setting AP mac address failed" message is to change "wpa-ap-scan 1" to "wpa-ap-scan 2" in your /etc/network/interfaces / /etc/wpa_supplicant.conf

---

