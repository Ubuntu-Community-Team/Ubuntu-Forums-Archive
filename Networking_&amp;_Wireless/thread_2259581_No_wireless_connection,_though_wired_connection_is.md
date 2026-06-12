---
title: "No wireless connection, though wired connection is OK"
date: 2015-01-05
forum: Networking &amp; Wireless
---

### Post by rakesh343 on 2015-01-05
I just installed Ubuntu 14.04.1 using a bootable pen drive. While I was using the OS from the pen drive the wireless connection was working. After the installation, wired connection is working, but not the wireless.
My Laptop is Lenovo G50-70 series. When I put this command in the terminal:

Code:

lspci | grep Wireless

I got the following information about my Network adapter: 

Network controller: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter

Results for:
 rfkill list

0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
5: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

Further, results ffor the following code:

sudo lshw -C network; sudo iwlist scan | head -n 25

Yielded the folloeing result:

*-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 10
       serial: 28:d2:44:b8:35:54
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-3_0.0.1 04/23/13 ip=192.168.1.4 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:62 ioport:4000(size=256) memory:c0504000-c0504fff memory:c0500000-c0503fff
  *-network
       description: Wireless interface
       product: RTL8723BE PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: b0:10:41:3f:d4:bd
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8723be driverversion=3.13.0-43-generic firmware=N/A ip=10.42.0.1 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 ioport:3000(size=256) memory:c0400000-c0403fff
eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 66:91:77:DB:34:20
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=0 dBm  
                    Encryption key:on
                    ESSID:"Te-te-pe-pe Chowk"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 3136384ms ago
                    IE: Unknown: 001154652D74652D70652D70652043686F776B
                    IE: Unknown: 010882040B160C121824
                    IE: Unknown: 030101
                    IE: Unknown: 06020000
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 7F080000000000000040
                    IE: Unknown: DD070050F202000100

Hope this is relevant for my problem. Please suggest some ways to resolve this problem.

---

### Post by adnancaraballo on 2015-01-05
Did you try going to system settings, then software and updates and where it says additional drivers(your broadcom or wireless driver should be there). Thats how i got mine to work. Apparently the driver doesnt get installed by default you have to enable it. if ubuntu does not recognize the driver there you would have to search on google to see if it is available. Thats what i had to do on another computer. Hope this helps.

---

### Post by rakesh343 on 2015-01-05
@  adnancaraballo


"Did you try going to system settings, then software and updates and where it says additional drivers(your broadcom or wireless driver should be there)."

It says that there are no addtional drivers available.
:mad:

---

### Post by praseodym on 2015-01-05
Hi,

the driver rtl8723be is there. Try the following module parameters:
```

echo "options rtl8723be swenc=1 fwlps=0 ips=0" | sudo tee /etc/modprobe.d/rtl8723be.conf
sudo modprobe -rfv rtl8723be
sudo modprobe -v rtl8723be
sudo service network-manager restart
```

---

### Post by rakesh343 on 2015-01-06
Thanks praseodym,

Problem solved with some modification in the modem setting. Hope your post help some more people. Thanks again everyone for helping out. :popcorn:

---

