---
title: "Laptop locks up every 10-15 minutes... related to wireless?"
date: 2008-08-19
forum: Networking &amp; Wireless
---

### Post by DaSal on 2008-08-19
Hey, I just did a clean installation of Ubuntu for one of the first times, however I have done it once before and got it running properly on a desktop machine. However on my dad's Packard Bell laptop (model: Argo C2) it locks up every time after about 10-15 minutes. It seems to be related to the wireless as in the messages and syslog log files it seems to be doing stuff with the wireless network every time right before it locks up.

Here's the log file from the messages log:

Aug 19 23:51:03 adriaan-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Aug 19 23:51:04 adriaan-laptop kernel: [ 43.825007] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 19
Aug 19 23:51:05 adriaan-laptop kernel: [ 45.435421] [fglrx] GART Table is not in FRAME_BUFFER range 
Aug 19 23:51:05 adriaan-laptop kernel: [ 45.435440] [fglrx] Reserve Block - 0 offset = 0X0 length = 0X40000
Aug 19 23:51:05 adriaan-laptop kernel: [ 45.435447] [fglrx] Reserve Block - 1 offset = 0X7ff5000 length = 0Xb000
Aug 19 23:51:05 adriaan-laptop kernel: [ 45.611317] [fglrx] interrupt source 10000000 successfully enabled
Aug 19 23:51:05 adriaan-laptop kernel: [ 45.611328] [fglrx] enable ID = 0x00000004
Aug 19 23:51:05 adriaan-laptop kernel: [ 45.611346] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
Aug 19 23:51:14 adriaan-laptop kernel: [ 53.824248] hda-intel: Invalid position buffer, using LPIB read method instead.
Aug 19 23:51:36 adriaan-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
Aug 19 23:51:39 adriaan-laptop kernel: [ 78.769427] NET: Registered protocol family 17
Aug 19 23:51:45 adriaan-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.host_name
Aug 19 23:51:45 adriaan-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_domain
Aug 19 23:51:45 adriaan-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_servers
Aug 19 23:51:45 adriaan-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.interface_mtu
Aug 20 00:03:52 adriaan-laptop syslogd 1.5.0#1ubuntu1: restart.

---

Anybody have any suggestion on how to fix this?:(

---

