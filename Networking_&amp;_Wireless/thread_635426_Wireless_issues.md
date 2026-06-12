---
title: "Wireless issues"
date: 2007-12-08
forum: Networking &amp; Wireless
---

### Post by dondon391 on 2007-12-08
Can someone please help!!
I have recently upgraded to Gutsy, and my wireless has now ceased to work.  I have followed various instructions on these forums and have now changed to Wicd with a static IP.  Wicd goes through the motions of connecting to my network but then says 'connected to none at 0%' in the status bar, and i can't connect to my server.
I can connect to other networks in my list (even though i probably shouldn't) with no problems, and they are DHCP.  Have tweaked every setting i know to no avail.
I run a dynalink RTA1025w ADSL modem and a Netgear Wg311v3 wireless card, both the same before the upgrade
here is output of iwconfig
***
don@don-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth1      no wireless extensions.
***
Thanks for your help, am a new user to linux and enjoying it but wondering if this is worth the hassle.

---

