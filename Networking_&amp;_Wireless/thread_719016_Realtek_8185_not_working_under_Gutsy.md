---
title: "Realtek 8185 not working under Gutsy"
date: 2008-03-08
forum: Networking &amp; Wireless
---

### Post by KenMac on 2008-03-08
Hi all,
I have a Gateway mt3423 laptop with a rtl8185 wireless card.  I had the card working in Feisty using NDISwrapper but the card stopped working after I upgraded to Gutsy.  I tried blacklisting r8185 and r8180 as suggested in the forums and this made it possible to 'see' networks but I am still unable to connect.  Here is my output from iwlist scan:

```
ken@Max:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:13:10:B5:9B:61
                    ESSID:"IHDI-EC"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:32/100  Signal level:-75 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:17:0F:22:25:10
                    ESSID:"ukyedu"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:51/100  Signal level:-63 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:1C:F9:C3:7D:70
                    ESSID:"ukyedu"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:32/100  Signal level:-75 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 04 - Address: 00:12:43:F1:6E:20
                    ESSID:"ukyedu"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:39/100  Signal level:-71 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

``` 

Any help would be greatly appreciated!
Thanks!

---

### Post by KenMac on 2008-03-10
*BUMP*
Any ideas?
Thanks!

---

### Post by KenMac on 2008-03-10
*bump*
plz :)

---

### Post by RxRated on 2008-03-10
I just spent days getting a 8180 card to work with Gutsy.  My problems were with using encryption.  The kernel would freeze when you tried to connect.  I had no problems connecting to unsecured networks.  Did you modify /etc/modprobe.d/blacklist by typing blacklist r8180 and blacklist r8185 without # sign?  You may have both drivers (net 8185 and ndiswrapper) loading and trying to run.  I also had better luck using ndiswrapper and wicd instead of network manager.

---

### Post by KenMac on 2008-03-14
Thanks very much for the reply.
I blacklisted both r8180 and r8185 after which I can even see signal strengths in Newtwork Manager but I still cannot connect.  I will give wicd a try and see if that helps.

---

### Post by darth rave on 2008-03-28
These drivers worked for me.

It took me hours to figure out a solution and turns out they were already on my flashdrive from something else.

I used the windows wireless drivers program to install them.

---

