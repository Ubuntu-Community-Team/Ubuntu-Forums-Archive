---
title: "NetworkManager suddenly using 100% CPU"
date: 2008-04-11
forum: Networking &amp; Wireless
---

### Post by c0ldfusi0n on 2008-04-11
Hey folks.

I've seen a few posts like the one I'm about to make, but no definite answer so I thought I'd share my problem and the solution I found for it.

The problem is that after a while, for no apparent reason, NetworkManager starts using 100% of my CPU. I'm still connected to the Wired Network, nothing has changed on that front, it just starts eating up resources. I do not have any special definitions in /etc/networking/interfaces (eth0 and eth1 aren't there), and this is what my syslog says about it:

> 
Apr 11 09:18:21 pLaptop NetworkManager: <WARN>  nm_hal_deinit(): libhal shutdown failed - Connection is closed 
Apr 11 09:18:21 pLaptop NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/dell_wlan_switch 
Apr 11 09:18:21 pLaptop NetworkManager: <info>  Successfully reconnected to the system bus. 
Apr 11 09:44:22 pLaptop NetworkManager: <WARN>  nm_hal_deinit(): libhal shutdown failed - Connection is closed 
Apr 11 09:44:22 pLaptop NetworkManager: nm_get_device_by_iface: assertion `data != NULL' failed
Apr 11 09:44:22 pLaptop NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/dell_wlan_switch 
Apr 11 09:44:22 pLaptop NetworkManager: <info>  Successfully reconnected to the system bus. 
Apr 11 09:48:42 pLaptop NetworkManager: <WARN>  nm_hal_deinit(): libhal shutdown failed - Connection is closed 
Apr 11 09:48:42 pLaptop NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/dell_wlan_switch 
Apr 11 09:48:42 pLaptop NetworkManager: <info>  Successfully reconnected to the system bus. 
Apr 11 09:55:12 pLaptop NetworkManager: <WARN>  nm_hal_deinit(): libhal shutdown failed - Connection is closed 
Apr 11 09:55:12 pLaptop NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/dell_wlan_switch 
Apr 11 09:55:12 pLaptop NetworkManager: <info>  Successfully reconnected to the system bus. 
Apr 11 10:01:42 pLaptop NetworkManager: <WARN>  nm_hal_deinit(): libhal shutdown failed - Connection is closed 
Apr 11 10:01:42 pLaptop NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/dell_wlan_switch 
Apr 11 10:01:42 pLaptop NetworkManager: <info>  Successfully reconnected to the system bus. 
Apr 11 10:01:42 pLaptop NetworkManager: <WARN>  nm_signal_handler(): Caught signal 11.  Generating backtrace... 
Apr 11 10:01:42 pLaptop NetworkManager: ******************* START **********************************
Apr 11 10:01:43 pLaptop NetworkManager: (no debugging symbols found)
Apr 11 10:01:43 pLaptop NetworkManager: Using host libthread_db library "/lib/libthread_db.so.1".
Apr 11 10:01:43 pLaptop NetworkManager: (no debugging symbols found)
Apr 11 10:01:43 pLaptop NetworkManager: [Thread debugging using libthread_db enabled]
Apr 11 10:01:43 pLaptop NetworkManager: [New Thread 46977723615552 (LWP 4628)]
Apr 11 10:01:43 pLaptop NetworkManager: [New Thread 1090525520 (LWP 4772)]
Apr 11 10:01:43 pLaptop NetworkManager: [New Thread 1082132816 (LWP 4729)]
Apr 11 10:01:43 pLaptop NetworkManager: (no debugging symbols found)
Apr 11 10:01:43 pLaptop NetworkManager: 0x00002ab9d9e6fc7f in waitpid () from /lib/libpthread.so.0
Apr 11 10:01:43 pLaptop NetworkManager: ******************* END **********************************
Apr 11 10:27:39 pLaptop NetworkManager: <info>  starting... 
Apr 11 10:27:39 pLaptop NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/dell_wlan_switch 
Apr 11 10:27:39 pLaptop NetworkManager: <info>  eth1: Device is fully-supported using driver 'bcm43xx'. 
Apr 11 10:27:39 pLaptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Apr 11 10:27:39 pLaptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Apr 11 10:27:39 pLaptop NetworkManager: <info>  Now managing wireless (802.11) device 'eth1'. 
Apr 11 10:27:39 pLaptop NetworkManager: <info>  Deactivating device eth1. 
Apr 11 10:27:39 pLaptop NetworkManager: <info>  eth0: Device is fully-supported using driver 'b44'. 
Apr 11 10:27:39 pLaptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Apr 11 10:27:39 pLaptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Apr 11 10:27:39 pLaptop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Apr 11 10:27:39 pLaptop NetworkManager: <info>  Deactivating device eth0. 
Apr 11 10:27:39 pLaptop NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Apr 11 10:27:39 pLaptop NetworkManager: <info>  Updating allowed wireless network lists. 
Apr 11 10:27:39 pLaptop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Apr 11 10:27:39 pLaptop NetworkManager: <info>  Will activate connection 'eth0'. 
Apr 11 10:27:39 pLaptop NetworkManager: <info>  Device eth0 activation scheduled... 
Apr 11 10:27:39 pLaptop NetworkManager: <info>  Activation (eth0) started... 
Apr 11 10:27:39 pLaptop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Apr 11 10:27:39 pLaptop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Apr 11 10:27:39 pLaptop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Apr 11 10:27:39 pLaptop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Apr 11 10:27:39 pLaptop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Apr 11 10:27:39 pLaptop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Apr 11 10:27:39 pLaptop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Apr 11 10:27:39 pLaptop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Apr 11 10:27:39 pLaptop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Apr 11 10:27:39 pLaptop NetworkManager: <info>  Old device 'eth0' activating, won't change. 
Apr 11 10:27:39 pLaptop NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface eth0 
Apr 11 10:27:39 pLaptop NetworkManager: <info>  Error getting killswitch power: org.freedesktop.Hal.Device.KillSwitch.NotSupported - Access type not supported 
Apr 11 10:27:39 pLaptop NetworkManager: <info>  Wireless now enabled by radio killswitch 
Apr 11 10:27:40 pLaptop NetworkManager: <info>  DHCP daemon state is now 11 (unknown) for interface eth0 
Apr 11 10:27:40 pLaptop NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface eth0 
Apr 11 10:27:41 pLaptop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Apr 11 10:27:41 pLaptop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0 
Apr 11 10:27:41 pLaptop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Apr 11 10:27:42 pLaptop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0 
Apr 11 10:27:43 pLaptop NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth0 
Apr 11 10:27:43 pLaptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Apr 11 10:27:43 pLaptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Apr 11 10:27:43 pLaptop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Apr 11 10:27:43 pLaptop NetworkManager: <info>    address 192.168.50.117 
Apr 11 10:27:43 pLaptop NetworkManager: <info>    netmask 255.255.255.0 
Apr 11 10:27:43 pLaptop NetworkManager: <info>    broadcast 192.168.50.255 
Apr 11 10:27:43 pLaptop NetworkManager: <info>    gateway 192.168.50.3 
Apr 11 10:27:43 pLaptop NetworkManager: <info>    nameserver 192.168.50.10 
Apr 11 10:27:43 pLaptop NetworkManager: <info>    domain name 'nvi.local' 
Apr 11 10:27:43 pLaptop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Apr 11 10:27:43 pLaptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Apr 11 10:27:43 pLaptop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Apr 11 10:27:44 pLaptop NetworkManager: <info>  Clearing nscd hosts cache. 
Apr 11 10:27:44 pLaptop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Apr 11 10:27:44 pLaptop NetworkManager: <info>  Activation (eth0) successful, device activated. 
Apr 11 10:27:44 pLaptop NetworkManager: <info>  Activation (eth0) Finish handler scheduled. 
Apr 11 10:27:44 pLaptop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Apr 11 10:27:45 pLaptop NetworkManager: <info>  Error getting killswitch power: org.freedesktop.Hal.Device.KillSwitch.NotSupported - Access type not supported 
Apr 11 10:27:51 pLaptop NetworkManager: <info>  Error getting killswitch power: org.freedesktop.Hal.Device.KillSwitch.NotSupported - Access type not supported 
Apr 11 10:27:57 pLaptop NetworkManager: <info>  Error getting killswitch power: org.freedesktop.Hal.Device.KillSwitch.NotSupported - Access type not supported 


You should be seeing above normal startup of NetworkManager, and a forced DBUS restart. The only way I found to make NetworkManager go back to its normal, CPU-friendly behavior is something I found in another post, to restart it via DBUS:
> sudo /etc/dbus-1/event.d/25NetworkManager restart

Doing that restarts NetworkManager and stops it from continuing to hog all my processing speed, and the tray icon goes back to "Connected" mode. Not sure what's causing the increase, but if anyone knows, please comment.

Hope this helps someone.

---

### Post by stream303 on 2008-04-12
I had that problem with NM on a few machines.  Since I'm only using a wired network and don't really "roam" with it, I just disable it, rather than uninstall it.  Disabling it seems to keep things happier:

[https://help.ubuntu.com/community/WifiDocs/NetworkManager#head-1de145d05f957ff659f5fdb58974ec3e5864def5](https://help.ubuntu.com/community/WifiDocs/NetworkManager#head-1de145d05f957ff659f5fdb58974ec3e5864def5)

---

### Post by c0ldfusi0n on 2008-04-16
What will be the effects of that?

---

