---
title: "I need help getting my wireless connection to work on new install."
date: 2009-01-21
forum: New to Ubuntu
---

### Post by Cherick on 2009-01-21
I have a dell XPS m140 laptop, with a wireless 1370 WLAN mini PCI card.
I connect using my home wireless network, with a WEP key, and using an AT&T 2WIRE modem/router.
I just installed Ubuntu using Wubi, but it's not detecting my wireless network.
Can someone help me here, tell me what info do you need from me and where do I get it, please?
If I need to run a command and bring the output here can you guys help as to how do I copy it from Ubuntu and bring it to Windows so I can paste it here.

Thanks in advance for the help.

---

### Post by jerome1232 on 2009-01-21
Well this would help figuring out what chipset you have and etc...

```
sudo lshw -C network
lspci
```

If you have a digital camera might be easiest to snap a pic and upload it to the windows computer. Or perhaps temporarily hook up an ethernet cable.

---

### Post by Cherick on 2009-01-21
Ok, I'm using the ethernet cable right now.
I don't know if I did that command correctly because it was asking me for my password, but it finally gave an output. Here it is:




SCSI                      
  *-network:0      
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:14:22:9a:b2:42
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.67 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:5b:df:d1
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 12:f5:9e:9d:10:94
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
cherick@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
02:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
02:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
02:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

---

### Post by Cherick on 2009-01-21
Something tells me I did it wrong, should I had unhooked the cable before the command? If so, here is the new output.


00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
02:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
02:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
02:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

---

### Post by jerome1232 on 2009-01-21
[http://www.sampbar.com/2008/11/broadcom-bcm4318-ubuntu-intrepid.html](http://www.sampbar.com/2008/11/broadcom-bcm4318-ubuntu-intrepid.html)

It seems you have a BCM4318, hopefully this how-to will do it for you.

--edit-- it doesn't matter whether the ethernet cable is hooked up or not.

---

### Post by Cherick on 2009-01-21
Didn't work.
The driver installed but said something about a "bcmwl5.sys" file missing 
Here is the last screen in the terminal.


cherick@ubuntu:~$ sudo cd ~/Desktop
sudo: cd: command not found
cherick@ubuntu:~$ sudo ndiswrapper -i bcmwl5a.inf
driver bcmwl5a is already installed
cherick@ubuntu:~$ sudo ndiswrapper -l
bcmwl5a : invalid driver!
cherick@ubuntu:~$ sudo depmod -a
cherick@ubuntu:~$ sudo modprobe ndiswrapper
cherick@ubuntu:~$ sudo cp /etc/network/interfaces /etc/network/interfaces.orig
cherick@ubuntu:~$ echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
auto lo
iface lo inet loopback

cherick@ubuntu:~$ sudo ndiswrapper -m
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...

************************************************************************
*
* The update-modules command is deprecated and should not be used!
*
************************************************************************

cherick@ubuntu:~$ echo 'ndiswrapper' | sudo tee -a /etc/modules
ndiswrapper
cherick@ubuntu:~$ echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
ENABLED=0
cherick@ubuntu:~$ cd /Desktop
bash: cd: /Desktop: No such file or directory
cherick@ubuntu:~$ cd Desktop
cherick@ubuntu:~/Desktop$ ls
BCM4318-Ubuntu-Intrepid.zip  bcmwl5a.inf  wifi.sh
cherick@ubuntu:~/Desktop$ sudo mv wifi.sh ~/etc/init.d/
mv: cannot move `wifi.sh' to `/home/cherick/etc/init.d/': No such file or directory
cherick@ubuntu:~/Desktop$ sudo mv wifi.sh /etc/init.d/
cherick@ubuntu:~/Desktop$ cd ~
cherick@ubuntu:~$ sudo cd /etc/init.d/
sudo: cd: command not found
cherick@ubuntu:~$ cd /etc/init.d/
cherick@ubuntu:/etc/init.d$ sudo update-rc.d wifi.sh defaults
update-rc.d: warning: /etc/init.d/wifi.sh missing LSB style header
 Adding system startup for /etc/init.d/wifi.sh ...
   /etc/rc0.d/K20wifi.sh -> ../init.d/wifi.sh
   /etc/rc1.d/K20wifi.sh -> ../init.d/wifi.sh
   /etc/rc6.d/K20wifi.sh -> ../init.d/wifi.sh
   /etc/rc2.d/S20wifi.sh -> ../init.d/wifi.sh
   /etc/rc3.d/S20wifi.sh -> ../init.d/wifi.sh
   /etc/rc4.d/S20wifi.sh -> ../init.d/wifi.sh
   /etc/rc5.d/S20wifi.sh -> ../init.d/wifi.sh
cherick@ubuntu:/etc/init.d$ sudo chmod +x wifi.sh

---

### Post by Cherick on 2009-01-21
bump.

---

### Post by Cherick on 2009-01-21
I activated the driver, but still no connection.

Should I uninstall Wubi, and then start again?

---

### Post by joe0212 on 2009-01-21
hi i am having a problem on ps3 with the new ubuntu i am not sure what to do in settings for internet eth0 i am a complete newbie i have a cisco access point and netgear router what do i do to connect to that and do i use router or wireless info 

any help for this will be appriciated i really could use it never programmed or used linux before and its so much faster

---

### Post by joe0212 on 2009-01-21
> **joe0212 said:**
> hi i am having a problem on ps3 with the new ubuntu i am not sure what to do in settings for internet eth0 i am a complete newbie i have a cisco access point and netgear router what do i do to connect to that and do i use router or wireless info 

any help for this will be appriciated i really could use it never programmed or used linux before and its so much faster

wep

---

### Post by sampbar on 2009-01-24
joe0212: I suggest you make your own thread for that problem as it has nothing to do with this thread.

Cherick: Have you got it working? If not im the creator of the guide you have been trying to use! If you email me at samuelbarrett {a} sampbar.com i can try and get down to the root of your problem. It also seems like you've used a combination of the .sh's provided and typing in the script yourself.

---

