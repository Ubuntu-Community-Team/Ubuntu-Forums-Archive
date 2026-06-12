---
title: "Wifi connection Problems Ubuntu 20"
date: 2021-06-23
forum: Networking &amp; Wireless
---

### Post by gerbio on 2021-06-23
Hi, my name is Gerson and I'm facing a problem in my Wifi connection here in Brazil.
My computer is an ASUS Z55OS with Ubuntu 20.04.
I lost my connection on friday and couldn't solve the problem until now. I even upgraded to Ubuntu 20.10 holping to replace some corrupted files or plugins for new ones, but I didn't succeed.
Running the troubleshoot I discovered that my network hardware is perfect and is recognized by the program:

**$ lscpi**
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5286 PCI Express Card Reader (rev 01)
03:00.2 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL810xE PCI Express Fast Ethernet controller (rev 06)

**$ lshw -c network**
AVISO: você deveria executar este programa como superusuário.
*-network
descrição: Interface sem fio
produto: RTL8723BE PCIe Wireless Network Adapter
fabricante: Realtek Semiconductor Co., Ltd.
ID físico: 0
informações do barramento: pci@0000:02:00.0
***nome lógico: wlp2s0***
versão: 00
serial: 70:4d:7b:cf:82:31
largura: 64 bits
clock: 33MHz
capacidades: bus_master cap_list ethernet physical wireless
configuração: broadcast=yes driver=rtl8723be driverversion=5.8.0-55-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11
recursos: irq:17 porta de E/S:e000(tamanho=256) memória:81300000-81303fff

*-network
descrição: Ethernet interface
produto: RTL810xE PCI Express Fast Ethernet controller
fabricante: Realtek Semiconductor Co., Ltd.
ID físico: 0.2
informações do barramento: pci@0000:03:00.2
nome lógico: enp3s0f2
versão: 06
serial: 70:4d:7b:cf:d7:bc
tamanho: 100Mbit/s
capacidade: 100Mbit/s
largura: 64 bits
clock: 33MHz
capacidades: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuração: autonegotiation=on broadcast=yes driver=r8169 driverversion=5.8.0-55-generic duplex=full firmware=rtl8402-1_0.0.1 10/26/11 ip=192.168.15.8 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
recursos: irq:19 porta de E/S:d000(tamanho=256) memória:81210000-81210fff memória:a0000000-a0003fff
AVISO: a saída pode ser incompleta e imprecisa, você deveria executar este programa como superusuário.

[B]$ lsmod
[/B](...)
realtek 24576 1
[B]
$ sudo iwconfig[/B]
lo no wireless extensions.

enp3s0f2 no wireless extensions.

wlp2s0 IEEE 802.11 ESSID:off/any
Mode:Managed Access Point: Not-Associated Tx-Power=20 dBm
Retry short limit:7 RTS thr=2347 B Fragment thr:off
Encryption key:off
Power Management:on

**$ sudo iwlist scanning**
lo Interface doesn't support scanning.

enp3s0f2 Interface doesn't support scanning.

wlp2s0 Scan completed :
Cell 01 - Address: F4:54:20:74:51:3F
Channel:1
Frequency:2.412 GHz (Channel 1)
Quality=34/70 Signal level=-76 dBm
Encryption key:on
ESSID:"VIVOFIBRA-5131"
Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=000000253296d75a
Extra: Last beacon: 884ms ago
IE: Unknown: 000E5649564F46494252412D35313331
IE: Unknown: 01080C1218243048606C
IE: Unknown: 030101
IE: Unknown: 0706425220010D14
IE: Unknown: 050402030020
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : CCMP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : PSK
IE: Unknown: DD310050F204104A000110104400010210470010BC329E001DD811B28601F4542074513F103C0001011049000600372A000120
IE: Unknown: 2D1A2C0017FFFF000000000000000000000000000000000000000000
IE: Unknown: 3D1601000700000000000000000000000000000000000000
IE: Unknown: 7F080000080000000000
IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
IE: Unknown: DD07000C4300000000

**$ rfkill list**
0: hci0: Bluetooth
Soft blocked: yes
Hard blocked: no

1: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no

**$ lshw**
*-network
descrição: Interface sem fio
produto: RTL8723BE PCIe Wireless Network Adapter
fabricante: Realtek Semiconductor Co., Ltd.
ID físico: 0
informações do barramento: pci@0000:02:00.0
nome lógico: wlp2s0
versão: 00
serial: 70:4d:7b:cf:82:31
largura: 64 bits
clock: 33MHz
capacidades: bus_master cap_list ethernet physical wireless
configuração: broadcast=yes driver=rtl8723be driverversion=5.8.0-55-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11
recursos: irq:17 porta de E/S:e000(tamanho=256) memória:81300000-81303fff

*-network
descrição: Ethernet interface
produto: RTL810xE PCI Express Fast Ethernet controller
fabricante: Realtek Semiconductor Co., Ltd.
ID físico: 0.2
informações do barramento: pci@0000:03:00.2
nome lógico: enp3s0f2
versão: 06
serial: 70:4d:7b:cf:d7:bc
tamanho: 100Mbit/s
capacidade: 100Mbit/s
largura: 64 bits
clock: 33MHz
capacidades: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuração: autonegotiation=on broadcast=yes driver=r8169 driverversion=5.8.0-55-generic duplex=full firmware=rtl8402-1_0.0.1 10/26/11 ip=192.168.15.8 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
recursos: irq:19 porta de E/S:d000(tamanho=256) memória:81210000-81210fff memória:a0000000-a0003fff
*-isa
descrição: ISA bridge
produto: Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series

**$ sudo systemctl restart network-manager**
Failed to restart network-manager.service: Unit network-manager.service not found.

**$ sudo modprobe -r wl**
libkmod: ERROR ../libkmod/libkmod-config.c:657 kmod_config_parse: /etc/modprobe.d/rt18723be.conf line 1: ignoring bad line starting with 'options'
modprobe: FATAL: Module wl not found.

**$ sudo dmesg | grep brcm**
**$ sudo modprobe brcmfmac**
libkmod: ERROR ../libkmod/libkmod-config.c:657 kmod_config_parse: /etc/modprobe.d/rt18723be.conf line 1: ignoring bad line starting with 'options'

**$ sudo dmesg | grep -e brcm -e 03:00**
[ 0.332490] pci 0000:03:00.0: [10ec:5286] type 00 class 0xff0000
[ 0.332533] pci 0000:03:00.0: reg 0x10: [mem 0x81200000-0x8120ffff]
[ 0.332757] pci 0000:03:00.0: supports D1 D2
[ 0.332760] pci 0000:03:00.0: PME# supported from D1 D2 D3hot D3cold
[ 0.333029] pci 0000:03:00.2: [10ec:8136] type 00 class 0x020000
[ 0.333071] pci 0000:03:00.2: reg 0x10: [io 0xd000-0xd0ff]
[ 0.333111] pci 0000:03:00.2: reg 0x18: [mem 0x81210000-0x81210fff 64bit]
[ 0.333137] pci 0000:03:00.2: reg 0x20: [mem 0xa0000000-0xa0003fff 64bit pref]
[ 0.333278] pci 0000:03:00.2: supports D1 D2
[ 0.333281] pci 0000:03:00.2: PME# supported from D0 D1 D2 D3hot D3cold
[ 2.259930] r8169 0000:03:00.2 eth0: RTL8402, 70:4d:7b:cf:d7:bc, XID 440, IRQ 122
[ 2.352601] r8169 0000:03:00.2 enp3s0f2: renamed from eth0
[ 12.705841] r8169 0000:03:00.2 enp3s0f2: Link is Down
[ 374.501796] r8169 0000:03:00.2 enp3s0f2: Link is Up - 100Mbps/Full - flow control rx/tx
[ 374.683247] r8169 0000:03:00.2 enp3s0f2: Link is Down
[ 376.252872] r8169 0000:03:00.2 enp3s0f2: Link is Up - 100Mbps/Full - flow control rx/tx
[ 376.417300] r8169 0000:03:00.2 enp3s0f2: Link is Down
[ 377.983143] r8169 0000:03:00.2 enp3s0f2: Link is Up - 100Mbps/Full - flow control rx/tx
[ 2267.879222] usbcore: registered new interface driver brcmfmac

