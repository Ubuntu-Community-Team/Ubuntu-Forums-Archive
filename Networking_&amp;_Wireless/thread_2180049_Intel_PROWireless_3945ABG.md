---
title: "Intel PRO/Wireless 3945ABG"
date: 2013-10-11
forum: Networking &amp; Wireless
---

### Post by QCFLKHJ on 2013-10-11
Hello all,

I'm having the following problem: I cannot connect to the wifi at work. 
Although network manager sees the wifi, when I choose to connect to it, it keeps asking for the password (and the password is correct).
I deleted the wireless connection and restarted my pc, which allowed to connect for maybe 30 seconds and then it returned to its previous behavior.
Other wireless connections seem to be working fine so I'm having trouble understanding the problem.
The connection identifier has "apple" in its name. I don't know if that means that the router is made by apple or if this information is useful but I thought it might be.

I'm running 
```
Linux ubuntu 3.12.0-031200rc4-generic #201310061735 SMP Sun Oct 6 21:37:14 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise
``` 

ifconfig gives the following
```
eth0      Link encap:Ethernet  HWaddr 00:1f:16:05:66:62  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:999 errors:0 dropped:0 overruns:0 frame:0
          TX packets:999 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:82858 (82.8 KB)  TX bytes:82858 (82.8 KB)


wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:7a:0d:27  
          inet addr:10.0.166.107  Bcast:10.0.167.255  Mask:255.255.248.0
          inet6 addr: fe80::21f:3cff:fe7a:d27/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12336 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9711 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14129727 (14.1 MB)  TX bytes:1500871 (1.5 MB)
```


If you would like to help me, please post commands with explanations of what they're supposed to do.
If you need any further info, please inform me.

Thanks!

---

### Post by varunendra on 2013-10-11
Welcome to the forums !

Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

This script makes no changes to the system. It just collects some useful info that helps us finding the problem and suggest a solution accordingly. The report it creates is stored in a file "wireless-info.txt" which you can examine yourself before uploading here. All the information that can potentially be sensitive is filtered by the script so the report is perfectly safe.

---

