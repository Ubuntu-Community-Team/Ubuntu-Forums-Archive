---
title: "Madwifi svn r2525 - Unable to set countrycode or regdomain on Ubiquity SRC in Feisty"
date: 2007-07-01
forum: Networking &amp; Wireless
---

### Post by aeaster on 2007-07-01
Hi,

I have an issue whereby I am unable to set the countrycode or regdomain for my wireless card - Ubiquiti SRC (300mW). I am running Ubuntu 7.04 and madwifi svn revision 2525; when I query the card, the regdomain and countrycode are shown as 0.

On re-installation of the madwifi driver I am able to correctly set the countrycode and the channels are listed correctly; however, as soon as I reboot the settings all disappear. I have tried adding "ath_pci countrycode=826" to the /etc/modules file but to no avail.

```
% grep -r . /proc/sys/dev/{wifi0,ath}/* | egrep 'country|reg'

/proc/sys/dev/wifi0/countrycode:0
/proc/sys/dev/wifi0/regdomain:0
/proc/sys/dev/ath/countrycode:0
```
```
% wlanconfig ath0 list freq

Channel   1 : 2412  Mhz 11g          Channel  48 : 5240  Mhz 11a Dynamic  
Channel   2 : 2417  Mhz 11g          Channel  50 : 5250  Mhz 11a Static   
Channel   3 : 2422  Mhz 11g          Channel  52 : 5260  Mhz 11a          
Channel   4 : 2427  Mhz 11g          Channel  56 : 5280  Mhz 11a Dynamic  
Channel   5 : 2432  Mhz 11g          Channel  58 : 5290  Mhz 11a Static   
Channel   6 : 2437  Mhz 11g Dynamic  Channel  60 : 5300  Mhz 11a          
Channel   7 : 2442  Mhz 11g          Channel  64 : 5320  Mhz 11a          
Channel   8 : 2447  Mhz 11g          Channel 149 : 5745  Mhz 11a          
Channel   9 : 2452  Mhz 11g          Channel 152 : 5760  Mhz 11a Static   
Channel  10 : 2457  Mhz 11g          Channel 153 : 5765  Mhz 11a Dynamic  
Channel  11 : 2462  Mhz 11g          Channel 157 : 5785  Mhz 11a          
Channel  36 : 5180  Mhz 11a          Channel 160 : 5800  Mhz 11a Static   
Channel  40 : 5200  Mhz 11a Dynamic  Channel 161 : 5805  Mhz 11a Dynamic  
Channel  42 : 5210  Mhz 11a Static   Channel 165 : 5825  Mhz 11a          
Channel  44 : 5220  Mhz 11a  
```
```
% iwlist ath0 txpower

ath0      8 available transmit-powers :
          0 dBm         (1 mW)
          7 dBm         (5 mW)
          9 dBm         (7 mW)
          11 dBm        (12 mW)
          13 dBm        (19 mW)
          15 dBm        (31 mW)
          17 dBm        (50 mW)
          19 dBm        (79 mW)
          Current Tx-Power:19 dBm       (79 mW)
```

I am based in the UK so after looking at 'http://madwifi.org/wiki/UserDocs/CountryCode' I ran: 
```
% sudo modprobe ath_pci countrycode=826
```
and tried:
```
% sudo sysctl dev.wifi0.regdomain=55

error: "Operation not permitted" setting key "dev.wifi0.regdomain"
```

I understand that the regdomian may be set to 0 as this is a universal type code. But if any one can add additional light on this, I would really appreciate it.

I have seen some posts that suggest re-programming the EEPROM as a possible solution; however, many of these also indicate that this is a tricky process and should not be done until all other avenues have been exhausted.

Thanks in advance,

Adam


Here is some additional system information:

```
% uname-a
Linux Laptop 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux

% lspci -v
07:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
        Subsystem: Atheros Communications, Inc. Ubiquiti Networks SuperRange a/b/g Cardbus Adapter
        Flags: bus master, medium devsel, latency 168, IRQ 16
        Memory at 34000000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [44] Power Management version 2

% dmesg
[   19.524000] ath_hal: 0.9.30.13 (AR5210, AR5211, AR5212, AR5416, RF5111, RF5112, RF2413, RF5413, RF2133)
[   19.648000] wlan: 0.8.4.2 (svn r2525)
[   19.696000] ath_pci: 0.9.4.5 (svn r2525)
[   20.280000] ath_pci: switching rfkill capability off
[   20.280000] ath_pci: ath_pci: switching per-packet transmit power control off
[   20.344000] ath_rate_sample: 1.2 (svn r2525)
[   20.360000] wifi0: 11a rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   20.360000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   20.360000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   20.360000] wifi0: turboA rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   20.360000] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   20.360000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   20.360000] wifi0: mac 5.9 phy 4.3 radio 3.6
[   20.360000] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   20.360000] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   20.360000] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   20.360000] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   20.360000] wifi0: Use hw queue 8 for CAB traffic
[   20.360000] wifi0: Use hw queue 9 for beacons
[   20.396000] wifi0: Atheros 5212: mem=0x34000000, irq=16
```

---

