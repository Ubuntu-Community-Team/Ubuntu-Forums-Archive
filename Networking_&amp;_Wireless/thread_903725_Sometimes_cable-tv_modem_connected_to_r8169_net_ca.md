---
title: "Sometimes cable-tv modem connected to r8169 net card doesn't work"
date: 2008-08-28
forum: Networking &amp; Wireless
---

### Post by jujo on 2008-08-28
Sometime when I boot my ubuntu my internet connection doesn't work. But when I restart ( by plugging the wire out and in) my modem and then reboot computer everything works fine. However it doesn't go when I just restart the modem even when I try it with restarting avahi daemon and networking in /etc/init.d. The modem is connected to computer via normal lan network adapter. I attach some logs down there.

Dmesg when everything is all right:
> (...)
[   44.538985] r8169: eth1: link up
[   44.538998] r8169: eth1: link up
[   44.776448] Bluetooth: Core ver 2.11
[   44.776811] NET: Registered protocol family 31
[   44.776817] Bluetooth: HCI device and connection manager initialized
[   44.776822] Bluetooth: HCI socket layer initialized
[   44.907016] Bluetooth: L2CAP ver 2.9
[   44.907023] Bluetooth: L2CAP socket layer initialized
[   45.014443] Bluetooth: RFCOMM socket layer initialized
[   45.014462] Bluetooth: RFCOMM TTY layer initialized
[   45.014464] Bluetooth: RFCOMM ver 1.8
[   47.676242] [drm] Initialized drm 1.1.0 20060810
[   47.679521] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   47.679531] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   47.679609] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   47.781905] NET: Registered protocol family 17
[   47.959138] set status page addr 0x00033000
[   52.498717] NET: Registered protocol family 10
[   52.499077] lo: Disabled Privacy Extensions
[   62.699102] eth1: no IPv6 routers present
[  725.762527] r8169: eth1: link down
[  795.884656] r8169: eth1: link up
[  795.885066] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  814.453616] eth1: no IPv6 routers present

and dmesg in those times when after everything is booted internet doesn't work:
> (...)
[   44.318602] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   44.318608] apm: disabled - APM is not SMP safe.
[   45.757935] Bluetooth: Core ver 2.11
[   45.758208] NET: Registered protocol family 31
[   45.758214] Bluetooth: HCI device and connection manager initialized
[   45.758219] Bluetooth: HCI socket layer initialized
[   45.775754] Bluetooth: L2CAP ver 2.9
[   45.775760] Bluetooth: L2CAP socket layer initialized
[   45.816180] Bluetooth: RFCOMM socket layer initialized
[   45.816195] Bluetooth: RFCOMM TTY layer initialized
[   45.816197] Bluetooth: RFCOMM ver 1.8
[   46.287950] r8169: eth1: link up
[   48.534486] [drm] Initialized drm 1.1.0 20060810
[   48.537391] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   48.537401] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   48.537494] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   48.816035] set status page addr 0x00033000
[   49.472850] NET: Registered protocol family 17
[   55.121196] NET: Registered protocol family 10
[   55.121543] lo: Disabled Privacy Extensions
[   65.949314] eth1: no IPv6 routers present
[  124.478102] NETDEV WATCHDOG: eth1: transmit timed out
[  125.292846] r8169: eth1: link up
[ 3281.742411] NETDEV WATCHDOG: eth1: transmit timed out
[ 3282.570308] r8169: eth1: link up
[ 3360.998918] r8169: eth1: link up

