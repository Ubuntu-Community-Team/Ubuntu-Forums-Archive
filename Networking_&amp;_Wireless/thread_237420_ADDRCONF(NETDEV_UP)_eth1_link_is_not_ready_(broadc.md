---
title: "ADDRCONF(NETDEV_UP): eth1: link is not ready (broadcom 4306)"
date: 2006-08-16
forum: Networking &amp; Wireless
---

### Post by closet geek on 2006-08-16
Hi,

I'm running an powerbook G4. I have dapper drake installed. I've cut the firmware out of the recommended file and follow all the steps in the most popular howto on this board.

Yet my wirless wont receive an IP. When I do an iwconfig I get:

eth1      IEEE 802.11b/g  ESSID:"Becki"  Nickname:"Becki"
          Mode:Ad-Hoc  Frequency=2.484 GHz  Access Point: 02:00:5F:74:E2:E0
          Bit Rate:11 Mb/s   Tx-Power=15 dBm
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

and when I perform a sudo iwlist eth1 scan I get what I'd expect:

eth1      Scan completed :
          Cell 01 - Address: 00:06:25:FF:D8:17
                    ESSID:"linksys"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=100/100  Signal level=-207 dBm
                    Extra: Last beacon: 108ms ago
          Cell 02 - Address: 02:00:58:FE:F7:1C
                    ESSID:"Becki"
                    Protocol:IEEE 802.11b
                    Mode:Ad-Hoc
                    Channel:10
                    Encryption key:off
                    Bit Rates:11 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11
                    Quality=100/100  Signal level=-152 dBm
                    Extra: Last beacon: 96ms ago


However 'dhclient eth1' never receives an IP from either network.

I think the appropriate message from dmesg is:

ADDRCONF(NETDEV_UP): eth1: link is not ready (broadcom 4306)

how do I rectify this "link is not ready" problem - Google draws a blank as does searching these forums.

cg

---

### Post by elmo2k3 on 2006-11-08
Hi!

Same problem here with the difference that it sometimes works but often not, after completely rebooting the system. I'm using an orinoco card (D-Link DWL660) and an IBM ThinkPad X24. Un-plugging and re-inserting the card doesn't change anything.

---

### Post by dughutch on 2007-03-15
Bump...

I am getting the same message on a TYAN H2000 with all 3 on board NIC's and Feisty Fawn... Troubleshooting has shown that once logged in the user can click on the network configuration and it suddenly starts working....

Any ideas?

thanks,
Doug

---

