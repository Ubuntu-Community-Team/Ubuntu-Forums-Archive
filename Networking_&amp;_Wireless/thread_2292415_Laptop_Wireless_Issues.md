---
title: "Laptop Wireless Issues"
date: 2015-08-27
forum: Networking &amp; Wireless
---

### Post by curtis17 on 2015-08-27
So I just tried to set up ubuntu on my laptop, and this is the first time I will actually be using ubuntu on a regular basis. I know how to use the terminal a little bit. Anyways, ubuntu itself works fine, however I cant get wifi working. I had the wifi to work while I was using ubuntu off of a usb stick, but after it was finished installing, the wifi wont work anymore. I have been searching for an answer for this for about a week now, and nothing has seemed to work. below are some outputs I got from the terminal that are current, and I found the commands online within the past week. 

sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 10
       serial: f0:76:1c:c3:b7:91
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-3_0.0.1 04/23/13 ip=192.168.2.44 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:35 ioport:2000(size=256) memory:f0b04000-f0b04fff memory:f0b00000-f0b03fff
  *-network DISABLED
       description: Wireless interface
       product: QCA9565 / AR9565 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 5c:93:a2:90:39:cc
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.19.0-26-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:41 memory:f0a00000-f0a7ffff memory:f0a80000-f0a8ffff



rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: acer-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no




iwconfig
eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.







regarding the hard block on the rfkill list, I don't have a switch on my laptop. I do have a wireless button on my keyboard which can be used usint Fn F3, however, it doesn't seem to do anything in either ubuntu or linux. 

anyways, I hope to get this resolved soon, and thanks in advance.

---

### Post by brad-bogar on 2015-08-28
[FONT=arial]Try this first:

sudo nano /etc/modprobe.d/ath9k.conf
Add the following line to it:
options ath9k nohwcrypt=1
Save and reboot.[/FONT]

---

### Post by jeremy31 on 2015-08-28
Post the model name of your laptop and the results from ```
lsmod
```

---

### Post by funman2 on 2015-08-30
I have the same issue for some time now and I read about the hard blocked problem somewhere but unfourtunatly I can't find the link anymore. But I remember that besides a switch it can be blocked by the bios. Maybe you can find something in that direction.

---