and syslog from those (error) times:
> Aug 26 12:53:24 jujo syslogd 1.5.0#1ubuntu1: restart.
Aug 26 12:53:24 jujo anacron[5254]: Job `cron.daily' terminated
Aug 26 12:57:53 jujo anacron[5254]: Job `cron.weekly' started
Aug 26 12:57:53 jujo anacron[5843]: Updated timestamp for job `cron.weekly' to 2008-08-26
Aug 26 12:57:54 jujo syslogd 1.5.0#1ubuntu1: restart.
Aug 26 12:57:54 jujo anacron[5254]: Job `cron.weekly' terminated
Aug 26 12:57:54 jujo anacron[5254]: Normal exit (2 jobs run)
Aug 26 13:17:01 jujo /USR/SBIN/CRON[6033]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 26 13:27:48 jujo -- MARK --
Aug 26 13:41:51 jujo kernel: [ 3281.742411] NETDEV WATCHDOG: eth1: transmit timed out
Aug 26 13:41:52 jujo kernel: [ 3282.570308] r8169: eth1: link up
Aug 26 13:43:09 jujo NetworkManager: <info>  Disconnected. 
Aug 26 13:43:09 jujo avahi-daemon[4870]: Interface eth1.IPv4 no longer relevant for mDNS.
Aug 26 13:43:09 jujo avahi-daemon[4870]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.9.112.
Aug 26 13:43:09 jujo avahi-autoipd(eth1)[5594]: SIOCSIFFLAGS failed: Permission denied
Aug 26 13:43:09 jujo avahi-autoipd(eth1)[5594]: Callout STOP, address 169.254.9.112 on interface eth1
Aug 26 13:43:09 jujo avahi-daemon[4870]: Withdrawing address record for fe80::21d:7dff:fe74:d4bc on eth1.
Aug 26 13:43:09 jujo avahi-daemon[4870]: Withdrawing address record for 169.254.9.112 on eth1.
Aug 26 13:43:09 jujo avahi-autoipd(eth1)[5595]: client: RTNETLINK answers: No such process
Aug 26 13:43:10 jujo NetworkManager: <info>  Enabling networking. 
Aug 26 13:43:10 jujo NetworkManager: <info>  Deactivating device eth1. 
Aug 26 13:43:11 jujo kernel: [ 3360.998918] r8169: eth1: link up
Aug 26 13:43:11 jujo NetworkManager: <info>  eth1: Device is fully-supported using driver 'r8169'. 
Aug 26 13:43:11 jujo NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Aug 26 13:43:11 jujo NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Aug 26 13:43:11 jujo NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth1'. 
Aug 26 13:43:11 jujo NetworkManager: <info>  Deactivating device eth1. 
Aug 26 13:43:11 jujo NetworkManager: <info>  Will activate wired connection 'eth1' because it now has a link. 
Aug 26 13:43:11 jujo NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Aug 26 13:43:11 jujo NetworkManager: <info>  Will activate connection 'eth1'. 
Aug 26 13:43:11 jujo NetworkManager: <info>  Device eth1 activation scheduled... 
Aug 26 13:43:11 jujo NetworkManager: <info>  Activation (eth1) started... 
Aug 26 13:43:11 jujo NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Aug 26 13:43:11 jujo NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Aug 26 13:43:11 jujo NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Aug 26 13:43:11 jujo NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Aug 26 13:43:11 jujo NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Aug 26 13:43:11 jujo NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful. 
Aug 26 13:43:11 jujo NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Aug 26 13:43:11 jujo NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Aug 26 13:43:11 jujo NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Aug 26 13:43:13 jujo NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Aug 26 13:43:13 jujo NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Aug 26 13:43:13 jujo NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
Aug 26 13:43:14 jujo NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Aug 26 13:43:16 jujo dhclient: DHCPREQUEST of 10.27.240.231 on eth1 to 255.255.255.255 port 67
Aug 26 13:43:24 jujo last message repeated 2 times
Aug 26 13:43:29 jujo dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Aug 26 13:43:32 jujo dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Aug 26 13:43:35 jujo dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Aug 26 13:43:43 jujo dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
Aug 26 13:44:00 jujo dhclient: No DHCPOFFERS received.
Aug 26 13:44:00 jujo dhclient: Trying recorded lease 10.27.240.231
Aug 26 13:44:00 jujo avahi-daemon[4870]: Joining mDNS multicast group on interface eth1.IPv4 with address 10.27.240.231.
Aug 26 13:44:00 jujo avahi-daemon[4870]: New relevant interface eth1.IPv4 for mDNS.
Aug 26 13:44:00 jujo avahi-daemon[4870]: Registering new address record for 10.27.240.231 on eth1.IPv4.
Aug 26 13:44:00 jujo avahi-daemon[4870]: Withdrawing address record for 10.27.240.231 on eth1.
Aug 26 13:44:00 jujo avahi-daemon[4870]: Leaving mDNS multicast group on interface eth1.IPv4 with address 10.27.240.231.
Aug 26 13:44:00 jujo avahi-daemon[4870]: Interface eth1.IPv4 no longer relevant for mDNS.
Aug 26 13:44:00 jujo avahi-daemon[4870]: Joining mDNS multicast group on interface eth1.IPv4 with address 10.27.240.231.
Aug 26 13:44:00 jujo avahi-daemon[4870]: New relevant interface eth1.IPv4 for mDNS.
Aug 26 13:44:00 jujo avahi-daemon[4870]: Registering new address record for 10.27.240.231 on eth1.IPv4.
Aug 26 13:44:03 jujo avahi-daemon[4870]: Withdrawing address record for 10.27.240.231 on eth1.
Aug 26 13:44:03 jujo avahi-daemon[4870]: Leaving mDNS multicast group on interface eth1.IPv4 with address 10.27.240.231.
Aug 26 13:44:03 jujo avahi-daemon[4870]: Interface eth1.IPv4 no longer relevant for mDNS.
Aug 26 13:44:03 jujo avahi-autoipd(eth1)[6214]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Aug 26 13:44:03 jujo avahi-autoipd(eth1)[6214]: Successfully called chroot().
Aug 26 13:44:03 jujo avahi-autoipd(eth1)[6214]: Successfully dropped root privileges.
Aug 26 13:44:03 jujo avahi-autoipd(eth1)[6214]: Starting with address 169.254.9.112
Aug 26 13:44:08 jujo avahi-autoipd(eth1)[6214]: Callout BIND, address 169.254.9.112 on interface eth1
Aug 26 13:44:08 jujo avahi-daemon[4870]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.9.112.
Aug 26 13:44:08 jujo avahi-daemon[4870]: New relevant interface eth1.IPv4 for mDNS.
Aug 26 13:44:08 jujo avahi-daemon[4870]: Registering new address record for 169.254.9.112 on eth1.IPv4.
Aug 26 13:44:12 jujo avahi-autoipd(eth1)[6214]: Successfully claimed IP address 169.254.9.112
Aug 26 13:44:12 jujo NetworkManager: <info>  DHCP daemon state is now 8 (timeout) for interface eth1 
Aug 26 13:44:12 jujo NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Aug 26 13:44:12 jujo NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) started... 
Aug 26 13:44:12 jujo NetworkManager: <info>  No DHCP reply received.  Automatically obtaining IP via Zeroconf. 
Aug 26 13:44:12 jujo NetworkManager: <info>  avahi-autoipd running on eth1, assuming IPv4LL address 
Aug 26 13:44:12 jujo NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Aug 26 13:44:12 jujo NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) complete. 
Aug 26 13:44:12 jujo NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Aug 26 13:44:12 jujo NetworkManager: <info>  not touching eth1 configuration, was configured externally 
Aug 26 13:44:12 jujo NetworkManager: <info>  Activation (eth1) successful, device activated. 
Aug 26 13:44:12 jujo NetworkManager: <info>  Activation (eth1) Finish handler scheduled. 
Aug 26 13:44:12 jujo NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Aug 26 13:44:12 jujo NetworkManager: <info>  DHCP daemon state is now 9 (fail) for interface eth1 
Aug 26 13:44:12 jujo dhcdbd: Unrequested down ?:3
Aug 26 13:44:12 jujo NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface eth1 
Aug 26 13:44:29 jujo kernel: [ 3439.484609] NETDEV WATCHDOG: eth1: transmit timed out
Aug 26 13:44:30 jujo kernel: [ 3440.299358] r8169: eth1: link up
Aug 26 13:45:08 jujo ntpdate[6261]: can't find host ntp.ubuntu.com 
Aug 26 13:45:08 jujo ntpdate[6261]: no servers can be used, exiting
Aug 26 13:51:58 jujo hcid[5131]: Stopping SDP server
Aug 26 13:51:58 jujo hcid[5131]: Unregister path: /org/bluez
Aug 26 13:51:58 jujo hcid[5131]: Shutting down local server
Aug 26 13:51:58 jujo hcid[5131]: Exit
Aug 26 13:51:58 jujo input[5189]: Unregistered manager path
Aug 26 13:51:58 jujo input[5189]: Exit

Sorry for my silly style and language. I'm not English. Thanks for reading. Regards.

---

### Post by jujo on 2008-08-30
Bump. Please, I need your help.

---

### Post by jujo on 2008-09-01
Bump.

---

