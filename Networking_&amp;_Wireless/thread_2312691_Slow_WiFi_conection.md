---
title: "Slow WiFi conection"
date: 2016-02-06
forum: Networking &amp; Wireless
---

### Post by Ignacio_de_Villafa on 2016-02-06
Here I show this information.

[PHP]root@idevillafane-K52Dr:~# sudo -i
root@idevillafane-K52Dr:~# lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] RS880 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 1)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 41)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge (rev 40)
00:16.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Link Control
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Park [Mobility Radeon HD 5430/5450/5470]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Cedar HDMI Audio [Radeon HD 5400/6300 Series]
04:00.0 Network controller: Broadcom Corporation BCM43142 802.11b/g/n (rev 01)
05:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 80)
05:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 80)
05:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 80)
05:00.4 System peripheral: JMicron Technology Corp. xD Host Controller (rev 80)
05:00.5 Ethernet controller: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller (rev 03)
root@idevillafane-K52Dr:~# lspci | grep -i ethernet   
05:00.5 Ethernet controller: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller (rev 03)
root@idevillafane-K52Dr:~# lspci | grep -i network
04:00.0 Network controller: Broadcom Corporation BCM43142 802.11b/g/n (rev 01)
root@idevillafane-K52Dr:~# lsusb  
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 04ca:2006 Lite-On Technology Corp. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 13d3:5130 IMC Networks 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
root@idevillafane-K52Dr:~# lsusb | grep -i ethernet
root@idevillafane-K52Dr:~# lsusb | grep -i network
Bus 002 Device 002: ID 13d3:5130 IMC Networks 
root@idevillafane-K52Dr:~# lsmod | grep iwl
root@idevillafane-K52Dr:~# ifconfig
eth0      Link encap:Ethernet  direcciónHW 20:cf:30:2b:19:2f  
          ACTIVO DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:30 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:65536  Métrica:1
          Paquetes RX:1700 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:1700 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:170728 (170.7 KB)  TX bytes:170728 (170.7 KB)

wlan0     Link encap:Ethernet  direcciónHW 30:10:b3:2c:4e:08  
          Direc. inet:192.168.0.108  Difus.:192.168.0.255  Másc:255.255.255.0
          Dirección inet6: fe80::3210:b3ff:fe2c:4e08/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:10885 errores:0 perdidos:0 overruns:0 frame:4298
          Paquetes TX:10610 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:9501450 (9.5 MB)  TX bytes:1289879 (1.2 MB)
          Interrupción:16 

root@idevillafane-K52Dr:~# ifconfig -a
eth0      Link encap:Ethernet  direcciónHW 20:cf:30:2b:19:2f  
          ACTIVO DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:30 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:65536  Métrica:1
          Paquetes RX:1700 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:1700 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:170728 (170.7 KB)  TX bytes:170728 (170.7 KB)

wlan0     Link encap:Ethernet  direcciónHW 30:10:b3:2c:4e:08  
          Direc. inet:192.168.0.108  Difus.:192.168.0.255  Másc:255.255.255.0
          Dirección inet6: fe80::3210:b3ff:fe2c:4e08/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:10885 errores:0 perdidos:0 overruns:0 frame:4298
          Paquetes TX:10610 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:9501450 (9.5 MB)  TX bytes:1289879 (1.2 MB)
          Interrupción:16 

root@idevillafane-K52Dr:~# iwconfig
eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"OliWIFI"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 5C:D9:98:2C:09:B8   
          Bit Rate=52 Mb/s   Tx-Power=200 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=44/70  Signal level=-66 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lo        no wireless extensions.[/PHP]

Muchísimas gracias a quien sea que pueda ayudar.

---

