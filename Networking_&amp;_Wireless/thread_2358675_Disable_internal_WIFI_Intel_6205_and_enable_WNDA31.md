---
title: "Disable internal WIFI Intel 6205 and enable WNDA3100v2 USB ?"
date: 2017-04-16
forum: Networking &amp; Wireless
---

### Post by donnywood-studio on 2017-04-16
Is there a gui or apps  to easily disable the internal Intel 6205 wifi and enable the NetGear WNDA3100v2 usb dongle?

How do you enable USB dongle WIFI in ubuntu ? LTS 16.04 . 

I found some commands to view usb  devices   


```
orcanet@hp8460p:~$ lsusb|grep NetGear
Bus 003 Device 002: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]
orcanet@hp8460p:~$ lspci -nnk | grep -iA2 net
00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
    Subsystem: Hewlett-Packard Company 82579LM Gigabit Network Connection [103c:161c]
    Kernel driver in use: e1000e
    Kernel modules: e1000e
--
24:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6205 [Taylor Peak] [8086:0085] (rev 34)
    DeviceName: WLAN
    Subsystem: Intel Corporation Centrino Advanced-N 6205 AGN [8086:1311]
```

Any pointers

cheers Don

---

### Post by donnywood-studio on 2017-04-16
I tried as in this thread 
[https://askubuntu.com/questions/814364/usb-wireless-netgear-adapter-ubuntu-16-04](https://askubuntu.com/questions/814364/usb-wireless-netgear-adapter-ubuntu-16-04)

i can see the NDIS  in dmesg but with error.
```
orcanet@hp8460p:~$ dmesg|grep ndis

[ 8131.110651] ndiswrapper: module verification failed: signature and/or required key missing - tainting kernel
[ 8131.113255] ndiswrapper version 1.60 loaded (smp=yes, preempt=no)
[ 8131.367248] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[ 8131.937487] usbcore: registered new interface driver ndiswrapper
[ 8131.966866] ndiswrapper 3-2:1.0 enx2cb05d71745c: renamed from wlan1
[ 8131.982946] ndiswrapper: interface renamed to 'enx2cb05d71745c'
```

```
orcanet@hp8460p:~$ dmesg|grep ndis
[ 8131.110651] ndiswrapper: module verification failed: signature and/or required key missing - tainting kernel
[ 8131.113255] ndiswrapper version 1.60 loaded (smp=yes, preempt=no)
[ 8131.367248] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[ 8131.937487] usbcore: registered new interface driver ndiswrapper
[ 8131.966866]** ndiswrapper 3-2:1.0 enx2cb05d71745c: renamed from wlan1**
[ 8131.982946] ndiswrapper: interface renamed to 'enx2cb05d71745c'
```

I tried to disable wlan0 and enable wlan1 ? but i get this error

```
ifconfig wlan0 down
SIOCSIFFLAGS: Operation not permitted
orcanet@hp8460p:~$ sudo ifconfig wlan0 down
orcanet@hp8460p:~$ sudo ifconfig wlan1 up
**wlan1: ERROR while getting interface flags: No such device**
orcanet@hp8460p:~$ 
```

is this the right command to enable wlan1 ?

rgds

---

### Post by jeremy31 on 2017-04-16
You don't have wlan0 or wlan1 because of predictable interface naming used since Ubuntu 15.10.  Check results for ```
ifconfig
```
To see what the Intel card is named, the broadcom device is enx2cb05d71745c

Is there a big issue with the Intel internal card?  Anything that needs ndiswrapper usually works poorly in Linux compared to a device supported by the kernel like the Intel 6205

---

### Post by donnywood-studio on 2017-04-16
```
orcanet@hp8460p:~$ ifconfig
enx2cb05d71745c Link encap:Ethernet  HWaddr 2c:b0:5d:71:74:5c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:270 (270.0 B)  TX bytes:270 (270.0 B)

eth0      Link encap:Ethernet  HWaddr e4:11:5b:5e:61:32  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:d4800000-d4820000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1005 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1005 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:176212 (176.2 KB)  TX bytes:176212 (176.2 KB)

wlan0     Link encap:Ethernet  HWaddr 8c:70:5a:4c:94:c8  
          inet addr:192.168.0.8  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::8e70:5aff:fe4c:94c8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2304 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2250 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1418564 (1.4 MB)  TX bytes:433408 (433.4 KB)

orcanet@hp8460p:~$
```

---

### Post by jeremy31 on 2017-04-16
See if removing the kernel module works
```
sudo modprobe -r iwlwifi
```

Please use code tags for commands and terminal output as it preserves the formatting and keeps smilies from appearing

---

### Post by donnywood-studio on 2017-04-16
no issues with 6502 but  hoping to get better then 300mbps with my NetGear D7000 Fiber/Wifirouter .

sudo modprobe -r iwlwifi disabled 6502 and was totally without any network.  
i inserted iwlwifi back and 6502 is back on wifi.

When i remove/insert the broadcom dongle i get this message i.e  unable to authenticate with the SID..
Anyway I will flag trying to get this dongle working for now  . Thanks for your help Jeremy ! 

[ 3042.752249] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3054.746663] usb 3-2: USB disconnect, device number 9
[ 3054.764520] ndiswrapper: device enx2cb05d71745c removed
[ 3058.104279] usb 3-2: new high-speed USB device number 10 using xhci_hcd
[ 3058.236559] usb 3-2: New USB device found, idVendor=0846, idProduct=9011
[ 3058.236569] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 3058.236575] usb 3-2: Product: Remote Download Wireless Adapter
[ 3058.236579] usb 3-2: Manufacturer: Broadcom
[ 3058.236583] usb 3-2: SerialNumber: 0
[ 3058.348461] usb 3-2: reset high-speed USB device number 10 using xhci_hcd
[ 3058.484230] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[ 3059.046264] wlan1: ethernet device 2c:b0:5d:71:74:5c using NDIS driver: bcmn43xx64, version: 0x50a4f1e, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0846:9011.F.conf
[ 3059.049581] wlan1: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
[ 3060.117326] ndiswrapper 3-2:1.0 enx2cb05d71745c: renamed from wlan1
[ 3060.139690] ndiswrapper: interface renamed to 'enx2cb05d71745c'
[ 3060.145790] IPv6: ADDRCONF(NETDEV_UP): enx2cb05d71745c: link is not ready
[ 3060.146522] IPv6: ADDRCONF(NETDEV_UP): enx2cb05d71745c: link is not ready
[ 3060.230819] IPv6: ADDRCONF(NETDEV_UP): enx2cb05d71745c: link is not ready
[ 3327.143106] usb 3-2: USB disconnect, device number 10
[ 3327.172604] ndiswrapper: device enx2cb05d71745c removed
[ 3338.739383] usb 3-2: new high-speed USB device number 11 using xhci_hcd
[ 3338.872348] usb 3-2: New USB device found, idVendor=0846, idProduct=9011
[ 3338.872358] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 3338.872363] usb 3-2: Product: Remote Download Wireless Adapter
[ 3338.872367] usb 3-2: Manufacturer: Broadcom
[ 3338.872371] usb 3-2: SerialNumber: 0
[ 3338.988095] usb 3-2: reset high-speed USB device number 11 using xhci_hcd
[ 3339.123859] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[ 3339.694726] wlan1: ethernet device 2c:b0:5d:71:74:5c using NDIS driver: bcmn43xx64, version: 0x50a4f1e, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0846:9011.F.conf
[ 3339.699807] wlan1: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
[ 3340.734735] ndiswrapper 3-2:1.0 enx2cb05d71745c: renamed from wlan1
[ 3340.759354] ndiswrapper: interface renamed to 'enx2cb05d71745c'
[ 3340.770103] IPv6: ADDRCONF(NETDEV_UP): enx2cb05d71745c: link is not ready
[ 3340.772357] IPv6: ADDRCONF(NETDEV_UP): enx2cb05d71745c: link is not ready
[ 3340.860470] IPv6: ADDRCONF(NETDEV_UP): enx2cb05d71745c: link is not ready

---

