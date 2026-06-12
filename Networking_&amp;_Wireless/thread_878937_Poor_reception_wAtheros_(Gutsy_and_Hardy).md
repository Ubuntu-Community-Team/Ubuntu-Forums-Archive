---
title: "Poor reception w/Atheros (Gutsy and Hardy)"
date: 2008-08-03
forum: Networking &amp; Wireless
---

### Post by mfbernstein on 2008-08-03
Hi all,

have been using Gutsy (and more recently Hardy) on my Thinkpad X61 (w/Atheros 5212). This is the 64-bit version, so I've stuck to madwifi. Problem is that reception is poor - I need to be right next to the router to be able to successfully connect. Farther away (more than about 15 feet), I get okay signal strength (50-60%), but NetworkManager never successfully gets an IP (via dhclient) from the router.

I'm pretty sure that the issue is not the wireless card or the router, since the same laptop can connect without difficulty from much farther away, when running XP.

Any ideas? Thanks,

MFBernstein

---

### Post by amontero on 2008-11-02
Bump.

I have the same problem with my T61 and Intrepid Ibex.  If I get 15 ft away from the router, it drops the signal.  The system works fine in Vista.  Any ideas?  This is driving me crazy!


lspci:
amontero@kronos:~$ lspci | grep -i ethernet
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
03:00.0 Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)

iwconfig:
amontero@kronos:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"anderson"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:21:29:B0:D5:9B   
          Bit Rate:5 Mb/s   Tx-Power:8 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=72/70  Signal level=-23 dBm  Noise level=-95 dBm
          Rx invalid nwid:1161522  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

---

### Post by amontero on 2008-11-02
Can anybody help out with this?  I'm still stuck.  I'm having to run windows because if I get 10 ft away from my router, it will drop the connection in ubuntu.

This is a tricky problem because if I'm right next to the router, it will connect (but tx rates are still slow).  So the driver does work.  It just works really badly.

Any suggestions?  Anything would help!

Thanks,
Anthony

---

