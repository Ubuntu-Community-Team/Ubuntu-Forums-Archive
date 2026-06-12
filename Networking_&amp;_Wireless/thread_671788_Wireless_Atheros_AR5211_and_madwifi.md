---
title: "Wireless: Atheros AR5211 and madwifi"
date: 2008-01-18
forum: Networking &amp; Wireless
---

### Post by jayharvard on 2008-01-18
Hello All. I'm jonesing for some help. I've got a Toshiba A25-s307 that has an Atheros AR521 1 wireless pci card.I've had this laptop for 4 years and have only ever gotten the on-board card to work with 6.06. I've decided to install 7.10 and not quit until I get this card working. I'm working with Madwifi. I've followed several "how-tos" and hoping someone may point out something I'm missing.

Here's all of the pertinent information that I've tried. The last statement is a dhcp ip request. And still no joy.

Any advice would be greatly appreciated.

sudo#$uname -r
2.6.22-14-386

sudo#$lspci
00:00.0 Host bridge: ALi Corporation M1672 Northbridge [CyberALADDiN-P4]
00:01.0 PCI bridge: ALi Corporation PCI to AGP Controller
00:04.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:09.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0c.0 USB Controller: NEC Corporation USB (rev 43)
00:0c.1 USB Controller: NEC Corporation USB (rev 43)
00:0c.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
00:10.0 Ethernet controller: Atheros Communications, Inc. AR5211 802.11ab NIC (rev 01)
00:11.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 33)
00:12.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 05)
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade XPAi1 (rev 82)

sudo#$dmesg | egrep -i '(ath|wifi)'
[   21.220000] ath_hal: module license 'Proprietary' taints kernel.
[   21.220000] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   21.864000] ath_pci: 0.9.4.5 (0.9.3.2)
[   22.180000] ath_rate_sample: 1.2 (0.9.3.2)
[   22.180000] wifi0: 11a rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   22.180000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   22.180000] wifi0: turboA rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   22.180000] wifi0: H/W encryption support: WEP AES
[   22.180000] wifi0: mac 4.2 phy 3.0 5 GHz radio 1.7 2 GHz radio 2.3
[   22.180000] wifi0: Use hw queue 0 for WME_AC_BE traffic
[   22.180000] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   22.180000] wifi0: Use hw queue 0 for WME_AC_VI traffic
[   22.180000] wifi0: Use hw queue 0 for WME_AC_VO traffic
[   22.180000] wifi0: Use hw queue 8 for CAB traffic
[   22.180000] wifi0: Use hw queue 9 for beacons
[   22.360000] wifi0: Atheros 5211: mem=0xf7ee0000, irq=11
[   53.488000] ath0: no IPv6 routers present
sudo#$modprobe ath_pci

sudo#$wlanconfig ath0 destroy

sudo#$wlanconfig ath0 create wlandev wifi0 wlanmode sta

sudo#$ifconfig ath0 up

sudo#$modprobe wlan_scan_sta

sudo#$iwconfig ath0 key <s:mykey>

sudo#$iwpriv ath0 authmode 1

sudo#$wlanconfig ath0 list scan

sudo#$iwlist ath0 scan
ath0      No scan results

sudo#$iwlist scan
ath0      No scan results
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      No scan results

sudo#$iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11a  ESSID:""  Nickname:""
          Mode:Managed  Frequency:5.805 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:0 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:<mykey>   Security mode:restricted
          Power Management:off
          Link Quality=0/70  Signal level=-98 dBm  Noise level=-98 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sudo#$iwconfig ath0 essid <myessid>

sudo#$iwconfig ath0 key <s:mykeyagain>

sudo#$iwconfig ath0 ap <myap>

sudo#$iwconfig ath0 channel 6

sudo#$dhclient ath0

Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/mynetmac
Sending on   LPF/ath0/mynetmac
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

