---
title: "Cannot connect Wireless Internet"
date: 2009-07-02
forum: New to Ubuntu
---

### Post by RDawg44 on 2009-07-02
Hello,

I'm still new to Ubuntu, so find certain things much harder than I did on Windows.  My problem is with the wireless internet.  It was working fine, but then my music player, banshee crashed, and at the same time, my wireless internet stopped working.  I ran a hardware test, and it says it's okay, but there is no connection.  I click on the drop down menu, but there are no wireless neworks available, although there should be.  I can manually connect, but there is 0% connection, and I can even manually connect to wireless networks that don't even exist (of course with 0% connection).

My laptop is a DELL Inspiron 1525 which uses Ubuntu 8.04 LTS Hardy Heron.

the lspci command also gives the following output:
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

Any ideas would be greatly appreciated.  Thanks!

---

### Post by ubudog on 2009-07-02
Try turning off your wireless via the switch and if that doesn't work then reboot.

---

### Post by sdlynx on 2009-07-02
are you sure the wireless is turned on...?

---

### Post by ubudog on 2009-07-02
> **ubudog said:**
> Try turning off your wireless via the switch and if that doesn't work then reboot.

And then turn it back on of course.

---

### Post by RDawg44 on 2009-07-06
Thanks for the help everyone, I think I got it working.  But instead of having the bars in the top right hand corner as I normally do for wireless, I have the two computers, which I thought was normal only for wired connections.  I got the connection working by turning off the roaming on my wireless, and manually entering the info for the wireless network I wanted to connect to (done under network settings).  I have never had to do this before.  Is there a better way to connect, or should I just now follow that saying, "if it ain't broke, don't fix it"?

Also, is there a wireless switch on a Dell Inspiron 1525?  I can't seem to find it and my instructions are packed away somewhere. . .

---

### Post by RDawg44 on 2009-07-07
Well, it looks like I fixed it.  I deleted the network off my list of wireless networks that I regularily connected to, and then re-entered all the information and now it works great!

---

### Post by ubudog on 2009-07-07
If you have any more problems check out:[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/).  It's like network manager.  Pretty easy to use.

---

### Post by LewRockwell on 2009-07-07
> **RDawg44 said:**
> Thanks for the help everyone, I think I got it working.  But instead of having the bars in the top right hand corner as I normally do for wireless, I have the two computers, which I thought was normal only for wired connections.  I got the connection working by turning off the roaming on my wireless, and manually entering the info for the wireless network I wanted to connect to (done under network settings).  I have never had to do this before.  Is there a better way to connect, or should I just now follow that saying, "if it ain't broke, don't fix it"?

Also, is there a wireless switch on a Dell Inspiron 1525?  I can't seem to find it and my instructions are packed away somewhere. . .

some laptops use the function button and an F(number) button to turn the "radio/wireless" on and off

others have actual switches located somewhere on the exterior

and still others have none

.

---

