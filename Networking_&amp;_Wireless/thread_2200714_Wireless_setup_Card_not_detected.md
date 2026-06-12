---
title: "Wireless setup Card not detected"
date: 2014-01-20
forum: Networking &amp; Wireless
---

### Post by lcb503 on 2014-01-20
Hi 
I'm qute new to ubuntu and am trying to set up my wireless card. I have tried iwconfig and no device is detected also no additional drivers are detected. The card is a TP link WN881ND. Any help would be great.

---

### Post by tfrue on 2014-01-21
I would like to see the output of:
```
nm-tool
lshw -C network
lspci

```

Thanks,
Chris

---

### Post by lcb503 on 2014-01-21
nm-tool

- Device: eth0  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        50:E5:49:CC:6E:61

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.8
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1

---

### Post by lcb503 on 2014-01-21
lshw -C network
 *-network        
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 06
       serial: 50:e5:49:cc:6e:61
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.0.8 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:42 ioport:d000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff

---

### Post by lcb503 on 2014-01-21
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation H61 Express Chipset Family LPC Controller (rev 05)
00:1f.2 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 4 port SATA IDE Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
00:1f.5 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 2 port SATA IDE Controller (rev 05)
02:00.0 USB controller: Etron Technology, Inc. EJ168 USB 3.0 Host Controller (rev 01)
03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE9172 SATA III 6Gb/s RAID Controller (rev 11)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)


Thanks for helping Chris

---

### Post by tfrue on 2014-01-21
Hmm... I would turn off your computer, drain all the power by unplugged it, and pressing the power button, then re-seat the card and turn on the computer. I didn't see anything that about your card so try that and see what happens. If nothing, try running 
```
partprobe
then
sudo apt-get update
```

And see if that helps.

Good luck, 
Chris

---

### Post by lcb503 on 2014-01-21
Tried turning off the power and reseating the card (even tried another pciex1 slot), no luck. Just to check is the command partprobe the entire commmand (which i've done)

---

### Post by tfrue on 2014-01-21
Sorry, wrong command, partprobe isn't for hardware. I don't know what I was thinking.

Type:
```

ifconfig wlan0 up
```

And see if that makes the wireless interface come up.

Chris

---

### Post by lcb503 on 2014-01-21
Got the error message.

wlan0: ERROR while getting interface flags: No such device

---

### Post by tfrue on 2014-01-22
Have you tried this card in a different system to see if it works? Or even a different OS?

---

