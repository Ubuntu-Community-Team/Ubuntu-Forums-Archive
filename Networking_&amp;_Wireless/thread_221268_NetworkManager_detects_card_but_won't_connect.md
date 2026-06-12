---
title: "NetworkManager detects card but won't connect"
date: 2006-07-22
forum: Networking &amp; Wireless
---

### Post by line72 on 2006-07-22
I have a dell precision with a TrueMobile 1150 wireless card.  The card uses the orinoco_cs and I can connect to wireless networks manually with iwconfig or the network configuration tool.  NetworkManager (nm-applet) detects that card, scans the network and shows all the available networks.  However, NetworkManager is never able to fully establish a connection to any network (with or without wep).  In /var/log/message is get the following repeated several times

```

Jul 22 19:35:03 localhost kernel: [17206275.756000] eth1: New link status: Disconnected (0002)
Jul 22 19:35:03 localhost kernel: [17206275.928000] eth1: New link status: Connected (0001)

```

and in /var/log/daemon.log:

```

Jul 22 19:34:58 localhost NetworkManager: <information>^Iwpa_supplicant(16721): Wireless event: cmd=0x8b15 len=20
Jul 22 19:34:58 localhost NetworkManager: <information>^Iwpa_supplicant(16721): Wireless event: new AP: 00:0f:b5:ea:a5:ba
Jul 22 19:34:58 localhost NetworkManager: <information>^Iwpa_supplicant(16721): State: DISCONNECTED -> ASSOCIATED
Jul 22 19:34:58 localhost NetworkManager: <information>^Iwpa_supplicant(16721): Associated to a new BSS: BSSID=00:0f:b5:ea:a5:ba
Jul 22 19:34:58 localhost NetworkManager: <information>^Iwpa_supplicant(16721): No network configuration found for the current AP
Jul 22 19:34:58 localhost NetworkManager: <information>^Iwpa_supplicant(16721): State: ASSOCIATED -> DISCONNECTED
Jul 22 19:34:58 localhost NetworkManager: <information>^Iwpa_supplicant(16721): wpa_driver_wext_disassociate
Jul 22 19:34:58 localhost NetworkManager: <information>^Iwpa_supplicant(16721): No keys have been configured - skip key clearing
Jul 22 19:34:58 localhost NetworkManager: <information>^Iwpa_supplicant(16721): EAPOL: External notification - portEnabled=0
Jul 22 19:34:58 localhost NetworkManager: <information>^Iwpa_supplicant(16721): EAPOL: External notification - portValid=0
Jul 22 19:34:58 localhost NetworkManager: <information>^Iwpa_supplicant(16721): RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
Jul 22 19:34:58 localhost NetworkManager: <information>^Iwpa_supplicant(16721): Authentication with 00:0f:b5:ea:a5:ba timed out.
Jul 22 19:34:58 localhost NetworkManager: <information>^Iwpa_supplicant(16721): CTRL_IFACE monitor send - hexdump(len=42): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 34 39 30 2d 31 00 01 00
Jul 22 19:34:58 localhost NetworkManager: <information>^Iwpa_supplicant(16721): BSSID 00:0f:b5:ea:a5:ba blacklist count incremented to 19
Jul 22 19:34:58 localhost NetworkManager: <information>^Iwpa_supplicant(16721): State: DISCONNECTED -> DISCONNECTED
Jul 22 19:34:58 localhost NetworkManager: <information>^Iwpa_supplicant(16721): wpa_driver_wext_disassociate
Jul 22 19:34:58 localhost NetworkManager: <information>^Iwpa_supplicant(16721): No keys have been configured - skip key clearing
Jul 22 19:34:58 localhost NetworkManager: <information>^Iwpa_supplicant(16721): EAPOL: External notification - portEnabled=0
Jul 22 19:34:58 localhost NetworkManager: <information>^Iwpa_supplicant(16721): EAPOL: External notification - portValid=0
Jul 22 19:34:58 localhost NetworkManager: <information>^Iwpa_supplicant(16721): Setting scan request: 0 sec 0 usec
Jul 22 19:34:58 localhost NetworkManager: <information>^Iwpa_supplicant(16721): State: DISCONNECTED -> SCANNING
Jul 22 19:34:58 localhost NetworkManager: <information>^Iwpa_supplicant(16721): Trying to associate with SSID 'Becks'
Jul 22 19:34:58 localhost NetworkManager: <information>^Iwpa_supplicant(16721): 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 34 39 30 2d 31 00 01 00
Jul 22 19:34:58 localhost NetworkManager: <information>^Iwpa_supplicant(16721): Cancelling scan request
Jul 22 19:34:58 localhost NetworkManager: <information>^Iwpa_supplicant(16721): WPA: clearing own WPA/RSN IE
Jul 22 19:34:58 localhost NetworkManager: <information>^Iwpa_supplicant(16721): Automatic auth_alg selection: 0x1
Jul 22 19:34:58 localhost NetworkManager: <information>^Iwpa_supplicant(16721): WPA: clearing AP WPA IE
Jul 22 19:34:58 localhost NetworkManager: <information>^Iwpa_supplicant(16721): WPA: clearing AP RSN IE
Jul 22 19:34:58 localhost NetworkManager: <information>^Iwpa_supplicant(16721): WPA: clearing own WPA/RSN IE
Jul 22 19:34:58 localhost NetworkManager: <information>^Iwpa_supplicant(16721): No keys have been configured - skip key clearing
Jul 22 19:34:58 localhost NetworkManager: <information>^Iwpa_supplicant(16721): wpa_driver_wext_set_drop_unencrypted
Jul 22 19:34:58 localhost NetworkManager: <information>^Iwpa_supplicant(16721): State: SCANNING -> ASSOCIATING
Jul 22 19:34:58 localhost NetworkManager: <information>^Iwpa_supplicant(16721): wpa_driver_wext_associate
Jul 22 19:34:58 localhost NetworkManager: <information>^Iwpa_supplicant(16721): Association request to the driver failed
Jul 22 19:34:58 localhost NetworkManager: <information>^Iwpa_supplicant(16721): CTRL_IFACE monitor send - hexdump(len=42): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 34 39 30 2d 31 00 01 00
Jul 22 19:34:58 localhost NetworkManager: <information>^Iwpa_supplicant(16721): Setting authentication timeout: 5 sec 0 usec
Jul 22 19:34:58 localhost NetworkManager: <information>^Iwpa_supplicant(16721): EAPOL: External notification - portControl=ForceAuthorized
Jul 22 19:34:58 localhost NetworkManager: <information>^Iwpa_supplicant(16721): Wireless event: cmd=0x8b06 len=8
Jul 22 19:34:58 localhost NetworkManager: <information>^Iwpa_supplicant(16721): Wireless event: cmd=0x8b1a len=14
Jul 22 19:34:58 localhost NetworkManager: <information>^Iwpa_supplicant(16721): RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
Jul 22 19:34:58 localhost NetworkManager: <information>^Iwpa_supplicant(16721): Wireless event: cmd=0x8b15 len=20
Jul 22 19:34:58 localhost NetworkManager: <information>^Iwpa_supplicant(16721): Wireless event: new AP: 44:44:44:44:44:44
Jul 22 19:34:58 localhost NetworkManager: <information>^Iwpa_supplicant(16721): BSSID 00:0f:b5:ea:a5:ba blacklist count incremented to 20
Jul 22 19:34:58 localhost NetworkManager: <information>^Iwpa_supplicant(16721): State: ASSOCIATING -> DISCONNECTED
Jul 22 19:35:08 localhost NetworkManager: <information>^IActivation (eth1/wireless): association took too long (>60s), failing activation.
Jul 22 19:35:08 localhost NetworkManager: <information>^IActivation (eth1) failure scheduled...
Jul 22 19:35:08 localhost NetworkManager: <information>^IActivation (eth1) failed for access point (Becks)
Jul 22 19:35:08 localhost NetworkManager: <information>^IActivation (eth1) failed.
Jul 22 19:35:08 localhost NetworkManager: <information>^IDeactivating device eth1.
Jul 22 19:35:08 localhost dhclient: receive_packet failed on eth1: Network is down
Jul 22 19:35:08 localhost dhclient: receive_packet failed on eth1: Network is down
Jul 22 19:35:10 localhost NetworkManager: <information>^Imatch

```

