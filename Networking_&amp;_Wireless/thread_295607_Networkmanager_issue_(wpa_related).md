---
title: "Networkmanager issue (wpa related)"
date: 2006-11-08
forum: Networking &amp; Wireless
---

### Post by Julius on 2006-11-08
So I could finally connect to my uni wifi network under ubuntu. My uni uses WPA/WPA2 enterprise, TTLS, etc.

The /etc/wpa_supplicant.conf file I use is this:
```

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
eapol_version=1
ap_scan=2
fast_reauth=1
network={

ssid="eduroam"
key_mgmt=WPA-EAP
proto=WPA
pairwise=TKIP
group=TKIP
eap=TTLS
identity="<username>"
password="<password>"
phase2="auth=PAP"

}

```

When I attempted to connect, doing
sudo wpa_supplicant -c /etc/wpa_supplicant.conf -i eth1 -Dipw

I got the following:
```

ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Failed to set encryption.
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Failed to set encryption.
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Failed to set encryption.
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Failed to set encryption.
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Trying to associate with SSID 'eduroam'
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
CTRL-EVENT-TERMINATING - signal 2 received
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported

```

Then, I read somwhere I should've tried with wext, and it worked, and I could connect using dhclient eth1

```

julius@julius-laptop:~$ sudo wpa_supplicant -c /etc/wpa_supplicant.conf -i eth1 -Dwext
Password:
Trying to associate with SSID 'eduroam'
Associated with 00:0b:86:cd:c2:20
CTRL-EVENT-EAP-STARTED EAP authentication started
CTRL-EVENT-EAP-METHOD EAP vendor 0 method 21 (TTLS) selected
CTRL-EVENT-EAP-SUCCESS EAP authentication completed successfully
WPA: Key negotiation completed with 00:0b:86:cd:c2:20 [PTK=TKIP GTK=TKIP]
CTRL-EVENT-CONNECTED - Connection to 00:0b:86:cd:c2:20 completed (auth) [id=0 id_str=]

```

Since I use NetworkManager to manage my networks (in home and somewhere else), I tried connecting with it, but it returns this (used NetworkManager --no-daemon)

