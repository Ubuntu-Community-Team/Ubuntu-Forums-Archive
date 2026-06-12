---
title: "Broadcom BCM4313"
date: 2014-01-09
forum: Networking &amp; Wireless
---

### Post by helge2 on 2014-01-09
Hi,

**Problem**: I can't connect to my local wifi network. I see it, and other networks and I'm promted for the password, yet the connection times out.
**Hardware**: Netbook with Broadcom chipset. Wasn't working after setup, got it to work somehow (I'm a Linux newbie) after following instructions in threads here. May have ****ed up some configs along the way. Did work eventually in another wifi hotspot though. Also works on wired connections.

For grep -R brcm /etc/modprobe.d I get the following:

```
/etc/modprobe.d/blacklist-bcm43.conf:# blacklist brcm80211
/etc/modprobe.d/blacklist-bcm43.conf:# blacklist brcmfmac
/etc/modprobe.d/blacklist-bcm43.conf:# blacklist brcmsmac
/etc/modprobe.d/blacklist-bcm43.conf~:# blacklist brcm80211
/etc/modprobe.d/blacklist-bcm43.conf~:# blacklist brcmfmac
/etc/modprobe.d/blacklist-bcm43.conf~:# blacklist brcmsmac
```

(Following the advice on another thread I commented them out. Didn't help.)

For cat /etc/lsb-release; uname -a:

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.3 LTS"
Linux WolfgangAmadeusMozart 3.8.0-29-generic #42~precise1-Ubuntu SMP Wed Aug 14 16:19:23 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

For lspci -nnk | grep -iA2 net:

```
01:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:1483]
    Kernel driver in use: wl
--
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:1584]
    Kernel driver in use: r8169
```

For lsusb:
```

Bus 001 Device 002: ID 5986:0313 Acer, Inc 
Bus 005 Device 002: ID 0a5c:21b4 Broadcom Corp. BCM2070 Bluetooth 2.1 + EDR
Bus 005 Device 003: ID 10c4:ea60 Cygnal Integrated Products, Inc. CP210x Composite Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

For iwconfig:

```
eth0      no wireless extensions.

eth1      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
lo        no wireless extensions.
```

Thanks in advance, guys!!

---

### Post by tfrue on 2014-01-09
Would you be so kind to post the output of
```
sudo lshw -C network
lscpi | grep Network
and 
sudo nm-tool
```

Thanks,
Chris

---

### Post by helge2 on 2014-01-09
Sure, thanks! The results:

```
PCI (sysfs)

```
```
01:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)

```
and

```
NetworkManager Tool


State: connected (global)


