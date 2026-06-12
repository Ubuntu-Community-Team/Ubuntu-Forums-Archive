---
title: "Ralink RT3290 on HP 650; Lubuntu 17.10 does not connect"
date: 2017-12-16
forum: Networking &amp; Wireless
---

### Post by mark346236 on 2017-12-16
Hello,

the card used to work under Lubuntu 15.04. IIRC there was some hassle to get it working back then, but I don't remember details. 
Right now the card shows available networks, but doesn't autoconnect and using 'Manage Networks' from the panel I am asked for the password, but then nothing happens.

I tried the Jim Colaco driver patch ([https://askubuntu.com/questions/545238/how-to-install-wifi-driver-ralink-rt3290/557427#](https://askubuntu.com/questions/545238/how-to-install-wifi-driver-ralink-rt3290/557427#)) but got an error in the dkms step and then tried to restore everything to factory default.
[ATTACH]277859[/ATTACH]

---

### Post by chili555 on 2017-12-16
> Cell 01 - Address: <MAC 'capecod' [AC1]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=67/70  Signal level=-43 dBm  
                    Encryption key:on
                    ESSID:"capecod"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000068a94f60
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : [COLOR="#FF0000"]TKIP[/COLOR]
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : [COLOR="#FF0000"]TKIP[/COLOR]
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSKYour driver and hardware and old Chili hate hate hate TKIP.

Please, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

I have worked on more than one case for the rt2800 series where 802.11N prevented connection. If the above change doesn't help, please change the wireless mode in the router to 802.11B and G only and see if it helps.

---

### Post by mark346236 on 2017-12-16
Hello, and thanks for the suggestions. I tried a couple of things, but still no luck:
- set encryption to WPA2 CCMP
- activated/deactivated 802.11g++
- activated/deactivated WMM (whatever that is)
- set the network to unsecured (i.e. iwlist scan returns 'Encryption key:off')

Also, as mentioned above, the exact same router configuration and hardware worked perfectly fine under 15.04. two days ago.

---

### Post by chili555 on 2017-12-16
> **mark346236 said:**
> Hello, and thanks for the suggestions. I tried a couple of things, but still no luck:
- set encryption to WPA2 CCMP
- activated/deactivated 802.11g++
- activated/deactivated WMM (whatever that is)
- set the network to unsecured (i.e. iwlist scan returns 'Encryption key:off')

Also, as mentioned above, the exact same router configuration and hardware worked perfectly fine under 15.04. two days ago.And after each and every of these changes, did you reboot the router?

---

### Post by mark346236 on 2017-12-17
Hi,

previously I checked the network went down between changes and I verified the changes by iwlist scan as mentioned because I could not find a dedicated reboot option in the router software. This time I unplugged the router completely and got both the unsecured network and the WPA2-CCMP secured network to run. I'll have to see whether the change affects any other devices that connect to the WLAN, but for now my problem is solved.
FWIW, I did install dhcpcd5 before the latest attempts.

Thank you very much!

---

