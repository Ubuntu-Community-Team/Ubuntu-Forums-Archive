---
title: "Wireless IPW2200BG 4 times slower than XP"
date: 2006-10-07
forum: Networking &amp; Wireless
---

### Post by ileavache on 2006-10-07
Hi,
I have installed dapper on my thinkpad t41p. It has an IPW2200BG. Eveything is fine except that my wireless connection is 4 times slower than with XP (I dual boot). I measure the speed with the [speakeasy]("http://www.speakeasy.net/speedtest/") speed test.

My SBC DSL connection is 6016 kbps Down / 768 up.
- On XP, I get over 4000 kbps every time I run the test
- On Ubuntu, I cannot above a meager 900 kpbs.
(With a Wired connection on Ubuntu, I also get above 4000 easily).

Desperate to get the same test results, I have stupidly and ignorantly tried all the various trips (diable ipv6, i686 image) that google yields. Nothing does it. Can't feel any difference while browsing since 900k is not that bad after all. Also, pinging seems to be about 20% slower.

Does anybody understand what's going on?
Thanks a lot in advance for the help.

My iwconfig is as follows:

eth1     IEEE 802.11b  ESSID:"2WIRE751"
         Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0D:72:48:42:D9
         Bit Rate=11 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0
         Retry limit:7   RTS thr:off   Fragment thr:off
         Power Management:off
         Link Quality=98/100  Signal level=-26 dBm  Noise level=-80 dBm
         Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
         Tx excessive retries:0  Invalid misc:0   Missed beacon:1

---

