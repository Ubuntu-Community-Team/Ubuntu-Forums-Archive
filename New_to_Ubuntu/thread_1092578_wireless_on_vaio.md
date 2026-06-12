---
title: "wireless on vaio"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by retarduser on 2009-03-10
hey guys retard here

I noticed there was some talk about issues with kubuntu's wireless drivers and the vaio computer, but if the wireless signal is reckognised but not connecting, what's the dealio?

The key is right, all the settings correct, but it's not connecting.

How do I look into this further?

Keep in mind I'm a retard

---

### Post by Crafty Kisses on 2009-03-10
Hey there! I want the results of a couple commands but in order for you to put these commands in you need to open up the Konsole. Once you have the Konsole open, please copy and paste these commands in the Konsole one by one:
```
lspci
lsusb
lshw -C network
ifconfig
iwconfig
```
Below I've attached a thumbnail of where Konsole is located if you're not quite sure.

---

### Post by retarduser on 2009-03-10
...

---

### Post by retarduser on 2009-03-10
user@Hallcatcomp:~$ lspci                                    
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
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)                      
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)                      
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)                      
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)                     
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)                                              
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)                                       
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)                                  
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)                                     
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 13)       
04:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)      
05:03.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)                                     
05:03.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)                          
05:03.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)                               
user@Hallcatcomp:~$                                                                                               
user@Hallcatcomp:~$ lsusb                                                                                         
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub                                                      
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub                                                      
Bus 004 Device 002: ID 05ca:18b3 Ricoh Co., Ltd                                                                     
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub                                                      
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub                                                      
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub                                                      
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub                                                      
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub                                                      
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub                                                      
user@Hallcatcomp:~$                                                                                               
user@Hallcatcomp:~$ lshw -C network                                                                               
WARNING: you should run this program as super-user.                                                                 
  *-network                                                                                                         
       description: Ethernet interface                                                                              
       product: 88E8055 PCI-E Gigabit Ethernet Controller                                                           
       vendor: Marvell Technology Group Ltd.                                                                        
       physical id: 0                                                                                               
       bus info: pci@0000:01:00.0                                                                                   
       logical name: eth0                                                                                           
       version: 13                                                                                                  
       serial: 00:1d:ba:27:ec:f3                                                                                    
       width: 64 bits                                                                                               
       clock: 33MHz                                                                                                 
       capabilities: bus_master cap_list ethernet physical                                                          
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 module=sky2 multicast=yes 
  *-network                                                                                                         
       description: Wireless interface                                                                              
       product: AR928X Wireless Network Adapter (PCI-Express)                                                       
       vendor: Atheros Communications Inc.                                                                          
       physical id: 0                                                                                               
       bus info: pci@0000:04:00.0                                                                                   
       logical name: wmaster0                                                                                       
       version: 01                                                                                                  
       serial: 00:1f:e1:d6:71:cb                                                                                    
       width: 64 bits                                                                                               
       clock: 33MHz                                                                                                 
       capabilities: bus_master cap_list logical ethernet physical wireless                                         
       configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn       
  *-network DISABLED                                                                                                
       description: Ethernet interface                                                                              
       physical id: 1                                                                                               
       logical name: pan0                                                                                           
       serial: 4e:04:18:a3:6c:cf                                                                                    
       capabilities: ethernet physical                                                                              
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes                      
user@Hallcatcomp:~$                                                                                               
user@Hallcatcomp:~$ ifconfig                                                                                      
eth0      Link encap:Ethernet  HWaddr 00:1d:ba:27:ec:f3                                                             
          UP BROADCAST MULTICAST  MTU:1500  Metric:1                                                                
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0                                                        
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0                                                      
          collisions:0 txqueuelen:1000                                                                              
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)                                                                    
          Interrupt:16                                                                                              

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host     
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:136 errors:0 dropped:0 overruns:0 frame:0
          TX packets:136 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0                             
          RX bytes:8736 (8.7 KB)  TX bytes:8736 (8.7 KB)        

wlan0     Link encap:Ethernet  HWaddr 00:1f:e1:d6:71:cb
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-E1-D6-71-CB-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

user@Hallcatcomp:~$
user@Hallcatcomp:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Tx-Power=27 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

---

### Post by retarduser on 2009-03-10
we good now

Also like to mention that I'm without an ethernet cable as well and am using a friend's computer and have to transfer everything as I try and solve this.

---

### Post by retarduser on 2009-03-11
Hey  still having issues,

I was wondering if it would be in my best interests to download something from this website?

[http://www.linuxant.com/driverloader/](http://www.linuxant.com/driverloader/)

---

