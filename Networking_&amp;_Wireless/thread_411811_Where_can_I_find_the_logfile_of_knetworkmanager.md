---
title: "Where can I find the logfile of knetworkmanager?"
date: 2007-04-17
forum: Networking &amp; Wireless
---

### Post by movies1978 on 2007-04-17
See topic,
cannot find the location of the logfile in Dapper LTS
Best regards 
movies

---

### Post by dbott67 on 2007-04-17
On Ubuntu, the NetworkManager is in /var/log/daemon.log:
```
dbott@feisty:/var/log$ cat daemon.log | grep NetworkManager
Apr 15 22:35:03 feisty NetworkManager: <information>^IUpdating allowed wireless network lists.
Apr 15 22:35:03 feisty NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored..
Apr 15 22:41:54 feisty NetworkManager: <information>^IUpdating allowed wireless network lists.
Apr 15 22:41:55 feisty NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored..
Apr 15 22:41:59 feisty NetworkManager: <information>^IDHCP daemon state is now 14 (normal exit) for interface eth0
Apr 15 22:42:10 feisty NetworkManager: <information>^ISWITCH: terminating current connection 'eth0' because it's no longer valid.
Apr 15 22:42:10 feisty NetworkManager: <information>^IDeactivating device eth0.
Apr 15 22:42:10 feisty NetworkManager: nm_device_is_802_3_ethernet: assertion `dev != NULL' failed
Apr 15 22:42:10 feisty NetworkManager: nm_device_is_802_11_wireless: assertion `dev != NULL' failed
Apr 15 22:42:10 feisty NetworkManager: <information>^IWill activate wired connection 'eth0' because it now has a link.
Apr 15 22:42:10 feisty NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'.
Apr 15 22:42:10 feisty NetworkManager: <information>^IWill activate connection 'eth0'.
Apr 15 22:42:10 feisty NetworkManager: <information>^IDevice eth0 activation scheduled...
Apr 15 22:42:10 feisty NetworkManager: <information>^IActivation (eth0) started...
Apr 15 22:42:10 feisty NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 15 22:42:10 feisty NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started...
Apr 15 22:42:10 feisty NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Apr 15 22:42:10 feisty NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete.
Apr 15 22:42:10 feisty NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting...
Apr 15 22:42:10 feisty NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) successful.
Apr 15 22:42:10 feisty NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Apr 15 22:42:10 feisty NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete.
Apr 15 22:42:10 feisty NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) started...
Apr 15 22:42:12 feisty NetworkManager: <information>^IActivation (eth0) Beginning DHCP transaction.
Apr 15 22:42:12 feisty NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Apr 15 22:42:12 feisty NetworkManager: <information>^IDHCP daemon state is now 12 (successfully started) for interface eth0
Apr 15 22:42:13 feisty NetworkManager: <information>^IDHCP daemon state is now 1 (starting) for interface eth0
Apr 15 22:42:20 feisty NetworkManager: <information>^IDHCP daemon state is now 2 (bound) for interface eth0
Apr 15 22:42:20 feisty NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) scheduled...
Apr 15 22:42:20 feisty NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) started...
Apr 15 22:42:20 feisty NetworkManager: <information>^IRetrieved the following IP4 configuration from the DHCP daemon:
Apr 15 22:42:20 feisty NetworkManager: <information>^I  address 192.168.1.106
Apr 15 22:42:20 feisty NetworkManager: <information>^I  netmask 255.255.255.0
Apr 15 22:42:20 feisty NetworkManager: <information>^I  broadcast 192.168.1.255
Apr 15 22:42:20 feisty NetworkManager: <information>^I  gateway 192.168.1.1
Apr 15 22:42:20 feisty NetworkManager: <information>^I  nameserver 192.168.1.1
Apr 15 22:42:20 feisty NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Apr 15 22:42:20 feisty NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) complete.
Apr 15 22:42:20 feisty NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Apr 15 22:42:21 feisty NetworkManager: <information>^IClearing nscd hosts cache.
Apr 15 22:42:21 feisty NetworkManager: <WARNING>^I nm_spawn_process (): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))
Apr 15 22:42:21 feisty NetworkManager: <information>^IActivation (eth0) successful, device activated.
Apr 15 22:42:21 feisty NetworkManager: <information>^IActivation (eth0) Finish handler scheduled.
Apr 15 22:42:21 feisty NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Apr 15 23:16:49 feisty NetworkManager: <information>^IUpdating allowed wireless network lists.
Apr 15 23:16:49 feisty NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored..
Apr 15 23:17:31 feisty NetworkManager: <information>^IDHCP daemon state is now 14 (normal exit) for interface eth0
Apr 15 23:17:41 feisty NetworkManager: <information>^ISWITCH: terminating current connection 'eth0' because it's no longer valid.
Apr 15 23:17:41 feisty NetworkManager: <information>^IDeactivating device eth0.
Apr 15 23:17:41 feisty NetworkManager: nm_device_is_802_3_ethernet: assertion `dev != NULL' failed
Apr 15 23:17:41 feisty NetworkManager: nm_device_is_802_11_wireless: assertion `dev != NULL' failed
Apr 15 23:17:41 feisty NetworkManager: <information>^IWill activate wired connection 'eth0' because it now has a link.
Apr 15 23:17:41 feisty NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'.
Apr 15 23:17:41 feisty NetworkManager: <information>^IWill activate connection 'eth0'.
Apr 15 23:17:41 feisty NetworkManager: <information>^IDevice eth0 activation scheduled...
Apr 15 23:17:41 feisty NetworkManager: <information>^IActivation (eth0) started...
Apr 15 23:17:41 feisty NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 15 23:17:41 feisty NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started...
Apr 15 23:17:41 feisty NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Apr 15 23:17:41 feisty NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete.
Apr 15 23:17:41 feisty NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting...
Apr 15 23:17:41 feisty NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) successful.
Apr 15 23:17:41 feisty NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Apr 15 23:17:41 feisty NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete.
Apr 15 23:17:41 feisty NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) started...
Apr 15 23:17:43 feisty NetworkManager: <information>^IActivation (eth0) Beginning DHCP transaction.
Apr 15 23:17:43 feisty NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Apr 15 23:17:43 feisty NetworkManager: <information>^IDHCP daemon state is now 12 (successfully started) for interface eth0
Apr 15 23:17:44 feisty NetworkManager: <information>^IDHCP daemon state is now 1 (starting) for interface eth0
Apr 15 23:17:47 feisty NetworkManager: <information>^IDHCP daemon state is now 2 (bound) for interface eth0
Apr 15 23:17:47 feisty NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) scheduled...
Apr 15 23:17:47 feisty NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) started...
Apr 15 23:17:47 feisty NetworkManager: <information>^IRetrieved the following IP4 configuration from the DHCP daemon:
Apr 15 23:17:47 feisty NetworkManager: <information>^I  address 192.168.1.106
Apr 15 23:17:47 feisty NetworkManager: <information>^I  netmask 255.255.255.0
Apr 15 23:17:47 feisty NetworkManager: <information>^I  broadcast 192.168.1.255
Apr 15 23:17:47 feisty NetworkManager: <information>^I  gateway 192.168.1.1
Apr 15 23:17:47 feisty NetworkManager: <information>^I  nameserver 192.168.1.1
Apr 15 23:17:47 feisty NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Apr 15 23:17:47 feisty NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) complete.
Apr 15 23:17:47 feisty NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Apr 15 23:17:48 feisty NetworkManager: <information>^IClearing nscd hosts cache.
Apr 15 23:17:48 feisty NetworkManager: <WARNING>^I nm_spawn_process (): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))
Apr 15 23:17:48 feisty NetworkManager: <information>^IActivation (eth0) successful, device activated.
Apr 15 23:17:48 feisty NetworkManager: <information>^IActivation (eth0) Finish handler scheduled.
Apr 15 23:17:48 feisty NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) complete.

```

-Dave

---