What do I do to fix my wifi connection? I don't know what to do, since I discovered this "libkmod" is preventing my laptopto make correct actualizations for the Wifi card and internet modules.
Sorry it's too long message, but I guess if I'm able to share the complete situation it will be easier to solve my problem.
Thanks for this opportunity

---

### Post by chili555 on 2021-06-23
> $ sudo modprobe -r wl
libkmod: ERROR ../libkmod/libkmod-config.c:657 kmod_config_parse: /etc/modprobe.d/rt18723be.conf line 1: ignoring bad line starting with 'options'
modprobe: FATAL: Module wl not found.

$ sudo dmesg | grep brcm
$ sudo modprobe brcmfmac
libkmod: ERROR ../libkmod/libkmod-config.c:657 kmod_config_parse: /etc/modprobe.d/rt18723be.conf line 1: ignoring bad line starting with 'options'

$ sudo dmesg | grep -e brcm -e 03:00
The drivers wl and brcmfmac are for Broadcom devices; yours is a Realtek. Those readings are not useful.

This, however is useful:> kmod_config_parse: /etc/modprobe.d/rt18723be.conf line 1: ignoring bad line starting with 'options'That suggests that there is a faulty line in the file. Let's have a look:

```
cat /etc/modprobe.d/rt18723be.conf 
```Thanks.

---

### Post by gerbio on 2021-06-25
**$ kmod_config_parse: /etc/modprobe.d/rt18723be.conf line 1: ignoring bad line starting with 'options'**
kmod_config_parse:: comando não encontrado

**$ cat /etc/modprobe.d/rt18723be.conf**
options fwips=N

That is my Laptop answer. 
Thanks for helping me out.

---

### Post by chili555 on 2021-06-25
> options fwips=NThe parameter is fwlps not fwips. The operator is 1 or  0. From modinfo rtl8723be:

```
parm:           fwlps:Set to 1 to use FW control power save (default 1) (bool)
```While I doubt that this is the soluton to the underlying issue, Let's amend the file to read:

```
options rtl8723be fwlps=0
```Unload and reload the module:

```
sudo modprobe -r rtl8723be
sudo modprobe rtl8723be  fwlps=0

```
I doubt that there is any improvement, but we'll get rid of the error.

Please try to connect and then show us:

```
sudo dmesg | grep -ie rtl -ie wlp
nmcli device wifi list
```

---