### Post by QCFLKHJ on 2013-10-13
Hi there [COLOR=#000000]varunendra. Thanks for the welcome.[/COLOR]

I ran the script and got the following:

```


*************** info trace ***************


***** uname -a *****


Linux ubuntu 3.12.0-031200rc4-generic #201310061735 SMP Sun Oct 6 21:37:14 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


***** lsb_release *****


Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise


***** lspci *****


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)
    Subsystem: Fujitsu Technology Solutions Device [1734:1123]
    Kernel driver in use: r8169
--
08:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
    Subsystem: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:1001]
    Kernel driver in use: iwl3945
    Kernel modules: iwl3945


***** lsusb *****


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


***** PCMCIA Card Info *****




***** iwconfig *****


wlan0     IEEE 802.11abg  ESSID:"NEUF_BAC8"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC address removed>   
          Bit Rate=36 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=36/70  Signal level=-74 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:3058   Missed beacon:0




***** rfkill *****


0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


***** lsmod *****


iwl3945                74256  0 
iwlegacy              105007  1 iwl3945
mac80211              634661  2 iwl3945,iwlegacy
cfg80211              504229  3 iwl3945,iwlegacy,mac80211


***** nm-tool *****


NetworkManager Tool


State: connected (global)


- Device: wlan0  [NEUF_BAC8] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwl3945
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           36 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    Livebox de Kim:  Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 67 WPA WPA2
    orange:          Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 49
    *NEUF_BAC8:      Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 48 WPA


  IPv4 Settings:
    Address:         192.168.1.33
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             208.67.222.222
    DNS:             208.67.220.220




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off






***** NetworkManager.state *****


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


***** NetworkManager.conf *****




[main]
plugins=ifupdown,keyfile
dns=dnsmasq


no-auto-default=<MAC address removed>,


[ifupdown]
managed=false


***** interfaces *****


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


***** iwlist *****


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"NEUF_BAC8"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000199e22e132
                    Extra: Last beacon: 32ms ago
                    IE: Unknown: 00094E4555465F42414338
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD840050F204104A00011010440001021041000100103B00010310470010D96C7EFC2F8938F1EFBD6E5148BFA812102100044E4555461023000A4E42342D4658432D72311024000A4E42342D4658432D72311042000C3030313733333431424143381054000800060050F2040001101100094E4555465F42414338100800020084103C000101
                    IE: Unknown: DD090010180203F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"Livebox de Kim"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003a3d911e26
                    Extra: Last beacon: 36ms ago
                    IE: Unknown: 000E4C697665626F78206465204B696D
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010020000000
                    IE: Unknown: 0706465220010D14
                    IE: Unknown: DD880050F204104A000110104400010210570001001041000100103B000103104700106C2E853E56926C2E853E5692853E569210210005536167656D102300084C697665626F7832102400084C697665626F78321042000A4C4B31323236344450331054000800060050F20400011011000D4C697665626F78322D35363932100800020086103C000101
          Cell 03 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:off
                    ESSID:"orange"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003a3d906b11
                    Extra: Last beacon: 36ms ago
                    IE: Unknown: 00066F72616E6765
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010020000000
                    IE: Unknown: 0706465220010D14




***** resolv.conf *****


nameserver 127.0.0.1


***** blacklist *****


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


***** modinfo *****


filename:       /lib/modules/3.12.0-031200rc4-generic/kernel/drivers/net/wireless/iwlegacy/iwl3945.ko
firmware:       iwlwifi-3945-2.ucode
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:s
description:    Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux
srcversion:     13DA4808345F1E38AF0CB69
alias:          pci:v00008086d00004227sv*sd*bc*sc*i*
alias:          pci:v00008086d00004222sv*sd*bc*sc*i*
alias:          pci:v00008086d00004227sv*sd00001014bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001044bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001034bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001005bc*sc*i*
depends:        iwlegacy,cfg80211,mac80211
intree:         Y
vermagic:       3.12.0-031200rc4-generic SMP mod_unload modversions 
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           swcrypto:using software crypto (default 1 [software]) (int)
parm:           disable_hw_scan:disable hardware scanning (default 1) (int)
parm:           fw_restart:restart firmware in case of error (int)


filename:       /lib/modules/3.12.0-031200rc4-generic/kernel/drivers/net/wireless/iwlegacy/iwlegacy.ko
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    iwl-legacy: common functions for 3945 and 4965
srcversion:     BC2DEA74DD4DC4E093C27BE
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.12.0-031200rc4-generic SMP mod_unload modversions 
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking (int)
parm:           bt_coex_active:enable wifi/bluetooth co-exist (bool)




***** udev rules *****


# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1c.2/0000:08:00.0 (iwl3945)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


***** dmesg *****


[   16.832604] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   16.832610] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   16.832698] iwl3945 0000:08:00.0: can't disable ASPM; OS doesn't have ASPM control
[   16.888116] iwl3945 0000:08:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   16.888122] iwl3945 0000:08:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   16.888197] iwl3945 0000:08:00.0: irq 46 for MSI/MSI-X
[   17.224270] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   26.979653] iwl3945 0000:08:00.0: loaded firmware version 15.32.2.9
[   27.050714] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   34.544743] wlan0: authenticate with <MAC address removed>
[   34.547943] wlan0: send auth to <MAC address removed> (try 1/3)
[   34.748052] wlan0: send auth to <MAC address removed> (try 2/3)
[   34.749865] wlan0: authenticated
[   34.752060] wlan0: associate with <MAC address removed> (try 1/3)
[   34.754701] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[   34.756092] wlan0: associated
[   34.756130] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


****************** done ******************



```

---

### Post by varunendra on 2013-10-13
> **QCFLKHJ said:**
> ```

Linux ubuntu **[COLOR="#FF0000"]3.12.0-031200rc4-generic[/COLOR]** #201310061735 SMP Sun Oct 6 21:37:14 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

```

Why are you using a non-stable kernel? Was there something that didn't work with the default one (or the latest stable - 3.12-rc4) and is working with this one?

Your wireless card is an ancient model that uses a legacy driver, so I don't think anything is going to change with kernel versions.

As a wild shot, you may try these when it fails to connect -
```
sudo modprobe -rv iwl3945
sudo modprobe -v iwl3945 swcrypto=1
```

If this doesn't help, try this -
```
sudo modprobe -rv iwl3945
sudo modprobe -v iwlegacy bt_coex_active=N
sudo modprobe -v iwl3945
```
These changes are temporary and will be lost at reboot. If any of these seems to help, we can make it permanent. If none of these help, please download this alternate version of the wireless script : [http://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script](http://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script) and run it when you are at work and the connection fails with the access point you were originally concerned about.

Along with the script report, please also post the output of -
```
grep -R [[:alnum:]] /sys/module/iwl*/parameters
```

---

### Post by QCFLKHJ on 2013-10-13
I have an unstable version of the kernel because I was trying to fix my issue and one of the fixes I found online suggested a kernel problem.
I'm going back to 3.12-rc4.

I was looking at the manual pages for modprobe and it says that this command removes kernel modules. Why would removing the iwl3945 module fix the issue? 

Furthermore, what does swcrypto=1 do ? same for bt_coex_active=N? Why are you turning them on/off?

Update: I can't seem to be able to go back to [3.12.0-031200rc4.201310080738]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.12-rc4-saucy/linux-image-3.12.0-031200rc4-generic_3.12.0-031200rc4.201310080738_amd64.deb")

---

### Post by varunendra on 2013-10-13
> **QCFLKHJ said:**
> I have an unstable version of the kernel because I was trying to fix my issue and one of the fixes I found online suggested a kernel problem.
I'm going back to 3.12-rc4.
You mean 3.11.4, you are already on 3.12-rc4 (yeah, I made the same mistake in my post too, looks like you copy pasted :P). See here : [https://www.kernel.org/](https://www.kernel.org/)

> I was looking at the manual pages for modprobe and it says that this command removes kernel modules. Why would removing the iwl3945 module fix the issue? 

Furthermore, what does swcrypto=1 do ? same for bt_coex_active=N? Why are you turning them on/off?
Yeah, modprobe -r removes the module, then the second modprobe (without -r) loads it again, with the given parameters this time. In order to load with the parameters, it has to be removed first.

The **swcrypto=1** parameter enables software encryption, which means now the burden of packet encryption will be shifted from the card's hardware (hardware encryption) to the software (Software encryption, driver+OS). This helps when the hardware can't keep up with the speed of encryption required to keep the connection stable, sometimes not even good enough to establish the connection first.

The **bt_coex_active=N** parameter disables bluetooth and wifi signal coexistence. A wide range of wifi frequencies are same as those of bluetooth which may cause mutual interference (when bluetooth is in use or is transmitting signals). To avoid that, the 'coexistence' technique is implied which is supposed to transmit/receive the signals in such a way so that they don't interfere. What is done to achieve this doesn't always work as expected. Sometimes the access-point may not like it, sometimes the driver or the device firmware may be buggy. And when that happens, disabling that 'feature' is the best and perhaps the only remedy.

The firmware your card uses has been buggy since the beginning and Intel never cared to fix those bugs, perhaps they were more busy developing better cards. When this card works, it just works. When it starts acting, we can just try different things and hope they can make it happy again.

> Update: I can't seem to be able to go back to [3.12.0-031200rc4.201310080738]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.12-rc4-saucy/linux-image-3.12.0-031200rc4-generic_3.12.0-031200rc4.201310080738_amd64.deb")

You must have the older kernel still installed. Do you get the Grub menu at booting time? If not, press 'any' key during the purple splash screen to get the Grub boot menu, and choose the older kernel to boot from. If things work better or even the same way there, you may choose to purge the latest one.

---

### Post by perkowski-karol on 2014-01-29
Hi
I have same problem. I've gone through forum but it would not help me. I don't have wire/cable connection but I have another laptop where wifi is working
I ran the script and got the following:
Could you help me 
please
```

*************** info trace ***************

***** uname -a *****

Linux karol-HP-Pavilion-dv6700-Notebook-PC 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:12:00 UTC 2013 i686 i686 i686 GNU/Linux

***** lsb_release *****

Distributor ID:    LinuxMint
Description:    Linux Mint 16 Petra
Release:    16
Codename:    petra

***** lspci *****

02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
    Subsystem: Hewlett-Packard Company PRO/Wireless 3945ABG [Golan] Network Connection [103c:135c]
    Kernel driver in use: iwl3945
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)
    Subsystem: Hewlett-Packard Company Pavilion dv6700 [103c:30cc]
    Kernel driver in use: r8169

***** lsusb *****

Bus 002 Device 002: ID 0408:030c Quanta Computer, Inc. HP Webcam
Bus 002 Device 003: ID 0718:070a Imation Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

***** rfkill *****

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

***** lsmod *****

iwl3945                63619  0 
iwlegacy               87971  1 iwl3945
mac80211              513247  2 iwl3945,iwlegacy
cfg80211              401436  3 iwl3945,iwlegacy,mac80211

***** nm-tool *****

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwl3945
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 



***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

***** iwlist *****


***** resolv.conf *****


***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

***** modinfo *****

filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/iwlegacy/iwl3945.ko
firmware:       iwlwifi-3945-2.ucode
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:s
description:    Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux
srcversion:     4675AA357ACE4FC4BF610F7
alias:          pci:v00008086d00004227sv*sd*bc*sc*i*
alias:          pci:v00008086d00004222sv*sd*bc*sc*i*
alias:          pci:v00008086d00004227sv*sd00001014bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001044bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001034bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001005bc*sc*i*
depends:        iwlegacy,cfg80211,mac80211
intree:         Y
vermagic:       3.11.0-12-generic SMP mod_unload modversions 686 
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           swcrypto:using software crypto (default 1 [software]) (int)
parm:           disable_hw_scan:disable hardware scanning (default 1) (int)
parm:           fw_restart:restart firmware in case of error (int)

filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/iwlegacy/iwlegacy.ko
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    iwl-legacy: common functions for 3945 and 4965
srcversion:     BC2DEA74DD4DC4E093C27BE
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.11.0-12-generic SMP mod_unload modversions 686 
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking (int)
parm:           bt_coex_active:enable wifi/bluetooth co-exist (bool)


***** udev rules *****

# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x4222 (iwl3945)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[   12.794413] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   12.794419] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   12.794481] iwl3945 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[   12.863016] iwl3945 0000:02:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   12.863023] iwl3945 0000:02:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   12.863108] iwl3945 0000:02:00.0: irq 47 for MSI/MSI-X
[   12.871608] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   15.343551] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

****************** done ******************


```

---

### Post by varunendra on 2014-01-29
Hi Karol,

Your wifi is currently physically turned off, most probably via the hardware switch (a dedicated switch or a Fn+key combination, whatever it is) -
> **perkowski-karol said:**
> 
```

***** rfkill *****

0: phy0: Wireless LAN
    Soft blocked: no
    **Hard blocked: [COLOR="#FF0000"]yes[/COLOR]**
1: hp-wifi: Wireless LAN
    Soft blocked: no
    **Hard blocked: [COLOR="#FF0000"]yes[/COLOR]**

```

Please make sure the hardware switch is on first. Try the switch or the combination to toggle it on/off, then check with -
```
rfkill list
```
Both hard and softblock should appear as "no". If not, try resetting your laptop's BIOS (if it is not a UEFI based system, which it doesn't seem to be, since the card is a real old one).

Try this and post back the report. Once the wifi is enabled (hard/soft block is disabled), try to scan available networks and connect to them. If it fails to connect, post back a fresh report of the wireless_script.

---

### Post by Lucio01 on 2014-02-01
Hello i'm having the same issue; with repeating password requested.
It works perfectly with a Ralink "big" dongle, if i disable the Intel in the bios.

I would prefer the integrated solution.

Here is the output of the script
```


*************** info trace ***************

***** uname -a *****

Linux asus 3.2.0-58-generic #88-Ubuntu SMP Tue Dec 3 17:40:43 UTC 2013 i686 i686 i386 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

***** lspci *****

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 01)
    Subsystem: ASUSTeK Computer Inc. A6J-Q008 [1043:11f5]
    Kernel driver in use: r8169
--
02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
    Subsystem: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:1001]
    Kernel driver in use: iwl3945
    Kernel modules: iwl3945

***** lsusb *****

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0b05:1712 ASUSTek Computer, Inc. BT-183 Bluetooth 2.0+EDR adapter

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

***** rfkill *****

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** lsmod *****

iwl3945                73145  0 
iwl_legacy             71334  1 iwl3945
mac80211              436493  2 iwl3945,iwl_legacy
cfg80211              178877  3 iwl3945,iwl_legacy,mac80211

***** nm-tool *****

NetworkManager Tool

State: connecting

- Device: wlan0  [xxxxxxxxx] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwl3945
  State:             connecting (need authentication)
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    FreeWifi_secure: Infra, <MAC address removed>, Freq 2442 MHz, Rate 54 Mb/s, Strength 65 WPA2 Enterprise
    FreeWifi:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30
    xxxxxxxxx:       Infra, <MAC address removed>, Freq 2442 MHz, Rate 54 Mb/s, Strength 44 WPA


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off



***** NetworkManager.state *****

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

auto lo
iface lo inet loopback

auto wlan0

***** iwlist *****


***** resolv.conf *****


***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

***** modinfo *****

filename:       /lib/modules/3.2.0-58-generic/kernel/drivers/net/wireless/iwlegacy/iwl3945.ko
firmware:       iwlwifi-3945-2.ucode
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:s
description:    Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux
srcversion:     301B04B4010DED41B0830D0
alias:          pci:v00008086d00004227sv*sd*bc*sc*i*
alias:          pci:v00008086d00004222sv*sd*bc*sc*i*
alias:          pci:v00008086d00004227sv*sd00001014bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001044bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001034bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001005bc*sc*i*
depends:        iwl-legacy,cfg80211,mac80211
intree:         Y
vermagic:       3.2.0-58-generic SMP mod_unload modversions 686 
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           swcrypto:using software crypto (default 1 [software]) (int)
parm:           disable_hw_scan:disable hardware scanning (default 1) (int)
parm:           fw_restart:restart firmware in case of error (int)

filename:       /lib/modules/3.2.0-58-generic/kernel/drivers/net/wireless/iwlegacy/iwl-legacy.ko
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    iwl-legacy: common functions for 3945 and 4965
srcversion:     E722FD105B84D0374546E93
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.2.0-58-generic SMP mod_unload modversions 686 
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking (int)
parm:           bt_coex_active:enable wifi/bluetooth co-exist (bool)


***** udev rules *****

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x4222 (iwl3945)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# USB device 0x0db0:0x6861 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

***** dmesg *****

[   25.850998] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   25.851003] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   25.851083] iwl3945 0000:02:00.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[   25.851099] iwl3945 0000:02:00.0: setting latency timer to 64
[   26.099327] iwl3945 0000:02:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   26.099332] iwl3945 0000:02:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   26.114094] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   29.792722] iwl3945 0000:02:00.0: loaded firmware version 15.32.2.9
[   29.868066] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   38.159975] wlan0: direct probe to <MAC address removed> (try 1/3)
[   38.356038] wlan0: direct probe to <MAC address removed> (try 2/3)
[   38.556242] wlan0: direct probe to <MAC address removed> (try 3/3)
[   38.756048] wlan0: direct probe to <MAC address removed> timed out
[   46.831864] wlan0: direct probe to <MAC address removed> (try 1/3)
[   47.028027] wlan0: direct probe to <MAC address removed> (try 2/3)
[   47.228027] wlan0: direct probe to <MAC address removed> (try 3/3)
[   47.428026] wlan0: direct probe to <MAC address removed> timed out
[   55.503866] wlan0: direct probe to <MAC address removed> (try 1/3)
[   55.700027] wlan0: direct probe to <MAC address removed> (try 2/3)
[   55.900026] wlan0: direct probe to <MAC address removed> (try 3/3)
[   56.100027] wlan0: direct probe to <MAC address removed> timed out
[   64.216441] wlan0: direct probe to <MAC address removed> (try 1/3)
[   64.416041] wlan0: direct probe to <MAC address removed> (try 2/3)
[   64.616056] wlan0: direct probe to <MAC address removed> (try 3/3)
[   64.816051] wlan0: direct probe to <MAC address removed> timed out
[   72.891919] wlan0: direct probe to <MAC address removed> (try 1/3)
[   73.088058] wlan0: direct probe to <MAC address removed> (try 2/3)
[   73.288048] wlan0: direct probe to <MAC address removed> (try 3/3)
[   73.488051] wlan0: direct probe to <MAC address removed> timed out
[   81.570777] wlan0: direct probe to <MAC address removed> (try 1/3)
[   81.768037] wlan0: direct probe to <MAC address removed> (try 2/3)
[   81.968044] wlan0: direct probe to <MAC address removed> (try 3/3)
[   82.168037] wlan0: direct probe to <MAC address removed> timed out
[   90.244710] wlan0: direct probe to <MAC address removed> (try 1/3)
[   90.444046] wlan0: direct probe to <MAC address removed> (try 2/3)
[   90.644051] wlan0: direct probe to <MAC address removed> (try 3/3)
[   90.844037] wlan0: direct probe to <MAC address removed> timed out
[  105.672611] wlan0: direct probe to <MAC address removed> (try 1/3)
[  105.872056] wlan0: direct probe to <MAC address removed> (try 2/3)
[  106.072064] wlan0: direct probe to <MAC address removed> (try 3/3)
[  106.272059] wlan0: direct probe to <MAC address removed> timed out

****************** done ******************


```
And the parameters

```

/sys/module/iwl3945/parameters/fw_restart:1
/sys/module/iwl3945/parameters/disable_hw_scan:1
/sys/module/iwl3945/parameters/swcrypto:1
/sys/module/iwl3945/parameters/antenna:0
/sys/module/iwl_legacy/parameters/bt_coex_active:Y
/sys/module/iwl_legacy/parameters/led_mode:0

```


**Note** i've tested w/o success the two options for iwl3945

Many thanks for all help you may give to me
Lucio

---

### Post by varunendra on 2014-02-02
> **Lucio01 said:**
> **Note** i've tested w/o success the two options for iwl3945

You may try both the parameters at once, and you should try that -
```
sudo modprobe -rv iwl3945
sudo modprobe -v iwlegacy bt_coex_active=N
sudo modprobe -v iwl3945 swcrypto=1
```

..and if it doesn't help, can you try changing the encryption type in the router for a test? Like WEP, WPA2 or no security at all? This would be just for a test and if it lets you connect, report back. Leave the changed encryption to WPA2 (with AES, not TKIP) if that is what lets you connect, or reset it to the current settings (WPA/TKIP) after the test.

I trust you have already cross-checked that the security settings save in Network Manager are correct.

Can you also try a newer version if downloading a whole new ISO is not a problem for you? Because as you can see in the report, you are still using kernel 3.2 series despite having upgraded to 12.4.4. We can manually upgrade your kernel and Xorg packages as mentioned [here]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack"), but trying a newer version in a Live session would be much safer and easier, especially if the rest of your current installation has been properly setup to your liking and is behaving nicely.

---

### Post by Lucio01 on 2014-02-03
Hello thanks for the updates.
I've unsuccessfully tested the two options combined.

I've as well tested the unsecure logon, one of the SSID my box is publishing is unsecured.
It loops trying to connect, finishes by a timeout.

Testing with a brand new iso will re quire more time to me.
I'll let you know.

Many thankds
Lucio

---

### Post by 8valve.head on 2014-02-10
Hi, I have been having the same problem with this card on a Dell D830 for a few weeks. I just tried the second suggested code in the 4th post 

 ```
bt_coex_active=N 
```

and have had success! I was hoping that you might be able to give me some direction for making it a permanent solution, as I read that it goes away after reboot. Any help is much appreciated!

---

### Post by varunendra on 2014-02-10
> **8valve.head said:**
> Hi, I have been having the same problem with this card on a Dell D830 for a few weeks. I just tried the second suggested code in the 4th post 

 ```
bt_coex_active=N 
```

and have had success! I was hoping that you might be able to give me some direction for making it a permanent solution, as I read that it goes away after reboot. Any help is much appreciated!

Welcome to the forums 8valve.head! :)

Please run the following command to make it permanent -
```
echo "options iwlegacy bt_coex_active=N" | sudo tee /etc/modprobe.d/iwlegacy.conf
```
This will create a .conf file "iwlegacy.conf" in your /etc/modprobe.d directory that will make the driver "iwlegacy" automatically load the parameter at startup.

---

### Post by 8valve.head on 2014-02-12
Thank you so much! I will give this a try tonight, and just to be clear - I run this bit:
```
echo "options iwlegacy bt_coex_active=N" | sudo tee /etc/modprobe.d/iwlegacy.conf
```
after, or instead of:
```
sudo modprobe -rv iwl3945
sudo modprobe -v iwlegacy bt_coex_active=N
sudo modprobe -v iwl3945
```upon start up. I am new to coding and programming, only started learning a few weeks ago, so please forgive my need to be explicit. Thank you again!

---

### Post by varunendra on 2014-02-12
No problem ! :)> **8valve.head said:**
> ....after, or instead of:

