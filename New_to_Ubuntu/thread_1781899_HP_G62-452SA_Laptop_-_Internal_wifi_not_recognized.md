---
title: "HP G62-452SA Laptop - Internal wifi not recognized"
date: 2011-06-14
forum: New to Ubuntu
---

### Post by kalimojo on 2011-06-14
HP G62-452SA Laptop - Internal wifi not recognized. Any tips on how to get it working ? I ran KNOPPIX and it never picked it up either.

lspci -v shows the following

02:00.0 Network controller: Ralink corp. Device 5390
    Subsystem: Hewlett-Packard Company Device 1636
    Flags: bus master, fast devsel, latency 0, IRQ 10
    Memory at d3400000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>


lshw -C network 
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: Ralink corp.
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:d3400000-d340ffff

i did the following

[LIST=1]
[*]Download the driver from ralinktech.com --> Software --> Linux
[*]Unzip the download zip file anywhere. I did it in the default Downloads directory
[*]cd to the 2010_xxx extracted directory
[*]cd os/linux/
[*]Edit the config.mk file as below:
HAS_ATE=y (no change, it was originally as is)
HAS_WPA_SUPPLICANT=y (no change, it was originally as is)
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y (no change, it was originally as is)
HAS_ANTENNA_DIVERSITY_SUPPORT=y originally was n -- this was the only thing I modified)
[*]Go back to the 2010_xx directory
[*]run command 'make'
[*]Make sure 'make compile' exists without errors. I got an error "too  many arguments to format" towards the end of the compile but it did  compile successfully eventually. And so I ignored the errors. You would  see ***errors*** if the compile is not successful. In which, something  went wrong and you may need to tweak the makefile or config.mk files  before compile is successful.
[*]run command 'make install' as root. This is not listed in the  README_STA_pci file that comes with downloaded driver zip file. This  takes of copying the file to  /lib/modules/2.6.35-22-generic/kernel/drivers/net/wireless/rt5390sta.ko.  running depmod, creating /etc/Wireless/... folder.
[*]Edit the /etc/modules and add the line  at the end of this file
rt5390sta
[*]Edit the file /etc/modprobe.d/blacklist.conf and add the below line to it...
blacklist rt2800pci
[*]Reboot and you should see an ra0 interface when you run the command 'ifconfig'
[*]You may have to run '/etc/init.d/network-manager restart' command to have it show in the first go.
[*]Once, the wireless icon shows up, look for your wireless SSID and there you go surfing :smile:
[/LIST]
I had to do the following

-edit config.mk (should be under ..../os/linux
-look for this line:
 HAS_CFG80211_SUPPORT=y
-change "y" to "n" then recompile and run make install.

ifconfig

ra0       Ralink STA  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

but it still cant connect to my wireless router

lshw -C network 
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: Ralink corp.
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: ra0
       version: 00
       serial: 90:00:4e:2b:96:06
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN driverversion=2.4.0.4 ip=192.168.0.7 latency=0 multicast=yes wireless=Ralink STA
       resources: irq:16 memory:d3400000-d340ffff

it appears to have an ip address !!!!

its working !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

ra0       Link encap:Ethernet  HWaddr 90:00:4e:2b:96:06  
          inet addr:192.168.0.7  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::9200:4eff:fe2b:9606/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4515 errors:0 dropped:0 overruns:0 frame:0
          TX packets:583 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1205154 (1.2 MB)  TX bytes:42319 (42.3 KB)
          Interrupt:16

---

