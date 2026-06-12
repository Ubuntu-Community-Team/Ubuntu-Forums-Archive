---
title: "Changing Default Wireless Network"
date: 2008-05-07
forum: Networking &amp; Wireless
---

### Post by condawg on 2008-05-07
Hey
For some reason, every time I start up my machine it connects me to a crappy wireless network with **** internet.
I'd rather have it connect to my wireless network with good internet.
How can I change the default wireless network?

Thanks =]

---

### Post by him610 on 2008-05-07
How about posting the results from each of these two commands?

```

iwconfig


iwlist scan


```

Maybe we can figure something out.

---

### Post by condawg on 2008-05-07
Alrighty =]

iwconfig -

```
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"NETGEAR"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:4D:53:91:BE   
          Bit Rate:36 Mb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=27/70  Signal level=-69 dBm  Noise level=-96 dBm
          Rx invalid nwid:177392  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

iwlist scan -

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:18:F8:E1:EF:BA
                    ESSID:"magic"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=14/70  Signal level=-81 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 00:18:4D:53:91:BE
                    ESSID:"NETGEAR"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-69 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:ath_ie=dd0900037f0101001dff7f
          Cell 03 - Address: 00:09:5B:DD:C4:2E
                    ESSID:"NETGEAR"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=9/70  Signal level=-86 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 04 - Address: 00:11:D8:0F:D8:1A
                    ESSID:"0036716503"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=7/70  Signal level=-88 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 05 - Address: 00:E0:98:D8:C1:ED
                    ESSID:"Andrews"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=17/70  Signal level=-78 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
          Cell 06 - Address: 00:18:F3:DA:6E:5C
                    ESSID:"0036541801"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=5/70  Signal level=-90 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 07 - Address: 00:E0:98:F1:A6:8A
                    ESSID:"05B404111766"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=9/70  Signal level=-86 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
          Cell 08 - Address: 00:1A:70:78:73:5E
                    ESSID:"tazcam56"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=255/70  Signal level=-96 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 09 - Address: 00:13:10:9E:C4:65
                    ESSID:"DUERAEW"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=1/70  Signal level=-94 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: 00:1C:10:05:D4:E1
                    ESSID:"fullerton"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=2/70  Signal level=-93 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK


```

Thanks =]


EDIT: Plus, even when I DO  connect to the correct network, I get around 6 KB/s on downloads where I should be getting at LEAST 600 KB/s. Any idea why this might be happening?
Been happening since last week when I switched to Ubuntu.

Thanks again =]

---

### Post by him610 on 2008-05-08
You have connected to one of your neighbors' non-secured wireless routers. 

What you might want to do is to connect to your own router with a Cat 5 cable and reconfigure your router for some encryption, either WEP or WPA. It doesn't make much difference; it just depends how secure you want it to be. Be sure you make a note of which key and hex string you use, you will need it later. The idea here is to get some separation. You might want to change your router address to something other than the default setting, like 192.168.72.1 By the way, if your ESSID is still called "NETGEAR" or something generic, change it to something that is unique. Save the the new configuration. Disconnect the Cat 5 cable. All of these actions are documented in your router manual.

On your Ubuntu machine, in Network Settings, set up your wireless settings - ESSID, Password type, Network password, and set your Connection Settings to correspond with the way you setup your router. If you used hex keys in your router use hex keys in the Network Settings. Open the DNS tab, in the box DNS Servers, delete the server address you no longer wish to connect to. Add your own server address; down in the Search Domains box, add your own unique ESSID.

Hope this works for you; it has always worked for me. 

Good luck.

---

### Post by mrbuntuman on 2008-05-08
Don't use wep , use WPA if u can

---

