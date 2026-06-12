---
title: "[ubuntu 18.04] How to force 5Ghz wifi instead of 2.4Ghz"
date: 2018-06-26
forum: Networking &amp; Wireless
---

### Post by Finarfin on 2018-06-26
Hi,

I have a problem with connect with usage only of 5GHz frequency instead of 2.4Ghz. I don't see that in network manager options, even in GUI possibilities, so I've tried to played with CLI. When I've checked available channels, it seems everything is possible:

```
iwlist wlo1 freq 
wlo1      32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Current Frequency:2.412 GHz (Channel 1)
```

However when I'm trying to "force" desired channel, nothing is changed:

```
sudo iwconfig wlo1 channel 100

```

Is there any suitable way how to make it? Perfectly if I can make that change permanently or if I can select to connect with  5Ghz at first.

Thank you in advance for your help here.

Best regards,
Finarfin

---

### Post by chili555 on 2018-06-26
I suggest that you rename the 2.4 and 5 Ghz segments of your router; something like myrouter2.4 and myrouter5. Turn off auto channel select in both segments. Connect to the 5 Ghz segment and you should be all set.

From my machine:> wlp3s0    IEEE 802.11  ESSID:"[COLOR="#FF0000"]GBR5[/COLOR]"  
          Mode:Managed  [COLOR="#FF0000"]Frequency:5.745 GHz[/COLOR]  Access Point: xx:2B:B0:DC:45:xx
          [COLOR="#FF0000"]Bit Rate=866.7 Mb/s[/COLOR]   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=66/70  Signal level=-44 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:450   Missed beacon:0


---

### Post by Finarfin on 2018-06-28
Proposed solution is just a workaround, not a real solution. Unfortunately I cannot change SSID, as it's a corporate network. I simply would like to select 5Ghz channel by OS user, which shouldn't be an issue in other systems(RedHat, Fedora, even Windows...).

My scan is as below:
```
wlo1      Scan completed :
          Cell 01 - Address: 70:0F:6A:92:11:E0
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"NOSI"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=000003c83dbc3216
                    Extra: Last beacon: 27552ms ago
                    IE: Unknown: 00044E4F5349
                    IE: Unknown: 010618A43048606C
                    IE: Unknown: 030101
                    IE: Unknown: 0706504C20010D14
                    IE: Unknown: 0B050600208D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1AAC191BFFFFFF0000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (2) : 802.1x Proprietary
                    IE: Unknown: 3D1601080400000000000000000000000000000000000000
                    IE: Unknown: 7F080010000001400001
                    IE: Unknown: 851E0A008F000F00FF035900706C77726F616B2D61703430330000000600004C
                    IE: Unknown: 9606004096000400
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD080040961301003401
                    IE: Unknown: DD050040961405
          Cell 02 - Address: 70:0F:6A:94:8C:AF
                    Channel:44
                    Frequency:5.22 GHz (Channel 44)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"NOSI"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=000003bf4b93afa6
                    Extra: Last beacon: 2536ms ago
                    IE: Unknown: 00044E4F5349
                    IE: Unknown: 010618A43048606C
                    IE: Unknown: 070C504C2024081764051784031E
                    IE: Unknown: 0B050000008D5B
                    IE: Unknown: 2D1AEE191BFFFFFF0000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (2) : 802.1x Proprietary
                    IE: Unknown: 3D162C050400000000000000000000000000000000000000
                    IE: Unknown: 7F080010000001400041
                    IE: Unknown: 851E02008F000F00FF035900706C77726F616B2D617034303600000000000047
                    IE: Unknown: 9606004096000500
                    IE: Unknown: BF0CB259820FEAFF0000EAFF0000
                    IE: Unknown: C005000000C0FF
                    IE: Unknown: C303010202
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD080040961301003401
                    IE: Unknown: DD050040961405
          Cell 03 - Address: 70:0F:6A:92:11:EF
                    Channel:64
                    Frequency:5.32 GHz (Channel 64)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"NOSI"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=000003c83f86f836
                    Extra: Last beacon: 1628ms ago
                    IE: Unknown: 00044E4F5349
                    IE: Unknown: 010618A43048606C
                    IE: Unknown: 070C504C2024081764051784031E
                    IE: Unknown: 0B050500008D5B
                    IE: Unknown: 2D1AEE191BFFFFFF0000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (2) : 802.1x Proprietary
                    IE: Unknown: 3D1640070400000000000000000000000000000000000000
                    IE: Unknown: 7F080010000001400041
                    IE: Unknown: 851E01008F000F00FF035900706C77726F616B2D617034303300000005000047
                    IE: Unknown: 9606004096000500
                    IE: Unknown: BF0CB279830FEAFF0000EAFF0000
                    IE: Unknown: C005000000C0FF
                    IE: Unknown: C303010202
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD080040961301003401
                    IE: Unknown: DD050040961405
          Cell 04 - Address: 70:79:B3:EC:E9:AE
                    Channel:136
                    Frequency:5.68 GHz (Channel 136)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:off
                    ESSID:"NSN-GUEST"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=000003bf4a512387
                    Extra: Last beacon: 216ms ago
                    IE: Unknown: 00094E534E2D4755455354
                    IE: Unknown: 010618A43048606C
                    IE: Unknown: 070C504C2024081764051784031E
                    IE: Unknown: 0B050000008D5B
                    IE: Unknown: 2D1AEE191BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1688070400000000000000000000000000000000000000
                    IE: Unknown: 7F080010000001400041
                    IE: Unknown: 851E00008F000F00FF035900706C77726F616B2D617034303500000000000047
                    IE: Unknown: 9606004096000200
                    IE: Unknown: BF0CB279830FEAFF0000EAFF0000
                    IE: Unknown: C005000000C0FF
                    IE: Unknown: C303010202
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD080040961301003401
                    IE: Unknown: DD050040961404
          Cell 05 - Address: 70:79:B3:EC:E9:AF
                    Channel:136
                    Frequency:5.68 GHz (Channel 136)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"NOSI"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=000003bf4a504a96
                    Extra: Last beacon: 216ms ago
                    IE: Unknown: 00044E4F5349
                    IE: Unknown: 010618A43048606C
                    IE: Unknown: 070C504C2024081764051784031E
                    IE: Unknown: 0B050000008D5B
                    IE: Unknown: 2D1AEE191BFFFFFF0000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (2) : 802.1x Proprietary
                    IE: Unknown: 3D1688070400000000000000000000000000000000000000
                    IE: Unknown: 7F080010000001400041
                    IE: Unknown: 851E00008F000F00FF035900706C77726F616B2D617034303500000000000047
                    IE: Unknown: 9606004096000200
                    IE: Unknown: BF0CB279830FEAFF0000EAFF0000
                    IE: Unknown: C005000000C0FF
                    IE: Unknown: C303010202
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD080040961301003401
                    IE: Unknown: DD050040961405
          Cell 06 - Address: 70:0F:6A:94:8B:9F
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"NOSI"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=000003c83675313d
                    Extra: Last beacon: 2840ms ago
                    IE: Unknown: 00044E4F5349
                    IE: Unknown: 010618A43048606C
                    IE: Unknown: 070C504C2024081764051784031E
                    IE: Unknown: 0B050500068D5B
                    IE: Unknown: 2D1AEE191BFFFFFF0000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (2) : 802.1x Proprietary
                    IE: Unknown: 3D1624050400000000000000000000000000000000000000
                    IE: Unknown: 7F080010000001400041
                    IE: Unknown: 851E03008F000F00FF035900706C77726F616B2D617034303200000005000047
                    IE: Unknown: 9606004096000500
                    IE: Unknown: BF0CB279830FEAFF0000EAFF0000
                    IE: Unknown: C005000000C0FF
                    IE: Unknown: C303010202
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD080040961301003401
                    IE: Unknown: DD050040961405

```

