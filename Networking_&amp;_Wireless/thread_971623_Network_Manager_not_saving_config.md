---
title: "Network Manager not saving config"
date: 2008-11-05
forum: Networking &amp; Wireless
---

### Post by hornetster on 2008-11-05
Installed 8.10 and DHCP networking working fine. I want to configure a manual IP and have done that using network manager, saved and forced a restart of network manager (sudo /etc/init.d/NetworkManager restart) and that works ok.... BUT... after a reboot it reverts back to DHCP.
Have noticed that there is no 'unlock' button on the networkmanager GUI, therefore I am really only editing it as a standard user... so why is it letting me change it, and where is the unlock button??:confused:
   John.

---

### Post by mscherer82 on 2008-11-05
I got the same problem. 
I upgraded from 8.04 and had a wireless configuration left. Now, I try to delete this connection and get the following message on the command line: 

(nm-connection-editor:7462): GLib-CRITICAL **: g_hash_table_foreach: assertion `hash_table != NULL' failed
** Message: nm_connection_list_new: failed to load VPN plugins: Couldn't read VPN .name files directory /etc/NetworkManager/VPN.

** (nm-connection-editor:7462): WARNING **: nma_gconf_connection_changed: Invalid connection /system/networking/connections/1: 'NMSettingWireless' / 'ssid' invalid: 2

---

### Post by hornetster on 2008-11-06
OK, if nobody can tell me that :( , How about being able to tell me the commands I need to put in (I assume...) /network/interfaces to set a fixed IP/DNS?

PLEASE!

---

### Post by TenPlus1 on 2008-11-06
I tried editing my wireless settings using the network manager and it didn't save the settings in the /etc/network/interfaces so I dunno where it's actually kept...

Your better off editing the file itself and changing the following to suit you:

auto lo
iface lo inet loopback

iface wlan0 inet static
address 192.168.0.1
netmask 255.255.255.0
wireless-mode ad-hoc
wireless-keymode open <---  these are only needed for wireless
wireless-key s:password
wireless-essid mywireless

auto wlan0

---

