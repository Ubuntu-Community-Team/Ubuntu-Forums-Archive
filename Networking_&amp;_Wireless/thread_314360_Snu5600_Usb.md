---
title: "Snu5600 Usb"
date: 2006-12-07
forum: Networking &amp; Wireless
---

### Post by XelleX90 on 2006-12-07
Hallo, i found the driver for my Philips SNU5600 USB thing. or at least i think lol, i tryed Ndiswrapper and ndisgtk.

Ndisgtk shows me that the driver is  installed and hardware is pressent, BUT it dosnt show up inn Networking (eth1) and the Philips SNU5600 dosnt seem to register that its been instaled so it whont blink with it's light as it is supose to do:( can any one please tell me how i can fix this?
can someone please help me?
I'm desperat to get it to work!!!

Thanks!

---

### Post by FrodoB on 2006-12-07
Publish the output of:

lsusb

If it says that it is a ZyDas device or if a search on the web reveals that this is a Zydas zd1211 or zd1211b then follow these instructions:

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29)

---

