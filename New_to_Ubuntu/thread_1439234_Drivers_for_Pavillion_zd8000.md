---
title: "Drivers for Pavillion zd8000"
date: 2010-03-25
forum: New to Ubuntu
---

### Post by havic54 on 2010-03-25
While I'm not 100% new to ubuntu, I haven't used it in long enough to remember much.
Here's my deal...
I am running an old Hp Pavillion zd8000. I just installed 9.10 the other day and need some help with getting drivers and everything figured out. I'm pretty sure I have the graphics driver worked out, using xorg, but I still need help getting the wireless driver to work. I have ndiswrapper installed and WINE, and I downloaded the driver off the HP website...where do I go from here? I had it working once upon a time when I used ubuntu again but I can't remember for the life of me how I got it all running. Also, the sound seems to be disabled as well. I have tried a few different videos and ran the test and nothing on that either. Any help would be very much appreciated. Thanks!

---

### Post by mullinsn2000 on 2010-03-25
Have you tried using a wired connection and see if update manager/harware manager has any drivers for the wireless card?

---

### Post by anewguy on 2010-03-25
If you have no luck with what mullinsn2000 suggested, then we need to know the device in order to really provide direct help:

In a terminal window (applications/accessories/terminal):

type:

lspci <press enter>

lsusb <press enter>

Post the output of both of these back here and we can go from there.

Dave :)

---

### Post by havic54 on 2010-03-26
lspci:
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M24 1P [Radeon Mobility X600]
0b:00.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
0b:00.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
0b:00.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
0b:00.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
0b:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0b:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)


lsusb:
Bus 001 Device 003: ID 136b:cb07 STEC 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 03f0:011d Hewlett-Packard Integrated Bluetooth Module
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by anewguy on 2010-03-26
If you can hardwire a network connection, do an update and look under restricted drivers to see if the wireless driver appears there.  If not, we can always use ndiswrapper and ndisgtk if you want.

For ndiswrapper:

copy the .inf and .sys files for your driver (probably something like bcmwl5.inf and .sys) to your desktop

open a terminal window (applications/accessories/terminal)

type:

sudo ndiswrapper -l <press enter>  That's a lower case "L" for "list"

If this returns anything, you must clear it out before we can start by doing the following for each entry returned:

sudo ndiswrapper -e xxxxx <press enter> where xxxxx is the name returned in the list above

Once ndiswrapper doesn't return anything, proceed on with the following:

cd Desktop <press enter>

sudo ndiswrapper -i xxxxxx.inf <press enter> where xxxxxx is the driver .inf file name, as an example bcmwl5.sys

sudo depmod -a <press enter>

sudo ndiswrapper -m <press enter>

sudo modprobe ndiswrapper <press enter>

sudo gedit /etc/modprobe.d/blacklist.conf <press enter>

This will call up an editor and open the blacklist.conf file.  Scroll to the bottom of this file and add the following lines:

blacklist b43
blacklist ssb 
blacklist bcm43xx
blacklist b43legacy

(not sure with 9.10, but I *think* the bottom 2 are still needed).

Save the file and exit the editor.

gedit /etc/modules <press enter>

scroll to the bottom and add the following line:

ndiswrapper

Save the file and exit the editor.

Reboot your PC.  See if the wireless is now showing.  If not, post back the outputs from the following:

sudo ndiswrapper -l <press enter>

iwconfig <press enter>

ifconfig <press enter>

Dave :)

---

### Post by havic54 on 2010-03-26
I got up to the line where you enter
```
sudo ndiswrapper -m
```
and was returned with
```
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
module configuration already contains alias directive

```

---

### Post by anewguy on 2010-03-27
Just ignore those messages for now and keep going.

Dave :)

---

### Post by havic54 on 2010-03-27
Got it all set up and working =)
Thankyou so much for your help!

---

### Post by anewguy on 2010-03-27
Your welcome.  If you wouldn't mind, please use the "Thread Tools" option at the top of the post and mark the thread as solved.

Dave ;)

---

