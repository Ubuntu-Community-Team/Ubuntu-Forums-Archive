---
title: "Networking problems in Gutsy"
date: 2007-11-05
forum: Networking &amp; Wireless
---

### Post by mikeazo on 2007-11-05
Since upgrading to gutsy I have been having tons of problems with networking (mostly wireless).  I followed the instructions at [http://ubuntuforums.org/showthread.php?t=599474](http://ubuntuforums.org/showthread.php?t=599474) but am still having the same issues.  

NetworkManager displays the following information:

NetworkManager: <info>  starting...
NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/dell_wlan_switch

(NetworkManager:5662): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `handler_id > 0' failed
NetworkManager: <info>  Updating allowed wireless network lists.
NetworkManager: <info>  Error getting killswitch power: org.freedesktop.Hal.Device.KillSwitch.NotSupported - dellWirelessCtl returned 4
NetworkManager: <info>  Wireless now enabled by radio killswitch
NetworkManager: <WARN>  nm_dbus_get_network_data_cb(): nm_dbus_get_network_data_cb(): dbus returned an error.
  (org.freedesktop.NetworkManagerInfo.NoSecurity) org.freedesktop.NetworkManagerInfo.NoSecurity

NetworkManager: <WARN>  nm_dbus_get_network_data_cb(): nm_dbus_get_network_data_cb(): dbus returned an error.
  (org.freedesktop.NetworkManagerInfo.NoSecurity) org.freedesktop.NetworkManagerInfo.NoSecurity

NetworkManager: <WARN>  nm_dbus_get_network_data_cb(): nm_dbus_get_network_data_cb(): dbus returned an error.
  (org.freedesktop.NetworkManagerInfo.NoSecurity) org.freedesktop.NetworkManagerInfo.NoSecurity

NetworkManager: <WARN>  nm_dbus_get_network_data_cb(): nm_dbus_get_network_data_cb(): dbus returned an error.
  (org.freedesktop.NetworkManagerInfo.NoSecurity) org.freedesktop.NetworkManagerInfo.NoSecurity

NetworkManager: <info>  Error getting killswitch power: org.freedesktop.Hal.Device.KillSwitch.NotSupported - dellWirelessCtl returned 4
NetworkManager: <info>  Error getting killswitch power: org.freedesktop.Hal.Device.KillSwitch.NotSupported - dellWirelessCtl returned 4
NetworkManager: <info>  Error getting killswitch power: org.freedesktop.Hal.Device.KillSwitch.NotSupported - dellWirelessCtl returned 4
NetworkManager: <info>  Error getting killswitch power: org.freedesktop.Hal.Device.KillSwitch.NotSupported - dellWirelessCtl returned 4
NetworkManager: <info>  Error getting killswitch power: org.freedesktop.Hal.Device.KillSwitch.NotSupported - dellWirelessCtl returned 4


I have an ipw2200.  Any ideas?  Everything worked great in feisty.  Also, my ethernet card more or less works.  I usually have to manually send dhcp requests, but other than that it works fine.

---

