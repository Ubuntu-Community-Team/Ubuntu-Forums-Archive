---
title: "[SOLVED] Intel 2200BG Wireless problems"
date: 2008-08-12
forum: Networking &amp; Wireless
---

### Post by afbase on 2008-08-12
I have a dell inspiron 9300 laptop with the intel 2200bg wireless hardware device.  The problem is that *iwconfig* doesn't see my wireless hardware:
```
$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

The funny thing is *lspci* sees the card (it is the very last item in the list):
```
$lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port [8086:2591] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d3)
00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller [8086:266e] (rev 03)
00:1e.3 Modem [0703]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller [8086:266d] (rev 03)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 03)
00:1f.2 IDE interface [0101]: Intel Corporation 82801FBM (ICH6M) SATA Controller [8086:2653] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [8086:266a] (rev 03)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc M22 [Mobility Radeon X300] [1002:5460]
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
03:01.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev b3)
03:01.1 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C552 IEEE 1394 Controller [1180:0552] (rev 08)
03:01.2 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 17)
03:03.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG Network Connection [8086:4220] (rev 05)


```


I'm using hardy heron.  I've followed the basic guidlines from here: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Each time, I've used the 2200BG driver from the dell support page or from the ndiswrapper sourceforge drivers.  Every time I followed these guidelines I've had to add an extra step:
```
sudo ndiswrapper -a 8086:4220 net4x32
```
I'm figuring that this is associated with the fact that iwconfig doesn't see my wireless card. 

Nonetheless, the little green light on my wifi icon on my laptop doesn't light up in ubuntu, but does in windows XP.  I've tried Fn+F2, but that doesn't work either.  ANY HELP IS APPRECIATED :-)

---

### Post by Crafty Kisses on 2008-08-12
Post the following output:
```
lshw -C network
```

---

### Post by chili555 on 2008-08-12
> eth1      radio offThat's the whole answer. Is there a switch or key combination on your laptop that enable and disables wireless? It's evidently in the 'Off' position. I am quite certain that once you find it and switch it, wireless will work well.

---

### Post by afbase on 2008-08-12
> **Codename said:**
> Post the following output:
```
lshw -C network
```

```
 *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:12:3f:e0:69:b4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=10.10.1.103 latency=64 module=ssb multicast=yes
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:38:65:47
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=unassociated

```

---

### Post by afbase on 2008-08-12
> **chili555 said:**
> That's the whole answer. Is there a switch or key combination on your laptop that enable and disables wireless? It's evidently in the 'Off' position. I am quite certain that once you find it and switch it, wireless will work well.

As I understand about the Dell inspiron 9300 laptops, the BIOS controls the 'on/off switch' of the wireless device.  I have the laptop running XP and hardy heron.  In XP, the wireless device automatically turn on and the icon indicated on the laptop itself is lit.  In Hardy, the icon indicated on the laptop for the wireless device isn't lit.  

To enable/disable the device the I only need to hit Fn+F2.  This works to enable/disable the wireless device in XP.  This doesn't work in Hardy.  I am not exactly sure how to turn this device 'on'.  

As i posted before, Hardy sees the device.  But my guess is that it doesn't know how to turn it on.  :(

---

### Post by chili555 on 2008-08-13
Please try these two commands and let us know if your wireless comes to life:```
sudo rmmod -f ipw2200
sudo modprobe ipw2200 disable=0 led=1
```Now does the 'wireless=radio off' disappear? The next thing to try is:```
sudo su
echo 0 > /sys/bus/pci/drivers/ipw2200/*/rf_kill
```If one of these works, we can easily make it permanent.

---

### Post by afbase on 2008-08-18
> **chili555 said:**
> Please try these two commands and let us know if your wireless comes to life:```
sudo rmmod -f ipw2200
sudo modprobe ipw2200 disable=0 led=1
```Now does the 'wireless=radio off' disappear? The next thing to try is:```
sudo su
echo 0 > /sys/bus/pci/drivers/ipw2200/*/rf_kill
```If one of these works, we can easily make it permanent.


I tried the first set of commands only.
```
sudo rmmod -f ipw2200
sudo modprobe ipw2200 disable=0 led=1
```

It came to life!!!  So how do I make this permanent?

(I was on vacation for a few days, I didn't have time to tackle this problem sooner :()

---

### Post by ozanamn on 2008-09-15
Hi 

I am having that same problem and this is the output when i try that command. I have a Nx8220 laptop with the intel 2200 wireless 

```
scott@scott-laptop:~$ sudo rmmod -f ipw2200
[sudo] password for scott: 
ERROR: Removing 'ipw2200': No such file or directory
scott@scott-laptop:~$ sudo modprobe ipw2200 disable=0 led=1
scott@scott-laptop:~$
```

The output for iwconfig and lshw -C network

lshw -C netowrk
```
cott@scott-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
*-network
description: Ethernet interface
product: NetXtreme BCM5751M Gigabit Ethernet PCI Express
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:10:00.0
logical name: eth0
version: 11
serial: 00:14:c2:e2:fb:48
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=tg3 driverversion=3.86 firmware=5751m-v3.29a latency=0 module=tg3 multicast=yes
*-network
description: Wireless interface
product: PRO/Wireless 2200BG Network Connection
vendor: Intel Corporation
physical id: 4
bus info: pci@0000:02:04.0
logical name: wlan0
version: 05
serial: 00:15:00:4d:56:7e
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ndiswrapper+w29n51 driverversion=1.52+Intel,09/12/2005,9.0.3.9 latency=64 maxlatency=24 mingnt=3 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
*-network
description: Ethernet interface
physical id: 1
logical name: vnet0
serial: 1e:30:92:a1:9d:4c
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A ip=192.168.122.1 multicast=yes
scott@scott-laptop:~$
```

iwconfig
```
scott@scott-laptop:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

wlan0 IEEE 802.11g ESSIDff/any
Mode:Managed Frequency:2.462 GHz Access Point: Not-Associated
Bit Rate:54 Mb/s
RTS thr=1600 B Fragment thr=2304 B
Power Managementff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

irda0 no wireless extensions.

vnet0 no wireless extensions.
```

I have the card installed with the windows drivers over ndiswrapper. Thanks in advance for any help you can give.

Regards,
Oz

---

### Post by jasonkirk2006 on 2008-09-17
Seems you are using ndiswrapper rather than ipw2200. So you are trying to remove a module that is not loaded yet.

---

### Post by ozanamn on 2008-09-18
Oh Ok well is there any easy to follow tutorials on installing ipw2200 driver. Thanks 

Regards,
Oz

---

### Post by ozanamn on 2008-09-24
I have been trying to install the ieee80211 in with module assistant but i get the feeling that the 80211 us already part of the kernal. Anybody got any ideas on how to install the drivers. 

Kind Regards,
Oz

---

