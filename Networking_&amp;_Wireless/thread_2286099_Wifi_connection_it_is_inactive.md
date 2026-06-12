---
title: "Wifi connection it is inactive"
date: 2015-07-09
forum: Networking &amp; Wireless
---

### Post by luigi_s on 2015-07-09
Good afternoon to greet tastes
 I'm having problems with wifi connection it is inactive in the Ubuntu menu bar .... Install in Ubuntu 15.04 on a Lenovo Miix 2 and the time to complete the installation notice that the option to search and connect the wireless is disabled ..
  hardwareI see that the connection is recognized[INDENT=3]

[/INDENT]
$   ifconfig -a  

 lo Link encap:Bucle local
Direc. inet:127.0.0.1 Másc:255.0.0.0
Dirección inet6: ::1/128 Alcance:Anfitrión
ACTIVO BUCLE FUNCIONANDO MTU:65536 Métrica:1
Paquetes RX:1682 errores:0 perdidos:0 overruns:0 frame:0
Paquetes TX:1682 errores:0 perdidos:0 overruns:0 carrier:0
colisiones:0 long.colaTX:0
Bytes RX:140165 (140.1 KB) TX bytes:140165 (140.1 KB)
 wlan0 Link encap:Ethernet direcciónHW 48:d5:25:45:ab:2f
DIFUSIÓN MULTICAST MTU:1500 Métrica:1
Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
colisiones:0 long.colaTX:1000
Bytes RX:0 (0.0 B) TX bytes:0 (0.0 B)




 
 
 run the command: rfkill unblock all to activate all radio frequency devices and restart the computer fault persists[INDENT=3]

[/INDENT]
$   rfkill list

 0: ideapad_wlan: Wireless LAN
Soft blocked: no
Hard blocked: yes
1: ideapad_bluetooth: Bluetooth
Soft blocked: no
Hard blocked: yes
2: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no
3: hci0: Bluetooth
Soft blocked: no
Hard blocked: no

verify if the Hardware is correctly installed




$   sudo lspci -nnk

 02:00.0 Network controller [0280]: Qualcomm Atheros AR9462 Wireless Network Adapter [168c:0034] (rev 01)
Subsystem: Lenovo Device [17aa:3214]
Kernel driver in use: ath9k

 $   dmesg | grep phy0
[ 2.000445] ath: phy0: ASPM enabled: 0x43
[ 2.006792] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[ 2.007213] ieee80211 phy0: Atheros AR9462 Rev:2 mem=0xffffc90015800000, irq=18

 $   sudo lshw -short

 ruta H/W Dispositivo Clase Descripción
=========================================================
system Computer
/0 bus Motherboard
/0/0 memory 3860MiB Memoria de sistema
/0/1 processor Intel(R) Core(TM) i5-4202Y CPU @ 1.60GHz
/0/100 bridge Haswell-ULT DRAM Controller
/0/100/2 display Intel Corporation
/0/100/3 multimedia Haswell-ULT HD Audio Controller
/0/100/4 generic Intel Corporation
/0/100/14 bus 8 Series USB xHCI HC
/0/100/14/0 usb2 bus xHCI Host Controller
/0/100/14/1 usb1 bus xHCI Host Controller
/0/100/14/1/3 bus USB2.0 Hub
/0/100/14/1/3/2 input Microsoft
/0/100/14/1/3/3 input ITE Device(8595)
/0/100/14/1/4 multimedia Lenovo EasyCamera
/0/100/14/1/5 multimedia Imaging Device
/0/100/16 communication 8 Series HECI #0
/0/100/1b multimedia 8 Series HD Audio Controller
/0/100/1c bridge 8 Series PCI Express Root Port 1
/0/100/1c.2 bridge 8 Series PCI Express Root Port 3
/0/100/1c.2/0 wlan0 network AR9462 Wireless Network Adapter
/0/100/1d bus 8 Series USB EHCI #1
/0/100/1d/1 usb3 bus EHCI Host Controller
/0/100/1d/1/1 bus USB hub
/0/100/1d/1/1/6 communication Interfaz Bluetooth
/0/100/1d/1/1/8 input Atmel maXTouch Digitizer
/0/100/1f bridge 8 Series LPC Controller
/0/100/1f.2 storage 8 Series SATA Controller 1 [AHCI mode]
/0/100/1f.3 bus 8 Series SMBus Controller
/0/100/1f.6 generic 8 Series Thermal
/0/2 scsi0 storage
/0/2/0.0.0 ev/sda disk 512GB Crucial_CT512M55
/0/2/0.0.0/1 volume 511MiB Windows FAT volumen
/0/2/0.0.0/2 /dev/sda2 volume 472GiB partición EXT4
/0/2/0.0.0/3 /dev/sda3 volume 4002MiB Linux swap volumen

 $   sudo lshw -c network

 *-network DESACTIVADO
descripción: Interfaz inalámbrica
producto: AR9462 Wireless Network Adapter
fabricante: Qualcomm Atheros
id físico: 0
información del bus: pci@0000:02:00.0
nombre lógico: wlan0
versión: 01
serie: 48:d5:25:45:ab:2f
anchura: 64 bits
reloj: 33MHz
capacidades: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
configuración: broadcast=yes driver=ath9k driverversion=3.19.0-21-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
recursos: irq:18 memoria:f0400000-f047ffff memoria:f0480000-f048ffff

 I notice that the Wireless is disabled .. to activate use the command

 $  ifconfig Wlan0 up

 $   sudo lshw -c network
*-network
descripción: Interfaz inalámbrica
producto: AR9462 Wireless Network Adapter
fabricante: Qualcomm Atheros
id físico: 0
información del bus: pci@0000:02:00.0
nombre lógico: wlan0
versión: 01
serie: 48:d5:25:45:ab:2f
anchura: 64 bits
reloj: 33MHz
capacidades: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
configuración: broadcast=yes driver=ath9k driverversion=3.19.0-21-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
recursos: irq:18 memoria:f0400000-f047ffff memoria:f0480000-f048ffff








 
 
 but equally Wireless is disabled in the menu bar of Ubuntu
 I see the hardware is recognized without problem but do not know because the wireless option is disabled've activated all I get off and try anything .. also configure Windows Drivers have the computer using ndiswrapper but the result is the same .. It notes that the team has no lock on the Wi-Fi to install Windows Hardware level and the Wi-Fi works without problem ..
 please I can to help solve my little problem ....

---

### Post by praseodym on 2015-07-10
Please check here:

[http://ubuntuforums.org/showthread.php?t=2111690&p=12490285#post12490285](http://ubuntuforums.org/showthread.php?t=2111690&p=12490285#post12490285)

---

### Post by luigi_s on 2015-07-12
Hola.. ya ingrese al bios del equipo y realice la activavion de la Wifi pero persiste el problema.. 

lo que no entiendo por que la 0: ideapad_wlan: Wireless LAN y el 1: ideapad_bluetooth: Bluetooth esta  ---  Hard blocked: yes ????

hago pruebas con el Bluetooth funciona sin problema 




\\\\\\\\\\\   $   rfkill list  \\\\\\\\\\\\\\\

 _0: ideapad_wlan: Wireless LAN_
Soft blocked: no
**Hard blocked: yes**
_1: ideapad_bluetooth: Bluetooth_
Soft blocked: no
**Hard blocked: yes**

2: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no
3: hci0: Bluetooth
Soft blocked: no
Hard blocked: no

---

### Post by Bucky Ball on 2015-07-13
Please use code tags for terminal output. Neater, space saving and easier to read. See the last link in my signature and add them to your output, please. Thanks. :)

---

