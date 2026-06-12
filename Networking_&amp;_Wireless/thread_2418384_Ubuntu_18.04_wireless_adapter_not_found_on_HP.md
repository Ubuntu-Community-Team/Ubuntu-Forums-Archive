---
title: "Ubuntu 18.04 wireless adapter not found on HP"
date: 2019-05-06
forum: Networking &amp; Wireless
---

### Post by luiscri96 on 2019-05-06
WiFi has stopped working on my computer two days ago. Until that I haven't had any problem with it and it happened suddenly.

My computer is a HP Pavilion 13 x360 from 2014.

I have tried several solutions on internet but none of them worked for me. Some solved it temporaly but when I hibernated my computer and reopen it WiFi wasn't working again. Now WiFi doesn't works even when I try what it solved it before.

[This]("https://askubuntu.com/questions/1047245/wifi-adapter-not-found-in-ubuntu-18-04") didn't work either.

My output for `lspci` command:

    ```
00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 0b)
    00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)
    00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 0b)
    00:14.0 USB controller: Intel Corporation 8 Series USB xHCI HC (rev 04)
    00:16.0 Communication controller: Intel Corporation 8 Series HECI #0 (rev 04)
    00:1b.0 Audio device: Intel Corporation 8 Series HD Audio Controller (rev 04)
    00:1c.0 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 1 (rev e4)
    00:1c.1 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 2 (rev e4)
    00:1c.2 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 3 (rev e4)
    00:1c.3 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 4 (rev e4)
    00:1d.0 USB controller: Intel Corporation 8 Series USB EHCI #1 (rev 04)
    00:1f.0 ISA bridge: Intel Corporation 8 Series LPC Controller (rev 04)
    00:1f.2 SATA controller: Intel Corporation 8 Series SATA Controller 1 [AHCI mode] (rev 04)
    00:1f.3 SMBus: Intel Corporation 8 Series SMBus Controller (rev 04)
    02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5227 PCI Express Card Reader (rev 01)
    09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL810xE PCI Express Fast Ethernet controller (rev 08)
```

Seems that wireless controller isn't there, and I don't know what to do.

Any idea what could solve this?

Here is my **lshw -c network** output:

      ```
*-network                 
           descripción: Ethernet interface
           producto: RTL810xE PCI Express Fast Ethernet controller
           fabricante: Realtek Semiconductor Co., Ltd.
           id físico: 0
           información del bus: pci@0000:09:00.0
           nombre lógico: eno1
           versión: 08
           serie: 6c:c2:17:6e:86:5b
           tamaño: 10Mbit/s
           capacidad: 100Mbit/s
           anchura: 64 bits
           reloj: 33MHz
           capacidades: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
           configuración: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8106e-2_0.0.1 04/23/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
           recursos: irq:19 ioport:3000(size=256) memoria:b2404000-b2404fff memoria:b2400000-b2403fff
      *-network:0 DESACTIVADO
           descripción: Ethernet interface
           id físico: 3
           nombre lógico: virbr0-nic
           serie: 52:54:00:a7:f3:d6
           tamaño: 10Mbit/s
           capacidades: ethernet physical
           configuración: autonegotiation=off broadcast=yes driver=tun driverversion=1.6 duplex=full link=no multicast=yes port=twisted pair speed=10Mbit/s
      *-network:1
           descripción: Ethernet interface
           id físico: 4
           nombre lógico: lxcbr0
           serie: 00:16:3e:00:00:00
           capacidades: ethernet physical
           configuración: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A ip=10.0.3.1 link=no multicast=yes
      *-network:2
           descripción: Ethernet interface
           id físico: 5
           nombre lógico: virbr0
           serie: 52:54:00:a7:f3:d6
           capacidades: ethernet physical
           configuración: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A ip=192.168.122.1 link=no multicast=yes
      *-network:3
           descripción: Ethernet interface
           id físico: 6
           nombre lógico: docker0
           serie: 02:42:e4:96:48:1b
           capacidades: ethernet physical
           configuración: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A ip=172.17.0.1 link=no multicast=yes
      *-network:4
           descripción: Ethernet interface
           id físico: 7
           nombre lógico: br-2c754fe6c808
           serie: 02:42:e0:1f:0f:ab
           capacidades: ethernet physical
           configuración: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A ip=172.18.0.1 link=no multicast=yes
```

Also sometimes wireless connection works. One time it was working I captured this commands:

