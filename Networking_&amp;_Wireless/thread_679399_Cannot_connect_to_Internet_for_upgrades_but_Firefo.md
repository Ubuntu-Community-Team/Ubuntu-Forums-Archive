---
title: "Cannot connect to Internet for upgrades but Firefox connects"
date: 2008-01-26
forum: Networking &amp; Wireless
---

### Post by san2004 on 2008-01-26
Hello Everybody.
I m running Ubuntu 7.10 32 bit version on a desktop.
I connect to the internet through Dlink PCI wifi card (Atheros Chipset) and wireless broadband modem.
I've disabled ipv6 both in Firefox as well as system wide by changing the line in /etc/modprobe.d/aliases   
from alias net-pf-10 ipv6 to alias net-pf-10 off
Now I am able to browse through Firefox but upgrades/ updates are not working.

Output of 

~$** lsmod | grep ipv6**
~$ 

Output of 

**iwlist scan**
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:50:F1:12:12:10
                    ESSID:"WA1003A"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=28/70  Signal level=-67 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:15:E9:F9:3C:3F
                    ESSID:"default"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=160/70  Signal level=-191 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100


Any suggestions ?
Thanks.

---

### Post by bwtranch on 2008-01-26
I've been looking at this thing and can't find a thing wrong. The only thing I can figure is that maybe a server is down. If Firefox is up, then you are up. To verify this, just ping something, like anything, google or whatever. ping ubuntu, for that matter.

---