Doesn't matter. The first command will create a .conf file that will come into effect since next boot.
It is meant to do the same thing as those three commands do, only automatically, so that you don't have to run those commands again.

---

### Post by chele-modica on 2014-03-01
Thank you varunendra.  My network is LifeISGOOD.

```

*************** info trace ***************

***** uname -a *****

Linux Lucas-toshiba 3.11.0-17-generic #31-Ubuntu SMP Mon Feb 3 21:53:31 UTC 2014 i686 i686 i686 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy

***** lspci *****

02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller [11ab:4363] (rev 12)
    Subsystem: Fujitsu Limited. Device [10cf:139a]
    Kernel driver in use: sky2
05:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
    Subsystem: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:1000]
    Kernel driver in use: iwl3945
08:03.0 CardBus bridge [0607]: O2 Micro, Inc. OZ711MP1/MS1 MemoryCardBus Controller [1217:7134] (rev 20)

***** lsusb *****

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 004 Device 002: ID 0c24:000f Taiyo Yuden Bluetooth Device (V2.0+EDR)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

***** PCMCIA Card Info *****

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255
PRODID_1="O2Micro
"
PRODID_2="SmartCardBus Reader
"
PRODID_3="V1.0
"
PRODID_4=""
MANFID=ffff,0001
FUNCID=255

***** iwconfig *****

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

***** rfkill *****

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** iw reg get *****

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

***** route -n *****

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

***** lsmod *****

iwl3945                63619  0 
iwlegacy               88016  1 iwl3945
mac80211              517444  2 iwl3945,iwlegacy
cfg80211              401762  3 iwl3945,iwlegacy,mac80211

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwl3945
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    ATT313:          Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    JA113:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    LIFEISGOOD:      Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 92 WPA2
    7P32O3K3:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA2


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.241
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254



***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

***** iwlist *****

Aquiring of root rights failed.

***** resolv.conf *****

nameserver 127.0.1.1
search att.net

***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

***** modinfo *****

filename:       /lib/modules/3.11.0-17-generic/kernel/drivers/net/wireless/iwlegacy/iwl3945.ko
firmware:       iwlwifi-3945-2.ucode
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:s
description:    Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux
srcversion:     35209C1F4B317C0961FADAF
alias:          pci:v00008086d00004227sv*sd*bc*sc*i*
alias:          pci:v00008086d00004222sv*sd*bc*sc*i*
alias:          pci:v00008086d00004227sv*sd00001014bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001044bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001034bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001005bc*sc*i*
depends:        iwlegacy,cfg80211,mac80211
intree:         Y
vermagic:       3.11.0-17-generic SMP mod_unload modversions 686 
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           swcrypto:using software crypto (default 1 [software]) (int)
parm:           disable_hw_scan:disable hardware scanning (default 1) (int)
parm:           fw_restart:restart firmware in case of error (int)

filename:       /lib/modules/3.11.0-17-generic/kernel/drivers/net/wireless/iwlegacy/iwlegacy.ko
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    iwl-legacy: common functions for 3945 and 4965
srcversion:     BC2DEA74DD4DC4E093C27BE
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.11.0-17-generic SMP mod_unload modversions 686 
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking (int)
parm:           bt_coex_active:enable wifi/bluetooth co-exist (bool)


***** udev rules *****

# PCI device 0x11ab:/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1c.2/0000:05:00.0 (iwl3945)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[   21.721530] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   21.721533] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   21.721581] iwl3945 0000:05:00.0: can't disable ASPM; OS doesn't have ASPM control
[   21.784785] iwl3945 0000:05:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   21.784789] iwl3945 0000:05:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   21.784861] iwl3945 0000:05:00.0: irq 45 for MSI/MSI-X
[   21.834002] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   25.551402] iwl3945 0000:05:00.0: loaded firmware version 15.32.2.9
[   25.621557] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.622059] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   48.140684] wlan0: authenticate with <MAC address removed>
[   48.144231] wlan0: send auth to <MAC address removed> (try 1/3)
[   48.146191] wlan0: authenticated
[   48.148093] wlan0: associate with <MAC address removed> (try 1/3)
[   48.150501] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   48.150505] wlan0: <MAC address removed> denied association (code=18)
[   48.161234] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   50.292609] wlan0: authenticate with <MAC address removed>
[   50.294573] wlan0: send auth to <MAC address removed> (try 1/3)
[   50.304504] wlan0: authenticated
[   50.308066] wlan0: associate with <MAC address removed> (try 1/3)
[   50.312964] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   50.312969] wlan0: <MAC address removed> denied association (code=18)
[   50.326480] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   52.452603] wlan0: authenticate with <MAC address removed>
[   52.454545] wlan0: send auth to <MAC address removed> (try 1/3)
[   52.456375] wlan0: authenticated
[   52.460096] wlan0: associate with <MAC address removed> (try 1/3)
[   52.462614] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   52.462618] wlan0: <MAC address removed> denied association (code=18)
[   52.480411] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   54.604612] wlan0: authenticate with <MAC address removed>
[   54.606368] wlan0: send auth to <MAC address removed> (try 1/3)
[   54.608170] wlan0: authenticated
[   54.612083] wlan0: associate with <MAC address removed> (try 1/3)
[   54.614475] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   54.614480] wlan0: <MAC address removed> denied association (code=18)
[   54.624454] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   56.768733] wlan0: authenticate with <MAC address removed>
[   56.770545] wlan0: send auth to <MAC address removed> (try 1/3)
[   56.772377] wlan0: authenticated
[   56.776132] wlan0: associate with <MAC address removed> (try 1/3)
[   56.778534] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   56.778539] wlan0: <MAC address removed> denied association (code=18)
[   56.804180] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   58.948525] wlan0: authenticate with <MAC address removed>
[   58.950238] wlan0: send auth to <MAC address removed> (try 1/3)
[   58.952212] wlan0: authenticated
[   58.956178] wlan0: associate with <MAC address removed> (try 1/3)
[   58.959773] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   58.959780] wlan0: <MAC address removed> denied association (code=18)
[   58.960640] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   61.084528] wlan0: authenticate with <MAC address removed>
[   61.086554] wlan0: send auth to <MAC address removed> (try 1/3)
[   61.095966] wlan0: authenticated
[   61.100048] wlan0: associate with <MAC address removed> (try 1/3)
[   61.134086] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   61.134093] wlan0: <MAC address removed> denied association (code=18)
[   61.141491] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   63.260757] wlan0: authenticate with <MAC address removed>
[   63.263372] wlan0: send auth to <MAC address removed> (try 1/3)
[   63.265186] wlan0: authenticated
[   63.268138] wlan0: associate with <MAC address removed> (try 1/3)
[   63.272310] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   63.272316] wlan0: <MAC address removed> denied association (code=18)
[   63.288274] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   65.416576] wlan0: authenticate with <MAC address removed>
[   65.418468] wlan0: send auth to <MAC address removed> (try 1/3)
[   65.420284] wlan0: authenticated
[   65.424059] wlan0: associate with <MAC address removed> (try 1/3)
[   65.426451] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   65.426455] wlan0: <MAC address removed> denied association (code=18)
[   65.437083] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   67.572539] wlan0: authenticate with <MAC address removed>
[   67.574486] wlan0: send auth to <MAC address removed> (try 1/3)
[   67.576323] wlan0: authenticated
[   67.580076] wlan0: associate with <MAC address removed> (try 1/3)
[   67.582481] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   67.582485] wlan0: <MAC address removed> denied association (code=18)
[   67.588694] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   69.727081] wlan0: authenticate with <MAC address removed>
[   69.728792] wlan0: send auth to <MAC address removed> (try 1/3)
[   69.730609] wlan0: authenticated
[   69.733001] wlan0: associate with <MAC address removed> (try 1/3)
[   69.735398] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   69.735403] wlan0: <MAC address removed> denied association (code=18)
[   69.752260] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)

****************** done ******************


```

