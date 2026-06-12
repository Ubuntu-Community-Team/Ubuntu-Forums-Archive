---
title: "Low wifi range - Intel wireless 3160 (Ubuntu 18.04 LTS)"
date: 2019-03-05
forum: Networking &amp; Wireless
---

### Post by kmartin62 on 2019-03-05
I switched from Windows to Linux recently and I'm facing a wireless problem. My wifi range is very low, I tried tons of things found here on the internet but none of that helped. Before switching I could get internet from my router through two other rooms and now I must be in the same room with the router so I can use it. My NIC is **Network controller: Intel Corporation Wireless 3160 (rev 83)** and my driver is **iwlwifi** (driver=iwlwifi driverversion=4.18.0-15-generic firmware=17.948900127.0). This is the result from my **sudo iwlist scan **and I'm currently connected on **wifi5G_B9D228**
```
lo        Interface doesn't support scanning.

enp7s0    Interface doesn't support scanning.

wlp6s0    Scan completed :
          Cell 01 - Address: X
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"wifi5G_B9D228"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000013e14e0232a
                    Extra: Last beacon: 3288ms ago
                    IE: Unknown: 000D7769666935475F423944323238
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 030124
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 7F080000000000000000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0706555320240410
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: DD07000CE700000000
          Cell 02 - Address: X
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"wifi2.4G_B9D228"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000013e14b87ef9
                    Extra: Last beacon: 4100ms ago
                    IE: Unknown: 000F77696669322E34475F423944323238
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030102
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 7F080000000000000000
                    IE: Unknown: 0B05000000127A
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0706545720010D10
                    IE: Unknown: DD07000C4303000000
```

---

### Post by chili555 on 2019-03-05
I own and use successfully two Intel wireless devices. I have honed a few techniques in several years and thousands of forum posts.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and *certainly not *TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

In the case of 5gHz, I'd select a fixed channel that has the least or no other occupancy; find out with the terminal command:```

nmcli dev wifi list

```

Then set your regulatory domain explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
sudo nano /etc/default/crda
```
Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save (Ctrl+o followed by Enter) and close (Ctrl+x) the text editor.

After making these changes, reboot the router and the computer and let us see another scan.

---

### Post by kmartin62 on 2019-03-06
First of all, thank you for helping me.

So I guess I did  everything you told me, I went into my router settings, changed TKIP to  AES, changed my bandwidth etc., but I think that nothing changed. Here's  what I get from the other room.

```
lo        Interface doesn't support scanning.

wlp6s0    Scan completed :
          Cell 01 - Address: X
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=17/70  Signal level=-93 dBm  
                    Encryption key:on
                    ESSID:"Rasko"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000009cedb6f375
                    Extra: Last beacon: 2432ms ago
                    IE: Unknown: 00055261736B6F
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 0706485520010D14
                    IE: Unknown: 200100
                    IE: Unknown: 23021100
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 0B050300130000
                    IE: Unknown: 2D1ABC191BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080400000000000000000000000000000000000000
                    IE: Unknown: 7F080400080000000040
                    IE: Unknown: DD090010180203000C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 46057208010000

enp7s0    Interface doesn't support scanning.

```
My point here is to clarify that I am not getting my WiFi networks. This is a scan from the room where my router is:
```
lo        Interface doesn't support scanning.

wlp6s0    Scan completed :
          Cell 01 - Address: X
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"wifi2.4G_B9D228"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000000e32cca8
                    Extra: Last beacon: 4120ms ago
                    IE: Unknown: 000F77696669322E34475F423944323238
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1601050000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 7F080000000000000000
                    IE: Unknown: 0B05000000127A
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 0706545720010D10
                    IE: Unknown: DDA70050F204104A0001101044000102103B00010310470010BC329E001DD811B286011C497BB9D2291021001852616C696E6B20546563686E6F6C6F67792C20436F72702E1023001C52616C696E6B20576972656C6573732041636365737320506F696E74102400065254323836301042000831323334353637381054000800060050F20400011011000952616C696E6B41505310080002210C103C0001011049000600372A000120
                    IE: Unknown: DD07000C4303000000
          Cell 02 - Address: X
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"wifi5G_B9D228"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000000dcf8aee
                    Extra: Last beacon: 3824ms ago
                    IE: Unknown: 000D7769666935475F423944323238
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 030124
                    IE: Unknown: 2D1A6D0017FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1624000700000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 7F080000000000000000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0706555320240910
                    IE: Unknown: BF0C2000C031FAFF0C03FAFF0C03
                    IE: Unknown: C005000000F5FF
                    IE: Unknown: DDA70050F204104A0001101044000102103B00010310470010BC329E001DD811B286011C497BB9D22A1021001852616C696E6B20546563686E6F6C6F67792C20436F72702E1023001C52616C696E6B20576972656C6573732041636365737320506F696E74102400065254323836301042000831323334353637381054000800060050F20400011011000952616C696E6B41505310080002210C103C0001021049000600372A000120
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: DD07000CE700000000

enp7s0    Interface doesn't support scanning.

```

And this is from nmcli dev wifi list:
```
IN-USE  SSID             MODE   CHAN  RATE        SIGNAL  BARS  SECURITY 
        wifi2.4G_B9D228  Infra  1     270 Mbit/s  52      &#9602;&#9604;__  WPA2     
*       wifi5G_B9D228    Infra  36    130 Mbit/s  37      &#9602;&#9604;__  WPA2  

```

Is there a chance that there might be a hardware problem?

EDIT: I had to switch wifi2.4G_B9D228 back to TKIP because other laptop in my house couldn't get the network

---

### Post by chili555 on 2019-03-06
A hardware problem is the next thing I suspect. Please check to see that both antenna connections are firmly snapped in place.

---

