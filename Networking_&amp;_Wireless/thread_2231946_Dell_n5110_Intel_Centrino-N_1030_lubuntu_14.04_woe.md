---
title: "Dell n5110 Intel Centrino-N 1030 lubuntu 14.04 woes"
date: 2014-06-28
forum: Networking &amp; Wireless
---

### Post by chrisco23 on 2014-06-28
I have had it working before with both Fedora and earlier versions of Kubuntu, and the machine even today dual-boots to Windows 7 with no problem.

I'm trying to make it work with Lubuntu (it is 3 years old) 14.04, but there are problems.

Somehow, after countless forum reads and trying things, I do have it working with my home office router, but I go to a cafe, or a meetup, or anywhere else, and it's an embarassment.

I can see the Networks in range, but I go to choose one, and nothing happens.  I have tried NetworkManager and wicd, and everything I can think of on the command line.

I don't use a laptop often--work out of home office on desktop, so it's hard for me to justify (and afford) a new laptop over this issue alone, but with the hours spent, I could easily have bought one.

Q1:  Somewhere I read someone had a 6250 working.  I bought one and I got nowhere with it, so I put the 1030 back in.  Now I'm finding more posts suggesting the 6230.  One of the things that prompted all this is that the 1030 won't do 5Ghz, which caused me some embarassment when I went to a tech meetup and I'm the only who can't even get online.  So should I order the 6230?  And/or should I consider a USB dongle solution?

Now I'm home and I realize what would probably be most helpful would be for me to go back to the cafe I just left and post the output from various commands there.  If necessary, I will do that.  I'm hoping someone has an idea based on what I'm giving in this post.

I'm posting only excerpts in places where it is fully obvious the full output is irrelevant.
```
lspci -v 
09:00.0 Network controller: Intel Corporation Centrino Wireless-N 1030 [Rainbow Peak] (rev 34)
    Subsystem: Intel Corporation Centrino Wireless-N 1030 BGN
    Flags: bus master, fast devsel, latency 0, IRQ 53
    Memory at f7e00000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: [c8] Power Management version 3
    Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [e0] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Device Serial Number ac-72-89-ff-ff-83-b4-95
    Kernel driver in use: iwlwifi
[CODE]

[CODE]iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"mub"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: 14:D6:4D:23:F3:58   
          Bit Rate=65 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=70/70  Signal level=-36 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:261   Missed beacon:0

```