---

### Post by varunendra on 2014-03-02
> **chele-modica said:**
> ```

***** iwlist *****

[COLOR="#FF0000"]Aquiring of root rights failed.[/COLOR]

```
It seems you didn't provide your password when sudo command asked for it. So I can't see your router's configuration and therefore can't suggest if something needs to be optimized there.

Apart from that, the rest of the setup looks good. Please try the commands suggested in post #4 first, and if they don't seem to help, try the commands in post #10.

These commands will temporarily load certain parameters with the drivers that may sometimes help. If they do, please confirm which one(s) worked and we'll make them permanent.

If not, please run the script again, supply your login password when asked (if running the script from terminal, you won't see any characters while typing the password, just type in correctly and press 'Enter'). That will generate a fresh report showing your router's channel and encryption settings too.

Post that new report, and along with that, please also post the output of the "grep -R.." command as asked in post #4.

---

### Post by pdcastro on 2014-06-28
Hello,
I'm experienced same problem "Although network manager sees the wifi, when I choose to connect to it,  it keeps asking for the password (and the password is correct)".
I tried running codes in post #4 without success.
Here's the output given by the script "wget -N -t 5 -T 10 [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script) && chmod +x wireless_script && ./wireless_script"
Thanks in advanced by your help.

---

### Post by pdcastro on 2014-06-28
I want to add that is a new installed 14.04. It didn't connected even in the install process.

---

### Post by varunendra on 2014-06-28
Welcome to the forums pdcastro!

Please edit your first post to wrap the report part within 'Code' tags. It preserves the formatting, and makes the outputs more readable.

Your router is using WPA/WPA2 mixed mode encryption. Usually we recommend pure WPA2-PSK with AES (not TKIP), but since your card is pretty old, please try the encryption combinations in the following order (change to one > save & reboot both router & laptop > try to connect > try next if no success).

1) WPA2 with AES (CCMP)
2) WPA with AES (CCMP)
3) WPA with TKIP

