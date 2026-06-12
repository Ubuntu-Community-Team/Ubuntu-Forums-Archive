---
title: "inspiron 1520 with wireless doesn't work"
date: 2008-06-21
forum: Networking &amp; Wireless
---

### Post by yu090jp on 2008-06-21
hi all

Although I followed the operation in the url below, I have yet to work it out.
[http://ubuntuforums.org/showthread.php?t=112526&highlight=inspiron+1520](http://ubuntuforums.org/showthread.php?t=112526&highlight=inspiron+1520)

It appears that I could get by to run the driver. but it couldn't find out ESSID.


> sudo iwlist wlan0 scan shows
wlan0     Scan completed :
          Cell 01 - Address: 00:0F:B5:E8:A7:0A
                    ESSID:""
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=74/100  Signal level=-60 dBm  Noise level=-88 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000003874a03c


>lspci shows
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

>ndismod shows
ndiswrapper           192920  0 

>iwconfig shows

wlan0     IEEE 802.11g  ESSID:"xxx"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:B5:E8:A7:0A   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


I have tried everything that I can think of..
if you have any idea to try, let me know please.
feel free to ask me for any further information, if it helps
thank you in advance

---

