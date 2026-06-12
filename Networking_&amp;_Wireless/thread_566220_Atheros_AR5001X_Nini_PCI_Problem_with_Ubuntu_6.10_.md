---
title: "Atheros AR5001X Nini PCI Problem with Ubuntu 6.10 - 7.10"
date: 2007-10-03
forum: Networking &amp; Wireless
---

### Post by Bleys on 2007-10-03
Notebook Toshiba Satellite 2430-201
Toshiba WLan Mini PCI Card (Atheros AR5001X)

Dual Boot (Win/Ubuntu)

Win XP SP2: The Card works just fine out of the Box
Ubuntu 6.06LTS: The Card works just fine out of the Box, even from LiveCD!

Ubuntu 6.10 - 7.10: No Connection possible (have tried all Versions)

1. Can see only Wlan Networks with same Channel...
2. From the Network Icon I choose my WLan Router
The Icon start spinning
A Dialog appears, ask vor Passwort (Router: WEP 128 is adjusted)
Enter 13 Charakter Ascii Password 
After a Minute spinning the Dialog comes again.... and so on...

switch to Manual Configuration: Allso, no Connection

> ralf@lappi:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11a  ESSID:""  Nickname:""
          Mode:Managed  Frequency:5.805 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:0 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-98 dBm  Noise level=-98 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

irda0     no wireless extensions.

> dmseg (Wlan relatet)
[   25.420000] ath_hal: module license 'Proprietary' taints kernel.
[   25.424000] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   25.980000] wlan: 0.8.4.2 (0.9.3.2)
[   26.028000] ath_pci: 0.9.4.5 (0.9.3.2)
--------
[   27.164000] ath_rate_sample: 1.2 (0.9.3.2)
[   27.164000] wifi0: 11a rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   27.164000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   27.164000] wifi0: turboA rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   27.164000] wifi0: H/W encryption support: WEP AES
[   27.164000] wifi0: mac 4.2 phy 3.0 5 GHz radio 1.7 2 GHz radio 2.3
[   27.164000] wifi0: Use hw queue 0 for WME_AC_BE traffic
[   27.164000] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   27.164000] wifi0: Use hw queue 0 for WME_AC_VI traffic
[   27.164000] wifi0: Use hw queue 0 for WME_AC_VO traffic
[   27.164000] wifi0: Use hw queue 8 for CAB traffic
[   27.164000] wifi0: Use hw queue 9 for beacons
[   27.204000] wifi0: Atheros 5211: mem=0xd2000000, irq=5

To compare: The working Wlan Output with 6.06 LiveCD :

> ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ath0      IEEE 802.11b  ESSID:"PS"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:A0:C5:EC:69:5C
          Bit Rate:11 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=41/94  Signal level=-54 dBm  Noise level=-95 dBm
          Rx invalid nwid:1223  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:24

sit0      no wireless extensions.


[17179676.132000] ath_hal: module license 'Proprietary' taints kernel.
[17179676.132000] ath_hal: 0.9.14.9 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2 413)
[17179676.292000] wlan: 0.8.6.0 (EXPERIMENTAL)
[17179676.360000] ath_rate_sample: 1.2
[17179676.368000] ath_pci: 0.9.6.0 (EXPERIMENTAL)
[17179676.368000] ACPI: PCI Interrupt 0000:02:02.0[A] -> Link [LNKC] -> GSI 5 (l evel, low) -> IRQ 5
[17179676.716000] Build date: Jul 10 2006
[17179676.716000] Debugging version (IEEE80211)
[17179676.716000] ath0: 11a rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbp s 54Mbps
[17179676.716000] ath0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[17179676.716000] ath0: turboA rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48 Mbps 54Mbps
[17179676.720000] ath0: H/W encryption support: WEP AES
[17179676.720000] ath0: mac 4.2 phy 3.0 5ghz radio 1.7 2ghz radio 2.3
[17179676.720000] ath0: Use hw queue 0 for WME_AC_BE traffic
[17179676.720000] ath0: Use hw queue 0 for WME_AC_BK traffic
[17179676.720000] ath0: Use hw queue 0 for WME_AC_VI traffic
[17179676.720000] ath0: Use hw queue 0 for WME_AC_VO traffic
[17179676.720000] ath0: Use hw queue 8 for CAB traffic
[17179676.720000] ath0: Use hw queue 9 for beacons
[17179676.720000] Debugging version (ATH)
[17179676.720000] ath0: Atheros 5211: mem=0xd2000000, irq=5


---

### Post by Bleys on 2007-10-03
Just tried the Kubuntu 7.10 Beta

Same Thing...

The "Activation Wireless Network Connection" Advise shows:
Activation stage: Configuring device (28%)
after a Minute the Encryption Dialog pops up.. and so on

Device: AR5211 802.11ab NIC (ath0)

---

### Post by Bleys on 2007-10-03
Sorry for my bad english.
Add to Panel: network 
Properties - Name: wifi0

I can see Trafic! but when i try to configure: The interface not exist (Die Schnittstelle existiert nicht)

Confused now...

---

### Post by Bleys on 2007-10-04
Problem solved with ndiswrapper and a Third Party XP Driver, found with Pciid on [http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)
The original XP Driver vor this Card does not work.

---

