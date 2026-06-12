---
title: "ASUS WL-330NUL pocket router"
date: 2014-04-29
forum: Networking &amp; Wireless
---

### Post by lemoirl on 2014-04-29
I just bought one of these ingenious little routers from ASUS:

[http://www.asus.com/Networking/WL330NUL/](http://www.asus.com/Networking/WL330NUL/)

It can do many things but what I need it for is to share the network connection from my laptop with other devices (my phone, tablet etc.). This is very useful when I've bought Wifi access in a hotel but it's limited to one device accessing at a time. The WL-330NUL creates a second, private, hotspot that my other devices connect to to share the connection.

That's the theory, anyway but the drivers and application are only available for Windows and OSX.

When I plug it into my USB, lsusb sees it but I can't get any further than that:

[FONT=courier new]Bus 001 Device 012: ID 0b05:17c7 ASUSTek Computer, Inc.[/FONT]



Has anyone had any success with this device? ASUS support pointed me towards the source code on their site ([http://dlcdnet.asus.com/pub/ASUS/wireless/WL-330NUL/GPL_WL_330NUL_30036.zip](http://dlcdnet.asus.com/pub/ASUS/wireless/WL-330NUL/GPL_WL_330NUL_30036.zip))  which I was able to compile but what I ended up compiling looks like the kernel and firmware for the device itself. I ended up with these files:

[FONT=courier new]-rwxr-xr-x 1 liam liam    8192 Apr 29 14:07 Default_HW_Setting.bin
-rwxr-xr-x 1 liam liam   65536 Apr 29 14:07 Default_SW_Setting.bin
-rw-r--r-- 1 liam liam  983040 Apr 29 14:07 linux.bin
-rwxr-xr-x 1 liam liam  935936 Apr 29 14:07 nfjrom
-rwxr-xr-x 1 liam liam 1519638 Apr 29 14:07 root.bin
-rwxr-xr-x 1 liam liam   65536 Apr 29 14:07 SW_Current_Setting.bin
-rwxr-xr-x 1 liam liam 3968219 Apr 29 14:07 vmlinux.elf
-rw-rw-rw- 1 liam liam 2502738 Apr 29 14:07 WL-330NUL_3.0.0.36.trx
-rwxr-xr-x 1 liam liam   24592 Apr 29 14:07 WL-330NUL_Boot_0-0-0-9_c2ebf6f4.trx[/FONT]


Any thoughts or help appreciated. Am I wasting my time even trying if ASUS don't provide compiled drivers?

---

### Post by lemoirl on 2014-04-29
UPDATE

For anyone who's interested, I managed to get this working the way I want but using a slightly different approach. I connected an ethernet cable from the WL-330NUL to the ethernet port on my laptop. I also plugged in the USB connector but just to power the device.

Then, by following the instructions below for sharing a network connection between the wireless and fixed ethernet devices on my laptop, I was able to share my connection over wifi to my phone.

[http://askubuntu.com/questions/359856/ubuntu-13-10-share-wireless-internet-connection-through-ethernet](http://askubuntu.com/questions/359856/ubuntu-13-10-share-wireless-internet-connection-through-ethernet)

So the end result looks like this:

WIFI -----> Laptop WLAN0 ----> Laptop eth0 ----> WL-330NUL ethernet port -----> WL-330NUL wifi hotspot

---

