---
title: "Thinkpad T60 Wireless Question"
date: 2007-12-12
forum: Networking &amp; Wireless
---

### Post by raheelk on 2007-12-12
I recently installed Gutsy Gibbons (7.10) on a thinkpad t60 laptop. However, I am attempting to get wireless working. The network manager sees my router "lynksys" with good reception, however, attempting to connect to it nothing happens. It can't connect to any of my neighbor's routers which are unsecure. I am at a loss, what do I need to do? I've googl'd everything and majority of the people who have T60 seems to have had their wireless work "out-of-the-box".

I've pasted my iwconfig and lpsci

ubuntu@ubuntu:~$ iwconfig
lo                  no wireless extensions.

eth0              no wireless extensions.

irda0              no wireless extensions.

wifi0               no wireless extensions.

ath0               IEEE 802.11a ESSID: "lynksys"   Nickname:""
                      Mode: Managed Frequency: 5.22 GHz Access Point: Not-Associated
                      Bit Rate: 1 Mb/s Tx-power:8 dBm Sensitivity=1/1
                     Retry: off RTS thr:off Fragment thr:off
                     Power Management:off
                     Link Quality= 37/70 Signal level=-58 dBm Noise level=-95 dBm
                     Rx invalid nwid:1615 Rx invalid crypt:0 Rx invalid frag:0
                     Tx excessive retries:0 Invalid misc:0 Missed beacon:0

lspci shows "Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

Any help is greatly appreciated. Thanks.

---

