---
title: "NetworkManager crashing (dbus problem?) Need help!"
date: 2007-02-16
forum: Networking &amp; Wireless
---

### Post by pentium4borg on 2007-02-16
Hey all -

I've recently (past 1 or 2 days) been having a big problem with NetworkManager, it crashes either immediately when starting or after a while, it's pretty random. Everything was working before this, I don't remember what I upgraded recently (I know there have been a few updates in the past few days).

Here's what happens when I run NetworkManager --no-daemon:

> NetworkManager: <information>	starting...
NetworkManager: <information>	Adding VPN service 'org.freedesktop.NetworkManager.vpnc' with name 'vpnc' and program '/usr/bin/nm-vpnc-service'
NetworkManager: <information>	Adding VPN service 'org.freedesktop.NetworkManager.ppp_starter' with name 'ppp' and program '/usr/bin/nm-ppp-starter'
NetworkManager: <information>	Adding VPN service 'org.freedesktop.NetworkManager.openvpn' with name 'openvpn' and program '/usr/lib/network-manager-openvpn/nm-openvpn-service'
NetworkManager: <information>	ath0: Device is fully-supported using driver 'ath_pci'.
NetworkManager: <information>	nm_device_init(): waiting for device's worker thread to start
NetworkManager: <information>	nm_device_init(): device's worker thread started, continuing.
NetworkManager: <information>	Now managing wireless (802.11) device 'ath0'.
NetworkManager: <information>	Deactivating device ath0.
NetworkManager: <information>	eth0: Device is fully-supported using driver '8139too'.
NetworkManager: <information>	nm_device_init(): waiting for device's worker thread to start
NetworkManager: <information>	nm_device_init(): device's worker thread started, continuing.
NetworkManager: <information>	Now managing wired Ethernet (802.3) device 'eth0'.
NetworkManager: <information>	Deactivating device eth0.
NetworkManager: <information>	Will activate wired connection 'eth0' because it now has a link.
NetworkManager: <information>	Updating allowed wireless network lists.
NetworkManager: <information>	Updating VPN Connections...
NetworkManager: <information>	SWITCH: no current connection, found better connection 'eth0'.
NetworkManager: <information>	Will activate connection 'eth0'.
NetworkManager: <information>	Device eth0 activation scheduled...
7731: arguments to dbus_pending_call_block() were incorrect, assertion "pending != NULL" failed in file dbus-pending-call.c line 636.
This is normally a bug in some application using the D-Bus library.
7731: arguments to dbus_pending_call_steal_reply() were incorrect, assertion "pending != NULL" failed in file dbus-pending-call.c line 604.
This is normally a bug in some application using the D-Bus library.
7731: arguments to dbus_pending_call_unref() were incorrect, assertion "pending != NULL" failed in file dbus-pending-call.c line 487.
This is normally a bug in some application using the D-Bus library.
7731: arguments to dbus_set_error_from_message() were incorrect, assertion "message != NULL" failed in file dbus-message.c line 3085.
This is normally a bug in some application using the D-Bus library.
NetworkManager: <information>	Activation (eth0) started...
7731: arguments to dbus_connection_send() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 2349.
This is normally a bug in some application using the D-Bus library.
NetworkManager: <WARNING>	 nm_act_request_set_stage (): nm_act_request_set_stage(): Could not raise the signal!
7731: arguments to dbus_connection_send() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 2349.
This is normally a bug in some application using the D-Bus library.
NetworkManager: <WARNING>	 nm_act_request_set_stage (): nm_act_request_set_stage(): Could not raise the signal!
NetworkManager: <information>	Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
NetworkManager: <information>	Activation (eth0) Stage 1 of 5 (Device Prepare) started...
7731: arguments to dbus_connection_send() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 2349.
This is normally a bug in some application using the D-Bus library.
NetworkManager: <WARNING>	 nm_act_request_set_stage (): nm_act_request_set_stage(): Could not raise the signal!
NetworkManager: <information>	Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
NetworkManager: <information>	Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
NetworkManager: <information>	Activation (eth0) Stage 2 of 5 (Device Configure) starting...
NetworkManager: <information>	Activation (eth0) Stage 2 of 5 (Device Configure) successful.
7731: arguments to dbus_connection_send() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 2349.
This is normally a bug in some application using the D-Bus library.
NetworkManager: <WARNING>	 nm_act_request_set_stage (): nm_act_request_set_stage(): Could not raise the signal!
NetworkManager: <information>	Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
NetworkManager: <information>	Activation (eth0) Stage 2 of 5 (Device Configure) complete.
NetworkManager: <information>	Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
NetworkManager: nm_dbus_signal_state_change: assertion `connection != NULL' failed
NetworkManager: nm_dbus_signal_device_status_change: assertion `cb_data->data->dbus_connection' failed
NetworkManager: <information>	Old device 'eth0' activating, won't change.
NetworkManager: <information>	Successfully reconnected to the system bus.
NetworkManager: <information>	Activation (eth0) Beginning DHCP transaction.
NetworkManager: <WARNING>	 nm_signal_handler (): Caught signal 11.  Generating backtrace...
NetworkManager: ******************* START **********************************
NetworkManager: Frame 0: NetworkManager [0x806c535]
NetworkManager: Frame 1: NetworkManager [0x806c6c1]
NetworkManager: Frame 2: [0xffffe420]
NetworkManager: Frame 3: NetworkManager [0x8053980]
NetworkManager: Frame 4: NetworkManager [0x8054e1d]
NetworkManager: Frame 5: /usr/lib/libglib-2.0.so.0 [0xb7e06aa1]
NetworkManager: Frame 6: /usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x182) [0xb7e08802]
NetworkManager: Frame 7: /usr/lib/libglib-2.0.so.0 [0xb7e0b7df]
NetworkManager: Frame 8: /usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1a9) [0xb7e0bb89]
NetworkManager: Frame 9: NetworkManager [0x8055a1e]
NetworkManager: Frame 10: /usr/lib/libglib-2.0.so.0 [0xb7e2638f]
NetworkManager: Frame 11: /lib/tls/i686/cmov/libpthread.so.0 [0xb7ec8504]
NetworkManager: Frame 12: /lib/tls/i686/cmov/libc.so.6(__clone+0x5e) [0xb7d0451e]
NetworkManager: ******************* END **********************************


It always crashes after receiving signal 11 from dbus (whatever that is). From this it looks like a dbus problem, but I don't remember upgrading either NM or dbus recently. Anybody have ideas? I'd like to get this fixed soon.

Thanks

---

### Post by pentium4borg on 2007-02-17
Sorry to bump guys but if anyone knows how to fix this, I'd appreciate it. My wireless is broken and I dunno how to fix it, this has only been happening within the past few days and I don't think anything is really different about my system.

---

### Post by fraia on 2008-02-16
I've heard dbus has some problems but I don't know any more about it than you do.

I gave up on network manager a while ago - try using  'Wicd'; There is a lot of active development on the project and decent support, such as their own forum just for wireless issues. 
The latest release is 1.4.1... I think it's in the repositories, otherwise you can get it from their website:

[http://wicd.sourceforge.net](http://wicd.sourceforge.net)

one note, you will have to uninstall network manager before it will let you install wicd, someting like the following should work:
sudo apt-get remove networkmanager

---

