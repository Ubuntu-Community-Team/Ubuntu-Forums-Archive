---
title: "loss of ESSID Associated with Broadcom 4306"
date: 2007-02-06
forum: Networking &amp; Wireless
---

### Post by sephirothsigep on 2007-02-06
after about 20 min my Essid association is lost. is there a script that is checking for association that could be causing this problem. could this be the ubuntu network manager or is it my card.

(after 20 minutes, it shows not-associated)
> root@jenova:/# /sbin/iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:48 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

(I then have to re-associate it with my ap)
> 
[email]root@jenova:/etc/cron.hour[/email]ly# /sbin/iwconfig eth1 essid IndianaTechOpen
[email]root@jenova:/etc/cron.hour[/email]ly# /sbin/iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"IndianaTechOpen"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:17:0F:E4:31:A0   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

and then can re-run dhcp

---

### Post by spd106 on 2007-02-06
I think it's more likely to be the bcm43xx driver. I found this happened a lot with my card, so I switched to ndiswrapper.

---

### Post by sephirothsigep on 2007-02-06
I am using ndiswrapper 
I used the following how to  to set up my wireless
[http://www.ubuntuforums.org/showthread.php?t=201902](http://www.ubuntuforums.org/showthread.php?t=201902)

---

### Post by spd106 on 2007-02-06
Sorry, I saw eth1 and assumed the worst.

Maybe you would have a better experience with a newer version of ndiswrapper, I've had good results with v1.34. Though it does mean building from source.

---

