---
title: "D-link DWL-G122 USB 64bit 6.06 c1"
date: 2008-02-18
forum: Networking &amp; Wireless
---

### Post by Hidetsu on 2008-02-18
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?t=104312](http://ubuntuforums.org/showthread.php?t=104312) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Allright I need help as fast as possible!

I can't get my USB DWL-G122 Ver.: C1 to work on my Ubuntu 6.06

I've read billions of forums but no good... I am a bit new in ubuntu but his never happened to me... And it's my first time i'm using a usb adapter for linux.

I can't get my on terminal when i write: 
user@user-desktop:~$
sudo ndiswrapper - l 
Installed ndis drivers:
dr71wu          driver present, hardware present

Allright, cool. I got the driver working:), but when i type 
user@user-desktop:~$ lsusb
Bus 005 Device 009: ID 071b:3203 Domain Technologies, Inc.
Bus 005 Device 002: ID 07d1:3c03 D-Link System
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 004 Device 002: ID 0738:4716 Mad Catz, Inc.
Bus 004 Device 001: ID 0000:0000

:(:confused::(
My D-link doesn't respond neither does a command for Wlan0
such as
user@user-desktop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

Or
user@user-desktop:~$ sudo iwconfig wlan0
wlan0     No such device

:confused:

And i've tried everything, basically at this part at least...:(
Please i need help!

I very much appreciate.

Hidetsu.:)

---

