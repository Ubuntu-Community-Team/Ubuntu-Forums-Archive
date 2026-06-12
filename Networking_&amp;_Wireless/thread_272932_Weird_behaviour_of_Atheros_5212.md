---
title: "Weird behaviour of Atheros 5212"
date: 2006-10-07
forum: Networking &amp; Wireless
---

### Post by Jackaroo on 2006-10-07
Hi,

I've installed kubuntu 6.06 on my Toshiba libretto U100. Everything works well, except the Atheros 5212 WLAN adaptor. The driver is loaded, it scans for networks and is also able to find networks. The problems is, that the adaptor does not retreive the ESSIDs right. My ESSID at home (DWL 7000 AP) is "Rumpel-Base". When I scan for networks I can only find a combination of weird symbols. Does anybody have an idea how to fix this? Here my details:

[I]root@localhost:/home/jackaroo# iwconfig ath0
ath0      IEEE 802.11  **ESSID:"Rumpel-Base"**
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[/I]


[I]root@localhost:/home/jackaroo# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:0D:88:56:2E:CA
                   **ESSID:"&#506;"**
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/94  Signal level=-71 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:rsn_ie=3010000000037f20020000037f0000037f20

sit0      Interface doesn't support scanning.
[/I]


[I]root@localhost:/home/jackaroo# dmesg | less | grep ath
[17179590.264000] ath_hal: module license 'Proprietary' taints kernel.
[17179590.264000] ath_hal: 0.9.14.9 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413)
[17179590.320000] ath_rate_sample: 1.2
[17179590.328000] ath_pci: 0.9.6.0 (EXPERIMENTAL)
[17179591.068000] ath0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[17179591.068000] ath0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[17179591.068000] ath0: turboG rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[17179591.068000] ath0: H/W encryption support: WEP AES AES_CCM TKIP
[17179591.068000] ath0: mac 7.9 phy 4.5 radio 5.6
[17179591.068000] ath0: Use hw queue 1 for WME_AC_BE traffic
[17179591.068000] ath0: Use hw queue 0 for WME_AC_BK traffic
[17179591.068000] ath0: Use hw queue 2 for WME_AC_VI traffic
[17179591.068000] ath0: Use hw queue 3 for WME_AC_VO traffic
[17179591.068000] ath0: Use hw queue 8 for CAB traffic
[17179591.068000] ath0: Use hw queue 9 for beacons
[17179591.068000] ath0: Atheros 5212: mem=0xcfff0000, irq=11
[/I]


[I]root@localhost:/home/jackaroo# dpkg -s wireless-tools
Package: wireless-tools
Status: install ok installed
Priority: extra
Section: net
Installed-Size: 332
Maintainer: Guus Sliepen <guus@debian.org>
Architecture: i386
Version: 27+28pre13-1ubuntu2
Depends: libc6 (>= 2.3.4-1), libiw28 (>= 27+28pre13)
Conffiles:
 /etc/network/if-pre-up.d/wireless-tools e95ae0b172b744370a400140059d52d4
 /etc/network/if-post-down.d/wireless-tools 5ddd964cf276955df3353def88eb5268
Description: Tools for manipulating Linux Wireless Extensions
 This package contains the Wireless tools, used to manipulate
 the Linux Wireless Extensions. The Wireless Extension is an interface
 allowing you to set Wireless LAN specific parameters and get the
 specific stats.
[/I]

Same problem using KWiFi :(

Thanks for your help, best regards,
Jackaroo

---

### Post by tturrisi on 2006-10-07
There's conflicting data...
iwconfig says encryption = off
iwlist says encryption = on

set ap to encryption off,
then try just:
iwlist ath0 scan

The ssid standard states that the ssid case sensitive text string is supposed to consist of a max of 32 alph numeric characters. There are supposed to be no restrictions about what characters can be used in a ssid, however, I have seen issues with hyphens used in wep & wpa keys in Ubuntu, thus the hyphen in your ssid may be what is causing the issue.

---

### Post by Jackaroo on 2006-10-07
Thanks for your quick reply.

I have changed the AP's SSID to "rumpel", switched encryption off and then on again, together with the libretto's adaptor. Thing have not changed unfortunately. Here's the result with encryption on on both sides and changed SSID:

[I]ath0      Scan completed :
          Cell 01 - Address: 00:0D:88:56:2E:CA
                    ESSID:"rrDD&#9618;<H&#65533;;&#65533;Z]"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/94  Signal level=-69 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:rsn_ie=3010000000037f20020000037f0000037f20
[/I]

---

### Post by tturrisi on 2006-10-07
strange characters!

Try using the net-admin applet to connect:
System > Administration > Networking

Set wep key using Hexadecimal (not Plain).  You may have to use a hyphen in between every 4 characters of wep key:
abcd-efgh-hijk-lmno-pqrs-1234-5678 etc etc

---

