---
title: "Wireless not working on Thinkpad T42"
date: 2019-09-02
forum: Networking &amp; Wireless
---

### Post by pbpersson on 2019-09-02
I have installed Ubuntu 18.04 on an IBM Thinkpad T42 laptop

I can see wireless networks but when I attempt to join mine it keeps asking me to re-enter the password even though I know that I am entering the correct password.

I did some searching on the web and located this page: [https://github.com/tomaspinho/rtl8821ce](https://github.com/tomaspinho/rtl8821ce)

I downloaded and installed this new driver but upon rebooting received the same results.

Then I followed the instructions to enter the "pci=noaer" parameter in the GRUB configuration.

My wireless still is not working.

Would anyone happen to know what further troubleshooting steps would be needed to resolve this issue?

Thank you in advance for any help


Phil Persson

---

### Post by mörgæs on 2019-09-02
There might be better chances for getting an answer in the networking forum. 
If you click 'report' you can ask for the post to be moved.

---

### Post by wildmanne39 on 2019-09-02
*Thread moved to **Networking & Wireless a more appropriate sub-forum**.*

---

### Post by praseodym on 2019-09-02
Did you deactivate SecureBoot?

---

### Post by pbpersson on 2019-09-02
I did the pci=noaer parameter in GRUB.  If that is not secure boot then I need more details as to what steps I need to follow.

---

### Post by pbpersson on 2019-09-02
I went into the BIOS settings under security but did not see any setting for Secure Boot.  This laptop is 15 years old, did they even have UEFI back then?

---

### Post by him610 on 2019-09-02
> This laptop is 15 years old, did they even have UEFI back then?
No, it was BIOS back then, and there was also no Secure Boot either.
How about  running *inxi -FZ* from a terminal and showing the results between the code tags. It will provide more information about your system.

---

### Post by chili555 on 2019-09-02
It is fairly common for new users of Ubuntu to read a forum post about solving a wireless issue and then blindly apply it to their system. They are usually disappointed when there is no improvement. While it is not dangerous to add a new wireless driver that your system doesn't even use, it is futile if you don't know what driver you have. I urge all Ubuntu users to determine what wireless driver they have before applying any fixes to the system. You can do so with the terminal command:

```
lspci -nnk | grep 0280 -A3
```I will be quite shocked if it turns out to be an RTL8821CE.

---

### Post by pbpersson on 2019-09-02
> **him610 said:**
> No, it was BIOS back then, and there was also no Secure Boot either.
How about  running *inxi -FZ* from a terminal and showing the results between the code tags. It will provide more information about your system.

```

System:    Host: phil-ThinkPad-T42 Kernel: 4.15.0-58-generic i686 bits: 32 Desktop: LXDE (Openbox 3.6.1)
           Distro: Ubuntu 18.04.3 LTS
Machine:   Device: laptop System: IBM product: 2373L6U v: ThinkPad T42 serial: N/A
           Mobo: IBM model: 2373L6U serial: N/A BIOS: IBM v: 1RETDHWW (3.13 ) date: 10/29/2004
Battery    BAT0: charge: 45.6 Wh 99.9% condition: 45.7/47.5 Wh (96%)
CPU:       Single core Intel Pentium M (-UP-) cache: 2048 KB speed: 1700 MHz (max)
Graphics:  Card: Advanced Micro Devices [AMD/ATI] RV350/M10 / RV360/M11 [Mobility Radeon 9600 (PRO) / 9700]
           Display Server: x11 (X.Org 1.19.6 ) drivers: ati,radeon (unloaded: modesetting,fbdev,vesa)
           Resolution: 1400x1050@60.19hz
           OpenGL: renderer: ATI RV350 version: 2.1 Mesa 19.0.8
Audio:     Card Intel 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller driver: snd_intel8x0
           Sound: Advanced Linux Sound Architecture v: k4.15.0-58-generic
Network:   Card-1: Intel 82540EP Gigabit Ethernet Controller (Mobile) driver: e1000
           IF: enp2s1 state: up speed: 100 Mbps duplex: full mac: 00:11:25:30:99:fb
           Card-2: Qualcomm Atheros AR5212/5213/2414 Wireless Network Adapter driver: ath5k
           IF: wlp2s2 state: down mac: 00:0e:9b:8c:ae:91
Drives:    HDD Total Size: 80.0GB (11.1% used)
           ID-1: /dev/sda model: WDC_WD800BEVE size: 80.0GB
Partition: ID-1: / size: 73G used: 8.3G (12%) fs: ext4 dev: /dev/sda1
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 52.0C mobo: 46.0C
           Fan Speeds (in rpm): cpu: 3644
Info:      Processes: 138 Uptime: 4 min Memory: 303.9/1947.6MB Client: Shell (bash) inxi: 2.3.56 


```

---

### Post by pbpersson on 2019-09-02
> **chili555 said:**
> It is fairly common for new users of Ubuntu to read a forum post about solving a wireless issue and then blindly apply it to their system. They are usually disappointed when there is no improvement. While it is not dangerous to add a new wireless driver that your system doesn't even use, it is futile if you don't know what driver you have. I urge all Ubuntu users to determine what wireless driver they have before applying any fixes to the system. You can do so with the terminal command:

```
lspci -nnk | grep 0280 -A3
```I will be quite shocked if it turns out to be an RTL8821CE.

The exact syntax you supplied did not return any results but this is likely the information you are seeking:

```

02:01.0 Ethernet controller [0200]: Intel Corporation 82540EP Gigabit Ethernet Controller (Mobile) [8086:101e] (rev 03)
	Subsystem: IBM Thinkpad [1014:0549]
	Kernel driver in use: e1000
	Kernel modules: e1000
02:02.0 Ethernet controller [0200]: Qualcomm Atheros AR5212/5213/2414 Wireless Network Adapter [168c:0013] (rev 01)
	Subsystem: AMBIT Microsystem Corp. ThinkPad 11b/g Wireless LAN Mini PCI Adapter [1468:0408]
	Kernel driver in use: ath5k
	Kernel modules: ath5k


```

---

### Post by pbpersson on 2019-09-03
This includes information on the driver being used:

```

       description: Wireless interface
       product: AR5212/5213/2414 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: wlp2s2
       version: 01
       serial: 00:0e:9b:8c:ae:91
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=4.15.0-58-generic firmware=N/A latency=168 link=no maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11
       resources: irq:11 memory:c0210000-c021ffff


```

---

### Post by pbpersson on 2019-09-03
I attempted to connect manually and was not able to get informative error messages until I used sudo.  I am not certain what any of this means.  Do I need to install a different driver?


```

phil@phil-ThinkPad-T42:~$ wpa_supplicant -iwlp2s2 -cwpa.conf
Successfully initialized wpa_supplicant
nl80211: deinit ifname=wlp2s2 disabled_11b_rates=0
wlp2s2: Failed to initialize driver interface

phil@phil-ThinkPad-T42:~$ sudo wpa_supplicant -iwlp2s2 -cwpa.conf
Successfully initialized wpa_supplicant
wlp2s2: SME: Trying to authenticate with 58:6d:8f:89:49:f7 (SSID='Butterscotch' freq=2422 MHz)
wlp2s2: Trying to associate with 58:6d:8f:89:49:f7 (SSID='Butterscotch' freq=2422 MHz)
wlp2s2: CTRL-EVENT-ASSOC-REJECT bssid=58:6d:8f:89:49:f7 status_code=18
wlp2s2: SME: Deauth request to the driver failed
wlp2s2: SME: Trying to authenticate with 58:6d:8f:89:49:f7 (SSID='Butterscotch' freq=2422 MHz)
wlp2s2: Trying to associate with 58:6d:8f:89:49:f7 (SSID='Butterscotch' freq=2422 MHz)
wlp2s2: CTRL-EVENT-ASSOC-REJECT bssid=58:6d:8f:89:49:f7 status_code=18
wlp2s2: SME: Deauth request to the driver failed
wlp2s2: SME: Trying to authenticate with 58:6d:8f:89:49:f7 (SSID='Butterscotch' freq=2422 MHz)
wlp2s2: Trying to associate with 58:6d:8f:89:49:f7 (SSID='Butterscotch' freq=2422 MHz)
wlp2s2: CTRL-EVENT-ASSOC-REJECT bssid=58:6d:8f:89:49:f7 status_code=18
wlp2s2: SME: Deauth request to the driver failed
wlp2s2: SME: Trying to authenticate with 58:6d:8f:89:49:f7 (SSID='Butterscotch' freq=2422 MHz)
wlp2s2: Trying to associate with 58:6d:8f:89:49:f7 (SSID='Butterscotch' freq=2422 MHz)
wlp2s2: CTRL-EVENT-ASSOC-REJECT bssid=58:6d:8f:89:49:f7 status_code=18
wlp2s2: SME: Deauth request to the driver failed
wlp2s2: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="Butterscotch" auth_failures=1 duration=10 reason=CONN_FAILED
wlp2s2: CTRL-EVENT-SSID-REENABLED id=0 ssid="Butterscotch"
wlp2s2: SME: Trying to authenticate with 58:6d:8f:89:49:f7 (SSID='Butterscotch' freq=2422 MHz)
wlp2s2: Trying to associate with 58:6d:8f:89:49:f7 (SSID='Butterscotch' freq=2422 MHz)
wlp2s2: CTRL-EVENT-ASSOC-REJECT bssid=58:6d:8f:89:49:f7 status_code=18
wlp2s2: SME: Deauth request to the driver failed
wlp2s2: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="Butterscotch" auth_failures=2 duration=23 reason=CONN_FAILED
wlp2s2: CTRL-EVENT-SSID-REENABLED id=0 ssid="Butterscotch"
wlp2s2: SME: Trying to authenticate with 58:6d:8f:89:49:f7 (SSID='Butterscotch' freq=2422 MHz)
wlp2s2: Trying to associate with 58:6d:8f:89:49:f7 (SSID='Butterscotch' freq=2422 MHz)
wlp2s2: CTRL-EVENT-ASSOC-REJECT bssid=58:6d:8f:89:49:f7 status_code=18
wlp2s2: SME: Deauth request to the driver failed
wlp2s2: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="Butterscotch" auth_failures=3 duration=46 reason=CONN_FAILED
wlp2s2: CTRL-EVENT-SSID-REENABLED id=0 ssid="Butterscotch"
wlp2s2: SME: Trying to authenticate with 58:6d:8f:89:49:f7 (SSID='Butterscotch' freq=2422 MHz)
wlp2s2: Trying to associate with 58:6d:8f:89:49:f7 (SSID='Butterscotch' freq=2422 MHz)
wlp2s2: CTRL-EVENT-ASSOC-REJECT bssid=58:6d:8f:89:49:f7 status_code=18
wlp2s2: SME: Deauth request to the driver failed
wlp2s2: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="Butterscotch" auth_failures=4 duration=77 reason=CONN_FAILED


```

---

### Post by chili555 on 2019-09-03
> 02:02.0 Ethernet controller [[COLOR="#FF0000"]0200[/COLOR]]: Qualcomm Atheros AR5212/5213/2414 Wireless Network Adapter [168c:0013] (rev 01)
	Subsystem: AMBIT Microsystem Corp. ThinkPad 11b/g Wireless LAN Mini PCI Adapter [1468:0408]
	Kernel driver in use: ath5k
	Kernel modules: ath5kIt's very unusual for a wireless device to appear at class 0200; it is typically 0280. I have seen wireless at 0200 only three or four times in my experience. Also, as I expected, your slightly older T42 predates the newer RTL8821CE.> 
Do I need to install a different driver?I suspect that you need to adjust the settings in the router. Please run:```
sudo iwlist scan
```Show us only your network, Butterscotch, and redact the MAC address like this:> 
wlp3s0    Scan completed :
          Cell 01 - Address: [COLOR="#FF0000"]XXXX[/COLOR]
                    Channel:149
                    Frequency:5.745 GHz (Channel 149)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"GBR5"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    <snip>
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK



---

### Post by praseodym on 2019-09-03
Try resetting the BIOS to default settings

---

### Post by pbpersson on 2019-09-03
> **praseodym said:**
> Try resetting the BIOS to default settings

I tried your suggestion but it did not help

---

### Post by pbpersson on 2019-09-03
> **chili555 said:**
> It's very unusual for a wireless device to appear at class 0200; it is typically 0280. I have seen wireless at 0200 only three or four times in my experience. Also, as I expected, your slightly older T42 predates the newer RTL8821CE.I suspect that you need to adjust the settings in the router. Please run:```
sudo iwlist scan
```Show us only your network, Butterscotch, and redact the MAC address like this:

I am including the information below that you requested.  If we change settings on the router, how will that affect my other Ubuntu 18.04 laptop where the wireless is currently working?

```

          Cell 01 - Address: XXXXXXXXXXXX
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption key:on
                    ESSID:"Butterscotch"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 16ms ago
                    IE: Unknown: 000C42757474657273636F746368
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030103
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1603080400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD810050F204104A00011010440001021041000100103B00010310470010B1492B7E735A7D95C5B6AF1D2981F2AC102100074C696E6B7379731023000D4C696E6B7379732045343230301024000776312E302E30361042000234321054000800060050F20400011011000D4C696E6B737973204534323030100800020084103C000103
                    IE: Unknown: DD090010180205F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

```

---

### Post by chili555 on 2019-09-03
Did you pick channel 3? That would be very unusual as it is an overlapped channel: [https://www.metageek.com/training/resources/why-channels-1-6-11.html](https://www.metageek.com/training/resources/why-channels-1-6-11.html) I rather suspect that your router is set to auto channel select. To many Linux drivers, that means that as soon as you figure out where I am, I will move!

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

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

After making these changes, is connectivity improved?

---

### Post by pbpersson on 2019-09-04
> **chili555 said:**
> Did you pick channel 3? That would be very unusual as it is an overlapped channel: [https://www.metageek.com/training/resources/why-channels-1-6-11.html](https://www.metageek.com/training/resources/why-channels-1-6-11.html) I rather suspect that your router is set to auto channel select. To many Linux drivers, that means that as soon as you figure out where I am, I will move!

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

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

After making these changes, is connectivity improved?

Where to begin?  

The router was set to WPA2-Personal and it was on channel 9.  For some odd reason it said the wireless radio was set to OFF (there are six other wireless devices using this router so that made no sense at all).  It was set to use 802.11N only.

I set the wireless radio on the router to ON (again, this makes no sense) and set the wireless type to B, G, or N.

Then on the laptop I set it to use channel 9 and set my regulatory domain to US (it was set to nothing).

That made no difference but after rebooting the laptop a couple of times it started working.  Thank you!! :D:D:D I am setting this issue to RESOLVED status.  \\:D/\\:D/\\:D/

---

