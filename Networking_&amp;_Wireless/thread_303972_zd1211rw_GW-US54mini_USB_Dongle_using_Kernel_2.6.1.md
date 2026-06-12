---
title: "zd1211rw GW-US54mini USB Dongle using Kernel 2.6.18.3"
date: 2006-11-21
forum: Networking &amp; Wireless
---

### Post by trippinnik on 2006-11-21
OK, I just bought a GW-US54mini USB dongle for my laptop because I saw that it had linux drivers on the companies website (Planex).  Then I did some more searching and found that if I got the newest kernel the driver zd1211rw is included.  So I have managed to build my own kernel etc.  But iwconfig doesn't see it as a net connection.  it looks like the module is loaded 
[  377.494000] usb_init()
[  377.494000] usbcore: registered new driver zd1211rw
[  377.494000] zd1211rw initialized

Do I need to do something else? Has anyone gotten this to work?

---

### Post by FrodoB on 2006-11-21
What is the output of iwconfig?

---

### Post by trippinnik on 2006-11-21
iwconfig:
lo        no wireless extensions.

irda0     no wireless extensions.

sit0      no wireless extensions.

eth0      no wireless extensions.

---

### Post by FrodoB on 2006-11-21
Can we see the output of lsusb. please. 

These instructions will take you through the process of disabling the zd1211rw and replacing it with Zydas native driver, which should work for you:

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29)

---

### Post by trippinnik on 2006-11-21
OK, here lsusb output:

Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 14ea:ab13  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 05e3:0702 Genesys Logic, Inc. USB 2.0 IDE Adapter
Bus 001 Device 005: ID 0411:0087 MelCo., Inc. 
Bus 001 Device 004: ID 0c3c:0660 Radius Co., Ltd 
Bus 001 Device 001: ID 0000:0000  

I saw this bit about disabling zd1211rw and using the zd1211, but I thought zd1211rw is supposed to be better.  I also had a bit of trouble with that one.

---

### Post by trippinnik on 2006-11-21
thanks, I'll try that way.  it's a different one.  i guess i still get something out of compiling my own kernel.

---

### Post by trippinnik on 2006-11-21
ok, i wish i had tried your version before.  i went through the steps and there were no errors but it's not working.  
dmesg
[ 7454.643000] Make sure the hotplug firmware loader is installed.
[ 7454.643000] zd1211_Download_IncludeFile failed
[ 7454.643000] zd1211: probe of 2-1:1.0 failed with error -5

I think I may have something leftover from a different way to install the zd1211 driver.  how can I get rid of it?  Should I try booting in the older kernel since it says i should make sure hotplug firmware loader is installed?
thanks for you help.

---

### Post by FrodoB on 2006-11-21
Which one of these is the device?

> **trippinnik said:**
> OK, here lsusb output:

Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 14ea:ab13  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 05e3:0702 Genesys Logic, Inc. USB 2.0 IDE Adapter
Bus 001 Device 005: ID 0411:0087 MelCo., Inc. 
Bus 001 Device 004: ID 0c3c:0660 Radius Co., Ltd 
Bus 001 Device 001: ID 0000:0000  

I saw this bit about disabling zd1211rw and using the zd1211, but I thought zd1211rw is supposed to be better.  I also had a bit of trouble with that one.

---

### Post by trippinnik on 2006-11-21
FrodoB, I cleaned up the other stuff (i think) and tried again after a reboot. 
dmesg gives me this
[  822.312000] zd1211: failed intr_urb
[  822.312000] zd1211:USB ST Code = -22
[  822.312000] zd1211: probe of 2-1:1.0 failed with error -5
[  822.314000] usbcore: registered new driver zd1211
and lsusb still lists the same thing.

---

### Post by trippinnik on 2006-11-21
It's the second one from that list.  When I searched it in google it came up with my hardware GW-us54mini.

---

### Post by trippinnik on 2006-11-21
Bus 002 Device 002: ID 14ea:ab13

---

### Post by trippinnik on 2006-11-21
OK, Got it working, I tried again with my generic kernel.  looks like I sucked at making my own.  thanks for your help.  you must laugh at all the stupid stuff people end up with that causes problems.

---

### Post by FrodoB on 2006-11-21
Yes, this may work fine for you. This is the original zd1211. 

I have the zd1211b, which appears to work, but actually does not without building a new driver.

---

