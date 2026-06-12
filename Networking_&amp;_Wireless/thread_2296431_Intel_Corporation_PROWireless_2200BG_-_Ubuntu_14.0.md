---
title: "Intel Corporation PRO/Wireless 2200BG - Ubuntu 14.04.3 LTS Server"
date: 2015-09-25
forum: Networking &amp; Wireless
---

### Post by fabricio4 on 2015-09-25
Hi, I have been years away from Unix/Linux systems so sorry for the newbie question. I also know nothing on wireless (did not have those back then!).

It is suposed to be my home automation/SCADA server on an old laptop, Sony Vaio VGN-FJ170. It is a Ubuntu Server distro without any X environment.

I am trying to connect to the wifi network with no luck. I tried:

```
  235  iwconfig eth1 power off  236  iwconfig eth1 mode managed
  237  iwconfig eth1 mode channel 1
  238  iwconfig eth1 channel 1
  239  iwconfig eth1 essid SEFAZ-SC-VISITANTE
  240  iwconfig eth1 key s:password@with@symbolsandnumbers
  241  iwconfig eth1 key restricted
  242  iwconfig eth1 key on
  243  dhclient eth1
```

But dhclient wont return. I guess it could not even authenticate with the Access Point...

And also tried wpa_supplicant:

```
wpa_supplicant -i eth1 -c /etc/wpa_supplicant/wpa_supplicant.conf
```

with conf file:
```
ctrl_interface=/var/run/wpa_supplicantctrl_interface_group=0


eapol_version=2
ap_scan=1
fast_reauth=1
country=BR


network={
   ssid=""
  key_mgmt=NONE
  priority=1
}


# WPA/WPA2
network={
	ssid="SEFAZ-SC-VISITANTE"
	#psk="password@with@symbolsandnumbers"
	psk=0384e29e3d7db4b983f80af69744a7dca9fb3e76cc4412ba903c75dea8dcbd70
}

```

I get:
```
Successfully initialized wpa_supplicantnl80211: Driver does not support authentication/association or connect commands
eth1: Failed to initialize driver interface
```

