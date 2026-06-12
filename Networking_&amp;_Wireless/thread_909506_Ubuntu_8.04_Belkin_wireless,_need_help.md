---
title: "Ubuntu 8.04 Belkin wireless, need help"
date: 2008-09-03
forum: Networking &amp; Wireless
---

### Post by alex0207 on 2008-09-03
Hey guys, i need some help.

I'm dual booting XP and Ubuntu 8.04, and i cannot seem to get the wireless working.

I've installed the ndiswrapper utility, and in the internet manager the wireless card is displaying. However it is still not wokring.

When i run the command iwconfig, i get the results:

```
alex@alex-ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"joking geoff's network"  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

alex@alex-ubuntu:~$ 
```

Here is the link status of the connection on XP:
[IMG]http://i170.photobucket.com/albums/u266/Moreton02/internet.jpg[/IMG]
Here are the Belkin software details:
[IMG]http://i170.photobucket.com/albums/u266/Moreton02/internetbelkinproduct.jpg[/IMG]

I have an idea that the channels are not the same, in Ubuntu it is set as 0 but in XP it is 1?

Cheers guys

---