**lspci:**

    ```
00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 0b)
    00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)
    00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 0b)
    00:14.0 USB controller: Intel Corporation 8 Series USB xHCI HC (rev 04)
    00:16.0 Communication controller: Intel Corporation 8 Series HECI #0 (rev 04)
    00:1b.0 Audio device: Intel Corporation 8 Series HD Audio Controller (rev 04)
    00:1c.0 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 1 (rev e4)
    00:1c.1 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 2 (rev e4)
    00:1c.2 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 3 (rev e4)
    00:1c.3 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 4 (rev e4)
    00:1d.0 USB controller: Intel Corporation 8 Series USB EHCI #1 (rev 04)
    00:1f.0 ISA bridge: Intel Corporation 8 Series LPC Controller (rev 04)
    00:1f.2 SATA controller: Intel Corporation 8 Series SATA Controller 1 [AHCI mode] (rev 04)
    00:1f.3 SMBus: Intel Corporation 8 Series SMBus Controller (rev 04)
    02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5227 PCI Express Card Reader (rev 01)
    08:00.0 Network controller: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev ff)
    09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL810xE PCI Express Fast Ethernet controller (rev 08)
```

[B]ifconfig
[/B]
```

    br-3e16b20b6485: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
            inet 172.23.0.1  netmask 255.255.0.0  broadcast 172.23.255.255
            ether 02:42:ce:2d:2f:00  txqueuelen 0  (Ethernet)
            RX packets 0  bytes 0 (0.0 B)
            RX errors 0  dropped 0  overruns 0  frame 0
            TX packets 0  bytes 0 (0.0 B)
            TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
    
    br-b4f85ba125f5: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
            inet 172.18.0.1  netmask 255.255.0.0  broadcast 172.18.255.255
            ether 02:42:22:77:05:a8  txqueuelen 0  (Ethernet)
            RX packets 0  bytes 0 (0.0 B)
            RX errors 0  dropped 0  overruns 0  frame 0
            TX packets 0  bytes 0 (0.0 B)
            TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
    
    br-ca5b6b9b884d: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
            inet 172.22.0.1  netmask 255.255.0.0  broadcast 172.22.255.255
            ether 02:42:52:68:5f:27  txqueuelen 0  (Ethernet)
            RX packets 0  bytes 0 (0.0 B)
            RX errors 0  dropped 0  overruns 0  frame 0
            TX packets 0  bytes 0 (0.0 B)
            TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
    
    br-e99fb540f27c: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
            inet 172.19.0.1  netmask 255.255.0.0  broadcast 172.19.255.255
            ether 02:42:33:86:c6:dd  txqueuelen 0  (Ethernet)
            RX packets 0  bytes 0 (0.0 B)
            RX errors 0  dropped 0  overruns 0  frame 0
            TX packets 0  bytes 0 (0.0 B)
            TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
    
    docker0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
            inet 172.17.0.1  netmask 255.255.0.0  broadcast 172.17.255.255
            ether 02:42:ca:77:6a:ef  txqueuelen 0  (Ethernet)
            RX packets 0  bytes 0 (0.0 B)
            RX errors 0  dropped 0  overruns 0  frame 0
            TX packets 0  bytes 0 (0.0 B)
            TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
    
    eno1: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
            ether 6c:c2:17:6e:86:5b  txqueuelen 1000  (Ethernet)
            RX packets 10940  bytes 982163 (982.1 KB)
            RX errors 0  dropped 0  overruns 0  frame 0
            TX packets 14238  bytes 1150158 (1.1 MB)
            TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
    
    lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
            inet 127.0.0.1  netmask 255.0.0.0
            inet6 ::1  prefixlen 128  scopeid 0x10<host>
            loop  txqueuelen 1000  (Bucle local)
            RX packets 5270  bytes 362984 (362.9 KB)
            RX errors 0  dropped 0  overruns 0  frame 0
            TX packets 5270  bytes 362984 (362.9 KB)
            TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
    
    lxcbr0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
            inet 10.0.3.1  netmask 255.255.255.0  broadcast 0.0.0.0
            ether 00:16:3e:00:00:00  txqueuelen 1000  (Ethernet)
            RX packets 0  bytes 0 (0.0 B)
            RX errors 0  dropped 0  overruns 0  frame 0
            TX packets 0  bytes 0 (0.0 B)
            TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
    
    virbr0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
            inet 192.168.122.1  netmask 255.255.255.0  broadcast 192.168.122.255
            ether 52:54:00:a7:f3:d6  txqueuelen 1000  (Ethernet)
            RX packets 0  bytes 0 (0.0 B)
            RX errors 0  dropped 0  overruns 0  frame 0
            TX packets 0  bytes 0 (0.0 B)
            TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
    
    wlo1: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
            ether b8:ee:65:b6:b8:f1  txqueuelen 1000  (Ethernet)
            RX packets 26  bytes 4644 (4.6 KB)
            RX errors 0  dropped 0  overruns 0  frame 0
            TX packets 198  bytes 24594 (24.5 KB)
            TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

**Another one**

    ```