But still selection to all of that channels: 

```
$ sudo iwconfig wlo1 channel 136
$  sudo iwconfig wlo1 channel 44
$ iwlist wlo1 freq 
wlo1      32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Current Frequency:2.412 GHz (Channel 1)
```

But it doesn't switch between frequencies.

Any ideas?

---

### Post by chili555 on 2018-06-28
>  which shouldn't be an issue in other systems(RedHat, Fedora, even Windows...).I would be very surprised to know that is true.

When we run the terminal command:```
iwconfig
```...we see that the mode is managed. In this context, 'managed' means that the router or other wireless access point is the master. If you have the name of the SSID and the password, you can connect. Then the router decides the bit-rate, channel, encryption protocol (WPA or WPA2; AES or TKIP or even open) and, if the wireless device advertises that it can do so, may, unless these things are fixed, rather than auto-select, the router may change any or all of the parameters as it (usually poorly) sees fit.

Typically, the only reason that the channel is manipulable by the user is for ad-hoc connections or when, if the device supports it, you want to put the device into master mode and use your system as a router.

The only other suggestion that I have is, unfortunately, also a workaround. You might tell Network Manager that you will only connect to the BSSID that's close and at a 5 GHz channel; for instance:```
Cell 03 - Address: 70:0F:6A:92:11:EF
                    Channel:64
                    Frequency:5.32 GHz (Channel 64)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"NOSI"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
```Tell Network Manager that you will only connect to the NOSI instance by specifying the BSSID 70:0F:6A:92:11:EF like this: [https://i.stack.imgur.com/C8Z6w.png](https://i.stack.imgur.com/C8Z6w.png)

---

### Post by Finarfin on 2018-07-02
Seems it''s not a perfect solution, but most probably it's an only possible option. Thanks for help.

---

### Post by donnadieu on 2018-11-19
Hey Finarfin,

I see that this was marked resolved but just as an FYI I've had the same issue and the following worked for me:

```
sudo iwconfig wlo1 freq 5.7G
```

Then turn your wifi off in you computer, turn it back on and it should picked the selected frequency.

---