Reboot the router everytime you make and save a change, just to be sure the change takes effect properly.

While trying these encryption types, please fix the channel in the router to 1 or 11. Currently it is set to 6 (or maybe "auto" in the router). Also try the commands in post #4 with each combination.

---

### Post by pdcastro on 2014-06-29
Varum,
Thanks for your quick reply. Sadly, I tried the steps just as you said with no success. Lately I made a factory reset of the router, but it didn't improve the situation. I attached the output of the script again.
Thanks,
Pablo

---

### Post by varunendra on 2014-06-29
Please post the report generated by a new, experimental version of the wireless script, since it provides much more info. Please follow the instructions in this post to download and run it : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

### Post by jeremy31 on 2014-06-29
Does the setting from ```
iw reg get
``` even matter, or the setting in /etc/default/crda?  It seems that the default is 00 for both and 00 equates to the US which is nice for anyone in the US.  And then there is even a parameter in cfg80211 called ieee80211_regdom.  I did find a listing once for all the countries but can't seem to find it.

Just asking because I had a Sony Vaio laptop with the 3945 and it worked without any issue

---

### Post by pdcastro on 2014-06-29
Varun,
Here's the report generated by the new script.

Thanks,
Pablo

---

### Post by varunendra on 2014-06-30
@ Pablo,

