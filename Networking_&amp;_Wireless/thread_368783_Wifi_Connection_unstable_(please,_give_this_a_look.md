---
title: "Wifi Connection unstable (please, give this a look and help!)"
date: 2007-02-23
forum: Networking &amp; Wireless
---

### Post by Lorenz on 2007-02-23
Hi guys!

I'm having an interesting problem with my Wifi Connection.
It's saved with a 64 Bit WEP Key. I'm running Ubuntu Edgy on a T60 with a IPW3945 card.

The problem is, I have got a signal for 5 seconds - then I lose it and it shows me as disconnected. After a second I get the signal again. See here the output when running "iwconfig".


1. I have a connection (for max. 5 seconds)

eth1      IEEE 802.11b  ESSID:"SpeedTouch7681EA"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:02:2D:76:81:EA   
          Bit Rate=11 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=99/100  Signal level=-72 dBm  Noise level=-73 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:3726   Missed beacon:0

2. I have no connection (for 1-2 seconds)

eth1 unassociated ESSID:"SpeedTouch7681EA"
Mode:Managed Frequency=nan kHz Access Point: Not-Associated
Bit Rate=0 kb/s Tx-Power:16 dBm
Retry limit:15 RTS thr:off Fragment thr:off
Power Management:off
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:3592 Missed beacon:0 

Please help me with this!

---

### Post by sdide on 2007-02-23
Hey,

I'm not exactly sure, but ... you loose a lot of packets.
from your output:
"Invalid misc:3726"

your noise/signal ratio doesn't look too good.
you have :
"Link Quality=99/100 Signal level=-72 dBm Noise level=-73 dBm"

If I look at my link, I have:
"Link Quality=51/100  Signal level=-70 dBm  Noise level=-88 dBm"

So maybe you get a lot of disconnects because there is too much noise.
Try changing to another channel on your AP.

---

