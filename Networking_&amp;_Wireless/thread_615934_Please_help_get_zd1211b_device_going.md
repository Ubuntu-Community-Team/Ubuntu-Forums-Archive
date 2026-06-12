---
title: "Please help get zd1211b device going"
date: 2007-11-17
forum: Networking &amp; Wireless
---

### Post by alanmzifa on 2007-11-17
[B]I've put in many nights already on this so any help will be appreciated.

Trying to get a USB wireless dongle with a zd1211b chip going on Feisty 7.04 Xubuntu.

Here is some terminal output...[/B]

monty@dell:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:06:5B:30:BC:3B  
          inet addr:192.168.1.33  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::206:5bff:fe30:bc3b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5471 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5430 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4338264 (4.1 MiB)  TX bytes:1090693 (1.0 MiB)
          Interrupt:10 Base address:0x6c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

monty@dell:~$ lsusb
Bus 001 Device 004: ID 0586:3410 ZyXEL Communications Corp. 
Bus 001 Device 001: ID 0000:0000  
monty@dell:~$ sudo tail -f /var/log/messages
Nov 17 20:32:56 dell kernel: [ 2125.676000] zd1211rw 1-1:1.0: firmware version 4725
Nov 17 20:32:56 dell kernel: [ 2125.748000] zd1211rw 1-1:1.0: zd1211b chip 0ace:1215 v4810 full 00-02-72 AL2230_RF pa0 g--N
Nov 17 20:32:56 dell kernel: [ 2125.752000] zd1211rw 1-1:1.0: eth1
Nov 17 20:32:56 dell kernel: [ 2125.752000] usbcore: registered new interface driver zd1211rw
Nov 17 20:33:00 dell kernel: [ 2130.280000] usb 1-1: USB disconnect, address 3
Nov 17 20:35:16 dell kernel: [ 2264.444000] usb 1-1: new full speed USB device using uhci_hcd and address 4
Nov 17 20:35:16 dell kernel: [ 2264.612000] usb 1-1: configuration #1 chosen from 1 choice
Nov 17 20:58:00 dell -- MARK --
Nov 17 21:18:03 dell -- MARK --
Nov 17 21:38:04 dell -- MARK --

---

### Post by alanmzifa on 2007-11-18
Just posting to say got this working by upgrading to Xubuntu Gutsy 7.10.

In fact, it worked out of the box although I'm finding this keyring manager a pain. 
I'll see if i can find something to sort that out.


The device is a ZyXEL G202 USB wireless dongle.

---