### Post by gerbio on 2021-06-25
**$ sudo dmesg | grep -ie rtl -ie wlp**
[    1.942992] r8169 0000:03:00.2 eth0: RTL8402, 70:4d:7b:cf:d7:bc, XID 440, IRQ 122
[    6.354378] Bluetooth: hci0: RTL: examining hci_ver=06 hci_rev=000b lmp_ver=06 lmp_subver=8723
[    6.355346] Bluetooth: hci0: RTL: rom_version status=0 version=1
[    6.355350] Bluetooth: hci0: RTL: loading rtl_bt/rtl8723b_fw.bin
[    6.408088] Bluetooth: hci0: RTL: loading rtl_bt/rtl8723b_config.bin
[    6.408157] bluetooth hci0: Direct firmware load for rtl_bt/rtl8723b_config.bin failed with error -2
[    6.408178] Bluetooth: hci0: RTL: cfg_sz -2, total sz 22496
[    6.709537] rtl8723be: Using firmware rtlwifi/rtl8723befw_36.bin
[    6.718595] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    6.719907] rtlwifi: rtlwifi: wireless switch is on
[    7.220383] Bluetooth: hci0: RTL: fw version 0x0e2f9f73
[    7.589645] rtl8723be 0000:02:00.0 wlp2s0: renamed from wlan0
[   12.428256] RTL8208 Fast Ethernet r8169-302:00: attached PHY driver [RTL8208 Fast Ethernet] (mii_bus:phy_addr=r8169-302:00, irq=IGNORE)
[   18.508201] wlp2s0: authenticate with f4:54:20:74:51:3f
[   18.508214] wlp2s0: No basic rates, using min rate instead
[   18.518521] wlp2s0: send auth to f4:54:20:74:51:3f (try 1/3)
[   18.538728] wlp2s0: authenticated
[   18.541052] wlp2s0: associate with f4:54:20:74:51:3f (try 1/3)
[   18.644970] wlp2s0: associate with f4:54:20:74:51:3f (try 2/3)
[   18.749030] wlp2s0: associate with f4:54:20:74:51:3f (try 3/3)
[   18.853025] wlp2s0: association with f4:54:20:74:51:3f timed out
[   25.873223] wlp2s0: authenticate with f4:54:20:74:51:3f
[   25.873249] wlp2s0: No basic rates, using min rate instead
[   25.890084] wlp2s0: send auth to f4:54:20:74:51:3f (try 1/3)
[   25.903743] wlp2s0: authenticated
[   25.905124] wlp2s0: associate with f4:54:20:74:51:3f (try 1/3)
[   26.009319] wlp2s0: associate with f4:54:20:74:51:3f (try 2/3)
[   26.018751] wlp2s0: RX AssocResp from f4:54:20:74:51:3f (capab=0xc11 status=0 aid=5)
[   26.019090] wlp2s0: associated
[   32.121274] wlp2s0: deauthenticated from f4:54:20:74:51:3f (Reason: 15=4WAY_HANDSHAKE_TIMEOUT)
[   33.235516] wlp2s0: authenticate with f4:54:20:74:51:3f
[   33.235527] wlp2s0: No basic rates, using min rate instead
[   33.249590] wlp2s0: send auth to f4:54:20:74:51:3f (try 1/3)
[   33.356971] wlp2s0: send auth to f4:54:20:74:51:3f (try 2/3)
[   33.460985] wlp2s0: send auth to f4:54:20:74:51:3f (try 3/3)
[   33.564990] wlp2s0: authentication with f4:54:20:74:51:3f timed out
[   41.522151] wlp2s0: authenticate with f4:54:20:74:51:3f
[   41.522162] wlp2s0: No basic rates, using min rate instead
[   41.551373] wlp2s0: send auth to f4:54:20:74:51:3f (try 1/3)
[   41.656969] wlp2s0: send auth to f4:54:20:74:51:3f (try 2/3)
[   41.765147] wlp2s0: send auth to f4:54:20:74:51:3f (try 3/3)
[   41.872992] wlp2s0: authentication with f4:54:20:74:51:3f timed out
[  281.999343] wlp2s0: authenticate with f4:54:20:74:51:3f
[  281.999356] wlp2s0: No basic rates, using min rate instead
[  282.015281] wlp2s0: send auth to f4:54:20:74:51:3f (try 1/3)
[  282.116309] wlp2s0: send auth to f4:54:20:74:51:3f (try 2/3)
[  282.220732] wlp2s0: send auth to f4:54:20:74:51:3f (try 3/3)
[  282.324523] wlp2s0: authentication with f4:54:20:74:51:3f timed out
[  293.325977] wlp2s0: authenticate with f4:54:20:74:51:3f
[  293.325994] wlp2s0: No basic rates, using min rate instead
[  293.347751] wlp2s0: send auth to f4:54:20:74:51:3f (try 1/3)
[  293.448232] wlp2s0: send auth to f4:54:20:74:51:3f (try 2/3)
[  293.556222] wlp2s0: send auth to f4:54:20:74:51:3f (try 3/3)
[  293.660385] wlp2s0: authentication with f4:54:20:74:51:3f timed out
[  309.084641] wlp2s0: authenticate with f4:54:20:74:51:3f
[  309.084655] wlp2s0: No basic rates, using min rate instead
[  309.101256] wlp2s0: send auth to f4:54:20:74:51:3f (try 1/3)
[  309.204318] wlp2s0: send auth to f4:54:20:74:51:3f (try 2/3)
[  309.308509] wlp2s0: send auth to f4:54:20:74:51:3f (try 3/3)
[  309.412509] wlp2s0: authentication with f4:54:20:74:51:3f timed out
[  326.385245] wlp2s0: authenticate with f4:54:20:74:51:3f
[  326.385259] wlp2s0: No basic rates, using min rate instead
[  326.414192] wlp2s0: send auth to f4:54:20:74:51:3f (try 1/3)
[  326.520374] wlp2s0: send auth to f4:54:20:74:51:3f (try 2/3)
[  326.624464] wlp2s0: send auth to f4:54:20:74:51:3f (try 3/3)
[  326.728137] wlp2s0: authentication with f4:54:20:74:51:3f timed out
[  336.080232] wlp2s0: authenticate with f4:54:20:74:51:3f
[  336.080245] wlp2s0: No basic rates, using min rate instead
[  336.091170] wlp2s0: send auth to f4:54:20:74:51:3f (try 1/3)
[  336.119624] wlp2s0: authenticated
[  336.132164] wlp2s0: associate with f4:54:20:74:51:3f (try 1/3)
[  336.236159] wlp2s0: associate with f4:54:20:74:51:3f (try 2/3)
[  336.340206] wlp2s0: associate with f4:54:20:74:51:3f (try 3/3)
[  336.444184] wlp2s0: association with f4:54:20:74:51:3f timed out
[  347.433807] wlp2s0: authenticate with f4:54:20:74:51:3f
[  347.433820] wlp2s0: No basic rates, using min rate instead
[  347.455093] wlp2s0: send auth to f4:54:20:74:51:3f (try 1/3)
[  347.556084] wlp2s0: send auth to f4:54:20:74:51:3f (try 2/3)
[  347.660029] wlp2s0: send auth to f4:54:20:74:51:3f (try 3/3)
[  347.764521] wlp2s0: authentication with f4:54:20:74:51:3f timed out
[  863.065198] wlp2s0: authenticate with f4:54:20:74:51:3f
[  863.065211] wlp2s0: No basic rates, using min rate instead
[  863.084042] wlp2s0: send auth to f4:54:20:74:51:3f (try 1/3)
[  863.187763] wlp2s0: send auth to f4:54:20:74:51:3f (try 2/3)
[  863.291894] wlp2s0: send auth to f4:54:20:74:51:3f (try 3/3)
[  863.399425] wlp2s0: authentication with f4:54:20:74:51:3f timed out
[  874.377739] wlp2s0: authenticate with f4:54:20:74:51:3f
[  874.377753] wlp2s0: No basic rates, using min rate instead
[  874.396332] wlp2s0: send auth to f4:54:20:74:51:3f (try 1/3)
[  874.419192] wlp2s0: authenticated
[  874.423352] wlp2s0: associate with f4:54:20:74:51:3f (try 1/3)
[  874.527512] wlp2s0: associate with f4:54:20:74:51:3f (try 2/3)
[  874.631408] wlp2s0: associate with f4:54:20:74:51:3f (try 3/3)
[  874.739353] wlp2s0: association with f4:54:20:74:51:3f timed out
[  890.233093] wlp2s0: authenticate with f4:54:20:74:51:3f
[  890.233111] wlp2s0: No basic rates, using min rate instead
[  890.252063] wlp2s0: send auth to f4:54:20:74:51:3f (try 1/3)
[  890.355445] wlp2s0: send auth to f4:54:20:74:51:3f (try 2/3)
[  890.372860] wlp2s0: authenticated
[  890.375389] wlp2s0: associate with f4:54:20:74:51:3f (try 1/3)
[  890.479481] wlp2s0: associate with f4:54:20:74:51:3f (try 2/3)
[  890.583471] wlp2s0: associate with f4:54:20:74:51:3f (try 3/3)
[  890.687317] wlp2s0: association with f4:54:20:74:51:3f timed out
[  955.433117] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready
[ 1026.879183] wlp2s0: authenticate with f4:54:20:74:51:3f
[ 1026.879195] wlp2s0: No basic rates, using min rate instead
[ 1027.383348] wlp2s0: send auth to f4:54:20:74:51:3f (try 1/3)
[ 1027.398452] wlp2s0: authenticated
[ 1027.399039] wlp2s0: associate with f4:54:20:74:51:3f (try 1/3)
[ 1027.409143] wlp2s0: RX AssocResp from f4:54:20:74:51:3f (capab=0xc11 status=0 aid=5)
[ 1027.409442] wlp2s0: associated
[ 1028.819789] wlp2s0: deauthenticating from f4:54:20:74:51:3f by local choice (Reason: 3=DEAUTH_LEAVING)
[ 1028.960463] wlp2s0: authenticate with f4:54:20:74:51:3f
[ 1028.960476] wlp2s0: No basic rates, using min rate instead
[ 1029.465115] wlp2s0: send auth to f4:54:20:74:51:3f (try 1/3)
[ 1029.566992] wlp2s0: send auth to f4:54:20:74:51:3f (try 2/3)
[ 1029.581246] wlp2s0: authenticated
[ 1029.583066] wlp2s0: associate with f4:54:20:74:51:3f (try 1/3)
[ 1029.596117] wlp2s0: RX AssocResp from f4:54:20:74:51:3f (capab=0xc11 status=0 aid=5)
[ 1029.596404] wlp2s0: associated
[ 1035.702872] wlp2s0: deauthenticated from f4:54:20:74:51:3f (Reason: 15=4WAY_HANDSHAKE_TIMEOUT)
[ 1036.825861] wlp2s0: authenticate with f4:54:20:74:51:3f
[ 1036.825879] wlp2s0: No basic rates, using min rate instead
[ 1036.843687] wlp2s0: send auth to f4:54:20:74:51:3f (try 1/3)
[ 1036.858772] wlp2s0: authenticated
[ 1036.863012] wlp2s0: associate with f4:54:20:74:51:3f (try 1/3)
[ 1036.971019] wlp2s0: associate with f4:54:20:74:51:3f (try 2/3)
[ 1036.987624] wlp2s0: RX AssocResp from f4:54:20:74:51:3f (capab=0xc11 status=0 aid=5)
[ 1036.987946] wlp2s0: associated
[ 1043.092708] wlp2s0: deauthenticated from f4:54:20:74:51:3f (Reason: 15=4WAY_HANDSHAKE_TIMEOUT)
[ 1044.675997] wlp2s0: authenticate with f4:54:20:74:51:3f
[ 1044.676009] wlp2s0: No basic rates, using min rate instead
[ 1044.697536] wlp2s0: send auth to f4:54:20:74:51:3f (try 1/3)
[ 1044.799177] wlp2s0: send auth to f4:54:20:74:51:3f (try 2/3)
[ 1044.903420] wlp2s0: send auth to f4:54:20:74:51:3f (try 3/3)
[ 1045.007398] wlp2s0: authentication with f4:54:20:74:51:3f timed out
[ 1380.964274] wlp2s0: authenticate with f4:54:20:74:51:3f
[ 1380.964287] wlp2s0: No basic rates, using min rate instead
[ 1380.984391] wlp2s0: send auth to f4:54:20:74:51:3f (try 1/3)
[ 1381.086486] wlp2s0: send auth to f4:54:20:74:51:3f (try 2/3)
[ 1381.194677] wlp2s0: send auth to f4:54:20:74:51:3f (try 3/3)
[ 1381.302639] wlp2s0: authentication with f4:54:20:74:51:3f timed out
[ 1391.303393] wlp2s0: authenticate with f4:54:20:74:51:3f
[ 1391.303414] wlp2s0: No basic rates, using min rate instead
[ 1391.313693] wlp2s0: send auth to f4:54:20:74:51:3f (try 1/3)
[ 1391.335077] wlp2s0: authenticated
[ 1391.343059] wlp2s0: associate with f4:54:20:74:51:3f (try 1/3)
[ 1391.384161] wlp2s0: RX AssocResp from f4:54:20:74:51:3f (capab=0xc11 status=0 aid=6)
[ 1391.384495] wlp2s0: associated
[ 1401.386651] wlp2s0: deauthenticating from f4:54:20:74:51:3f by local choice (Reason: 3=DEAUTH_LEAVING)
[ 1412.655422] wlp2s0: authenticate with f4:54:20:74:51:3f
[ 1412.655443] wlp2s0: No basic rates, using min rate instead
[ 1412.671123] wlp2s0: send auth to f4:54:20:74:51:3f (try 1/3)
[ 1412.774415] wlp2s0: send auth to f4:54:20:74:51:3f (try 2/3)
[ 1412.878504] wlp2s0: send auth to f4:54:20:74:51:3f (try 3/3)
[ 1412.982420] wlp2s0: authentication with f4:54:20:74:51:3f timed out
[ 1497.973211] wlp2s0: authenticate with f4:54:20:74:51:3f
[ 1497.973233] wlp2s0: No basic rates, using min rate instead
[ 1497.991264] wlp2s0: send auth to f4:54:20:74:51:3f (try 1/3)
[ 1498.094740] wlp2s0: send auth to f4:54:20:74:51:3f (try 2/3)
[ 1498.198340] wlp2s0: send auth to f4:54:20:74:51:3f (try 3/3)
[ 1498.302335] wlp2s0: authentication with f4:54:20:74:51:3f timed out
[ 1509.304815] wlp2s0: authenticate with f4:54:20:74:51:3f
[ 1509.304840] wlp2s0: No basic rates, using min rate instead
[ 1509.325330] wlp2s0: send auth to f4:54:20:74:51:3f (try 1/3)
[ 1509.426237] wlp2s0: send auth to f4:54:20:74:51:3f (try 2/3)
[ 1509.530296] wlp2s0: send auth to f4:54:20:74:51:3f (try 3/3)
[ 1509.634214] wlp2s0: authentication with f4:54:20:74:51:3f timed out
[ 1880.462687] wlp2s0: authenticate with f4:54:20:74:51:3f
[ 1880.462700] wlp2s0: No basic rates, using min rate instead
[ 1880.482167] wlp2s0: send auth to f4:54:20:74:51:3f (try 1/3)
[ 1880.543713] wlp2s0: authenticated
[ 1880.545379] wlp2s0: associate with f4:54:20:74:51:3f (try 1/3)
[ 1880.560338] wlp2s0: RX AssocResp from f4:54:20:74:51:3f (capab=0xc11 status=0 aid=6)
[ 1880.560629] wlp2s0: associated
[ 1886.665175] wlp2s0: deauthenticated from f4:54:20:74:51:3f (Reason: 15=4WAY_HANDSHAKE_TIMEOUT)
[ 1897.725172] wlp2s0: authenticate with f4:54:20:74:51:3f
[ 1897.725187] wlp2s0: No basic rates, using min rate instead
[ 1897.742419] wlp2s0: send auth to f4:54:20:74:51:3f (try 1/3)
[ 1897.756512] wlp2s0: authenticated
[ 1897.758362] wlp2s0: associate with f4:54:20:74:51:3f (try 1/3)
[ 1897.861425] wlp2s0: associate with f4:54:20:74:51:3f (try 2/3)
[ 1897.879443] wlp2s0: RX AssocResp from f4:54:20:74:51:3f (capab=0xc11 status=0 aid=6)
[ 1897.879888] wlp2s0: associated
[ 1903.978665] wlp2s0: deauthenticated from f4:54:20:74:51:3f (Reason: 15=4WAY_HANDSHAKE_TIMEOUT)
[ 4980.694764] wlp2s0: authenticate with f4:54:20:74:51:3f
[ 4980.694776] wlp2s0: No basic rates, using min rate instead
[ 4981.202394] wlp2s0: send auth to f4:54:20:74:51:3f (try 1/3)
[ 4981.304056] wlp2s0: send auth to f4:54:20:74:51:3f (try 2/3)
[ 4981.408225] wlp2s0: send auth to f4:54:20:74:51:3f (try 3/3)
[ 4981.516081] wlp2s0: authentication with f4:54:20:74:51:3f timed out
[ 5036.043050] wlp2s0: authenticate with f4:54:20:74:51:3f
[ 5036.043062] wlp2s0: No basic rates, using min rate instead
[ 5036.053297] wlp2s0: send auth to f4:54:20:74:51:3f (try 1/3)
[ 5036.156168] wlp2s0: send auth to f4:54:20:74:51:3f (try 2/3)
[ 5036.260350] wlp2s0: send auth to f4:54:20:74:51:3f (try 3/3)
[ 5036.365434] wlp2s0: authentication with f4:54:20:74:51:3f timed out
[ 5047.365801] wlp2s0: authenticate with f4:54:20:74:51:3f
[ 5047.365813] wlp2s0: No basic rates, using min rate instead
[ 5047.385345] wlp2s0: send auth to f4:54:20:74:51:3f (try 1/3)
[ 5047.488252] wlp2s0: send auth to f4:54:20:74:51:3f (try 2/3)
[ 5047.592265] wlp2s0: send auth to f4:54:20:74:51:3f (try 3/3)
[ 5047.696062] wlp2s0: authentication with f4:54:20:74:51:3f timed out
[ 5067.031096] wlp2s0: authenticate with f4:54:20:74:51:3f
[ 5067.031108] wlp2s0: No basic rates, using min rate instead
[ 5067.041370] wlp2s0: send auth to f4:54:20:74:51:3f (try 1/3)
[ 5067.144121] wlp2s0: send auth to f4:54:20:74:51:3f (try 2/3)
[ 5067.252125] wlp2s0: send auth to f4:54:20:74:51:3f (try 3/3)
[ 5067.360079] wlp2s0: authentication with f4:54:20:74:51:3f timed out
[ 5084.309884] wlp2s0: authenticate with f4:54:20:74:51:3f
[ 5084.309895] wlp2s0: No basic rates, using min rate instead
[ 5084.329017] wlp2s0: send auth to f4:54:20:74:51:3f (try 1/3)
[ 5084.432490] wlp2s0: send auth to f4:54:20:74:51:3f (try 2/3)
[ 5084.536381] wlp2s0: send auth to f4:54:20:74:51:3f (try 3/3)
[ 5084.644482] wlp2s0: authentication with f4:54:20:74:51:3f timed out
[34703.807012] rtl8723be: Using firmware rtlwifi/rtl8723befw_36.bin
[34703.814242] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[34703.820024] rtlwifi: rtlwifi: wireless switch is on
[34703.859105] rtl8723be 0000:02:00.0 wlp2s0: renamed from wlan0

