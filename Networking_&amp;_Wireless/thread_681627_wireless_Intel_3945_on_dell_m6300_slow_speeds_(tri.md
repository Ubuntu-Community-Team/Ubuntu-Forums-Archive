---
title: "wireless Intel 3945 on dell m6300 slow speeds (tried workarounds)"
date: 2008-01-29
forum: Networking &amp; Wireless
---

### Post by luckyluca on 2008-01-29
Hello,

First of all I've made extensive research on the topic and tried the following suggestions unsuccessfully:
I'm using the standard restricted driver.
I've disabled ipv6
I've changed the router address from 192.168.0.1 to 192.168.100.1 (just in case)
I've removed nm-applet from startup and started using wifi-radar (but this isn't working as it doesn't let me connect as the connect button is not visible in the gui)

I'm still getting speeds that are 20 times slower than it should and going from 1.5Mbps to 50kbps (everything works fine in windows xp).

Should I update drivers, switch to wifi-radar or else? help :)

Thanks a lot
Luca

ubuntu 7.10 64bit
dell m6300 laptop

---

### Post by hahahan on 2008-01-29
Luckyluca,

Does iwconfig list any rate that the card is working on currently?

regards,

---

### Post by luckyluca on 2008-01-29
iwconfig printout:
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"VIRUS"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:18:4D:0D:23:B4   
          Bit Rate:54 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=88/100  Signal level=-46 dBm  Noise level=-68 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:8   Missed beacon:0

---

### Post by luckyluca on 2008-01-31
Ok here's how I solved it:
it seems thanks to a combination of
-disabling the ipv6
[http://ubuntuforums.org/showthread.php?t=282034](http://ubuntuforums.org/showthread.php?t=282034)
-disabling wireless encryption

Wifi is now as fast as it should!
I've found a good solution to the non-encrypted connection by enabling authorized access only in the router. This should keep away intruders :)

Thanks
Luca

---