```

NetworkManager: <information>   Deactivating device eth1.
NetworkManager: <information>   Activation (eth1): cancelling...
NetworkManager: <information>   Activation (eth1) cancellation handler scheduled...
NetworkManager: <information>   Activation (eth1): waiting for device to cancel activation.
NetworkManager: <information>   Activation (eth1) cancellation handled.
NetworkManager: <information>   Activation (eth1): cancelled.
sendmsg(CTRL_IFACE monitor): No such file or directory
NetworkManager: <information>   Device eth1 activation scheduled...
NetworkManager: <information>   Activation (eth1) started...
NetworkManager: <information>   Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
NetworkManager: <information>   Activation (eth1) Stage 1 of 5 (Device Prepare) started...
NetworkManager: <information>   Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
NetworkManager: <information>   Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
NetworkManager: <information>   Activation (eth1) Stage 2 of 5 (Device Configure) starting...
NetworkManager: <information>   Activation (eth1/wireless): access point 'eduroam' is encrypted, but NO valid key exists.  New key needed.
NetworkManager: <information>   Activation (eth1) New wireless user key requested for network 'eduroam'.
NetworkManager: <information>   Activation (eth1) Stage 2 of 5 (Device Configure) complete.
NetworkManager: <information>   Activation (eth1) New wireless user key for network 'eduroam' received.
NetworkManager: <information>   Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
NetworkManager: <information>   Activation (eth1) Stage 1 of 5 (Device Prepare) started...
NetworkManager: <information>   Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
NetworkManager: <information>   Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
NetworkManager: <information>   Activation (eth1) Stage 2 of 5 (Device Configure) starting...
NetworkManager: <information>   Activation (eth1/wireless): access point 'eduroam' is encrypted, and a key exists.  No new key needed.
NetworkManager: <information>   SUP: sending command 'INTERFACE_ADD eth1                wext    /var/run/wpa_supplicant '
NetworkManager: <information>   SUP: response was 'OK'
NetworkManager: <information>   SUP: sending command 'AP_SCAN 1'
NetworkManager: <information>   SUP: response was 'OK'
NetworkManager: <information>   SUP: sending command 'ADD_NETWORK'
NetworkManager: <information>   SUP: response was '0'
NetworkManager: <information>   SUP: sending command 'SET_NETWORK 0 ssid 656475726f616d'
NetworkManager: <information>   SUP: response was 'OK'
NetworkManager: <information>   SUP: sending command 'SET_NETWORK 0 proto WPA'
NetworkManager: <information>   SUP: response was 'OK'
NetworkManager: <information>   SUP: sending command 'SET_NETWORK 0 key_mgmt WPA-EAP'
NetworkManager: <information>   SUP: response was 'OK'
NetworkManager: <information>   SUP: sending command 'SET_NETWORK 0 eap TTLS'
NetworkManager: <information>   SUP: response was 'OK'
NetworkManager: <information>   SUP: sending command 'SET_NETWORK 0 identity "<uname>"'
NetworkManager: <information>   SUP: response was 'OK'
NetworkManager: <information>   SUP: sending command 'SET_NETWORK 0 password <password>'
NetworkManager: <information>   SUP: response was 'OK'
NetworkManager: <information>   SUP: sending command 'SET_NETWORK 0 pairwise CCMP'
NetworkManager: <information>   SUP: response was 'OK'
NetworkManager: <information>   SUP: sending command 'SET_NETWORK 0 group CCMP'
NetworkManager: <information>   SUP: response was 'OK'
NetworkManager: <information>   SUP: sending command 'ENABLE_NETWORK 0'
NetworkManager: <information>   SUP: response was 'OK'
NetworkManager: <information>   Activation (eth1) Stage 2 of 5 (Device Configure) complete.
NetworkManager: <information>   wpa_supplicant(6468): Global control interface '/var/run/wpa_supplicant-global'
NetworkManager: <information>   wpa_supplicant(6468): RX global ctrl_iface - hexdump_ascii(len=49):
NetworkManager: <information>   wpa_supplicant(6468):      49 4e 54 45 52 46 41 43 45 5f 41 44 44 20 65 74   INTERFACE_ADD et
NetworkManager: <information>   wpa_supplicant(6468):      68 31 09 09 77 65 78 74 09 2f 76 61 72 2f 72 75   h1__wext_/var/ru
NetworkManager: <information>   wpa_supplicant(6468):      6e 2f 77 70 61 5f 73 75 70 70 6c 69 63 61 6e 74   n/wpa_supplicant
NetworkManager: <information>   wpa_supplicant(6468):      09       
...
...
                                                      
[cropped]

...
...

nm_device_802_11_wireless_update_bssid (): Roamed from BSSID 00:0B:86:CD:A5:80 to 00:0B:86:CD:C0:80 on wireless network 'eduroam'
NetworkManager: <debug info>    [1163002203.942446] nm_dbus_signal_filter (): NetworkManagerInfo triggered update of wireless network 'eduroam'
NetworkManager: <debug info>    [1163002203.942769] nm_dbus_signal_filter (): NetworkManagerInfo triggered update of wireless network 'eduroam'
NetworkManager: <information>   Old device 'eth1' activating, won't change.

```

(I cropped it because the log is too long)
Why can't NetworkManager connect? The settings seem to be the same. Is there anyway I can tweak it so I can connect using it?

---

### Post by emdeem on 2006-11-08
To get NM to work, I left the stock wpasupplicant.conf file as-is and did this:

[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

---

### Post by Julius on 2006-11-10
> **emdeem said:**
> To get NM to work, I left the stock wpasupplicant.conf file as-is and did this:

[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

The thing is that NM works, even with WPA. In home, I have SSID not broadcasted and WPA and NM works like a charm. It's with my uni I can't get it to work, even after copying the same things I have in the wpa_supplicant.conf file.
Will doing that /etc/default/ file thing change something? What does that do, exactly? Because my problem is not that WPA doesn't work with NM, it does!

---

