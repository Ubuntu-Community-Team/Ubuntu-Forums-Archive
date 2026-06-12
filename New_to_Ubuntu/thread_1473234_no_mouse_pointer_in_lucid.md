---
title: "no mouse pointer in lucid"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by virgu on 2010-05-05
Hello,
I have recently downloaded and installed Lucid on my desktop. It's an old P4 machine with 512Mb memory.Jaunty and Karmic worked fine for me on it.

However after installation everything is fine upto login.When the desktop appears I cant see my mouse pointer anywhere.I've had to press Ctrl to locate it or use the keyboard instead.Funny thing is once I open the Terminal and type something and press Return, the mouse pointer appears automatically,same thing happens for Gedit as well.

what can be the reason behind this? And what's the solution?

Apart from this there seems to be no problem so far.Please help guys.

---

### Post by clockworkpc on 2010-05-06
Hi, 

I've discovered exactly the same thing.  It's happened twice, both times after I let the battery run, which I assume prompted hibernation mode.

I'm using Lucid 32bit Desktop on an ASUS FSA Series.

Here's the output from ***hwinfo --short***:

cpu:                                                            
                       Intel(R) Core(TM)2 Duo CPU     P8600  @ 2.40GHz, 2400 MHz
                       Intel(R) Core(TM)2 Duo CPU     P8600  @ 2.40GHz, 800 MHz
keyboard:
  /dev/input/event5    Microsoft Wireless Desktop Receiver 3.1A
  /dev/input/event4    AT Translated Set 2 keyboard
mouse:
  /dev/input/mice      Microsoft Wireless Desktop Receiver 3.1A
  /dev/input/mice      Microsoft Basic Optical Mouse v2.0
  /dev/input/mice      Macintosh mouse button emulation
  /dev/input/mice      SynPS/2 Synaptics TouchPad
graphics card:
                       Intel Mobile 4 Series Chipset Integrated Graphics Controller
                       Intel Mobile 4 Series Chipset Integrated Graphics Controller
sound:
                       Intel 82801I (ICH9 Family) HD Audio Controller
storage:
                       Intel ICH9M/M-E SATA AHCI Controller
network:
  wlan0                Intel Wireless WiFi Link 5100
  eth0                 ASUSTeK U6V laptop
network interface:
  lo                   Loopback network interface
  eth0                 Ethernet network interface
  wlan0                WLAN network interface
  pan0                 Ethernet network interface
disk:
  /dev/sda             ST9320320AS
partition:
  /dev/sda1            Partition
  /dev/sda2            Partition
  /dev/sda3            Partition
  /dev/sda5            Partition
  /dev/sda6            Partition
  /dev/sda7            Partition
  /dev/sda8            Partition
  /dev/sda9            Partition
cdrom:
  /dev/sr0             TSSTcorp CDDVDW TS-L633A
usb controller:
                       Intel 82801I (ICH9 Family) USB UHCI Controller #4
                       Intel 82801I (ICH9 Family) USB UHCI Controller #5
                       Intel 82801I (ICH9 Family) USB UHCI Controller #6
                       Intel 82801I (ICH9 Family) USB2 EHCI Controller #2
                       Intel 82801I (ICH9 Family) USB UHCI Controller #1
                       Intel 82801I (ICH9 Family) USB UHCI Controller #2
                       Intel 82801I (ICH9 Family) USB UHCI Controller #3
                       Intel 82801I (ICH9 Family) USB2 EHCI Controller #1
bios:
                       BIOS
bridge:
                       Intel Mobile 4 Series Chipset Memory Controller Hub
                       Intel 82801I (ICH9 Family) PCI Express Port 1
                       Intel 82801I (ICH9 Family) PCI Express Port 2
                       Intel 82801I (ICH9 Family) PCI Express Port 3
                       Intel 82801I (ICH9 Family) PCI Express Port 6
                       Intel 82801 Mobile PCI Bridge
                       Intel ICH9M LPC Interface Controller
hub:
                       Linux 2.6.32-21-generic ehci_hcd EHCI Host Controller
                       Linux 2.6.32-21-generic ehci_hcd EHCI Host Controller
                       Linux 2.6.32-21-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.32-21-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.32-21-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.32-21-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.32-21-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.32-21-generic uhci_hcd UHCI Host Controller
                       Alcor Micro Hub