Here is wireless-info results:
```


########## wireless info START ##########


Report from: 25 Sep 2015 17:01 BRT -0300


Booted last: 25 Sep 2015 16:32 BRT -0300


Script from: 14 Jul 2015 17:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.3 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.19.0-25-generic #26~14.04.1-Ubuntu SMP Fri Jul 24 21:18:00 UTC 2015 i686 i686 i686 GNU/Linux


Parameters: ro


##### desktop ###########################


sed: can't read /root/.dmrc: No such file or directory


Could not be determined.


##### lspci #############################


06:08.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter [10ec:8139] (rev 10)
	Subsystem: Sony Corporation Device [104d:81f1]
	Kernel driver in use: 8139too


06:0a.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
	Subsystem: Intel Corporation Device [8086:2751]
	Kernel driver in use: ipw2200


##### lsusb #############################


Bus 001 Device 002: ID 0ac8:c002 Z-Star Microelectronics Corp. Visual Communication Camera VGP-VCC1
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


'pccardctl' is not installed (package "pcmciautils").


##### rfkill ############################


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


ipw2200               139264  0 
libipw                 36864  1 ipw2200
cfg80211              450560  2 libipw,ipw2200


##### interfaces ########################


auto lo
iface lo inet loopback


auto eth0
iface eth0 inet dhcp


auto eth1
iface eth1 inet dhcp


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:172.18.1.70  Bcast:172.18.3.255  Mask:255.255.252.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26120 errors:0 dropped:0 overruns:0 frame:0
          TX packets:63 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2305992 (2.3 MB)  TX bytes:5931 (5.9 KB)


eth1      Link encap:Ethernet  HWaddr <MAC 'eth1' [IF]>  
          inet6 addr: fe80::<IP6 'eth1' [IF]>/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:82 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:25464 (25.4 KB)


##### iwconfig ##########################


lo        no wireless extensions.


eth0      no wireless extensions.


eth1      IEEE 802.11bg  ESSID:"SEFAZ-SC-VISITANTE"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:7669-7369-7461-6E74-6540-7365-66   Security mode:restricted
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         172.18.1.254    0.0.0.0         UG    0      0        0 eth0
172.18.0.0      0.0.0.0         255.255.252.0   U     0      0        0 eth0


##### resolv.conf #######################


nameserver 172.19.212.75
nameserver 172.19.212.80
nameserver 172.19.212.68
search sef.sc.gov.br


##### network managers ##################


Installed:


	None found.


Running:


	None found.


##### NetworkManager info ###############


NetworkManager is not installed (package "network-manager").


##### NetworkManager.state ##############


cat: /var/lib/NetworkManager/NetworkManager.state: No such file or directory


##### NetworkManager.conf ###############


grep: /etc/NetworkManager/NetworkManager.conf: No such file or directory


##### NetworkManager profiles ###########


No NetworkManager profiles found.


##### iw reg get ########################


Region: America/Sao_Paulo (based on set time zone)


country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


lo        no frequency information.


eth0      no frequency information.


eth1      11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Current Frequency=2.412 GHz (Channel 1)


##### iwlist scan #######################


lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


Channel occupancy:


      4   APs on   Frequency:2.412 GHz (Channel 1)
      6   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.452 GHz (Channel 9)
      10   APs on   Frequency:2.462 GHz (Channel 11)


eth1      Scan completed :
          Cell 01 - Address: <MAC 'SEFAZSC' [AC1]>
                    ESSID:"SEFAZSC"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=84/100  Signal level=-46 dBm  
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    Extra: Last beacon: 248ms ago
          Cell 02 - Address: <MAC 'SEFAZ-SC-VISITANTE' [AC2]>
                    ESSID:"SEFAZ-SC-VISITANTE"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=59/100  Signal level=-46 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 208ms ago
          Cell 03 - Address: <MAC 'SEFAZSC' [AC3]>
                    ESSID:"SEFAZSC"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=78/100  Signal level=-51 dBm  
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    Extra: Last beacon: 124ms ago
        ...
		MANY MORE HERE
		...


##### module infos ######################


[ipw2200]
filename:       /lib/modules/3.19.0-25-generic/kernel/drivers/net/wireless/ipw2x00/ipw2200.ko
firmware:       ipw2200-bss.fw
firmware:       ipw2200-sniffer.fw
firmware:       ipw2200-ibss.fw
license:        GPL
author:         Copyright(c) 2003-2006 Intel Corporation
version:        1.2.2kmprq
description:    Intel(R) PRO/Wireless 2200/2915 Network Driver
srcversion:     B5711A76426895AF82FBFE3
depends:        cfg80211,libipw
intree:         Y
vermagic:       3.19.0-25-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        BB:26:8D:6D:EE:CB:ED:52:27:34:75:F8:CB:66:1B:D2:CA:20:8A:1B
sig_hashalgo:   sha512
parm:           disable:manually disable the radio (default 0 [radio on]) (int)
parm:           associate:auto associate when scanning (default off) (int)
parm:           auto_create:auto create adhoc network (default on) (int)
parm:           led:enable led control on some systems (default 1 on) (int)
parm:           debug:debug output mask (int)
parm:           channel:channel to limit associate to (default 0 [ANY]) (int)
parm:           rtap_iface:create the rtap interface (1 - create, default 0) (int)
parm:           qos_enable:enable all QoS functionalitis (int)
parm:           qos_burst_enable:enable QoS burst mode (int)
parm:           qos_no_ack_mask:mask Tx_Queue to no ack (int)
parm:           burst_duration_CCK:set CCK burst value (int)
parm:           burst_duration_OFDM:set OFDM burst value (int)
parm:           mode:network mode (0=BSS,1=IBSS,2=Monitor) (int)
parm:           bt_coexist:enable bluetooth coexistence (default off) (int)
parm:           hwcrypto:enable hardware crypto (default off) (int)
parm:           cmdlog:allocate a ring buffer for logging firmware commands (int)
parm:           roaming:enable roaming support (default on) (int)
parm:           antenna:select antenna 1=Main, 3=Aux, default 0 [both], 2=slow_diversity (choose the one with lower background noise) (int)


[cfg80211]
filename:       /lib/modules/3.19.0-25-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     E61EB836E1B33C2A2918485
depends:        
intree:         Y
vermagic:       3.19.0-25-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        BB:26:8D:6D:EE:CB:ED:52:27:34:75:F8:CB:66:1B:D2:CA:20:8A:1B
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[ipw2200]
antenna: 0
associate: 0
auto_create: 1
bt_coexist: 0
burst_duration_CCK: 0
burst_duration_OFDM: 0
channel: 0
cmdlog: 0
debug: 0
disable: 0
hwcrypto: 0
led: 1
mode: 0
qos_burst_enable: 0
qos_enable: 0
qos_no_ack_mask: 0
roaming: 1
rtap_iface: 0


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


lp


##### modprobe options ##################


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


[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8139 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x4220 (ipw2200)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth1' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


##### dmesg #############################


[   14.740523] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   14.740530] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   14.744603] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   15.668327] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)


########## wireless info END ############



```

Tried a few APs. I would rather not install any network manager also, but I am proun to do it by now... But it might well be some simple stupid thing I am doing!

I have run out of ideas and been a few days googling and reading through the forum with no luck, so any help will be greatly apreciated.

---

### Post by chili555 on 2015-09-26
> auto lo
iface lo inet loopback


auto eth0
iface eth0 inet dhcp


auto eth1
iface eth1 inet dhcp
I suggest you amend the */etc/network/interfaces* file to read:```
auto lo
iface lo inet loopback


auto eth0
iface eth0 inet dhcp


auto eth1
iface eth1 inet dhcp
wpa-essid SEFAZ-SC-VISITANTE
wpa-psk password@with@symbolsandnumbers

```Restart the interface:```
sudo ifdown eth1 && sudo ifup -v eth1
```The -v for verbose should produce some output telling us if you connect or, if not, a clue as to why.

---

### Post by fabricio4 on 2015-09-30
Thank you chilli555, seems that those two lines did the trick. Do I have to keep the wpa_supplicant.conf file?

(PS I had issues with a corrupted memory chip on that notebook and could only get back to it today).

---