```
nm-tool
NetworkManager Tool


State: connected (global)


- Device: wlan0  [mub] ---------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        AC:72:89:83:B4:95


  Capabilities:
    Speed:           65 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    *mub:            Infra, 14:D6:4D:23:F3:58, Freq 2427 MHz, Rate 54 Mb/s, Strength 87 WPA WPA2
    ATT328:          Infra, 3C:36:E4:E7:8F:70, Freq 2437 MHz, Rate 54 Mb/s, Strength 62 WPA WPA2
    2WIRE095:        Infra, 3C:EA:4F:32:9A:89, Freq 2462 MHz, Rate 54 Mb/s, Strength 70 WPA
    Freedom_Den:     Infra, 00:14:6C:7D:CC:00, Freq 2437 MHz, Rate 54 Mb/s, Strength 65 WPA2
    HOME-5502:       Infra, 88:F7:C7:30:55:02, Freq 2462 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2
    fredo:           Infra, 00:21:29:67:2F:AD, Freq 2412 MHz, Rate 54 Mb/s, Strength 64 WPA2
    jna's Guest Network: Infra, 66:33:4B:E4:D6:83, Freq 2462 MHz, Rate 54 Mb/s, Strength 50 WPA2
    jna's Network:   Infra, 60:33:4B:E4:D6:83, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WPA2
    ATT696:          Infra, 58:56:E8:AB:33:80, Freq 2462 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    HOME-7C12:       Infra, E8:3E:FC:8D:7C:10, Freq 2412 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    ATT784:          Infra, CC:65:AD:1D:0A:70, Freq 2437 MHz, Rate 54 Mb/s, Strength 55 WPA WPA2
    xfinitywifi:     Infra, 56:57:1A:D7:48:D0, Freq 2447 MHz, Rate 54 Mb/s, Strength 54
    xfinitywifi:     Infra, E6:3E:FC:8D:7C:10, Freq 2412 MHz, Rate 54 Mb/s, Strength 35
    MMG:             Infra, 60:A4:4C:6B:FE:C9, Freq 2437 MHz, Rate 54 Mb/s, Strength 50 WPA2
    SOMEHUM :        Infra, 08:BD:43:CD:28:D9, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WPA2
    dsf.cc:          Infra, BC:EE:7B:F0:47:4E, Freq 2452 MHz, Rate 54 Mb/s, Strength 42 WPA2
    xfinitywifi:     Infra, E6:89:2C:D5:34:60, Freq 2462 MHz, Rate 54 Mb/s, Strength 42
    HP-Print-8D-ENVY 5530 series: Infra, A4:5D:36:1D:6B:8D, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA2
    MM:              Infra, 60:A4:4C:6B:FE:C8, Freq 2437 MHz, Rate 54 Mb/s, Strength 55 WPA2
    Skype WiFi:      Infra, 74:91:1A:8E:23:58, Freq 2417 MHz, Rate 54 Mb/s, Strength 50
    .FREEWiFiGOWEX:  Infra, 74:91:1A:CE:23:58, Freq 2417 MHz, Rate 54 Mb/s, Strength 49
    Skype WiFi:      Infra, 74:91:1A:8E:3D:F8, Freq 2452 MHz, Rate 54 Mb/s, Strength 45
    Phoenix:         Infra, 20:C9:D0:24:FE:59, Freq 2422 MHz, Rate 54 Mb/s, Strength 40 WPA2
    2WIRE828:        Infra, 00:1E:C7:88:B3:89, Freq 2422 MHz, Rate 54 Mb/s, Strength 45 WEP
    Calimochos:      Infra, 68:7F:74:3A:4D:7A, Freq 2432 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    Viruses for free:Infra, 44:32:C8:F3:3F:18, Freq 2422 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    xfinitywifi:     Infra, 00:0D:67:23:BF:25, Freq 2412 MHz, Rate 54 Mb/s, Strength 49
    SmartFi:         Infra, C4:10:8A:61:E0:A8, Freq 2422 MHz, Rate 54 Mb/s, Strength 47
    Skype WiFi:      Infra, C4:10:8A:A1:E0:A8, Freq 2422 MHz, Rate 54 Mb/s, Strength 47
    metrowifi:       Infra, C4:10:8A:21:E0:A8, Freq 2422 MHz, Rate 54 Mb/s, Strength 44
    .FREEWiFiGOWEX:  Infra, C4:10:8A:E1:E0:A8, Freq 2422 MHz, Rate 54 Mb/s, Strength 44
    metrowifi:       Infra, 74:91:1A:0E:3D:F8, Freq 2452 MHz, Rate 54 Mb/s, Strength 44
    SmartFi:         Infra, 74:91:1A:4E:3D:F8, Freq 2452 MHz, Rate 54 Mb/s, Strength 42
    .FREEWiFiGOWEX:  Infra, 74:91:1A:CE:3D:F8, Freq 2452 MHz, Rate 54 Mb/s, Strength 42
    ATT152:          Infra, 64:55:B1:AB:D1:00, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    OMG Ponies!:     Infra, 00:26:B0:FE:21:61, Freq 2437 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2


  IPv4 Settings:
    Address:         192.168.0.103
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             192.168.0.1




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        18:03:73:86:85:EC


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off



```

```

lshw -c network
lshw -c network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 05
       serial: 18:03:73:86:85:ec
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:50 ioport:e000(size=256) memory:f1104000-f1104fff memory:f1100000-f1103fff
  *-network
       description: Wireless interface
       product: Centrino Wireless-N 1030 [Rainbow Peak]
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: wlan0
       version: 34
       serial: ac:72:89:83:b4:95
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.13.0-29-generic firmware=18.168.6.1 ip=192.168.0.103 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:53 memory:f7e00000-f7e01fff



```

This next I only commented out today by way of experiment.  It made no difference that I could see.
```
cat /etc/modprobe.d/iwlwifi.conf# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
#remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211



```
```
lsmod | grep wifiiwlwifi               169932  1 iwldvm
cfg80211              484040  3 iwlwifi,mac80211,iwldvm



```

```
 rfkill list all0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no



```

---

### Post by chrisco23 on 2014-06-29
I forgot to mention one other little thing:

It seems sometimes I don't even see the list of networks in NetworkManager unless I do "iwlist wlan scan" and then click the NetworkManager icon on the panel.

---

