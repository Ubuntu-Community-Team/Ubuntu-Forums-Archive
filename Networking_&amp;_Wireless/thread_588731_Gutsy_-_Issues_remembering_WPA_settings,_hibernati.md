---
title: "Gutsy - Issues remembering WPA settings, hibernation"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by Hyouko on 2007-10-23
I recently upgraded from Feisty to Gutsy and have run into difficulties with retaining my WPA settings; on reboot, my laptop cannot connect correctly to my school's wireless network unless I re-enter all of the WPA settings.  It remembered these settings under Feisty, but doesn't appear to be applying them correctly under Gutsy.

Furthermore, a problem that I have had under both - after bringing my laptop out of hibernation/suspend, it only sees "ghosts" of the wireless networks that were present when it went into hibernation/suspend; though it may show a connection, the connection does not appear to actually work or exist.  Any way around this?

---

### Post by babisch on 2007-10-24
I have similar problems. I solved the problem with the ghost networks on feisty after suspend by modifying /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux and /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux so that hibernate (from suspend2) was the script used to suspend the machine. 
I furthermore modfied the /etc/hibernate/common.conf so that my wireless modules was reloaded after resume and that the network manager was restarted too. That worked fine on feisty.
Modifications to common.conf are like this:
OnResume 25 modprobe -r ipw2200
OnResume 25 killall -KILL NetworkManager
OnResume 20 modprobe ipw2200
OnResume 15 sleep 2
OnResume 10 /usr/sbin/NetworkManager
That worked fine on feisty and solves the problem of ghost networks on gutsy too.

My Problem is that i have to reenter the password of my wpa on any reboot/suspend/hibernate now. Has anyone any clues what I could do?

From my logs:
Oct 24 18:11:15 spike NetworkManager: <debug> [1193242275.708402] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_XXX'). 
Oct 24 18:11:16 spike NetworkManager: <info>  eth1: Device is fully-supported using driver 'ipw2200'. 
Oct 24 18:11:16 spike NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 24 18:11:16 spike NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 24 18:11:16 spike NetworkManager: <info>  Now managing wireless (802.11) device 'eth1'. 
Oct 24 18:11:16 spike NetworkManager: <info>  Deactivating device eth1. 
Oct 24 18:11:16 spike NetworkManager: <debug> [1193242276.746844] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'). 
Oct 24 18:11:16 spike NetworkManager: <debug> [1193242276.778355] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'). 
Oct 24 18:11:16 spike NetworkManager: <debug> [1193242276.898727] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'). 
Oct 24 18:11:18 spike NetworkManager: <debug> [1193242278.749485] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX3_port_logicaldev_input'). 
Oct 24 18:11:18 spike NetworkManager: <debug> [1193242278.805918] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_3'). 
Oct 24 18:11:21 spike NetworkManager: <info>  starting... 
Oct 24 18:11:21 spike NetworkManager: <info>  New VPN service 'openvpn' (org.freedesktop.NetworkManager.openvpn). 
Oct 24 18:11:22 spike NetworkManager: <info>  eth1: Device is fully-supported using driver 'ipw2200'. 
Oct 24 18:11:22 spike NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 24 18:11:22 spike NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 24 18:11:22 spike NetworkManager: <info>  Now managing wireless (802.11) device 'eth1'. 
Oct 24 18:11:22 spike NetworkManager: <info>  Deactivating device eth1. 
Oct 24 18:11:22 spike NetworkManager: <info>  eth0: Device is fully-supported using driver 'sky2'. 
Oct 24 18:11:22 spike NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 24 18:11:22 spike NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 24 18:11:22 spike NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Oct 24 18:11:22 spike NetworkManager: <info>  Deactivating device eth0. 
Oct 24 18:11:22 spike NetworkManager: <info>  Updating allowed wireless network lists. 
Oct 24 18:11:28 spike avahi-daemon[5768]: Registering new address record for XXX on eth1.*.
Oct 24 18:11:32 spike NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Oct 24 18:11:32 spike NetworkManager: <info>  Will activate connection 'eth1/XXX'. 
Oct 24 18:11:32 spike NetworkManager: <info>  Device eth1 activation scheduled... 
Oct 24 18:11:32 spike NetworkManager: <info>  Activation (eth1) started... 
Oct 24 18:11:32 spike NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 24 18:11:32 spike NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Oct 24 18:11:32 spike NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Oct 24 18:11:32 spike NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Oct 24 18:11:32 spike NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Oct 24 18:11:32 spike NetworkManager: <info>  Activation (eth1/wireless): access point 'XXX' is encrypted, but NO valid key exists.  New key needed. 
Oct 24 18:11:32 spike NetworkManager: <info>  Activation (eth1) New wireless user key requested for network 'XXX'. 
Oct 24 18:11:32 spike NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete.

---

