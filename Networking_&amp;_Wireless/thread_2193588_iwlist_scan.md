---
title: "iwlist scan"
date: 2013-12-13
forum: Networking &amp; Wireless
---

### Post by donmatas on 2013-12-13
Hi,

I am trying to find which wifi channel I should use. The problem is that when I use "iwlist scan" it shows only the data of my own connection. I have read that it should show data about every connection detected by the antenna.
Any help?

```
$ iwlist scan
lo        Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:1D:D2:12:AE:40
                    **Channel:8**
                    Frequency:2.447 GHz (Channel 8)
                   ** Quality=34/70**  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"ANARKIA-TROPICAL"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 44500ms ago
                    IE: Unknown: 0010414E41524B49412D54524F504943414C
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030108
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6C0016FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D1608000400000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05010018127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706555320010B10

eth0      Interface doesn't support scanning.

```

---

### Post by steeldriver on 2013-12-13
To see other interfaces, you probably need to run it with sudo

```
sudo iwlist scan
```

Alternatively, if you are running a newish desktop version, you can use nm-tool or even nmcli e.g.

```
nmcli dev wifi list
```

Neither of these needs sudo - and the output is easier to read

---

### Post by chili555 on 2013-12-13
Just for the benefit of all the searchers out there:```
man iwlist
```> Triggering scanning is a privileged operation (root only) and  **normal  users  can  only  read left-over  scan  results.**In this context, root means with sudo.

---

### Post by donmatas on 2013-12-13
> **steeldriver said:**
> To see other interfaces, you probably need to run it with sudo

```
sudo iwlist scan
```

Alternatively, if you are running a newish desktop version, you can use nm-tool or even nmcli e.g.

```
nmcli dev wifi list
```

Neither of these needs sudo - and the output is easier to read

Amazing dude. Both options work, but nmcli dev wifi list does not show the channel (or I cannot find )

```
 $ nmcli dev wifi list
SSID                              BSSID               MODO             FREC       TASA       SEÑAL    SEGURIDAD  ACTIVO  
'MACA'                            58:98:35:BE:37:68   Infraestructura  2412 MHz   54 MB/s    37       WPA WPA2   no      
'depa'                            00:1E:58:C3:6A:11   Infraestructura  2462 MHz   54 MB/s    34       WPA        no      
'Depto-1912'                      A4:B1:E9:89:1D:87   Infraestructura  2422 MHz   54 MB/s    29       WPA WPA2   no      
'Omega'                           38:46:08:EA:07:AC   Infraestructura  2437 MHz   54 MB/s    29       WPA2       no      
'Ivalcarce'                       A4:B1:E9:AB:C0:05   Infraestructura  2437 MHz   54 MB/s    29       WPA WPA2   no      
'locoyou'                         20:10:7A:BB:98:08   Infraestructura  2442 MHz   54 MB/s    29       WPA WPA2   no      
'DPTO 1208..'                     24:EC:99:E7:D3:FB   Infraestructura  2452 MHz   54 MB/s    24       WPA WPA2   no      
'belkin54g'                       00:17:3F:64:8A:C2   Infraestructura  2462 MHz   54 MB/s    27       WPA        no      
'Jose_Felipe'                     00:0A:C2:83:F7:87   Infraestructura  2412 MHz   54 MB/s    25       WPA WPA2   no      
'LORENZO'                         A4:B1:E9:86:B4:41   Infraestructura  2422 MHz   54 MB/s    24       WPA WPA2   no      
'Milton'                          00:15:D1:5E:7D:34   Infraestructura  2427 MHz   54 MB/s    22       WPA WPA2   no      
'ximenaf'                         00:07:26:78:02:B5   Infraestructura  2437 MHz   54 MB/s    22       WPA WPA2   no      
'movistar_11D68B'                 00:07:26:11:D6:8C   Infraestructura  2457 MHz   54 MB/s    25       WPA WPA2   no      
'vision'                          8C:04:FF:13:C0:B6   Infraestructura  2412 MHz   54 MB/s    19       WPA        no      
'ROD'                             00:14:A5:C5:7F:25   Infraestructura  2432 MHz   54 MB/s    64       WEP        no      
'GordoStyle'                      B4:B3:62:55:47:01   Infraestructura  2462 MHz   54 MB/s    29       WEP        no      
'Heidy'                           00:26:B6:A8:9D:C1   Infraestructura  2412 MHz   54 MB/s    20       WEP        no      
'ANARKIA-TROPICAL'                00:1D:D2:12:AE:40   Infraestructura  2447 MHz   54 MB/s    39       WPA WPA2   sí      
'Malik'                           FC:8B:97:D0:3A:93   Infraestructura  2442 MHz   54 MB/s    25       WPA WPA2   no      
'roberto'                         C8:D3:A3:0E:73:06   Infraestructura  2462 MHz   54 MB/s    24       WPA WPA2   no      
'GABRIEL'                         00:1D:CE:C4:DD:04   Infraestructura  2452 MHz   54 MB/s    22       WPA        no      
'Torontito'                       90:F6:52:D7:39:E6   Infraestructura  2462 MHz   54 MB/s    22       WPA        no      
'movistar_7A606F'                 2C:AB:25:7A:60:70   Infraestructura  2412 MHz   54 MB/s    15       WPA WPA2   no      
'tomas'                           14:D6:4D:E0:7C:E2   Infraestructura  2437 MHz   54 MB/s    17       WPA2       no      
'JUANCARLOS'                      00:1A:73:DD:44:FC   Infraestructura  2447 MHz   54 MB/s    19       WEP        no      
'CH_FILMS'                        E0:69:95:80:68:DF   Infraestructura  2447 MHz   54 MB/s    19       WPA        no      
'MonoRed'                         A4:B1:E9:AB:B7:05   Infraestructura  2437 MHz   54 MB/s    14       WEP        no      
```

---

