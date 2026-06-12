---
title: "Utopic Unicorn Wireless Problems"
date: 2014-11-06
forum: Networking &amp; Wireless
---

### Post by th1mas on 2014-11-06
I recently upgraded my Lenovo z575 ideapad laptop to Ubuntu 14.10 (Utopic Unicorn) x86_64 bit from Ubuntu 14.04 (Trusty Tahr), and since the upgrade the wifi has stopped working. At first the notifications bar showed "Wireless networking, Device not ready", and i tried the solution given to me in [this]("http://www.ubuntuforums.org/showthread.php?t=1864392") thread, but now there isn't even a notification for wireless networking. All the bar shows is ethernet which I am currently connected to. I really need my laptop for school, so I need this to be solved quickly! Also this is the output from ifconfig in the terminal. 

eth0      Link encap:Ethernet  HWaddr f0:de:f1:a6:81:83  
          inet addr:192.168.1.124  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::f2de:f1ff:fea6:8183/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:94 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11523 (11.5 KB)  TX bytes:13414 (13.4 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:340 errors:0 dropped:0 overruns:0 frame:0
          TX packets:340 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:69287 (69.2 KB)  TX bytes:69287 (69.2 KB)

---

### Post by chili555 on 2014-11-07
> i tried the solution given to me in this thread,So you blacklisted rt2800pci, then. Is that the device you have? Let's take a look at what you really have:```
lspci -nn | grep 0280
rfkill list all
```

---

### Post by th1mas on 2014-11-07
Outputs:
     lspci -nn 
00:00.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h Processor Root Complex [1022:1705]
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] BeaverCreek [Radeon HD 6620G] [1002:9641]
00:01.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] BeaverCreek HDMI Audio [Radeon HD 6500D and 6400G-6600G series] [1002:1714]
00:04.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Family 12h Processor Root Port [1022:1709]
00:06.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Family 12h Processor Root Port [1022:170b]
00:11.0 SATA controller [0106]: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] [1022:7804]
00:12.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller [1022:7807] (rev 11)
00:12.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller [1022:7808] (rev 11)
00:13.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller [1022:7807] (rev 11)
00:13.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller [1022:7808] (rev 11)
00:14.0 SMBus [0c05]: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller [1022:780b] (rev 13)
00:14.2 Audio device [0403]: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller [1022:780d] (rev 01)
00:14.3 ISA bridge [0601]: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge [1022:780e] (rev 11)
00:14.4 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] FCH PCI Bridge [1022:780f] (rev 40)
00:18.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 0 [1022:1700] (rev 43)
00:18.1 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 1 [1022:1701]
00:18.2 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 2 [1022:1702]
00:18.3 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 3 [1022:1703]
00:18.4 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 4 [1022:1704]
00:18.5 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 6 [1022:1718]
00:18.6 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 5 [1022:1716]
00:18.7 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 7 [1022:1719]
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
02:00.0 Network controller [0280]: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]

grep 0280 came up with nothing

rfkill list all also came up with nothing.

---

### Post by chili555 on 2014-11-07
> [[COLOR="#FF0000"]0280[/COLOR]]: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]Well, indeed you do have an rt2800pci device! Awesome.

First, we need to undo the blacklist:```
gksudo gedit /etc/modprobe.d/blacklist.conf
```Use nano or kate or leafpad if you don't have the text editor gedit. Remove the line 'blacklist rt2800pci.' Proofread carefully, save and close the text editor. Now, let's load the module:```
sudo modprobe rt2800pci
```Is a wireless interface created, ideally wlan0?```
iwconfig
```Does it scan and see networks?```
sudo iwlist wlan0 scan
```If not, let's look for clues in the logs:```
dmesg | grep -e wlan -e rt2
```Thanks.

---

### Post by th1mas on 2014-11-07
This solution did not work, I just ended up reimaging my computer back to the LTS version. Thank you for your help though!

---

