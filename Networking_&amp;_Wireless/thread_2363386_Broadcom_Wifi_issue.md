---
title: "Broadcom Wifi issue"
date: 2017-06-09
forum: Networking &amp; Wireless
---

### Post by shivang3 on 2017-06-09
I have Dell laptop and I see ping response is very high. Also I have HP laptop, both laptop connected fine with Neatgear Wifi device.( Neatgear Wifi module have no issue)


But HP laptop ping response is normal and below 1 ms but in Dell laptop ping response is between 200 ms to 2000 ms so something is wrong in Broadcom wifi driver.


Please check below all details which need to solved this issue easily.

Laptop Make/Model : Dell Vostro 3546 - 15 3000 Series
Serial No     : 84SSH52
Processor  : Intel(R) Core(TM) i3-4030U CPU @ 1.90GHz
OS               : [CENTER]Ubuntu 12.04
Type            : 64 bit[/CENTER]


```
lspci -vnn | grep Network
06:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4365] (rev 01)

iwconfig
eth2      no wireless extensions.

lo        no wireless extensions.

wlan0  IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=200 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off

lshw -C network


 *-network               
       description: Wireless interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 01
       serial: ac:d1:b8:d4:f2:97
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.248 (r487574) latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:18 memory:f7d00000-f7d07fff



lspci


06:00.0 Network controller: Broadcom Corporation Device 4365 (rev 01)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 07)

Ping response as below (Dell Laptop)

PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.


64 bytes from [192.168.2.1]("http://192.168.2.1/"): icmp_req=1 ttl=64 time=200.799 ms
64 bytes from [192.168.2.1]("http://192.168.2.1/"): icmp_req=2 ttl=64 time=3000.241 ms
64 bytes from [192.168.2.1]("http://192.168.2.1/"): icmp_req=3 ttl=64 time=40.217 ms
64 bytes from [192.168.2.1]("http://192.168.2.1/"): icmp_req=4 ttl=64 time=50.209 ms
64 bytes from [192.168.2.1]("http://192.168.2.1/"): icmp_req=5 ttl=64 time=100.212 ms

```

Please guide me here to reinstall or how to reload Broadcom wiifi driver on this system.


I need to solved this issue on high priority so please check this and let me know if required more details.


I am waiting for your response.

---

### Post by Hadaka on 2017-06-09
Hi, Ubuntu 12.04 is at end of life, 14.04 or 16.04 should be loaded
to bring your system up to date. *If you do not wish to update the OS
you may try to clean up your current 12.04 as best as possible.
Please open a terminal ctrl...alt..t  then with a working wired connection
Copy and paste one line at a time.
```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get autoremove
sudo apt-get autoclean
```
then do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install bcmwl-kernel-source
sudo modprobe -rf wl
sudo modprobe -v wl
```
Remove wired connection and then do..
```
ping -c2 $(route -n | awk 'FNR==3{print$2}')
```
Did that improve your ping rate ??

---

### Post by wildmanne39 on 2017-06-09
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Please use the default font color and properties unless you need to highlight or draw attention to a part of your post, but they are not intended to be used for an entire post.

---