eno1      no wireless extensions.
    
    br-e99fb540f27c  no wireless extensions.
    
    br-b4f85ba125f5  no wireless extensions.
    
    docker0   no wireless extensions.
    
    wlo1      IEEE 802.11  ESSID:off/any  
              Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
              Retry short limit:7   RTS thr:off   Fragment thr:off
              Power Management:off
              
    lxcbr0    no wireless extensions.
    
    virbr0    no wireless extensions.
    
    lo        no wireless extensions.
    
    br-3e16b20b6485  no wireless extensions.
    
    virbr0-nic  no wireless extensions.
    
    br-ca5b6b9b884d  no wireless extensions.
```

I tried installing this repository: [https://github.com/smlinux/rtl8723de.git](https://github.com/smlinux/rtl8723de.git)

But it didn't work. I think I should blacklist the actual adapater in the **/etc/modprobe.d/blacklist.conf** file, but I don't know what I should add there.

Here is my **sudo ls /etc/modprobe.d/**

    ```
alsa-base.conf
    amd64-microcode-blacklist.conf
    blacklist-ath_pci.conf
    blacklist.conf
    blacklist-firewire.conf
    blacklist-frambuffer.conf
    blacklist-mode.conf
    blacklist-oss.conf
    blacklist-rare-network.conf
    blacklist-watchdog.conf
    dkms.conf
    intel-microcode-blacklist.conf
    iwlwifi.conf
    qemu-system-x86.conf
    rtl8723be.conf
```

**Note that it got installed rtl8723be instead of rtl8723de**

And I added this to **blacklist.conf** file

    ```
blacklist acer_wmi
    blacklist bcma/ d
    blacklist brcmsmac/ d
    blacklist iwlwifi
    blacklist dkms
```

Btw I'm my hp with a single boot, I have only Ubuntu 18.04 installed on it.

---

### Post by chili555 on 2019-05-06
This is a classic example of throwing everything in the toolbox at the problem ... and then throwing the kitchen sink! We see it often and you are not alone.

This is your wireless device:

> Network controller: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev ff)

As you can see, it is an Atheros. No Realtek driver you have installed is useful. Please stop.

Next, you have a number of useless and, in some cases, malformed entries in /etc/modprobe.d/blacklist.conf. Please remove them all:

```
blacklist acer_wmi
    blacklist bcma/ d
    blacklist brcmsmac/ d
    blacklist iwlwifi
    blacklist dkms
```

Finally, we see that sometimes the device appears and sometimes it does not. A device will appear on the PCI bus even if it has no driver. Compiling and installing a different driver, especially the wrong driver, won't make it magically appear.

I suggest that there are three possible reasons that your device appears intermittantly. First, that there is a setting in the BIOS or UEFI that enables or disables the wireless. Please check and be certain it is correctly set.

Second, the device is not properly seated in its slot. [http://www.laptoprepair101.com/wp-images/wi-fi-card/install-wireless-card.jpg](http://www.laptoprepair101.com/wp-images/wi-fi-card/install-wireless-card.jpg) Please check.

Finally, the card itself may be failing.

---

### Post by jwonch on 2019-05-07
I have an hp 560-p0044 with the same problem but wireless has never worked in linux. I've tried different versions of linux with no results. Tech support says I have a broadcom chip

---

### Post by chili555 on 2019-05-09
> **jwonch said:**
> I have an hp 560-p0044 with the same problem but wireless has never worked in linux. I've tried different versions of linux with no results. Tech support says I have a broadcom chipUnless your readings and your symptoms, that is, appearing and disapearing under lspci, are different, then the answer I gave above is still what I suggest.

If your symptoms are indeed different, start a new thread and  post:```
lspci -nnk
rfkill list all
```We'll be happy to help.

---