memory:
                       Main Memory
bluetooth:
                       ASUSTek BT-253
unknown:
                       FPU
                       DMA controller
                       PIC
                       Timer
                       Keyboard controller
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
  /dev/input/event10   Chicony Electronics USB2.0 1.3M UVC WebCam
  /dev/input/event8    Uni Class SP02-A1
clockworkpc@clockworkpc-laptop:~$ lspic
No command 'lspic' found, did you mean:
 Command 'lspci' from package 'pciutils' (main)
 Command 'lsdic' from package 'canna-utils' (universe)
lspic: command not found
clockworkpc@clockworkpc-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
02:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
clockworkpc@clockworkpc-laptop:~$ hwinfo --short
cpu:                                                            
                       Intel(R) Core(TM)2 Duo CPU     P8600  @ 2.40GHz, 2400 MHz
                       Intel(R) Core(TM)2 Duo CPU     P8600  @ 2.40GHz, 2400 MHz
keyboard:
  /dev/input/event5    Microsoft Wireless Desktop Receiver 3.1A
  /dev/input/event4    AT Translated Set 2 keyboard
mouse:
  /dev/input/mice      Microsoft Wireless Desktop Receiver 3.1A
  /dev/input/mice      Microsoft Basic Optical Mouse v2.0
  /dev/input/mice      Macintosh mouse button emulation
  /dev/input/mice      SynPS/2 Synaptics TouchPad
graphics card:
                       Intel Mobile 4 Series Chipset Integrated Graphics Controller
                       Intel Mobile 4 Series Chipset Integrated Graphics Controller
sound:
                       Intel 82801I (ICH9 Family) HD Audio Controller
storage:
                       Intel ICH9M/M-E SATA AHCI Controller
network:
  wlan0                Intel Wireless WiFi Link 5100
  eth0                 ASUSTeK U6V laptop
network interface:
  lo                   Loopback network interface
  eth0                 Ethernet network interface
  wlan0                WLAN network interface
  pan0                 Ethernet network interface
disk:
  /dev/sda             ST9320320AS
partition:
  /dev/sda1            Partition
  /dev/sda2            Partition
  /dev/sda3            Partition
  /dev/sda5            Partition
  /dev/sda6            Partition
  /dev/sda7            Partition
  /dev/sda8            Partition
  /dev/sda9            Partition
cdrom:
  /dev/sr0             TSSTcorp CDDVDW TS-L633A
usb controller:
                       Intel 82801I (ICH9 Family) USB UHCI Controller #4
                       Intel 82801I (ICH9 Family) USB UHCI Controller #5
                       Intel 82801I (ICH9 Family) USB UHCI Controller #6
                       Intel 82801I (ICH9 Family) USB2 EHCI Controller #2
                       Intel 82801I (ICH9 Family) USB UHCI Controller #1
                       Intel 82801I (ICH9 Family) USB UHCI Controller #2
                       Intel 82801I (ICH9 Family) USB UHCI Controller #3
                       Intel 82801I (ICH9 Family) USB2 EHCI Controller #1
bios:
                       BIOS
bridge:
                       Intel Mobile 4 Series Chipset Memory Controller Hub
                       Intel 82801I (ICH9 Family) PCI Express Port 1
                       Intel 82801I (ICH9 Family) PCI Express Port 2
                       Intel 82801I (ICH9 Family) PCI Express Port 3
                       Intel 82801I (ICH9 Family) PCI Express Port 6
                       Intel 82801 Mobile PCI Bridge
                       Intel ICH9M LPC Interface Controller
hub:
                       Linux 2.6.32-21-generic ehci_hcd EHCI Host Controller
                       Linux 2.6.32-21-generic ehci_hcd EHCI Host Controller
                       Linux 2.6.32-21-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.32-21-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.32-21-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.32-21-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.32-21-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.32-21-generic uhci_hcd UHCI Host Controller
                       Alcor Micro Hub
memory:
                       Main Memory
bluetooth:
                       ASUSTek BT-253
unknown:
                       FPU
                       DMA controller
                       PIC
                       Timer
                       Keyboard controller
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
  /dev/input/event10   Chicony Electronics USB2.0 1.3M UVC WebCam
  /dev/input/event8    Uni Class SP02-A1

Hope this helps someone.

Cheers,

clockworkpc

---