Please try defining your country code ('AR' - guessing from your language code) for regdomain settings. The command line way to do so is -
```
sudo sed -i 's/^REG.*=$/&AR/' /etc/default/crda
```
Reboot and check -
```
iw reg get
```
It should show settings for 'AR', as against '00' which it has currently defaulted to. Also log into your router and make sure its region setting is set to 'AR' (Argentina?). Some routers may not show this setting, or allow changing it, in which case just report back if you can confirm the regional setting of the router or not.

Apart from that, also set "IPv6" in Network Manager to "Ignore" > Save > Close.

If these don't help, there are a few more things we may try, but I rarely use them and not very sure in which order/combination to use them. So try these in the order given here -
```
sudo modprobe -rv iwl3945
sudo modprobe -v iwl3945 disable_hw_scan=0
```
Or, try increasing the AP response waiting time -
```
sudo modprobe -rv iwl3945
sudo modprobe -v mac80211 probe_wait_ms=2000
sudo modprobe -v iwl3945
```

You may also try some or all of these parameters in combination such as follows -
```
sudo modprobe -rv iwl3945
sudo modprobe -v mac80211 probe_wait_ms=2000
sudo modprobe -v iwlegacy bt_coex_active=N
sudo modprobe -v iwl3945 swcrypto=1 disable_hw_scan=0
```
..although I doubt that is going to help, unless there are multiple problems which the script report can't show.


