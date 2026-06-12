---
title: "iwlist showing 2 entries for WAP?"
date: 2007-02-21
forum: Networking &amp; Wireless
---

### Post by NotExcessive on 2007-02-21
I'm using an Atheros 5400G card on my laptop, and occasionally, the connection will drop out.  Looking at the syslog file, I see that when it has trouble reconnecting, it's complaining about no matching SSID being found. My 3Com WAP  is set to hide the SSID, and when things are working normally, iwlist will show:

> lo        Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 12:5a:9f:f3:00:d3
                    ESSID:""
                    Mode:Master
                    Frequency:2.417 GHz (Channel 2)
                    Quality=14/94  Signal level=-81 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
          Cell 02 - Address: 12:5a:9f:f3:00:d3
                    ESSID:"NetworkWiFi"
                    Mode:Master
                    Frequency:2.417 GHz (Channel 2)
                    Quality=14/94  Signal level=-81 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  

eth0      Interface doesn't support scanning.

When things fall over, I only see:

> 
lo        Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 12:5a:9f:f3:00:d3
                    ESSID:""
                    Mode:Master
                    Frequency:2.417 GHz (Channel 2)
                    Quality=14/94  Signal level=-81 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
        
eth0      Interface doesn't support scanning.


So  when there's no entry for "Cell 02", which has an ESSID, it can't connect. Question is, why am I seeing two entries (Cell 01 and Cell 02) for the one and only WAP, with one entry having the ESSID? Is this a fault with the atheros driver?

---

### Post by NotExcessive on 2007-02-23
One thing I noticed in examining /var/log/syslog was that 'AP_SCAN 1' was being sent to the card. In my old laptop installation with Gentoo, I had 'ap_scan=2' set in /etc/wpa_supplicant.conf, which worked perfectly for my network which is set to hidden SSID. Is there a way to configure the network manager deamon to use "ap_scan=2" when it runs?

---

