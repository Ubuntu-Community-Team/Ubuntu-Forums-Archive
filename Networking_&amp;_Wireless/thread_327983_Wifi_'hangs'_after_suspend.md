---
title: "Wifi 'hangs' after suspend"
date: 2006-12-30
forum: Networking &amp; Wireless
---

### Post by uBob on 2006-12-30
Hello,
My first post here. I had my mind set on switching to an OSX or Linux operating system. Some viral issues on XP last week, made me switch earlier than expected after trying the liveCD and dual boot. Since a couple of days I've cleaned my box from XP and completely switched to Ubuntu, and while I still need to adapt to the new environment I generally have no complaints. Except maybe this one.
Activating my Wifi connection was straightforward, it worked immediately. It also starts automatically after a reboot. However I also have the habit of suspending my desktop when I'm not using it for some time. When I wake it up, the Wifi no longer functions. I've found some reference to this problem [here]("http://www.linux.com/article.pl?sid=06/09/05/2055232"). However this refers to a WPA setup. As I do have a Wep key, this does not seem valid?
Maybe some info that I retrieved from iwconfig:
Before suspend
lo        no wireless extensions.

eth2      IEEE 802.11b/g  ESSID:"61126455"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:00:C5:C4:AD:E9   
          Bit Rate:11 Mb/s   Tx-Power=31 dBm   Sensitivity=20/200  
          Retry min limit:8   RTS thr:2347 B   Fragment thr:2346 B   
          Link Quality=202/0  Signal level=-56 dBm  Noise level=-2 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

After suspend
lo        no wireless extensions.

sit0      no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"61126455"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:00:C5:C4:AD:E9   
          Bit Rate:11 Mb/s   Tx-Power=31 dBm   Sensitivity=20/200  
          Retry min limit:8   RTS thr:2347 B   Fragment thr:2346 B   
          Link Quality=197/0  Signal level=-59 dBm  Noise level=-10 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

Thanks in advance & all the best for the new year !

---

