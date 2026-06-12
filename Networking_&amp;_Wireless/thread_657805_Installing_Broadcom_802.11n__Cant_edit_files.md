---
title: "Installing Broadcom 802.11n  Cant edit files?"
date: 2008-01-04
forum: Networking &amp; Wireless
---

### Post by mr_lemonade on 2008-01-04
Hello, I have been trying to install my wlan0 for the past week and read many post and now I am finally banging my head on the wall.

Dell 1520 802.11n broadcom Ubuntu 7.1 Gutsy ndiswrapper v1.9
tried using both
R174292.exe
R140747.EXE
which the r14 is the driver for xp and other for vista. I am dual booting vista.  The R17 driver works for vista.


I have found many post that say pretty much the same thing

[http://ubuntuforums.org/archive/index.php/t-611273.html]("http://ubuntuforums.org/archive/index.php/t-611273.html")

[http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/]("http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/")

[http://ubuntuforums.org/archive/index.php/t-336654.html]("http://ubuntuforums.org/archive/index.php/t-336654.html")
Here is what I get when I do lspci

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
hull@hull-laptop:~$ 




```


/org/freedesktop/Hal/devices/pci_8086_2841  ---->info.parent
/org/freedesktop/Hal/devices/pci_14e4_4328  ----->info.udi

hull@hull-laptop:~$ sudo ndiswrapper -i /home/hull/desktop/R140747.exe
driver r140747.exe is already installed
 
or I assume same thing
```

hull@hull-laptop:~$ sudo ndiswrapper -i /home/hull/Desktop/R140747.EXE_FILES/DRIVER/bcmwl5.sys
driver bcmwl5.sys is already installed
hull@hull-laptop:~$ sudo ndiswrapper -i /home/hull/Desktop/R140747.EXE_FILES/DRIVER/bcmwl5.inf
driver bcmwl5 is already installed

```
then 

```

hull@hull-laptop:~$ sudo ndiswrapper -1
install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid' (dangerous)
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card
hull@hull-laptop:~$ sudo depmod -a
hull@hull-laptop:~$ sudo modprobe ndiswrapper
hull@hull-laptop:~$ sudo ndiswrapper -m
module configuration already contains alias directive

hull@hull-laptop:~$ gksudo gedit /ect/modules

```
*****when I enter this it comes up with a blank file.  I went in the system and found file and then it wouldn't let me save it so I logged in as root and added ndiswrapper to the bottom and still didn't work.


When I click network button and click manual configuration, I don't have wlan0 only modem and wired.  

Please let me know if i need to post anything else.  This is my dream to make Linux work with internet.
I am new to Linux so be nice :)
Thanks a million guys and gals.

---

### Post by ajmorris on 2008-01-04
if sudo ndiswrapper -l lists the driver needed, (should be bcmwl5), then do sudo modrpobe -a bcmwl5
then do sudo modprobe ndiswrapper.
Then do sudo ifup wlan0 (or valid wireless device) and see if it 'ups' the wireless device.

---

### Post by mr_lemonade on 2008-01-04
When I type sudo modprobe -a /home/hull/Desktop/R140747.EXE_FILES/DRIVER/bcmwl5.inf   it says 
WARNING: Module  /home/hull/Desktop/R140747.EXE_FILES/DRIVER/bcmwl5.inf    is not found.  I even did several variants.  

Also, when I typed ndiswrapper -l    does it look like it has right driver?

Thanks for any help.

---

### Post by ajmorris on 2008-01-05
> **mr_lemonade said:**
> When I type sudo modprobe -a /home/hull/Desktop/R140747.EXE_FILES/DRIVER/bcmwl5.inf   it says 
WARNING: Module  /home/hull/Desktop/R140747.EXE_FILES/DRIVER/bcmwl5.inf    is not found.  I even did several variants.  

Also, when I typed ndiswrapper -l    does it look like it has right driver?

Thanks for any help.

Post the output of ndiswrapper -l, and also, you dont need the path to the actual .exe install, just do sudo modprobe -a <driver name> e.g sudo modprobe -a bcmwl5 (sudo modprobe -l will tell you the driver name)

---

### Post by mr_lemonade on 2008-01-15
```

hull@hull-laptop:~$ ndiswrapper -l
bcmwl5 : invalid driver!
hull@hull-laptop:~$ sudo modprobe bcmwl5.inf
FATAL: Module bcmwl5.inf not found.
hull@hull-laptop:~$ clear
hull@hull-laptop:~$ sudo modprobe bcmwl5.inf
FATAL: Module bcmwl5.inf not found.
hull@hull-laptop:~$ ndiswrapper -l
bcmwl5 : invalid driver!
hull@hull-laptop:~$ sudo modprobe -a bcmwl5.inf
WARNING: Module bcmwl5.inf not found.
hull@hull-laptop:~$ ****The .inf file is installed..*****
bash: ****The: command not found
hull@hull-laptop:~$ sudo ndiswrapper -i /home/hull/bcmwl5.inf
driver bcmwl5 is already installed
hull@hull-laptop:~$ 

```

does show up in iwconfig 
lo not wireless extentsion and eth0 no wireless extentions
Thanks for all the help.

---

