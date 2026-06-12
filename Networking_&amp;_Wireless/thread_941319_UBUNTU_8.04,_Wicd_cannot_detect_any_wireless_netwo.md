---
title: "UBUNTU 8.04, Wicd cannot detect any wireless networds"
date: 2008-10-08
forum: Networking &amp; Wireless
---

### Post by shabbar on 2008-10-08
shabbar@shabbar-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wmaster0
       version: 02
       serial: 00:13:02:e3:b6:c0
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:08:08.0
       logical name: eth0
       version: 02
       serial: 00:16:d3:0b:f8:da
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A ip=99.255.85.145 latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes


anyone can help me out please

---

### Post by willca on 2008-10-08
can you try if this command actually shows any either

sudo iwlist wlan0 scan

---

### Post by Kevbert on 2008-10-08
Try
```
iwlist scanning
```
which will look at all network connections.

---

### Post by shabbar on 2008-10-09
shabbar@shabbar-laptop:~$ sudo iwlist wlan0 scan
[sudo] password for shabbar: 
wlan0     Failed to read scan data : Resource temporarily unavailable

---

### Post by shabbar on 2008-10-09
shabbar@shabbar-laptop:~$ sudo iwlist wlan0 scan
[sudo] password for shabbar: 
wlan0     Failed to read scan data : Resource temporarily unavailable

shabbar@shabbar-laptop:~$ 
shabbar@shabbar-laptop:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Failed to read scan data : Resource temporarily unavailable

---

### Post by shabbar on 2008-10-09
my driver is intalled

shabbar@shabbar-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce Go 7200 (rev a1)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
08:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
08:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
08:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
08:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
08:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
shabbar@shabbar-laptop:~$

---

### Post by shabbar on 2008-10-09
shabbar@shabbar-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

shabbar@shabbar-laptop:~$

---

### Post by Kevbert on 2008-10-09
Please take a look at this[[COLOR="Red"] post[/COLOR]]("http://ubuntuforums.org/showthread.php?t=820297"). The answer is there.

---

### Post by shabbar on 2008-10-12
thanks..it work
but now there is another problem..it doesnt connect to the wireless network...it trying to connect but at the end it never connects

---

### Post by 73ckn797 on 2008-10-12
> **shabbar said:**
> thanks..it work
but now there is another problem..it doesnt connect to the wireless network...it trying to connect but at the end it never connects


Have you tried to reset your router and modem? Could be that simple! I had similar issue on a Ubuntu re-install on my laptop. Reset of router was all that was needed and I could have saved the time doing the re-install.

---

### Post by shabbar on 2008-10-14
my wireless doesnt detect any networks untill i put through these commands in the terminal

sudo rmmod -f iwl3945
 sudo modprobe iwl3945 disable_hw_scan=1

after that commands..it detects the wireless networks..and the Wicd shows available networks but once i click connect ..it says its connecting but at the end it doesnt connect on the not encrypted network.

and on my UofT wireless networks..it uses WEP..i tried all WEP(passphrase) and other WEP encryption but same problem..

---

### Post by shabbar on 2008-10-14
ok i solved the part where i had to type in the codes everytime...

still the problem is that i cannot connect to the wireless networks
it saying its connecting and its saying obtaining ip address..then suddenly it doesnt connect.

---

