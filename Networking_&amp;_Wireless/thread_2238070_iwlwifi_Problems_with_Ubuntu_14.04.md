---
title: "iwlwifi Problems with Ubuntu 14.04"
date: 2014-08-05
forum: Networking &amp; Wireless
---

### Post by Professor Frink on 2014-08-05
I randomly get disconnected from my hot spot all the time running 14.04.  Here is the output from dmesg:

[http://pastebin.com/UhiwbL3x](http://pastebin.com/UhiwbL3x)

the error I see is wlan0: deauthenticated from 00:26:62:46:16:5b (Reason: 6)

and the output from lshw -c network:

 *-network               
       description: Wireless interface
       product: Centrino Advanced-N 6230 [Rainbow Peak]
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 34
       serial: 88:53:2e:04:6e:f1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.13.0-32-generic firmware=18.168.6.1 ip=192.168.1.15 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:51 memory:f6900000-f6901fff

and iw reg get

country US:
        (2402 - 2472 @ 40), (3, 27)
        (5170 - 5250 @ 40), (3, 17)
        (5250 - 5330 @ 40), (3, 20), DFS
        (5490 - 5600 @ 40), (3, 20), DFS
        (5650 - 5710 @ 40), (3, 20), DFS
        (5735 - 5835 @ 40), (3, 30)
        (57240 - 63720 @ 2160), (N/A, 40)

and iwconfig

wlan0     IEEE 802.11abgn  ESSID:"LCTNet-N"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:26:62:46:16:5B   
          Bit Rate=65 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-36 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:622   Missed beacon:0

and iwlist scan

Cell 01 - Address: 00:26:62:46:16:5B
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption key:on
                    ESSID:"LCTNet-N"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000014009b28c9
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 00084C43544E65742D4E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 200100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F20201010A0003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A8C131BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010020000000
                    IE: Unknown: 0706555320010B1B

I have a pretty default install.  The hotspot works for mobile devices and the same laptop works on the hotspot running Windows 7.

Thanks for the help!

---

### Post by Hadaka on 2014-08-05
Hi, please COPY and paste the following...
```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwldvm
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```
boot
thanks

---

### Post by weatherman2 on 2014-08-06
> **Professor Frink said:**
> I randomly get disconnected from my hot spot all the time running 14.04.  Here is the output from dmesg:
and iwlist scan

Cell 01 - Address: 00:26:62:46:16:5B
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption key:on
                    ESSID:"LCTNet-N"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000014009b28c9
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 00084C43544E65742D4E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 200100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F20201010A0003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A8C131BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010020000000
                    IE: Unknown: 0706555320010B1B


Your access point seems to be set to "WPA2 + WPA Mixed" encryption mode.  The reason for this mode is to allow older devices that can't do the more secure WPA2 to drop down to WPA and still work.  But in 2014, most devices that are now even a few years old can do WPA2 perfectly well.  Also, I have seen more than one case where "WPA2 + WPA Mixed" causes some devices to have disconnect issues.  Yes, this same laptop may connect fine with Windows, but with a completely different driver in Linux, it's almost like you are using a different wireless card, even though it is physically the same card.

So - I would try changing the access point's encryption to only "WPA2 Personal AES" or "WPA2 Personal TKIP/AES" and not use the "mixed" mode with WPA at all.  You want WPA2 and AES for the best speeds as well; TKIP is a fall-back when AES isn't possible by the device.

---

### Post by weatherman2 on 2014-08-06
Although the "iwlwifi 11n_disable=1" option is often suggested as a solution to connection issues with Intel wireless cards, this also disables 802.11n, greatly slowing down your wireless connection speed (to 802.11g speeds), which you will notice especially if you transfer files over a local network.  I have never needed this option for any of my Intel wireless cards in Linux, including the 6235-N which is similar to the 6230-N the original poster has.  I have used the 6235 card in several laptops successfully with Ubuntu, with excellent reliability and connection speeds.

---

### Post by Professor Frink on 2014-08-06
> **weatherman2 said:**
> Your access point seems to be set to "WPA2 + WPA Mixed" encryption mode.  The reason for this mode is to allow older devices that can't do the more secure WPA2 to drop down to WPA and still work.  But in 2014, most devices that are now even a few years old can do WPA2 perfectly well.  Also, I have seen more than one case where "WPA2 + WPA Mixed" causes some devices to have disconnect issues.  Yes, this same laptop may connect fine with Windows, but with a completely different driver in Linux, it's almost like you are using a different wireless card, even though it is physically the same card.

So - I would try changing the access point's encryption to only "WPA2 Personal AES" or "WPA2 Personal TKIP/AES" and not use the "mixed" mode with WPA at all.  You want WPA2 and AES for the best speeds as well; TKIP is a fall-back when AES isn't possible by the device.

My dumb FIOS router has WEP, WPA, and WPA2 as radio buttons: [http://imgur.com/lOAz9sQ](http://imgur.com/lOAz9sQ)

The setup I have currently is WPA2 checked off and AES instead of TKIP and AES (which is the only other option): [http://imgur.com/MYF7OSj](http://imgur.com/MYF7OSj) (my password and Verizons pre shared key were removed).

Do you think I should go with just WPA?  I definitely don't want to switch to WEP as I personally "borrowed" someone's WEP access point for almost the first year that I moved into my co-op ;) so I know how easy it is to crack.

---

### Post by Professor Frink on 2014-08-06
Also, I disabled N and while it got better, the problem remained.

---

### Post by weatherman2 on 2014-08-06
> **Professor Frink said:**
> Do you think I should go with just WPA?  I definitely don't want to switch to WEP as I personally "borrowed" someone's WEP access point for almost the first year that I moved into my co-op ;) so I know how easy it is to crack.

You can try both WPA and WEP and see if your problem goes away.  I doubt it.  In any case, you should aim for WPA2 for sure, as it is the most secure.

WPA2 + AES is best.  You can also try TKIP + AES too.  If for some reason TKIP works and fixes your problem, you're still going to be limited to slower speeds.

You can even try unencrypted operation (no password) temporarily if you dare, to see if your problem goes away that way as well.  If not, obviously no other encryption change will help.

There is some chance there is simply an incompatibility with your router and the Linux driver.  Or, there is a problem with your specific wireless card and the iwlwifi driver or the firmware.  As I said, I have had excellent performance with iwlwifi and the 6235 card, but it probably uses a different firmware than your card.  You might try booting an older Ubuntu distro off a live USB or live CD (perhaps 12.04) and see if things work any better.

---

### Post by chili555 on 2014-08-11
> wlan0 IEEE 802.11abgn ESSID:"LCTNet-N" 
Mode:Managed Frequency:2.462 GHz Access Point: 00:26:62:46:16:5B 
Bit Rate=65 Mb/s Tx-Power=15 dBm 
Retry long limit:7 RTS thr:off Fragment thr:off
[COLOR="#FF0000"]Power Management:on[/COLOR]
Link Quality=70/70 Signal level=-36 dBm 
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:622 Missed beacon:0I am working on a theory that you can help me confirm or refute. Is the behavior better, worse or the same with power management off?```
sudo iwconfig wlan0 power off
```

---

### Post by jeremy31 on 2014-08-11
I saw a new one on a bug report 
iwlwifi 11n_disable=8
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1341068](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1341068)

I should say it is the first time I have seen it's use be recommended

---

### Post by chili555 on 2014-08-11
> **jeremy31 said:**
> I saw a new one on a bug report 
iwlwifi 11n_disable=8
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1341068](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1341068)

I should say it is the first time I have seen it's use be recommendedYes, indeed.  I will be interested in a report of success or failure.

Please note that this parameter is not available until later iwlwifi versions; check:```
modinfo iwlwifi
```

---

### Post by jeremy31 on 2014-08-11
It seems to be there with 3.13.0-32
```
vermagic:       3.13.0-32-generic SMP mod_unload modversions signer:         Magrathea: Glacier signing key
sig_key:        5E:3C:0F:9C:A6:E3:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           nvm_file:NVM file name (charp)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)

```

---

### Post by Gijsbert_Wiesenekk on 2014-09-08
My wireless connection of my Dell Precision M4800 laptop has become less and less stable since the last couple of kernel updates. I am now running 3.13.0-35-generic and it has become almost unusable. The fix that seems to work for now is to add the line:

options iwlwifi 11n_disable=8

to the file

/etc/modprobe.d/iwlwifi.conf

Regards,
Gijsbert

---