---

### Post by gerbio on 2021-06-25
**$ nmcli device wifi list**
IN-USE  BSSID              SSID                         MODE        CHAN            RATE        SIGNAL  BARS        SECURITY 
 F4:54:20:74:51:3F         VIVOFIBRA-5131      Infra  6        130 Mbit/s     40                 &#9602;&#9604;__                      WPA2     

This is the test answer while I was connected through the cable. 
VIVO is my network provider and VIVOFIBRA-5131 is my network internet name.
As you can see the test ran properly and the answers make sense...

---

### Post by gerbio on 2021-06-25
**$ sudo dmesg | grep -ie rtl -ie wlp**
[    1.942992] r8169 0000:03:00.2 eth0: RTL8402, 70:4d:7b:cf:d7:bc, XID 440, IRQ 122
[    6.354378] Bluetooth: hci0: RTL: examining hci_ver=06 hci_rev=000b lmp_ver=06 lmp_subver=8723
[    6.355346] Bluetooth: hci0: RTL: rom_version status=0 version=1
[    6.355350] Bluetooth: hci0: RTL: loading rtl_bt/rtl8723b_fw.bin
[    6.408088] Bluetooth: hci0: RTL: loading rtl_bt/rtl8723b_config.bin
[    6.408157] bluetooth hci0: Direct firmware load for rtl_bt/rtl8723b_config.bin failed with error -2
[    6.408178] Bluetooth: hci0: RTL: cfg_sz -2, total sz 22496
[    6.709537] rtl8723be: Using firmware rtlwifi/rtl8723befw_36.bin
[    6.718595] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    6.719907] rtlwifi: rtlwifi: wireless switch is on
[    7.220383] Bluetooth: hci0: RTL: fw version 0x0e2f9f73
[    7.589645] rtl8723be 0000:02:00.0 wlp2s0: renamed from wlan0
[   12.428256] RTL8208 Fast Ethernet r8169-302:00: attached PHY driver [RTL8208 Fast Ethernet] (mii_bus:phy_addr=r8169-302:00, irq=IGNORE)
[   18.508201] wlp2s0: authenticate with f4:54:20:74:51:3f
[   18.508214] wlp2s0: No basic rates, using min rate instead
[   18.518521] wlp2s0: send auth to f4:54:20:74:51:3f (try 1/3)
[   18.538728] wlp2s0: authenticated
[   18.541052] wlp2s0: associate with f4:54:20:74:51:3f (try 1/3)
[   18.644970] wlp2s0: associate with f4:54:20:74:51:3f (try 2/3)
[   18.749030] wlp2s0: associate with f4:54:20:74:51:3f (try 3/3)
[   18.853025] wlp2s0: association with f4:54:20:74:51:3f timed out
[   25.873223] wlp2s0: authenticate with f4:54:20:74:51:3f
[   25.873249] wlp2s0: No basic rates, using min rate instead
[   25.890084] wlp2s0: send auth to f4:54:20:74:51:3f (try 1/3)
[   25.903743] wlp2s0: authenticated
[   25.905124] wlp2s0: associate with f4:54:20:74:51:3f (try 1/3)
[   26.009319] wlp2s0: associate with f4:54:20:74:51:3f (try 2/3)
[   26.018751] wlp2s0: RX AssocResp from f4:54:20:74:51:3f (capab=0xc11 status=0 aid=5)
[   26.019090] wlp2s0: associated
[   32.121274] wlp2s0: deauthenticated from f4:54:20:74:51:3f (Reason: 15=4WAY_HANDSHAKE_TIMEOUT)
[   33.235516] wlp2s0: authenticate with f4:54:20:74:51:3f
[   33.235527] wlp2s0: No basic rates, using min rate instead
[   33.249590] wlp2s0: send auth to f4:54:20:74:51:3f (try 1/3)
[   33.356971] wlp2s0: send auth to f4:54:20:74:51:3f (try 2/3)
[   33.460985] wlp2s0: send auth to f4:54:20:74:51:3f (try 3/3)
[   33.564990] wlp2s0: authentication with f4:54:20:74:51:3f timed out
[   41.522151] wlp2s0: authenticate with f4:54:20:74:51:3f
[   41.522162] wlp2s0: No basic rates, using min rate instead
[   41.551373] wlp2s0: send auth to f4:54:20:74:51:3f (try 1/3)
[   41.656969] wlp2s0: send auth to f4:54:20:74:51:3f (try 2/3)
[   41.765147] wlp2s0: send auth to f4:54:20:74:51:3f (try 3/3)
[   41.872992] wlp2s0: authentication with f4:54:20:74:51:3f timed out
[  281.999343] wlp2s0: authenticate with f4:54:20:74:51:3f
[  281.999356] wlp2s0: No basic rates, using min rate instead
[  282.015281] wlp2s0: send auth to f4:54:20:74:51:3f (try 1/3)
[  282.116309] wlp2s0: send auth to f4:54:20:74:51:3f (try 2/3)
[  282.220732] wlp2s0: send auth to f4:54:20:74:51:3f (try 3/3)
[  282.324523] wlp2s0: authentication with f4:54:20:74:51:3f timed out
[  293.325977] wlp2s0: authenticate with f4:54:20:74:51:3f
[  293.325994] wlp2s0: No basic rates, using min rate instead
[  293.347751] wlp2s0: send auth to f4:54:20:74:51:3f (try 1/3)
[  293.448232] wlp2s0: send auth to f4:54:20:74:51:3f (try 2/3)
[  293.556222] wlp2s0: send auth to f4:54:20:74:51:3f (try 3/3)
[  293.660385] wlp2s0: authentication with f4:54:20:74:51:3f timed out
[  309.084641] wlp2s0: authenticate with f4:54:20:74:51:3f
[  309.084655] wlp2s0: No basic rates, using min rate instead
[  309.101256] wlp2s0: send auth to f4:54:20:74:51:3f (try 1/3)
[  309.204318] wlp2s0: send auth to f4:54:20:74:51:3f (try 2/3)
[  309.308509] wlp2s0: send auth to f4:54:20:74:51:3f (try 3/3)
[  309.412509] wlp2s0: authentication with f4:54:20:74:51:3f timed out
[  326.385245] wlp2s0: authenticate with f4:54:20:74:51:3f
[  326.385259] wlp2s0: No basic rates, using min rate instead
[  326.414192] wlp2s0: send auth to f4:54:20:74:51:3f (try 1/3)
[  326.520374] wlp2s0: send auth to f4:54:20:74:51:3f (try 2/3)
[  326.624464] wlp2s0: send auth to f4:54:20:74:51:3f (try 3/3)
[  326.728137] wlp2s0: authentication with f4:54:20:74:51:3f timed out
[  336.080232] wlp2s0: authenticate with f4:54:20:74:51:3f
[  336.080245] wlp2s0: No basic rates, using min rate instead
[  336.091170] wlp2s0: send auth to f4:54:20:74:51:3f (try 1/3)
[  336.119624] wlp2s0: authenticated
[  336.132164] wlp2s0: associate with f4:54:20:74:51:3f (try 1/3)
[  336.236159] wlp2s0: associate with f4:54:20:74:51:3f (try 2/3)
[  336.340206] wlp2s0: associate with f4:54:20:74:51:3f (try 3/3)
[  336.444184] wlp2s0: association with f4:54:20:74:51:3f timed out
[  347.433807] wlp2s0: authenticate with f4:54:20:74:51:3f
[  347.433820] wlp2s0: No basic rates, using min rate instead
[  347.455093] wlp2s0: send auth to f4:54:20:74:51:3f (try 1/3)
[  347.556084] wlp2s0: send auth to f4:54:20:74:51:3f (try 2/3)
[  347.660029] wlp2s0: send auth to f4:54:20:74:51:3f (try 3/3)
[  347.764521] wlp2s0: authentication with f4:54:20:74:51:3f timed out
[  863.065198] wlp2s0: authenticate with f4:54:20:74:51:3f
[  863.065211] wlp2s0: No basic rates, using min rate instead
[  863.084042] wlp2s0: send auth to f4:54:20:74:51:3f (try 1/3)
[  863.187763] wlp2s0: send auth to f4:54:20:74:51:3f (try 2/3)
[  863.291894] wlp2s0: send auth to f4:54:20:74:51:3f (try 3/3)
[  863.399425] wlp2s0: authentication with f4:54:20:74:51:3f timed out
[  874.377739] wlp2s0: authenticate with f4:54:20:74:51:3f
[  874.377753] wlp2s0: No basic rates, using min rate instead
[  874.396332] wlp2s0: send auth to f4:54:20:74:51:3f (try 1/3)
[  874.419192] wlp2s0: authenticated
[  874.423352] wlp2s0: associate with f4:54:20:74:51:3f (try 1/3)
[  874.527512] wlp2s0: associate with f4:54:20:74:51:3f (try 2/3)
[  874.631408] wlp2s0: associate with f4:54:20:74:51:3f (try 3/3)
[  874.739353] wlp2s0: association with f4:54:20:74:51:3f timed out
[  890.233093] wlp2s0: authenticate with f4:54:20:74:51:3f
[  890.233111] wlp2s0: No basic rates, using min rate instead
[  890.252063] wlp2s0: send auth to f4:54:20:74:51:3f (try 1/3)
[  890.355445] wlp2s0: send auth to f4:54:20:74:51:3f (try 2/3)
[  890.372860] wlp2s0: authenticated
[  890.375389] wlp2s0: associate with f4:54:20:74:51:3f (try 1/3)
[  890.479481] wlp2s0: associate with f4:54:20:74:51:3f (try 2/3)
[  890.583471] wlp2s0: associate with f4:54:20:74:51:3f (try 3/3)
[  890.687317] wlp2s0: association with f4:54:20:74:51:3f timed out
[  955.433117] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready
[ 1026.879183] wlp2s0: authenticate with f4:54:20:74:51:3f
[ 1026.879195] wlp2s0: No basic rates, using min rate instead
[ 1027.383348] wlp2s0: send auth to f4:54:20:74:51:3f (try 1/3)
[ 1027.398452] wlp2s0: authenticated
[ 1027.399039] wlp2s0: associate with f4:54:20:74:51:3f (try 1/3)
[ 1027.409143] wlp2s0: RX AssocResp from f4:54:20:74:51:3f (capab=0xc11 status=0 aid=5)
[ 1027.409442] wlp2s0: associated
[ 1028.819789] wlp2s0: deauthenticating from f4:54:20:74:51:3f by local choice (Reason: 3=DEAUTH_LEAVING)
[ 1028.960463] wlp2s0: authenticate with f4:54:20:74:51:3f
[ 1028.960476] wlp2s0: No basic rates, using min rate instead
[ 1029.465115] wlp2s0: send auth to f4:54:20:74:51:3f (try 1/3)
[ 1029.566992] wlp2s0: send auth to f4:54:20:74:51:3f (try 2/3)
[ 1029.581246] wlp2s0: authenticated
[ 1029.583066] wlp2s0: associate with f4:54:20:74:51:3f (try 1/3)
[ 1029.596117] wlp2s0: RX AssocResp from f4:54:20:74:51:3f (capab=0xc11 status=0 aid=5)
[ 1029.596404] wlp2s0: associated
[ 1035.702872] wlp2s0: deauthenticated from f4:54:20:74:51:3f (Reason: 15=4WAY_HANDSHAKE_TIMEOUT)
[ 1036.825861] wlp2s0: authenticate with f4:54:20:74:51:3f
[ 1036.825879] wlp2s0: No basic rates, using min rate instead
[ 1036.843687] wlp2s0: send auth to f4:54:20:74:51:3f (try 1/3)
[ 1036.858772] wlp2s0: authenticated
[ 1036.863012] wlp2s0: associate with f4:54:20:74:51:3f (try 1/3)
[ 1036.971019] wlp2s0: associate with f4:54:20:74:51:3f (try 2/3)
[ 1036.987624] wlp2s0: RX AssocResp from f4:54:20:74:51:3f (capab=0xc11 status=0 aid=5)
[ 1036.987946] wlp2s0: associated
[ 1043.092708] wlp2s0: deauthenticated from f4:54:20:74:51:3f (Reason: 15=4WAY_HANDSHAKE_TIMEOUT)
[ 1044.675997] wlp2s0: authenticate with f4:54:20:74:51:3f
[ 1044.676009] wlp2s0: No basic rates, using min rate instead
[ 1044.697536] wlp2s0: send auth to f4:54:20:74:51:3f (try 1/3)
[ 1044.799177] wlp2s0: send auth to f4:54:20:74:51:3f (try 2/3)
[ 1044.903420] wlp2s0: send auth to f4:54:20:74:51:3f (try 3/3)
[ 1045.007398] wlp2s0: authentication with f4:54:20:74:51:3f timed out
[ 1380.964274] wlp2s0: authenticate with f4:54:20:74:51:3f
[ 1380.964287] wlp2s0: No basic rates, using min rate instead
[ 1380.984391] wlp2s0: send auth to f4:54:20:74:51:3f (try 1/3)
[ 1381.086486] wlp2s0: send auth to f4:54:20:74:51:3f (try 2/3)
[ 1381.194677] wlp2s0: send auth to f4:54:20:74:51:3f (try 3/3)
[ 1381.302639] wlp2s0: authentication with f4:54:20:74:51:3f timed out
[ 1391.303393] wlp2s0: authenticate with f4:54:20:74:51:3f
[ 1391.303414] wlp2s0: No basic rates, using min rate instead
[ 1391.313693] wlp2s0: send auth to f4:54:20:74:51:3f (try 1/3)
[ 1391.335077] wlp2s0: authenticated
[ 1391.343059] wlp2s0: associate with f4:54:20:74:51:3f (try 1/3)
[ 1391.384161] wlp2s0: RX AssocResp from f4:54:20:74:51:3f (capab=0xc11 status=0 aid=6)
[ 1391.384495] wlp2s0: associated
[ 1401.386651] wlp2s0: deauthenticating from f4:54:20:74:51:3f by local choice (Reason: 3=DEAUTH_LEAVING)
[ 1412.655422] wlp2s0: authenticate with f4:54:20:74:51:3f
[ 1412.655443] wlp2s0: No basic rates, using min rate instead
[ 1412.671123] wlp2s0: send auth to f4:54:20:74:51:3f (try 1/3)
[ 1412.774415] wlp2s0: send auth to f4:54:20:74:51:3f (try 2/3)
[ 1412.878504] wlp2s0: send auth to f4:54:20:74:51:3f (try 3/3)
[ 1412.982420] wlp2s0: authentication with f4:54:20:74:51:3f timed out
[ 1497.973211] wlp2s0: authenticate with f4:54:20:74:51:3f
[ 1497.973233] wlp2s0: No basic rates, using min rate instead
[ 1497.991264] wlp2s0: send auth to f4:54:20:74:51:3f (try 1/3)
[ 1498.094740] wlp2s0: send auth to f4:54:20:74:51:3f (try 2/3)
[ 1498.198340] wlp2s0: send auth to f4:54:20:74:51:3f (try 3/3)
[ 1498.302335] wlp2s0: authentication with f4:54:20:74:51:3f timed out
[ 1509.304815] wlp2s0: authenticate with f4:54:20:74:51:3f
[ 1509.304840] wlp2s0: No basic rates, using min rate instead
[ 1509.325330] wlp2s0: send auth to f4:54:20:74:51:3f (try 1/3)
[ 1509.426237] wlp2s0: send auth to f4:54:20:74:51:3f (try 2/3)
[ 1509.530296] wlp2s0: send auth to f4:54:20:74:51:3f (try 3/3)
[ 1509.634214] wlp2s0: authentication with f4:54:20:74:51:3f timed out
[ 1880.462687] wlp2s0: authenticate with f4:54:20:74:51:3f
[ 1880.462700] wlp2s0: No basic rates, using min rate instead
[ 1880.482167] wlp2s0: send auth to f4:54:20:74:51:3f (try 1/3)
[ 1880.543713] wlp2s0: authenticated
[ 1880.545379] wlp2s0: associate with f4:54:20:74:51:3f (try 1/3)
[ 1880.560338] wlp2s0: RX AssocResp from f4:54:20:74:51:3f (capab=0xc11 status=0 aid=6)
[ 1880.560629] wlp2s0: associated
[ 1886.665175] wlp2s0: deauthenticated from f4:54:20:74:51:3f (Reason: 15=4WAY_HANDSHAKE_TIMEOUT)
[ 1897.725172] wlp2s0: authenticate with f4:54:20:74:51:3f
[ 1897.725187] wlp2s0: No basic rates, using min rate instead
[ 1897.742419] wlp2s0: send auth to f4:54:20:74:51:3f (try 1/3)
[ 1897.756512] wlp2s0: authenticated
[ 1897.758362] wlp2s0: associate with f4:54:20:74:51:3f (try 1/3)
[ 1897.861425] wlp2s0: associate with f4:54:20:74:51:3f (try 2/3)
[ 1897.879443] wlp2s0: RX AssocResp from f4:54:20:74:51:3f (capab=0xc11 status=0 aid=6)
[ 1897.879888] wlp2s0: associated
[ 1903.978665] wlp2s0: deauthenticated from f4:54:20:74:51:3f (Reason: 15=4WAY_HANDSHAKE_TIMEOUT)
[ 4980.694764] wlp2s0: authenticate with f4:54:20:74:51:3f
[ 4980.694776] wlp2s0: No basic rates, using min rate instead
[ 4981.202394] wlp2s0: send auth to f4:54:20:74:51:3f (try 1/3)
[ 4981.304056] wlp2s0: send auth to f4:54:20:74:51:3f (try 2/3)
[ 4981.408225] wlp2s0: send auth to f4:54:20:74:51:3f (try 3/3)
[ 4981.516081] wlp2s0: authentication with f4:54:20:74:51:3f timed out
[ 5036.043050] wlp2s0: authenticate with f4:54:20:74:51:3f
[ 5036.043062] wlp2s0: No basic rates, using min rate instead
[ 5036.053297] wlp2s0: send auth to f4:54:20:74:51:3f (try 1/3)
[ 5036.156168] wlp2s0: send auth to f4:54:20:74:51:3f (try 2/3)
[ 5036.260350] wlp2s0: send auth to f4:54:20:74:51:3f (try 3/3)
[ 5036.365434] wlp2s0: authentication with f4:54:20:74:51:3f timed out
[ 5047.365801] wlp2s0: authenticate with f4:54:20:74:51:3f
[ 5047.365813] wlp2s0: No basic rates, using min rate instead
[ 5047.385345] wlp2s0: send auth to f4:54:20:74:51:3f (try 1/3)
[ 5047.488252] wlp2s0: send auth to f4:54:20:74:51:3f (try 2/3)
[ 5047.592265] wlp2s0: send auth to f4:54:20:74:51:3f (try 3/3)
[ 5047.696062] wlp2s0: authentication with f4:54:20:74:51:3f timed out
[ 5067.031096] wlp2s0: authenticate with f4:54:20:74:51:3f
[ 5067.031108] wlp2s0: No basic rates, using min rate instead
[ 5067.041370] wlp2s0: send auth to f4:54:20:74:51:3f (try 1/3)
[ 5067.144121] wlp2s0: send auth to f4:54:20:74:51:3f (try 2/3)
[ 5067.252125] wlp2s0: send auth to f4:54:20:74:51:3f (try 3/3)
[ 5067.360079] wlp2s0: authentication with f4:54:20:74:51:3f timed out
[ 5084.309884] wlp2s0: authenticate with f4:54:20:74:51:3f
[ 5084.309895] wlp2s0: No basic rates, using min rate instead
[ 5084.329017] wlp2s0: send auth to f4:54:20:74:51:3f (try 1/3)
[ 5084.432490] wlp2s0: send auth to f4:54:20:74:51:3f (try 2/3)
[ 5084.536381] wlp2s0: send auth to f4:54:20:74:51:3f (try 3/3)
[ 5084.644482] wlp2s0: authentication with f4:54:20:74:51:3f timed out
[34703.807012] rtl8723be: Using firmware rtlwifi/rtl8723befw_36.bin
[34703.814242] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[34703.820024] rtlwifi: rtlwifi: wireless switch is on
[34703.859105] rtl8723be 0000:02:00.0 wlp2s0: renamed from wlan0
[36277.910351] rtl8723be: Using firmware rtlwifi/rtl8723befw_36.bin
[36277.917873] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[36277.919701] rtlwifi: rtlwifi: wireless switch is on
[36277.958864] rtl8723be 0000:02:00.0 wlp2s0: renamed from wlan0