- Device: eth0  [Conexão cabeada 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        44:1E:A1:19:C0:3D


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.1.104
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             201.6.2.174
    DNS:             201.6.2.84
    DNS:             201.6.4.116




- Device: eth1  [RavCorp] ------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connecting (getting IP configuration)
  Default:           no
  HW Address:        2C:76:8A:8C:1C:5E


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 
    eliete_home:     Infra, 64:70:02:DA:7D:40, Freq 2467 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    Rede Wi-Fi de CJB: Infra, B8:8D:12:60:68:73, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA2
    VIVIANE:         Infra, F8:D1:11:CF:50:98, Freq 2452 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2
    Convidado de Claudinei: Infra, BA:8D:12:60:68:74, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    Mtravel:         Infra, B8:8D:12:5E:F9:85, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA2
    41A:             Infra, F8:1A:67:DC:FD:DC, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    Carol:           Infra, 68:7F:74:EA:F1:03, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    Mtravel de Rede de Convidado: Infra, BA:8D:12:5E:F9:86, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA2
    Bombana Net:     Infra, 58:6D:8F:2A:32:41, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    RDCB-INFRA01:    Infra, 90:F6:52:26:75:82, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    ACR59:           Infra, D8:FE:E3:49:AF:C1, Freq 2467 MHz, Rate 54 Mb/s, Strength 22 WPA
    simoni132:       Infra, 1C:7E:E5:BA:E3:54, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    Leonardo:        Infra, 8C:04:FF:12:3B:B4, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    Maurinet:        Infra, 1C:7E:E5:41:61:52, Freq 2422 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    Rede Wi-Fi de Claudia: Infra, 88:1F:A1:37:17:9C, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA2
    aliciasmk:       Infra, 6C:FD:B9:31:A9:0C, Freq 2452 MHz, Rate 54 Mb/s, Strength 15 WPA2
    CLARO-WIFI2:     Infra, D4:D7:48:6C:7E:23, Freq 2462 MHz, Rate 54 Mb/s, Strength 24
    IVAN:            Infra, 00:21:29:A0:4E:98, Freq 2437 MHz, Rate 54 Mb/s, Strength 15 WPA
    TP-LINK_2.4GHz_B0EA10: Infra, A8:15:4D:B0:EA:10, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    Mais Cambuci:    Infra, 34:08:04:DD:C9:FA, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    Thom_D019311:    Infra, 80:C6:AB:8A:74:80, Freq 2437 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
    Fr212Amaral:     Infra, 00:1D:D6:65:A5:90, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA2
    pedroca:         Infra, F4:EC:38:AC:67:3C, Freq 2432 MHz, Rate 54 Mb/s, Strength 24 WEP
    Anne:            Infra, 20:AA:4B:C5:CF:BC, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    NET-VIRTUA-WIFI: Infra, D4:D7:48:6C:7E:20, Freq 2462 MHz, Rate 54 Mb/s, Strength 24
    Carlos:          Infra, 00:23:69:C1:BE:56, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    Dauro Melo Jr:   Infra, 20:AA:4B:FA:0E:C1, Freq 2412 MHz, Rate 54 Mb/s, Strength 7 WPA WPA2
    DolceVita:       Infra, F8:1A:67:DD:12:CC, Freq 2442 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2
    CLARO-WIFI:      Infra, D4:D7:48:6C:7E:22, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA2 Enterprise
    linksys:         Infra, 00:1E:E5:49:1A:3E, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WEP
    LEO:             Infra, 90:B1:34:C3:1A:42, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WPA
    Homework:        Infra, 20:AA:4B:4D:99:0D, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    NETVIRTUA_527L431: Infra, 70:54:D2:6A:BB:60, Freq 2412 MHz, Rate 54 Mb/s, Strength 12 WPA WPA2
    SpinningKick WiFii: Infra, B8:8D:12:5E:FA:59, Freq 2437 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
    shen:            Infra, A0:F3:C1:F5:13:F4, Freq 2427 MHz, Rate 54 Mb/s, Strength 24 WPA2
    dlink:           Infra, F0:7D:68:E3:0A:3A, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    Wi-fi 3:         Infra, 00:1D:0F:D4:A5:96, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA
    Alexandre:       Infra, 14:D6:4D:25:1F:B0, Freq 2432 MHz, Rate 54 Mb/s, Strength 17 WPA
    Netvirtua.apt.134: Infra, 28:BE:9B:9B:2E:E0, Freq 2462 MHz, Rate 54 Mb/s, Strength 9 WPA WPA2
    CLARO-WIFI2:     Infra, 2C:3F:38:BE:F9:03, Freq 2412 MHz, Rate 54 Mb/s, Strength 17
    Rede Wi-Fi de CJB: Infra, 00:24:36:9C:B5:B7, Freq 2412 MHz, Rate 54 Mb/s, Strength 14 WPA2
    TP-LINK:         Infra, 00:1D:0F:FC:CA:6A, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WEP
    LAN24:           Infra, 90:F6:52:59:E7:6C, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    internet Eugenio:Infra, 90:F6:52:59:AD:F2, Freq 2417 MHz, Rate 54 Mb/s, Strength 19 WPA2
    Reme:            Infra, 00:1C:F0:7E:52:EE, Freq 2437 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2
    xianxiuvirtua:   Infra, 00:25:F1:DA:1D:DA, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WPA
    dlinks:          Infra, 1C:7E:E5:C0:04:32, Freq 2437 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2
    Manfra:          Infra, 00:18:39:1F:FE:AE, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WEP
    NET-VIRTUA-WIFI: Infra, 2C:3F:38:BE:F9:00, Freq 2412 MHz, Rate 54 Mb/s, Strength 17
    Cisco08244-guest:Infra, 02:AA:4B:FA:0E:C2, Freq 2412 MHz, Rate 54 Mb/s, Strength 12
    CLARO-WIFI:      Infra, 2C:3F:38:BE:F9:02, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA2 Enterprise
    acr59:           Infra, D8:5D:4C:D3:24:CA, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA2
    RavCorp:         Infra, 00:25:9C:78:51:E2, Freq 2412 MHz, Rate 54 Mb/s, Strength 72 WPA2
    AMARAL VISTORIAS:Infra, 90:F6:52:23:D3:60, Freq 2427 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
```

---

### Post by tfrue on 2014-01-09
You have to give the command ```
lshw -C network
```
A little more time to load, so try it again and give it a moment, please and thanks!

You might want to hook up over ethernet for now and disable the eth1 interface. What I would like for you to try is to essential re-install your driver and firmware for the interface.

Disable eth1 by typing:
```
sudo ifconfig eth1 down
```

So try:
```
sudo apt-get update
```
```
sudo apt-get --reinstall install bcmwl-kernel-source
```

If that give's you an error, try:
```
sudo apt-get install linux-headers-generic
sudo apt-get install linux-headers-$(uname -r)
sudo apt-get install --reinstall bcmwl-kernel-source
```

Then let's test the driver so we don't have to restart the computer:
```
sudo modprobe -r b43 ssb wl brcmfmac brcmsmac bcma
sudo modprobe wl
```

Good Luck,
Chris

---

### Post by helge2 on 2014-01-09
Ah, I see. Here's the output (will try the rest afterwards):

```
  *-network               
       descrição: Interface sem fio
       produto: BCM4313 802.11b/g/n Wireless LAN Controller
       fabricante: Broadcom Corporation
       physical id: 0
       informações do barramento: pci@0000:01:00.0
       nome lógico: eth1
       versão: 01
       serial: 2c:76:8a:8c:1c:5e
       largura: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuração: broadcast=yes driver=wl0 driverversion=6.20.155.1 (r326264) latency=0 multicast=yes wireless=IEEE 802.11abg
       recursos: irq:16 memória:95000000-95003fff
  *-network
       descrição: Ethernet interface
       produto: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       fabricante: Realtek Semiconductor Co., Ltd.
       physical id: 0
       informações do barramento: pci@0000:03:00.0
       nome lógico: eth0
       versão: 05
       serial: 44:1e:a1:19:c0:3d
       tamanho: 100Mbit/s
       capacidade: 100Mbit/s
       largura: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuração: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=192.168.1.104 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       recursos: irq:43 ioport:1000(tamanho=256) memória:92004000-92004fff memória:92000000-92003fff

```

---

### Post by helge2 on 2014-01-09
Hi Chris,

i did what you said. (Thank you!) Did not get any error on the reinstall command. The test commands didn't give any results (don't know if they were supposed to). As wifi wasn't working I restarted the computer. Everything as before now. 

I tried all commands you had posted to see if anything was different now. I found these differences for eth1 to before the reinstall:

```
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
```

All the rest seems to be the same..

---

### Post by helge2 on 2014-01-09
Hi,a quick update: I tried the netbook in a local WiFi cafe: It works. So I have tried 3 different hotspots, it worked in 2 of them. My hypothesis now is that the configuration of the one hotspot that doesn't work somehow is incompatible with the driver. (The hotspot works without problem with OSX, iOS and Windows devices, including the same netbook when it was still on Windows 7.)Any ideas?Cheers, Helge

---

### Post by helge2 on 2014-01-10
I FOUND THE PROBLEM!

The driver doesn't seem to work with WPA2 encryption. I changed the router configuration to WPA, it works now. By the way, I found that on a Windows forum, so the problem seems to have existed for Windows users, too: [http://answers.microsoft.com/en-us/windows/forum/windows_7-networking/broadcom-4313-80211bgn-not-working-on-wpa2-psk-aes/25bfe295-9e21-4387-b888-56d456aac466](http://answers.microsoft.com/en-us/windows/forum/windows_7-networking/broadcom-4313-80211bgn-not-working-on-wpa2-psk-aes/25bfe295-9e21-4387-b888-56d456aac466)

---

### Post by helge2 on 2014-01-10
PS: Thank you, Chris!!

---

### Post by tfrue on 2014-01-10
Happy to hear all went well! And no problem, glad I could help!

Chris

---

