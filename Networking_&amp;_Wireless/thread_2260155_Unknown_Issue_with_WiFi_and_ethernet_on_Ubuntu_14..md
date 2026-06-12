---
title: "Unknown Issue with WiFi and ethernet on Ubuntu 14.04"
date: 2015-01-09
forum: Networking &amp; Wireless
---

### Post by thebatman313 on 2015-01-09
Hello, I seem to be having a frustrating issue with both my WiFi connection & my ethernet connection. I switched from Windows 8 to Ubuntu 14.04 soon after getting my laptop. The model is an HP 15 (per HP's provided info) and its a new device. The internet worked fine on both Win8 and Ubuntu but within a couple days it stopped connection to the internet. I dont believe I have changed anything in the system that would cause a network issue but I am very new to Ubuntu and it's a steep learning curve for me. Although I can actually connect to the router or be recognized that my ethernet connection is present, I am unable to access any website, update software or anything to do with online access. I am unable to check for any software updates or possible drivers since neither form of connection is possible. I do not currently have a CD or USB to possibly reinstall Ubuntu or anything along those lines. I dont want to go back to Windows as it will cost not only money but time and disappointment switching from Ubuntu. I've scoured forums and such to find a possible solution ranging from updating my system and it possibly being an issue with the Wifi card not having the correct drivers. 

If anyone could assist with any information or a possible fix to this issue it would be extremely appreciated. Although I have little to no knowledge about Terminals or advanced Ubuntu systems, I have included a few results that I've seen to be helpful and will be willing to provide any further system info if needed.

Again, thank you for any help.


IFCONFIG Results
eth0      Link encap:Ethernet  HWaddr 8c:dc:d4:85:c6:bd  
          inet addr:192.168.0.9  Bcast:192.168.0.255  Mask:255.255.255.0 
          inet6 addr: fe80::8edc:d4ff:fe85:c6bd/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:8627 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1305 errors:0 dropped:47 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:672303 (672.3 KB)  TX bytes:132620 (132.6 KB) 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:65536  Metric:1 
          RX packets:5032 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:5032 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:443933 (443.9 KB)  TX bytes:443933 (443.9 KB) 

virbr0    Link encap:Ethernet  HWaddr da:7a:d2:a9:48:f4  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


IWCONFIG results

eth0      no wireless extensions.

lo        no wireless extensions.

virbr0    no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"So Much Porn"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 2C:B0:5D:E8:4B:07   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=66/70  Signal level=-44 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

LSPCI Results

00:00.0 Host bridge: Intel Corporation ValleyView SSA-CUnit (rev 0e)
00:02.0 VGA compatible controller: Intel Corporation ValleyView Gen7 (rev 0e)
00:13.0 SATA controller: Intel Corporation ValleyView 6-Port SATA AHCI Controller (rev 0e)
00:14.0 USB controller: Intel Corporation ValleyView USB xHCI Host Controller (rev 0e)
00:1a.0 Encryption controller: Intel Corporation ValleyView SEC (rev 0e)
00:1b.0 Audio device: Intel Corporation ValleyView High Definition Audio Controller (rev 0e)
00:1c.0 PCI bridge: Intel Corporation ValleyView PCI Express Root Port (rev 0e)
00:1c.1 PCI bridge: Intel Corporation ValleyView PCI Express Root Port (rev 0e)
00:1c.2 PCI bridge: Intel Corporation ValleyView PCI Express Root Port (rev 0e)
00:1f.0 ISA bridge: Intel Corporation ValleyView Power Control Unit (rev 0e)
00:1f.3 SMBus: Intel Corporation ValleyView SMBus Controller (rev 0e)
01:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 08)

---

### Post by TheFu on 2015-01-10
It looks like your wired connection is working. It has an IP. Let's concentrate on getting that working since wifi can be picky.
[http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking) has steps to troubleshoot networks that will tell us exactly where the issue is. I suspect DNS, but cannot tell from here with what has been provided so far.

---

