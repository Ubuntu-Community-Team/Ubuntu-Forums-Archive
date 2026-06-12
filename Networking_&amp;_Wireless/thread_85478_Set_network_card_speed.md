---
title: "Set network card speed"
date: 2005-11-02
forum: Networking &amp; Wireless
---

### Post by valentin.dumitran on 2005-11-02
I want to set my network card to work at 10Mbps, but I don't know how.
The network card is a VIA VT6102 [Rhine-II] onboard 10/100 fast eth.

I seem to loose a lot of packets and reducing speed helped under windows.

Here's a MTR dump (ususaly it's not this bad):
```
                             My traceroute  [v0.69]
val (0.0.0.0)(tos=0x0 psize=64 bitpattern=0x00)        Thu Nov  3 01:17:41 2005
Resolver error: No error returned but no answers given. of fields   quit
                                       Packets               Pings
 Host                                Loss%   Snt   Last   Avg  Best  Wrst StDev
 1. 192.168.1.1                      77.6%  1671    0.5   0.9   0.4  53.4   3.6
 2. gw-dmz-univ.unitbv.ro            29.7%  1671    0.7   0.7   0.5  52.1   2.4
 3. gwa.unitbv.ro                    30.3%  1671    1.1   0.9   0.6  56.0   2.6
 4. rt1.unitbv.ro                    22.5%  1671    1.0   9.6   0.8 177.5  18.8
 5. 217.73.161.113                   16.3%  1671   18.9  15.8   5.1 164.7  18.5
 6. r-br2-g0-0.Bucharest.roedu.net   31.9%  1671   11.9  13.6   5.0 154.8  14.8
 7. roedunet.rt1.bud.hu.geant2.net   15.9%  1671   41.9  27.7  17.4 139.6  16.1
 8. bpt-b2-pos10-0.telia.net         31.3%  1671   45.1  30.1  17.5 148.9  21.5
 9. hbg-bb1-pos7-2-2.telia.net       10.4%  1671   41.9  45.9  37.3 267.5  14.1
10. hbg-b2-pos1-1-0.telia.net        23.3%  1671   41.0  49.9  37.3 214.2  21.9
11. google-110073-hbg-b2.c.telia.net 17.7%  1670   69.1  68.6  52.8 252.2  27.3
12. 66.249.95.133                    27.0%  1670   57.8  62.0  52.9 210.5  13.5
    66.249.95.135
13. 216.239.43.26                    25.3%  1670   60.9  67.6  53.3 158.8  15.0
    216.239.43.30
    216.239.43.38
    72.14.236.150
    216.239.43.34
    72.14.238.13814. 64.233.183.107  38.4%  1670   71.3  58.4  53.0 162.7   7.5

```

If you have any ideas, please help.
I must mention that the router isn't mine and the problem may be from a bad utp cable (I'll check that out when I have some time).

---

### Post by ranf on 2005-11-02
The command line tools `mii-diag' and `mii-tool' look interesting. 
I never used them though.

---

### Post by valentin.dumitran on 2005-11-02
Thx for your help.

It seems it is 10Mbps after all...
```
root@val:/home/vali# mii-diag
Using the default interface 'eth0'.
Basic registers of MII PHY #1:  0100 784d 0101 8f28 05e1 0000 0004 2801.
 Basic mode control register 0x0100: Auto-negotiation disabled, with
 Speed fixed at 10 mbps, full-duplex.
 You have link beat, and everything is working OK.
 Link partner information is not exchanged when in fixed speed mode.
   End of basic transceiver information.

root@val:/home/vali# mii-tool
eth0: 10 Mbit, full duplex, link ok

```

I'll have to try something else...my internet connection barely works...I can't even open gmail. :(

---

### Post by mips on 2005-11-03
What does the ethernet card connect to ?
Ensure speed/duplex settings on both sides are the same ?
Ensure the cable is good.
Check out Option 1 here, [http://ubuntuforums.org/showthread.php?t=78337](http://ubuntuforums.org/showthread.php?t=78337)

---

