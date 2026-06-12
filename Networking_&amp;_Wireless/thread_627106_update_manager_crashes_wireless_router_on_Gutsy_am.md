---
title: "update manager crashes wireless router on Gutsy amd64"
date: 2007-11-29
forum: Networking &amp; Wireless
---

### Post by darrenleeweber on 2007-11-29
Almost every time I get into a download within the update manager, using the wireless connection to my router, the download stalls, my router loses all connection to the net and my network manager cannot reconnect after I 'reboot' the router.  I can hardly believe this is happening, but I have observed this many times now on several laptops over the past few weeks.  I have a functional router and functional wireless connections for hours, until I use the update manager for a software download from any ubuntu repository.  I can almost predict what will happen when I start the update process.  If I use an ethernet connection instead of the wireless connection, everything is fine.  I figure there is something wrong with the network manager or something in the wireless management system.  Why in hell it should crash the router connection to the WAN I have no idea, but it does!  My ISP is comcast and I have no problems with the net connection except when using the update manager over the wireless connection - the ethernet connection is fine.

I'm running Ubuntu Gutsy Gibbon (7.10, amd64) on a Lenovo ThinkPad T61.

dweber@skiweber:~$ uname -a
Linux skiweber 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU/Linux

dweber@skiweber:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 140M (rev a1)
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)


The syslog messages have some entries related to dhcdbd, ie:

Nov 29 16:12:19 skiweber dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
Nov 29 16:12:21 skiweber kernel: [   69.621114] NET: Registered protocol family 17
Nov 29 16:12:23 skiweber kernel: [   71.437409] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Nov 29 16:12:29 skiweber dhcdbd: dhco_input_option: Value 3650722200 cannot be converted to type L 
Nov 29 16:12:29 skiweber dhcdbd: dhco_parse_option_settings: bad option setting: old_dhcp_rebinding_time = 3650722200 
Nov 29 16:12:29 skiweber dhcdbd: dhco_input_option: Value 4294967295 cannot be converted to type L 
Nov 29 16:12:29 skiweber dhcdbd: dhco_parse_option_settings: bad option setting: new_dhcp_lease_time = 4294967295 
Nov 29 16:12:29 skiweber dhcdbd: dhco_input_option: Value 4294967295 cannot be converted to type L 
Nov 29 16:12:29 skiweber dhcdbd: dhco_parse_option_settings: bad option setting: old_dhcp_lease_time = 4294967295 
Nov 29 16:12:29 skiweber dhcdbd: dhco_input_option: Value 3650722200 cannot be converted to type L 
Nov 29 16:12:29 skiweber dhcdbd: dhco_parse_option_settings: bad option setting: new_dhcp_rebinding_time = 3650722200 
Nov 29 16:12:29 skiweber dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.host_name
Nov 29 16:12:29 skiweber dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.domain_name
Nov 29 16:12:29 skiweber dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_domain
Nov 29 16:12:29 skiweber dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_servers

I have no idea why this thing is looking for /com/redhat/dhcp/* because that path certainly doesn't exist on this system.

---

