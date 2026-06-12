---
title: "Intel Pro 3945/Dell 6400/ Fiesty 7.04 wireless not connecting"
date: 2007-05-27
forum: Networking &amp; Wireless
---

### Post by cwesks on 2007-05-27
I have a Dell 6400 and I just switched to the Intel PRO 3945 and I see the card with iwconfig but it is not seeing the network.

carlos@carlos-delllnx:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:37   Missed beacon:0

I have read through the forum and have not had any luck.  I would welcome any help.
Thanks,
Carlos

---

### Post by Ateo on 2007-05-27
what is the output of ```
$ iwlist eth1 scan
```

---

### Post by cwesks on 2007-05-27
Thanks for any help I am tired of being tied to the wired connection. 

carlos@carlos-delllnx:~$ iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:18:01:E3:CA:1B
                    ESSID:"IRSV8"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=99/100  Signal level=-22 dBm  Noise level=-22 dBm
                    Extra: Last beacon: 24ms ago

---

### Post by cwesks on 2007-05-27
I found out what it was.  I went in to the router (FiOS Verizion) and took off the MAC filter (the thing were it will only let allowed MAC addresses to connect)  (n00b)  and rebooted and the wifi light came on solid and connected.  

I just wanted to say that if you have a Dell 6400 and the Intel Pro 3945 mini pci card is making the wifi light blink very fast and you have no connection... read the forums and ask questions and you will get some help and ideas that will, hopefully solve your problem also.

Thanks for all of the help and the ideas from all of the threads that had to do with 3945 cards.

:D

carlos@carlos-delllnx:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"IRSV8"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:01:E3:CA:1B
          Bit Rate:54 Mb/s   Tx-Power:15 dBm
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=75/100  Signal level=-59 dBm  Noise level=-60 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:109   Missed beacon:0

---