@ jeremy31,
> **jeremy31 said:**
> Does the setting from ```
iw reg get
``` even matter, or the setting in /etc/default/crda?
I don't know for sure, I believe it does. Please see a discussion we are having on this here : [http://ubuntuforums.org/showthread.php?t=2230811&p=13061444#post13061444](http://ubuntuforums.org/showthread.php?t=2230811&p=13061444#post13061444)

> It seems that the default is 00 for both and 00 equates to the US which is nice for anyone in the US.
Not exactly same as US, but yes, the 2.4xx GHz range is almost exactly covered in the defaulted (00) settings. The range 2.457 - 2.472 GHz has double settings in the defaulted mode (both 40 MHz allowed and 20 MHz restricted) which may be okay for US, but I have my doubts. The 5 GHz channels have other restrictions like Passive Scan, No IBSS etc. in the defaulted mode, whereas the 'US' settings don't seem to have such restrictions.

> And then there is even a parameter in cfg80211 called ieee80211_regdom.
That is just an alternative way provided in case you wish (or have to) force a regdomain setting via the driver. This is one thing that I am really sure about. :)

> I did find a listing once for all the countries but can't seem to find it.
Just for country codes, an online source is [wikipedia]("http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2#Decoding_table"), and offline source is "**/usr/share/zoneinfo/zone.tab**" file in Ubuntu installation.

