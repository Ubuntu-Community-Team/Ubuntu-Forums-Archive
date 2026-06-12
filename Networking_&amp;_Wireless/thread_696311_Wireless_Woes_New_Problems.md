---
title: "Wireless Woes: New Problems"
date: 2008-02-13
forum: Networking &amp; Wireless
---

### Post by 786souljah on 2008-02-13
I've installed Ubuntu 7.10 on my PC but have encountered some new problems with wireless connections. Ive listed my synopsis of observations below. The basic issue however is that the usb wireless device (Dlink WUA-1340) appears to be installed and seems to connect to a network but no data is sent. Other observations make it seem as though it may not be installed correctly or fully. Here's what i've found:

1. The command 'lsusb' shows the device ID etc etc as follows:

Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 045e:0053 Microsoft Corp.
Bus 001 Device 003: ID 07d1:3c04 D-Link System
Bus 001 Device 001: ID 0000:0000

2. Device Manager doesn't identify vendor, device, device type or capabilities.

3. The networks in the area are still detected and shown in the top right taskbar where they can be selected. At time of synopsis, the network was connected at 73% (three bars were also showing instead of the two circles connecting or the faulty connection icon)

4. Firefox will not load a simple page such as google.

5. Pinging a host through the terminal (such as my router) results in a message with ping id information and 'Destination Host Unreacheable'.

6. Roaming Mode in network manager will still find the networks. (related to number 3)

7. Windows Wireless Drivers opens a window but automatically closes itself in approximately 3 to 5 seconds. I used the program to try the windows driver (using the .inf file).

I am at a complete dead end and don't know what to do next. Could anyone give step by step instructions to fix my problem as I'm and EARLY adapter to linux.

Thank you for all your help,

-Alim

---

### Post by wieman01 on 2008-02-14
Start from [here]("http://ubuntuforums.org/showthread.php?t=684495") for troubleshooting your device.

---

### Post by rustybronco on 2008-02-14
> **786souljah said:**
> Bus 001 Device 003: ID **07d1:3c04** D-Link System
2. Device Manager doesn't identify vendor, device, device type or capabilities.

looks like a rt73 chipset.

---