**$ nmcli device wifi list**
IN-USE  BSSID  SSID  MODE  CHAN  RATE  SIGNAL  BARS  SECURITY 


This happens when I desconnected the cable.
I guess my router and my modem are not bad and that my problem is being generated by something related to software, not hardware.
What do you think?
Should I try to solve this issue, or reformat and reinstall the Ubuntu 20.10? (I liked the groovy-gorila)

---

### Post by chili555 on 2021-06-26
> This happens when I desconnected the cable.Fascinating! If I understand correctly, if the ethernet cable is plugged in and connected, the wireless works fine. If you disconnect the ethernet, the wireless stops working.

When everything is connected and working, please run:

```
tail -f /var/log/syslog

```
Watch the output of the terminal and detach the ethernet. The system will recognize the activity and record several messages that will appear in the terminal. Please capture all of the output. Get out of 'tail' with Ctrl+c.

Whenever it is helpful to post long log results as above, please paste them here and give us the link: [http://paste.ubuntu.com](http://paste.ubuntu.com) 

Since we have learned that the driver parameter you added is not useful, let's replace it.

We notice very low signal strength in your readings:

```
Cell 01 - Address: F4:54:20:74:51:3F
Channel:1
Frequency:2.412 GHz (Channel 1)
[COLOR="#FF0000"]Quality=34/70 [/COLOR]Signal level=-76 dBm

```Let's try antenna selection to see if it helps:

```
sudo -i
echo "options rtl8723be ant_sel=1"  >  /etc/modprobe.d/rtl8723be.conf
modprobe -r rtl8723be
modprobe rtl8723be ant_sel=1
exit
```Is there any improvement? Find out with:

```
sudo iwlist scan
```Check the quality of your router. Is it better now than 34/70? 

If not, please repeat the sequence with ant_sel=2.

---

### Post by gerbio on 2021-06-26
**$ tail -f /var/log/syslog**
Jun 26 16:25:02 gerson-Z550SA gnome-terminal-[3595]: Need to double-quote the value: "&#553;" U0229#011# LATIN SMALL LETTER E WITH CEDILLA: <Multi_key> <comma> <e> #011#011: "&#553;" U0229#011# LATIN SMALL LETTER E WITH CEDILLA
Jun 26 16:25:02 gerson-Z550SA gnome-terminal-[3595]: Need to double-quote the value: "&#7708;" U1E1C#011# LATIN CAPITAL LETTER E WITH CEDILLA AND BREVE: <Multi_key> <U> <comma> <E> #011#011: "&#7708;" U1E1C#011# LATIN CAPITAL LETTER E WITH CEDILLA AND BREVE
Jun 26 16:25:02 gerson-Z550SA gnome-terminal-[3595]: Need to double-quote the value: "&#7709;" U1E1D#011# LATIN SMALL LETTER E WITH CEDILLA AND BREVE: <Multi_key> <U> <comma> <e> #011#011: "&#7709;" U1E1D#011# LATIN SMALL LETTER E WITH CEDILLA AND BREVE
Jun 26 16:25:02 gerson-Z550SA gnome-terminal-[3595]: Need to double-quote the value: "&#979;" U03D3#011# GREEK UPSILON WITH ACUTE AND HOOK SYMBOL: <Multi_key> <acute> <U03D2> #011#011: "&#979;" U03D3#011# GREEK UPSILON WITH ACUTE AND HOOK SYMBOL
Jun 26 16:25:02 gerson-Z550SA gnome-terminal-[3595]: Need to double-quote the value: "&#979;" U03D3#011# GREEK UPSILON WITH ACUTE AND HOOK SYMBOL: <Multi_key> <apostrophe> <U03D2> #011: "&#979;" U03D3#011# GREEK UPSILON WITH ACUTE AND HOOK SYMBOL
Jun 26 16:25:02 gerson-Z550SA systemd[1763]: Started VTE child process 3600 launched by gnome-terminal-server process 3595.
Jun 26 16:25:03 gerson-Z550SA systemd[1763]: app-gnome-org.gnome.Terminal-3587.scope: Succeeded.
Jun 26 16:25:44 gerson-Z550SA systemd[1]: Starting Download data for packages that failed at package install time...
Jun 26 16:25:44 gerson-Z550SA systemd[1]: update-notifier-download.service: Succeeded.
Jun 26 16:25:44 gerson-Z550SA systemd[1]: Finished Download data for packages that failed at package install time.

Ok but how can I give you that link? Is it a command I could start to help you guys the most? Or I'm supposed to paste my results on that link. 
I'll try the last option and you can ask me to change whatever you want, ok?

[https://paste.ubuntu.com/p/7Dgk8HcGf4/](https://paste.ubuntu.com/p/7Dgk8HcGf4/)

---

### Post by chili555 on 2021-06-26
> Ok but how can I give you that link? Is it a command I could start to help you guys the most? Or I'm supposed to paste my results on that link.
I'll try the last option and you can ask me to change whatever you want, ok?
You gave the link correctly. However, when we can conveniently read the data in the paste, please do not *also *post it in your reply. It clutters the post and is bad practice to wall-of-text this or any forum.

What we'd hoped to see as your reply was:

> Here is the output from syslog as I removed the ethernet cable: [https://paste.ubuntu.com/p/7Dgk8HcGf4/](https://paste.ubuntu.com/p/7Dgk8HcGf4/)That said, I see nothing at all about your wireless or Network Manager or ethernet here at all. 

After you remove the ethernet cable and the wireless drops, is the driver still loaded?

```
lsmod | grep rtl87
```

Is the wireless then blocked?

```
rfkill list all

```
Is Network Manager still running?

```
sudo service NetworkManager status | grep Active

```
Let's see this, also in a paste:

```
cat /var/log/syslog | grep rtl8723
```

If you cold boot with the ethernet detached, does the wireless work?

---

### Post by gerbio on 2021-06-26
Now I'll perform the test as you teach me...

[https://paste.ubuntu.com/p/D8Pbg927FJ/](https://paste.ubuntu.com/p/D8Pbg927FJ/)

First I ran the commands connected as you taught me (at 16:40 = 4:40 PM), then I disconnected and wait for 10 minutes to catch all possible variations.
In the end I reconnected at 16:50 (4:50 PM) to send you my results and recorded the final answers.

---

### Post by gerbio on 2021-06-26
> **chili555 said:**
> You gave the link correctly. However, when we can conveniently read the data in the paste, please do not *also *post it in your reply. It clutters the post and is bad practice to wall-of-text this or any forum.

What we'd hoped to see as your reply was:

That said, I see nothing at all about your wireless or Network Manager or ethernet here at all. 

After you remove the ethernet cable and the wireless drops, is the driver still loaded?

```
lsmod | grep rtl87
```

Is the wireless then blocked?

```
rfkill list all

```
Is Network Manager still running?

```
sudo service NetworkManager status | grep Active

```
Let's see this, also in a paste:

```
cat /var/log/syslog | grep rtl8723
```

If you cold boot with the ethernet detached, does the wireless work?

Ok, I bag your pardon for making so much mistakes. Thank you for your help, I'm learning a lot about my own Laptop.

---

### Post by gerbio on 2021-06-26
I guess I have problems with the NetworkManager beause when I turn off my Laptop it appears a message very fast saing Warning in red letters and says something about this NetworkManager connection. 
Also, when I upgraded to 20.10, during the instalation, it said something about ERROR in libkmod modprobe/ect... that I don't understand.
When I disconnect the cable the wireless is still connected and lauched but it says that is in need of my password. I give it my password and it disconnects suddenly.

---

### Post by gerbio on 2021-06-26
Results of the tests you asked me

[https://paste.ubuntu.com/p/DcBnwKQs2c/](https://paste.ubuntu.com/p/DcBnwKQs2c/)

[https://paste.ubuntu.com/p/XqCWDnBN83/](https://paste.ubuntu.com/p/XqCWDnBN83/)

---

### Post by gerbio on 2021-06-26
The answers you requested above are here in a single paste.

[https://paste.ubuntu.com/p/Jr3SQP4tc2/](https://paste.ubuntu.com/p/Jr3SQP4tc2/)

And when I turn it on with the cable disconnected it doesn't connect. Only recognizes my network (VIVOFIBRA-5131) but don't connect. It keeps asking me for my password and don't connect.

---

### Post by gerbio on 2021-06-26
Running the command sudo iwlist scanning (on my Laptop is scanning I don't know why) it answered

[https://paste.ubuntu.com/p/X84ntTnhdq/](https://paste.ubuntu.com/p/X84ntTnhdq/)

I guess you found one problem of the quality of my connection. It's stuck in 38/70. Perhaps its the problem that keeps my laptop without wireless.

---

### Post by chili555 on 2021-06-26
> It's stuck in 38/70. With either ant_sel=1 or else ant_sel=2?

Is there a setting in your router to change the TX (transmit) power, like this?

[IMG]https://qph.fs.quoracdn.net/main-qimg-fc632342b786bc69d4f004c7d2a99d34.webp[/IMG]

---

### Post by gerbio on 2021-06-26
Yes, I'm stuck with quality about 33 to 38 of 70 either using ant_sel=1 or ant_sel=2.

[https://paste.ubuntu.com/p/Z8SqFDgQmC/](https://paste.ubuntu.com/p/Z8SqFDgQmC/)

---

### Post by chili555 on 2021-06-27
You wrote:

> $ sudo -i
echo "options rtl8723be ant_sel=1"  >  /etc/modprobe.d/rtl8723be.conf
modprobe -r rtl8723be
modprobe rtl8723be ant_sel=2
exitIt should have been:

```
$ sudo -i
echo "options rtl8723be ant_sel=[COLOR="#FF0000"]2[/COLOR]"  >  /etc/modprobe.d/rtl8723be.conf
modprobe -r rtl8723be
modprobe rtl8723be ant_sel=2
exit
```Although I doubt it will make any difference.

How far are you from the router? I am about 6-7 meters from mine and I have no difficulty connecting and staying connected:

```
Cell 05 - Address: xx:2B:B0:DC:45:xx
                    Channel:149
                    Frequency:5.745 GHz (Channel 149)
                    [COLOR="#FF0000"]Quality=58/70 [/COLOR] Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"GBR5"
                    <snip>
```

Does your card have antennae attached like this? 

[IMG]https://pisces.bbystatic.com/image2/BestBuy_US/images/products/6265/6265517_sa.jpg;maxHeight=640;maxWidth=550[/IMG]

Are they firmly attached?

---

### Post by gerbio on 2021-06-27
To tell you the truth I'm a two or three meters from the router. But I thought my problem would come from the router so I got the cable and inserted in another router (TP link), configured it to "bridge" and tried to connect. But the laptop got the information about the strengh of the signal and didn't connect.
My modem is an internal one and do not have antennae.

---

### Post by chili555 on 2021-06-28
> My modem is an internal one and do not have antennae.Is it in a laptop? If so, it usually does:

[IMG]https://c1.neweggimages.com/ProductImage/AE7R_1_20170717618569045.jpg[/IMG]

Those two connectors marked Aux and Main are where the antenna wires connect. Are both of yours securely snapped in place?

---

