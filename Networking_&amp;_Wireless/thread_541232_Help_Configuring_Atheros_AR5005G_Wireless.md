---
title: "Help Configuring Atheros AR5005G Wireless"
date: 2007-09-02
forum: Networking &amp; Wireless
---

### Post by WoodJRx on 2007-09-02
Hello, All.

I'm sorry to whine as a newbie, but I've been working on getting my wireless running for the last week now.  I've tried everything i've found, and all to no luck.  So, here the summary of my situation.

I'm running an Acer Aspire 5112WLMi (AMD Turion 64 x2), with an integrated Atheros AR5005G wireless chipset.  I've been running windows, but it was in FAT32.  Since I wanted to change it, I reformatted the drive to NTFS, installed XP pro, and then installed Ubuntu on it's own partition.

Thus, I'm dual booting Ubuntu (Fiesty Fawn) and XP Pro.  Being a native to XP, I set that account back up, reinstalled all my drivers, and everything is running perfectly.  Using the Acer supplied drivers for the wireless, it's running fine.  However, when I go to use wireless on ubuntu, it shows up that the device is installed, that the driver is installed.  When I mouse over the network manager on the task bar, it shows all available networks, including mine.

However, I am unable to connect to my network.  My network is running a WEP key (unknown level), that is a passphrase (as best as I can tell).  Ethernet is running perfectly fine, though.

Being new to linux, I don't know which commands to run, and display the output of.  Your help would be greatly appreciated.

---

### Post by moore.bryan on 2007-09-02
> **WoodJRx said:**
> My network is running a WEP key (unknown level), that is a passphrase (as best as I can tell).
*uh, you don't know? ;-)*
> **WoodJRx said:**
>  Being new to linux, I don't know which commands to run, and display the output of.  Your help would be greatly appreciated.
[I]how about the output of ```
lspci
sudo lshw -C network
iwconfig
```
[/I]

---

### Post by WoodJRx on 2007-09-02
Yeah... it's a cable modem/router installed the other day by my cable company.  It doesn't have a login that they gave me, and I haven't had the opportunity to call them for the login yet... which is yet another thing I have against my  cable company.  Anywyas...

lspci:
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37
00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc M56P [Radeon Mobility X1600]
06:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)
06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
06:02.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc Unknown device 0551 (rev 01)

sudo lshw -C network:
  *-network:0             
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@06:01.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:15:63:d9
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.0.14 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=twisted pair speed=100MB/s
       resources: ioport:a000-a0ff iomemory:c0210800-c02108ff irq:19
  *-network:1
       description: Wireless interface
       product: AR5005G 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 2
       bus info: pci@06:02.0
       logical name: wifi0
       version: 01
       serial: 00:16:cf:3a:34:47
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.3) latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:c0200000-c020ffff irq:20

iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:9 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:4180  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by moore.bryan on 2007-09-02
[I]well, you're in-luck and not.  it looks as though all your stuff is recognized and loaded, meaning the reason you can't get on is the unknown wep key.

can you log-in to the router to change any settings?
[/I]

---

### Post by oOMartinOo on 2007-09-02
yer if i were you i would type in the actual WEP key in Hex as for some reason the network manager sometimes dose not like it when you enter the passphase. Just my thought :)

---

### Post by WoodJRx on 2007-09-02
on a whim, I talked to one of my next door neighbors (I live in a complex), and i talked to them about their internet - turns out, Timewarner uses a default login to the routers... so, I now have access... I should have asked them sooner. 

I changed it to 128 bit encryption, changed the key, and it still didn't work. 

 However, I entered it in as a hex key, after changing to the 128 bit encryption and modifying the key, and it worked.  Apparently Ubuntu didn't like the 64 bit passphrase.... but it does like 128 bit hex keys... I'm not going to complain about the added security.

Sorry to bother everyone, and thanks for the help.  It's working now.

---

### Post by moore.bryan on 2007-09-03
*just glad to hear you got it working.  it possible, although i don't know why, your wireless card doesn't like 64-bit.*

---

