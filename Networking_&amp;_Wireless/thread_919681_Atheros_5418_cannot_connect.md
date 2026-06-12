---
title: "Atheros 5418 cannot connect"
date: 2008-09-14
forum: Networking &amp; Wireless
---

### Post by mnj1979 on 2008-09-14
Hello everyone,
 I am having problems with wireless networking.
I installed madwifi and can see all wireless networks but cannot connect to them with or without passwords.
 iwconfig
lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:14 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:62095  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.
It appears that link quality is 0/70, something is wrong.
Need some help with wireless connectivity.

---

### Post by pytheas22 on 2008-09-14
How did you install madwifi?  Did you compile the latest code from source?  Or did you install something using Synaptic (if you did, you probably installed the madwifi utilities, but not the drivers themselves, which are already built into Ubuntu)?

Please also post the output of these commands so that we can figure things out:
```

iwlist scan; iwlist scan
lspci -nn | grep -i atheros
modinfo ath_pci
dmesg | grep -e ath
uname -m
```

---

### Post by mnj1979 on 2008-09-15
I installed madwifi by compiling the source code using the latest subversion.
Here are the codes you requested:
 iwlist scan; iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:15:E9:E0:A4:95
                    ESSID:"ballout"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-67 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 00:1C:F0:A2:9F:AE
                    ESSID:"IDABOUS"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=6/70  Signal level=-89 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:ath_ie=dd0900037f010100170000

ppp0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:15:E9:E0:A4:95
                    ESSID:"ballout"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-67 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 00:1C:F0:A2:9F:AE
                    ESSID:"IDABOUS"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=6/70  Signal level=-89 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:ath_ie=dd0900037f010100170000

ppp0      Interface doesn't support scanning.
02:00.0 Network controller [0280]: Atheros Communications Inc. AR5418 802.11abgn Wireless PCI Express Adapter [168c:0024] (rev 01)

 modinfo ath_pci
filename:       /lib/modules/2.6.24-19-generic/net/ath_pci.ko
license:        Dual BSD/GPL
version:        svn r3856
description:    Support for Atheros 802.11 wireless LAN cards.
author:         Errno Consulting, Sam Leffler
srcversion:     53828DCE2B2CEC52C9E9103
alias:          pci:v0000168Cd00009013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000019sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000018sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000017sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000016sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000015sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000101Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00001014sv*sd*bc*sc*i*
alias:          pci:v000010B7d00000013sv*sd*bc*sc*i*
alias:          pci:v0000A727d00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000012sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000007sv*sd*bc*sc*i*
depends:        ath_hal,wlan
vermagic:       2.6.24-19-generic SMP mod_unload 
parm:           beacon_cal:int
parm:           countrycode:Override default country code.  Default is 0. (int)
parm:           maxvaps:Maximum VAPs.  Default is 4. (int)
parm:           outdoor:Enable/disable outdoor use.  Default is 0. (int)
parm:           xchanmode:Enable/disable extended channel mode. (int)
parm:           rfkill:Enable/disable RFKILL capability.  Default is 0. (int)
parm:           hal_tpc:Disables manual per-packet transmit power control and lets this be managed by the HAL.  Default is OFF. (int)
parm:           autocreate:Create ath device in [sta|ap|wds|adhoc|ahdemo|monitor] mode. defaults to sta, use 'none' to disable (charp)
parm:           ratectl:Rate control algorithm [amrr|minstrel|onoe|sample], defaults to 'sample' (charp)
parm:           intmit:Enable interference mitigation by default.  Default is 0. (int)
parm:           ath_debug:Load-time driver debug output enable (int)
parm:           ieee80211_debug:Load-time 802.11 debug output enable (int)

 dmesg | grep -e ath
[   41.487549] ath_hal: module license 'Proprietary' taints kernel.
[   41.930415] MadWifi: ath_attach: Switching rfkill capability off.
[   42.106912] ath_pci: wifi0: Atheros 5418: mem=0x90100000, irq=17
[   73.220679] ath0: no IPv6 routers present

uname -m
x86_64

By the way, thank you for your help and reply, hope this info will help out in solving the problem.

Mark

---

### Post by pytheas22 on 2008-09-15
I don't see any errors in the output you posted above, but perhaps the code that you checked out of svn when you built madwifi happened to be buggy.  You could install the latest stable madwifi (dated 3 September) by running:

```
sudo apt-get install build-essential
wget
http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
tar -zxvf madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
cd madwifi-hal-0.10.5.6-r3835-20080801
sudo make
sudo make install
```

Reboot, then please let me know if that helps.

---

### Post by mnj1979 on 2008-09-16
> **pytheas22 said:**
> I don't see any errors in the output you posted above, but perhaps the code that you checked out of svn when you built madwifi happened to be buggy.  You could install the latest stable madwifi (dated 3 September) by running:

```
sudo apt-get install build-essential
wget
http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
tar -zxvf madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
cd madwifi-hal-0.10.5.6-r3835-20080801
sudo make
sudo make install
```

Reboot, then please let me know if that helps.

Hey pytheas, thanks a lot it worked with PEAP connection, I will try it on the coming weekend with WEP to see if it works.

Mark

---

