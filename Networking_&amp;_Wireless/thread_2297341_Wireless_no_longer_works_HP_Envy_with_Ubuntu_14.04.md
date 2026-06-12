---
title: "Wireless no longer works HP Envy with Ubuntu 14.04  still works when boot to Windows"
date: 2015-10-02
forum: Networking &amp; Wireless
---

### Post by robgreen1987 on 2015-10-02
Hi I was having intermittent wireless drops with ubuntu - so I turned to the forums to try and fix the problem.  I've done something in terminal that I don't understand and now wireless will not work on ubuntu.  When I boot back into windows wireless works fine.  Ethernet still works on ubuntu & windows. 

Here is a list of commands and outputs that I've tried so far!  Please Ubuntu Forums - you're my only hope:

About This Computer:
HP Envy - Intel® Core™ i7-4700MQ CPU @ 2.40GHz × 8 
15.6 GiB
64 bit ubuntu 14.04

---

greenr@greener:~$lspci | grep -i net 
01:00.0 Networkcontroller: Realtek Semiconductor Co., Ltd. RTL8188EE WirelessNetwork Adapter (rev 01) 
09:00.0 Ethernetcontroller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCIExpress Gigabit Ethernet Controller (rev 0c) 

---

greenr@greener:~$rfkill listall 
Usage:    rfkill[options] command 
Options: 
    --version    showversion (0.5-1ubuntu1 (Ubuntu)) 
Commands: 
    help 
    event 
    list [IDENTIFIER] 
    block IDENTIFIER 
    unblock IDENTIFIER 
where IDENTIFIER isthe index no. of an rfkill switch or one of: 
    <idx> allwifi wlan bluetooth uwb ultrawideband wimax wwan gps fmnfc

---

greenr@greener:~$ iwconfig 
eth0      nowireless extensions. 


lo        nowireless extensions. 

---

greenr@greener:~$sudo lshw -c network 
  *-networkUNCLAIMED     
       description:Network controller 
       product:RTL8188EE Wireless Network Adapter 
       vendor:Realtek Semiconductor Co., Ltd. 
       physical id:0 
       bus info:pci@0000:01:00.0 
       version: 01 
       width: 64bits 
       clock: 33MHz 
       capabilities:pm msi pciexpress bus_master cap_list 
      configuration: latency=0 
       resources:ioport:5000(size=256) memory:b2600000-b2603fff 
  *-network 
       description:Ethernet interface 
       product:RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller 
       vendor:Realtek Semiconductor Co., Ltd. 
       physical id:0 
       bus info:pci@0000:09:00.0 
       logical name:eth0 
       version: 0c
serial: d0:bf:9c:24:15:73 
       size:10Mbit/s 
       capacity:1Gbit/s 
       width: 64bits 
       clock: 33MHz 
       capabilities:pm msi pciexpress msix vpd bus_master cap_list ethernet physical tpmii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
      configuration: autonegotiation=on broadcast=yes driver=r8169driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-2_0.0.102/06/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s 
       resources:irq:43 ioport:3000(size=256) memory:b2500000-b2500fffmemory:b2400000-b2403fff 

---

----

greenr@greener:~$sudo ifconfig wlan0 up 
wlan0: ERROR whilegetting interface flags: No such device 

greenr@greener:~$sudo service network-manager start 
start: Job isalready running: network-manager 

nm-applet-Message: PID 2414(we are 2399) sent signal 15, shutting down... 
greenr@greener:~$nm-applet & 
[2] 2415 
[1]   Done                   nm-applet 
greenr@greener:~$sudo 
(nm-applet:2415):nm-applet-WARNING **: Could not find ShellVersion property onorg.gnome.Shell after 5 tries 
 ifconfig wlan0 up 
wlan0: ERROR whilegetting interface flags: No such device 

---

