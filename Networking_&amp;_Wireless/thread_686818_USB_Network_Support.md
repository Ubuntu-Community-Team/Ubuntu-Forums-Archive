---
title: "USB Network Support"
date: 2008-02-03
forum: Networking &amp; Wireless
---

### Post by th1bill on 2008-02-03
I have Three computers on my LAN.  The one I'm on right now is my test bed and it is running Ubuntu 7.10.  It is connected to my 2Wire Router/modem, mod. 1000SW via NIC thru a Cat5e.  This is unit number 2.  Unit number 3 is running on WindowsXP connected to the 2Wire via a Home Phone Network Adapter that plugs to the computer in the USB ports. 

Unit number 1 is a problem.  It is presently on a dual boot system with Kubuntu and Windows XP.  Unit number one is connected to the 2Wire via the only Usb port on the 1000SW 2Wire modem/ router.  If I boot the unit #1in Windows XP all three computers connect to the internet, at the same time, and they communicate via the LAN.  If I boot unit #1 in Kubuntu, it will not communicate with any other device.

The lsusb results are;

First check with the 2Wire plugged in;

willis@workgroup:~$ lsusb

Bus 004 Device 002: ID 04a9:10b6 Canon, Inc.

Bus 004 Device 001: ID 0000:0000

Bus 003 Device 004: ID 1630:0042          <this appears to be the 2Wire>

Bus 003 Device 001: ID 0000:0000

Bus 001 Device 003: ID 05da:30d9 Microtek International, Inc.

Bus 001 Device 001: ID 0000:0000

Bus 002 Device 006: ID 047d:1022 Kensington

Bus 002 Device 005: ID 06a3:0471 Saitek PLC

Bus 002 Device 003: ID 045e:00db Microsoft Corp.

Bus 002 Device 002: ID 03eb:3301 Atmel Corp. at43301 4-port Hub

Bus 002 Device 001: ID 0000:0000

After a hot swap;

willis@workgroup:~$ lsusb

Bus 004 Device 002: ID 04a9:10b6 Canon, Inc.

Bus 004 Device 001: ID 0000:0000

Bus 003 Device 001: ID 0000:0000

Bus 001 Device 003: ID 05da:30d9 Microtek International, Inc.

Bus 001 Device 001: ID 0000:0000

Bus 002 Device 007: ID 1630:0042           <...........................>

Bus 002 Device 006: ID 047d:1022 Kensington

Bus 002 Device 005: ID 06a3:0471 Saitek PLC

Bus 002 Device 003: ID 045e:00db Microsoft Corp.

Bus 002 Device 002: ID 03eb:3301 Atmel Corp. at43301 4-port Hub

Bus 002 Device 001: ID 0000:0000

With the device unplugged;

willis@workgroup:~$ lsusb

Bus 004 Device 002: ID 04a9:10b6 Canon, Inc.

Bus 004 Device 001: ID 0000:0000

Bus 003 Device 001: ID 0000:0000

Bus 001 Device 003: ID 05da:30d9 Microtek International, Inc.

Bus 001 Device 001: ID 0000:0000

Bus 002 Device 006: ID 047d:1022 Kensington

Bus 002 Device 005: ID 06a3:0471 Saitek PLC

Bus 002 Device 003: ID 045e:00db Microsoft Corp.

Bus 002 Device 002: ID 03eb:3301 Atmel Corp. at43301 4-port Hub

Bus 002 Device 001: ID 0000:0000

With the 2Wire plugged back in;

willis@workgroup:~$ lsusb

Bus 004 Device 002: ID 04a9:10b6 Canon, Inc.

Bus 004 Device 001: ID 0000:0000

Bus 003 Device 001: ID 0000:0000

Bus 001 Device 003: ID 05da:30d9 Microtek International, Inc.

Bus 001 Device 001: ID 0000:0000

Bus 002 Device 006: ID 047d:1022 Kensington

Bus 002 Device 005: ID 06a3:0471 Saitek PLC

Bus 002 Device 004: ID 1630:0042

Bus 002 Device 003: ID 045e:00db Microsoft Corp.

Bus 002 Device 002: ID 03eb:3301 Atmel Corp. at43301 4-port Hub

Bus 002 Device 001: ID 0000:0000

willis@workgroup:~$ lsusb

I went first to the Ubuntu list and everyone centered on the device not being suitable for the task I wish to accomplish but ith the system working perfectly with computer #1 booted in Windows I just fail to see that as a valid statement.  And when I was asked to post the lsusb results everyone just fell silent.  Please help, I do not want to operate Windows any more.

---

