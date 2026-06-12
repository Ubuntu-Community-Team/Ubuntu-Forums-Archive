---
title: "Does the ARTEC T14BR mini digital TV receiver work in Ubuntu 10.04???"
date: 2010-07-06
forum: New to Ubuntu
---

### Post by suomalainen on 2010-07-06
Ubunteros,

I have a laptop running 10.04 LTS. I want to get the ARTEC T14BR mini digital TV receiver working.

Is this possible to do?

Thank you.

---

### Post by Ocxic on 2010-07-06
plug it in, and install "tvtime" and see if it works.

---

### Post by suomalainen on 2010-07-06
Does tvtime handle digital broadcasts?

---

### Post by suomalainen on 2010-07-06
Actually, I just got done following your advice by installing TV time. Each time I attempt to launch TV Time it opens and then immeadiately closes? Is this considered a crash?

What should I do now? Are there other tv viewers I could use.

Thank you

---

### Post by Ocxic on 2010-07-06
yep thats a crash.
open tvtime from the terminal that will display any errors it's getting and we might be able to fix it.

just type "tvtime" in a terminal window and post the output.

Edit: post the output of "sudo lspci" and "sudo lsusb" aswell.

---

### Post by suomalainen on 2010-07-07
Hope this helps you.....

:~$ tvtime
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/paavo/.tvtime/tvtime.xml
videoinput: Cannot open capture device /dev/video0: No such file or directory
Segmentation fault
:~$

F.Y.I. My mini USB TV receiver is connected.....




sudo lspci =
 
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
02:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
02:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
02:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 03)
03:00.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
03:00.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
03:00.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65)




sudo lsusb=

Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05d8:810f Ultima Electronics Corp. 
Bus 001 Device 002: ID 0bc2:2300 Seagate RSS LLC 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by Ocxic on 2010-07-07
ok, I think i see the issue your having. unplug your usb stick, then plugit back in, and post the output if "dmesg" right after you plug it back in.
I'm just looking for the output device your computer assigns to the tuner.

Also if possible post the output of "sudo lshw" with your receiver plugged in. Use "sudo lshw > $HOME/lshw.txt" to save the very long output to a file, and attach it to your post. (the file should be saved in your home folder)

---

