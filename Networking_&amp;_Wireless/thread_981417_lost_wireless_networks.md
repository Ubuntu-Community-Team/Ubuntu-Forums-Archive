---
title: "lost wireless networks"
date: 2008-11-13
forum: Networking &amp; Wireless
---

### Post by MistaMatt90 on 2008-11-13
I recently upgraded to 8.10, and have had no problems.  Wireless had been working without issues.  Yesterday, however, I noticed that it could not find any of my wireless networks.  I've tried rebooting, but that didn't help.  Here's some info: 

```
matt@laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=14 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

Have I somehow inadvertently disabled my wireless card?

Thanks,
Matt

---

### Post by nikgare on 2008-11-14
WHat info does the NetworkManager Applet give about the states of the networks?

---

### Post by superprash2003 on 2008-11-14
post output of lshw -C network from terminal

---