The corresponding settings are stored in "**/lib/crda/regulatory.bin**" file which is a binary file so that the system can quickly read it. To show its contents in human readable form, one has to use "regdbdump" command -
```
regdbdump /lib/crda/regulatory.bin
```
or,
```
regdbdump /lib/crda/regulatory.bin | less
```
(piping the output to "less", so you can scroll and see the whole output).

If you are interested, and/or have something to add to our knowledge regarding this, please join us in the above linked thread.

---

### Post by pdcastro on 2014-06-30
@Varun,
Well, still I have no luck. I change to AR and set IPv6 to ignore, as you told me. The router only let me choose US. I tried with it. Also I change it's firmware ([http://downloadcenter.netgear.com/en/product/WGT624v3](http://downloadcenter.netgear.com/en/product/WGT624v3)) and I was able to set the router to "South America". I tried every code again. No connection achieved. I attach the result of the script I run again. Thanks again!

---

### Post by jeremy31 on 2014-07-01
> **pdcastro said:**
> @Varun,
Well, still I have no luck. I change to AR and set IPv6 to ignore, as you told me. The router only let me choose US. I tried with it. Also I change it's firmware ([http://downloadcenter.netgear.com/en/product/WGT624v3](http://downloadcenter.netgear.com/en/product/WGT624v3)) and I was able to set the router to "South America". I tried every code again. No connection achieved. I attach the result of the script I run again. Thanks again!

I advised someone to upgrade the kernel on another forum the other day and someone who had this same card posted back and said it fixed their problem.  If you are interested in upgrading the kernel, here are the commands to run in terminal
```
[COLOR=#2E8B57][FONT=Monaco]wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.15.2-utopic/linux-headers-3.15.2-031502-generic_3.15.2-031502.201406261639_amd64.deb[/FONT][/COLOR]
```
```
[COLOR=#2E8B57][FONT=Monaco]wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.15.2-utopic/linux-headers-3.15.2-031502_3.15.2-031502.201406261639_all.deb[/FONT][/COLOR]
```
```
[COLOR=#2E8B57][FONT=Monaco]wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.15.2-utopic/linux-image-3.15.2-031502-generic_3.15.2-031502.201406261639_amd64.deb[/FONT][/COLOR]
```
```
[COLOR=#2E8B57][FONT=Monaco]sudo dpkg -i linux-*-3.15.2*.deb[/FONT][/COLOR]
```
and reboot

There is a chance that the router may be too old or be a bit buggy.  After updating the Android version on my cell phone it would refuse to connect to my router.  Put a new router in and problem was fixed

---

### Post by pdcastro on 2014-07-02
@Varun,
Great news! Yesterday I didn't turn on the notebook nor see your last post. Today it connected right away. I guess it was needed one last reboot. For the record, I didn't do anything explained in post #27.

I'm just happy.
Thanks,
P.

---

### Post by varunendra on 2014-07-04
Glad it worked, whatever did it. ;)

---

### Post by pdcastro on 2014-07-06
The story continued: the connection is lost every half an hour aprox. So I upgraded the kernel as it is said in post #27. After booting the screen is black: it seems that after a strange screen full of colored pixels it arrives to the login screen (I can hear the sound), but the only thing I could do is shut it down. I downgraded the kernel to the previous version. So, back to square two: connected but intermittently. And as I downgraded the router firmware to the one that matches my region, all devices connected to it have some problems browsing (the latest version solved this issues but it supports only US region). Really, I'm regreating having left Debian Wheezy (some limitations on software, ok, but it worked fine, no need to buy any new hardware). If it weren't for these community I wouldn't be thinking in spending more time giving Ubuntu a last try. Let's leave this threat here. I appreciate truely all your efforts. Thanks.

---

### Post by jeremy31 on 2014-07-06
> **pdcastro said:**
> The story continued: the connection is lost every half an hour aprox. So I upgraded the kernel as it is said in post #27. After booting the screen is black: it seems that after a strange screen full of colored pixels it arrives to the login screen (I can hear the sound), but the only thing I could do is shut it down. I downgraded the kernel to the previous version. So, back to square two: connected but intermittently. And as I downgraded the router firmware to the one that matches my region, all devices connected to it have some problems browsing (the latest version solved this issues but it supports only US region). Really, I'm regreating having left Debian Wheezy (some limitations on software, ok, but it worked fine, no need to buy any new hardware). If it weren't for these community I wouldn't be thinking in spending more time giving Ubuntu a last try. Let's leave this threat here. I appreciate truely all your efforts. Thanks.

Can you post the results of ```
lsmod
```

---