Thanks in advance.
/Mark

---

### Post by chuvisco on 2006-07-22
See this [post]("http://ubuntuforums.org/showpost.php?p=1053550&postcount=26").

---

### Post by line72 on 2006-07-23
I removed network-manager and network-manager-gnome, then rebooted and installed the older network-manager and nm-applet from your post.  I reboot again and when I tried to start nm-applet, it complained about missing resources and wouldn't start.

---

### Post by chuvisco on 2006-07-23
Oh, yes, there is a fix for that.  Do 

sudo gtk-update-icon-cache -f /usr/share/icons/hicolor/

---

### Post by line72 on 2006-07-23
Thanks, that worked perfectly!  Is there anyway to keep ubuntu from trying to update network manager?

---

### Post by chuvisco on 2006-07-23
Yes, lock the version in Synaptic (it's in one of the menus).  

NetworkManager started using wpa_supplicant (even for non-WPA networks) with version 0.6, which seems to be incompatible with the orinoco_cs driver included in Dapper.  0.6+ works perfectly in Fedora 5 and SuSE 10.1, and I think it's because they use a newer kernel, and therefore an updated orinoco driver.

---

### Post by line72 on 2006-07-24
Thanks for all your help.  It's working perfectly now!

---

### Post by line72 on 2006-09-20
Does anyone know if the latest version of NetworkManager is working with this card yet ?

---