wlan0:error fetching interface information: Device not found 
greenr@greener:~$sudo ifconfig -a 
eth0      Linkencap:Ethernet  HWaddr d0:bf:9c:24:15:73  
          UPBROADCAST MULTICAST  MTU:1500  Metric:1 
          RXpackets:0 errors:0 dropped:0 overruns:0 frame:0 
          TXpackets:0 errors:0 dropped:0 overruns:0 carrier:0 
         collisions:0 txqueuelen:1000 
          RX bytes:0(0.0 B)  TX bytes:0 (0.0 B) 


lo        Linkencap:Local Loopback  
          inetaddr:127.0.0.1  Mask:255.0.0.0 
          inet6addr: ::1/128 Scope:Host 
          UPLOOPBACK RUNNING  MTU:65536  Metric:1 
          RXpackets:159 errors:0 dropped:0 overruns:0 frame:0 
          TXpackets:159 errors:0 dropped:0 overruns:0 carrier:0 
         collisions:0 txqueuelen:0 
          RXbytes:11265 (11.2 KB)  TX bytes:11265 (11.2 KB)

---

greenr@greener:~$ lspci 
00:00.0 Host bridge:Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor DRAMController (rev 06) 
00:02.0 VGAcompatible controller: Intel Corporation 4th Gen Core ProcessorIntegrated Graphics Controller (rev 06) 
00:03.0 Audiodevice: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HDAudio Controller (rev 06) 
00:14.0 USBcontroller: Intel Corporation 8 Series/C220 Series Chipset Family USBxHCI (rev 05) 
00:16.0Communication controller: Intel Corporation 8 Series/C220 SeriesChipset Family MEI Controller #1 (rev 04) 
00:1b.0 Audiodevice: Intel Corporation 8 Series/C220 Series Chipset HighDefinition Audio Controller (rev 05) 
00:1c.0 PCI bridge:Intel Corporation 8 Series/C220 Series Chipset Family PCI ExpressRoot Port #3 (rev d5) 
00:1c.2 PCI bridge:Intel Corporation 8 Series/C220 Series Chipset Family PCI ExpressRoot Port #1 (rev d5) 
00:1c.3 PCI bridge:Intel Corporation 8 Series/C220 Series Chipset Family PCI ExpressRoot Port #4 (rev d5) 
00:1c.6 PCI bridge:Intel Corporation 8 Series/C220 Series Chipset Family PCI ExpressRoot Port #7 (rev d5) 
00:1d.0 USBcontroller: Intel Corporation 8 Series/C220 Series Chipset Family USBEHCI #1 (rev 05) 
00:1f.0 ISA bridge:Intel Corporation HM87 Express LPC Controller (rev 05) 
00:1f.2 SATAcontroller: Intel Corporation 8 Series/C220 Series Chipset Family6-port SATA Controller 1 [AHCI mode] (rev 05) 
00:1f.3 SMBus: IntelCorporation 8 Series/C220 Series Chipset Family SMBus Controller (rev05) 
01:00.0 Networkcontroller: Realtek Semiconductor Co., Ltd. RTL8188EE WirelessNetwork Adapter (rev 01) 
03:00.0 Unassignedclass [ff00]: Realtek Semiconductor Co., Ltd. RTS5227 PCI ExpressCard Reader (rev 01) 
09:00.0 Ethernetcontroller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCIExpress Gigabit Ethernet Controller (rev 0c)

---

### Post by Skywalker# on 2015-11-28
Hi, did you manage to sort this problem?

I want to purchase this laptop ([http://www.pcworld.co.uk/gbuk/computing/laptops/laptops/hp-envy-13-d050sa-13-3-laptop-aluminium-10137767-pdt.html](http://www.pcworld.co.uk/gbuk/computing/laptops/laptops/hp-envy-13-d050sa-13-3-laptop-aluminium-10137767-pdt.html)) but am worried that Ubuntu will have problems/incompatibilities that cant be fixed. Is rest of your laptop a similar spec to the one I have linked?

Do you have any other problems? What is your Ubuntu experience like on that laptop?

I hope you can help me narrow down the huge 2 week search I have been frustratingly doing in aid to find a good laptop for Ubuntu. :)

---

