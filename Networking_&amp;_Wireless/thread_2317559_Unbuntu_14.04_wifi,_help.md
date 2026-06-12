---
title: "Unbuntu 14.04 wifi, help"
date: 2016-03-17
forum: Networking &amp; Wireless
---

### Post by Sonata_Arctica on 2016-03-17
Hi everyone, I'm french and I have big problems to conect my unbuntu to wifi. I' m in dual boot with windows (wifi is ok on that) and unbutu (I have no problems at all, just wifi). My PC is an Asus X75VC.

Plese if someone can help me^^, there are some infos: 

Iwconfig
eth0      no wireless extensions. 

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 
          
lo        no wireless extensions. 

ifconfig 
eth0      Link encap:Ethernet  HWaddr 74:d0:2b:e5:3e:dd  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:65536  Metric:1 
          RX packets:169 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:169 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:12145 (12.1 KB)  TX bytes:12145 (12.1 KB) 



lsusb 
Bus 004 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 003 Device 003: ID 04f2:b354 Chicony Electronics Co., Ltd 
Bus 003 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 

lspci 
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09) 
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09) 
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09) 
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04) 
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04) 
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04) 
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04) 
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4) 
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4) 
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4) 
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04) 
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04) 
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04) 
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04) 
01:00.0 3D controller: NVIDIA Corporation GF117M [GeForce 610M/710M/820M / GT 620M/625M/630M/720M] (rev a1) 
03:00.0 Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01) 
04:00.0 Ethernet controller: Qualcomm Atheros AR8161 Gigabit Ethernet (rev 10) 
shorty@Shorty-777V:~$ lspci -nn | grep -i net 
03:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01) 
04:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8161 Gigabit Ethernet [1969:1091] (rev 10) 

lspci -k 
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09) 
    Subsystem: ASUSTeK Computer Inc. Device 14c7 
    Kernel driver in use: ivb_uncore 
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09) 
    Kernel driver in use: pcieport 
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09) 
    Subsystem: ASUSTeK Computer Inc. Device 14c7 
    Kernel driver in use: i915 
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04) 
    Subsystem: ASUSTeK Computer Inc. Device 14c7 
    Kernel driver in use: xhci_hcd 
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04) 
    Subsystem: ASUSTeK Computer Inc. Device 14c7 
    Kernel driver in use: mei_me 
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04) 
    Subsystem: ASUSTeK Computer Inc. Device 14c7 
    Kernel driver in use: ehci-pci 
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04) 
    Subsystem: ASUSTeK Computer Inc. Device 14c7 
    Kernel driver in use: snd_hda_intel 
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4) 
    Kernel driver in use: pcieport 
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4) 
    Kernel driver in use: pcieport 
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4) 
    Kernel driver in use: pcieport 
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04) 
    Subsystem: ASUSTeK Computer Inc. Device 14c7 
    Kernel driver in use: ehci-pci 
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04) 
    Subsystem: ASUSTeK Computer Inc. Device 14c7 
    Kernel driver in use: lpc_ich 
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04) 
    Subsystem: ASUSTeK Computer Inc. Device 14c7 
    Kernel driver in use: ahci 
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04) 
    Subsystem: ASUSTeK Computer Inc. Device 14c7 
01:00.0 3D controller: NVIDIA Corporation GF117M [GeForce 610M/710M/820M / GT 620M/625M/630M/720M] (rev a1) 
    Subsystem: ASUSTeK Computer Inc. GeForce GT 720M 
    Kernel driver in use: nouveau 
03:00.0 Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01) 
    Subsystem: AzureWave Device 1186 
    Kernel driver in use: ath9k 
04:00.0 Ethernet controller: Qualcomm Atheros AR8161 Gigabit Ethernet (rev 10) 
    Subsystem: ASUSTeK Computer Inc. Device 14c7 
    Kernel driver in use: alx 
shorty@Shorty-777V:~$ sudo lshw -C network 
[sudo] password for shorty: 
  *-network DISABLED      
       description: Wireless interface 
       product: AR9485 Wireless Network Adapter 
       vendor: Qualcomm Atheros 
       physical id: 0 
       bus info: pci@0000:03:00.0 
       logical name: wlan0 
       version: 01 
       serial: 24:0a:64:6a:8b:b0 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless 
       configuration: broadcast=yes driver=ath9k driverversion=3.19.0-25-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn 
       resources: irq:17 memory:f7900000-f797ffff memory:f7980000-f798ffff 
  *-network 
       description: Ethernet interface 
       product: AR8161 Gigabit Ethernet 
       vendor: Qualcomm Atheros 
       physical id: 0 
       bus info: pci@0000:04:00.0 
       logical name: eth0 
       version: 10 
       serial: 74:d0:2b:e5:3e:dd 
       capacity: 1Gbit/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=alx latency=0 link=no multicast=yes port=twisted pair 
       resources: irq:31 memory:f7800000-f783ffff ioport:d000(size=128) 

ismod 
No command 'ismod' found, did you mean: 
 Command 'insmod' from package 'kmod' (main) 
 Command 'lsmod' from package 'kmod' (main) 
ismod: command not found 
shorty@Shorty-777V:~$ sudo iwlist scan 
eth0      Interface doesn't support scanning. 

wlan0     Interface doesn't support scanning : Network is down 
 
lo        Interface doesn't support scanning. 


uname -r -m 
3.19.0-25-generic x86_64 



cat /etc/network/interfaces 
# interfaces(5) file used by ifup(8) and ifdown(8) 
auto lo 
iface lo inet loopback 


nm-tool 

NetworkManager Tool 

State: disconnected 

- Device: eth0 ----------------------------------------------------------------- 
  Type:              Wired 
  Driver:            alx 
  State:             unavailable 
  Default:           no 
  HW Address:        74:D0:2B:E5:3E:DD 

  Capabilities: 
    Carrier Detect:  yes 

  Wired Properties 
    Carrier:         off 


- Device: wlan0 ---------------------------------------------------------------- 
  Type:              802.11 WiFi 
  Driver:            ath9k 
  State:             unavailable 
  Default:           no 
  HW Address:        24:0A:64:6A:8B:B0 

  Capabilities: 

  Wireless Properties 
    WEP Encryption:  yes 
    WPA Encryption:  yes 
    WPA2 Encryption: yes 

  Wireless Access Points 



sudo rfkill list 
0: phy0: Wireless LAN 
    Soft blocked: no 
    Hard blocked: yes 
1: asus-wlan: Wireless LAN 
    Soft blocked: no 
    Hard blocked: no 
2: asus-bluetooth: Bluetooth 
    Soft blocked: no 
    Hard blocked: no 




nmcli connection show 
Usage: nmcli connection { COMMAND | help } 
  COMMAND := { list | status | up | down | delete } 

  list [id <id> | uuid <id>] 
  status [id <id> | uuid <id> | path <path>] 
  up id <id> | uuid <id> [iface <iface>] [ap <BSSID>] [--nowait] [--timeout <timeout>] 
  down id <id> | uuid <id> 
  delete id <id> | uuid <id>



Thank you so much if you can help me!!!

---

### Post by jeremy31 on 2016-03-17
```
echo "options asus-nb-wmi wapf=4" | sudo tee /etc/modprobe.d/asus-nb-wmi.conf
```

Reboot

---

### Post by Sonata_Arctica on 2016-03-27
Thanks !

---

