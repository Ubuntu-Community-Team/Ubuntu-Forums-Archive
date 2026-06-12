---
title: "&quot;NO valid key exists&quot; on some wirless networks"
date: 2008-07-07
forum: Networking &amp; Wireless
---

### Post by s_baramov on 2008-07-07
Hello: 

I am fairly new to Ubuntu and so far I am really impressed. The problem I am having is with some wireless networks. I have a Dell Latitude D620 with a  Dell 1390 WLAN (BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)) wireless. I have managed to install the ndiswrapper using the instructions posted here : [http://ubuntuforums.org/showthread.php?t=760568](http://ubuntuforums.org/showthread.php?t=760568). It has worked nicely with my home network with WPA2 encryption. However it fails to connect to the corporate network of the company I work for. Comparing the log from the office network and the log from my home network leads to the following message :

```

Activation (wlan0/wireless): access point 'mycorp-morris' is encrypted, but NO valid key exists.  New key needed.

```

Here is the log (/var/log/syslog) for the corporate network after grep wlan0: 

```

NetworkManager: <debug> nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:15:C7:A8:7F:D0 to 00:15:C7:A8:95:60 on wireless network 'mycorp-morris' 
NetworkManager: <debug> nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'mycorp-morris' 
NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
NetworkManager: <debug> nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:15:C7:A8:95:60 to 00:15:C7:A8:7F:D0 on wireless network 'mycorp-morris' 
NetworkManager: <debug> nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'mycorp-morris' 
NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
NetworkManager: <debug> nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:15:C7:A8:7F:D0 to 00:15:C7:A8:95:60 on wireless network 'mycorp-morris' 
NetworkManager: <debug> nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'mycorp-morris' 
NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
NetworkManager: <debug> nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:15:C7:A8:95:60 to 00:15:C7:A8:7F:D0 on wireless network 'mycorp-morris' 
NetworkManager: <debug> nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'mycorp-morris' 
NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
kernel: [ 1383.169913] ADDRCONF(NETDEV_UP): eth0: link is not ready
NetworkManager: <debug> nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:15:C7:A8:7F:D0 to 00:15:C7:A8:95:60 on wireless network 'mycorp-morris' 
NetworkManager: <debug> nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'mycorp-morris' 
NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
NetworkManager: <debug> nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:15:C7:A8:95:60 to 00:15:C7:A8:7F:D0 on wireless network 'mycorp-morris' 
NetworkManager: <debug> nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'mycorp-morris' 
NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
NetworkManager: <debug> nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:15:C7:A8:7F:D0 to 00:15:C7:A8:95:60 on wireless network 'mycorp-morris' 
NetworkManager: <debug> nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'mycorp-morris' 
NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
NetworkManager: <debug> nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:15:C7:A8:95:60 to 00:15:C7:A8:7F:D0 on wireless network 'mycorp-morris' 
NetworkManager: <debug> nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'mycorp-morris' 
NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
NetworkManager: <info>  Activation (wlan0/wireless): association took too long (>60s), failing activation. 
NetworkManager: <info>  Activation (wlan0) failure scheduled... 
NetworkManager: <info>  Activation (wlan0) failed for access point (mycorp-morris) 
NetworkManager: <info>  Activation (wlan0) failed. 
NetworkManager: <info>  Deactivating device wlan0. 
avahi-daemon[5080]: Withdrawing address record for fe80::218:f3ff:fee1:d20d on wlan0.
NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Invalid argument 
/USR/SBIN/CRON[8050]: (root) CMD ([ -x /usr/lib/sysstat/sa1 ] && { [ -r "$DEFAULT" ] && . "$DEFAULT" ; [ "$ENABLED" = "true" ] && exec /usr/lib/sysstat/sa1 $SA1_OPTIONS 1 1 ; })
NetworkManager: <debug> nm_device_802_11_wireless_get_activation_ap(): Forcing AP 'mycorp-morris' 
NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/wlan0 / mycorp-morris 
NetworkManager: <info>  Deactivating device wlan0. 
NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Invalid argument 
NetworkManager: <info>  Device wlan0 activation scheduled... 
NetworkManager: <info>  Activation (wlan0) started... 
NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
NetworkManager: <info>  Activation (wlan0/wireless): access point 'mycorp-morris' is encrypted, but NO valid key exists.  New key needed. 
NetworkManager: <info>  Activation (wlan0) New wireless user key requested for network 'mycorp-morris'. 
NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
NetworkManager: <info>  Activation (wlan0) New wireless user key for network 'mycorp-morris' received. 
NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 

```


Essentially, every time I try to connect it asks be for the password. I do provide the correct password for sure. Needless to say that the wireless just works like a charm under Win XP SP2. Windows reports a WPA connection with TKIP encryption. I have tried several location including a different floor in order to try different access points. Almost the same result. Once I manage to for a short period of time. However, the connection dropped in couple of minutes. Never managed to repeat that experience. 

On the other side no problem with my home network. It connects and works fine. 

I tried other unencrypted network and it worked fine as well. So how do i go about this. How do i troubleshoot it? Help will be appreciated. 

Here is some more info : 

```

$ lspci -nn | grep 14e4
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express [14e4:1600] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)

$ ndiswrapper -l

bcmwl5 : driver installed
        device (14E4:4311) present (alternate driver: bcm43xx)
 
$ lsmod | grep b43

$ lsmod | grep ndiswrapper
ndiswrapper           192920  0 
usbcore               146028  4 ndiswrapper,ehci_hcd,uhci_hcd

$ ls -l /etc/rc.local
-rwxr-xr-x 1 root root 421 2008-06-08 08:48 /etc/rc.local

```

---

### Post by s_baramov on 2008-07-08
Just this morning I have tried again, I was able to connect for a while. The card lost the connection almost immediately, less then a minute. I found this bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/199191](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/199191) that might be related. The bug seems to be fixed in Intrepid. I guess I have to wait until October. Kind a sad :(

---

