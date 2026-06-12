---
title: "Boot problems Netgear WG511T"
date: 2006-11-12
forum: Networking &amp; Wireless
---

### Post by G@itp on 2006-11-12
I'm having some issues with my netgear WG511T wireless PCcard.

It doesn't seem to work after booting dapper drake.
When i deactivate and activate the wireless card manually it works fine.

iwconfig after boot:
lo        no wireless extensions.

eth0      no wireless extensions.

ath0      IEEE 802.11  ESSID:"SpeedTouchxxxxx"
          Mode:Managed  Frequency:2.422 GHz  Access Point: Not-Associated
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


iwconfig after deactivate/activate:
lo        no wireless extensions.

eth0      no wireless extensions.

ath0      IEEE 802.11g  ESSID:"SpeedTouchxxxxx"
          Mode:Managed  Frequency:2.432 GHz  Access Point: 00:02:2D:61:E4:7C
          Bit Rate:11 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=44/94  Signal level=-51 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

How can I solve this problem so that it works after boot, the settings entered are correct, i  only have to restart the wireless card (Ath0).

---

