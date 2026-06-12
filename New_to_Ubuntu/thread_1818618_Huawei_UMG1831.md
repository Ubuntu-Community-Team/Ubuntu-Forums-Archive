---
title: "Huawei UMG1831"
date: 2011-08-05
forum: New to Ubuntu
---

### Post by kirankadali on 2011-08-05
Hello....
I have the following modem and i would like to use it in ubuntu, i have searched for the drivers for linux but didnt find anything. Please help.......

Model: UMG1831
Manuf: Huawei (made for T-Mobile)

---

### Post by 3rdalbum on 2011-08-05
Apparently it should work out-of-the-box on Ubuntu. Did you try going to the Network Manager applet in your top panel and going Edit Connections, and then setting it up in there?

---

### Post by kirankadali on 2011-08-05
i have tried.. but the modem is being detected as mass storage device (modem has a micro sd slot) not as a network adaptor.........

---

### Post by gandaran on 2011-08-05
> **kirankadali said:**
> i have tried.. but the modem is being detected as mass storage device (modem has a micro sd slot) not as a network adaptor.........
which Ubuntu release do you have? if it's 10.04 you need to install usb-modeswitch from software center.

---

### Post by kirankadali on 2011-08-06
ubuntu desktop edition 9.10.....

---

### Post by 3rdalbum on 2011-08-06
Ubuntu 9.10 is many times obsolete, and it's reached End Of Life for support. You might need to upgrade to a newer version of Ubuntu for this device to work. Try 10.04 LTS, or 11.04 (which is the latest Ubuntu).

In either case though, those USB HSDPA modems all appear as virtual CD-ROMs, but they can still be used as modems even though their "CD-ROM" is mounted on the desktop. The virtual "CD-ROM" is a feature of these devices that allows Windows users to install the driver without having to provide an actual CD in the package. Have you tried setting up the connection and connecting? Have you maybe tried the device on a live CD of Ubuntu 10.04 or later?

---

### Post by kirankadali on 2011-08-06
Thanks guys......... i will try the new version.....

---

