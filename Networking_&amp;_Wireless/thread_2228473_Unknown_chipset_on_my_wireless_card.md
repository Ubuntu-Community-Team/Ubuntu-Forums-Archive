---
title: "Unknown chipset on my wireless card"
date: 2014-06-07
forum: Networking &amp; Wireless
---

### Post by spirox2 on 2014-06-07
My model is: Edimax 7728in. tried to look for old threads but all the links are dead.
I only could fine the driver from the edimax's site, but there's an error when I'm doing "MAKE":
:2: error: implicit declaration of function ‘daemonize’ [-Werror=implicit-function-declaration]
cc1: some warnings being treated as errors
make[4]: *** [/root/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../os/linux/rt_linux.o] Error 1
make[3]: *** [_module_/root/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux] Error 2
make[2]: *** [sub-make] Error 2
make[1]: *** [all] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.14-kali1-amd64'
make: *** [LINUX] Error 2
I'm new. please, can someone help me and guide me through this?
Thanks ahead!

---

### Post by chili555 on 2014-06-07
Let's have a look at:```
lspci -nn | grep 0280
lsb_release -a
```> [COLOR="#FF0000"]2008[/COLOR]_0918_RT2860_Linux_STA_v1.8.0.0It is doubtful that you'll get this antique to work on any recent Ubuntu version.

---

### Post by spirox2 on 2014-06-07
Wow chili, I gotta say. when I looked on back old threads Iv'e saw many posts that you were the helper. it's amazing to see that you are still here, helping people. I really appreciate it!
and for the response:
1) 05:00.0 Network controller [0280]: Ralink corp. RT2800 802.11n PCI [1814:0601]
2) No LSB modules are available.
Distributor ID:    Debian
Description:    Debian GNU/Linux Kali Linux 1.0.7
Release:    Kali Linux 1.0.7
Codename:    n/a

---

### Post by chili555 on 2014-06-07
I am still here despite all the foolish risks I've taken!

I know nothing about Kali; most especially what kernel version you are running and therefore why the built-in rt2800pci driver doesn't claim your device. Please show me:```
modinfo rt2800pci | grep 0601
uname -r
lsmod | grep rt2
```Once we have more information, I'll tell you how I'd fix it in Ubuntu; I'm not too sure about Kali.

---

### Post by spirox2 on 2014-06-07
Okay, thanks! they both linux based, so I hope it'll be the same solution.
1) alias:          pci:v00001814d00000601sv*sd*bc*sc*i*
2) 3.14-kali1-amd64
3)  lsmod | grep rt2
rt2800pci              13100  0 
rt2800mmio             13390  1 rt2800pci
rt2800lib              77399  2 rt2800pci,rt2800mmio
rt2x00pci              12520  1 rt2800pci
rt2x00mmio             12601  2 rt2800pci,rt2800mmio
rt2x00lib              46372  5 rt2x00pci,rt2800lib,rt2800pci,rt2800mmio,rt2x00mmio
eeprom_93cx6           12625  1 rt2800pci
mac80211              488308  3 rt2x00lib,rt2x00pci,rt2800lib
cfg80211              436618  2 mac80211,rt2x00lib
crc_ccitt              12347  1 rt2800lib

---

### Post by chili555 on 2014-06-07
So you have a working driver in place. Why did you think you needed to haul out an antique driver? May we see:```
iwconfig
sudo iwlist wlan0 scan
```[http://www.carspicturesdb.com/wp-content/uploads/2012/10/Hummer-h3-wooden-wheels-hd-cars-photos-and-wallpapers.jpg](http://www.carspicturesdb.com/wp-content/uploads/2012/10/Hummer-h3-wooden-wheels-hd-cars-photos-and-wallpapers.jpg)

---

### Post by spirox2 on 2014-06-07
1) wlan0     IEEE 802.11bgn  ESSID:"XX  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:11:50:5F:8E:01   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=50/70  Signal level=-60 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:142  Invalid misc:1   Missed beacon:0
2) wlan0     Scan completed :
          Cell 01 - Address: XXX
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"XX"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000006bc2ba74ac
                    Extra: Last beacon: 204ms ago
                    IE: Unknown: 000962656C6B696E353467
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018010301
          Cell 02 - Address:XXXX
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"XXX"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000b3b23aef61
                    Extra: Last beacon: 2864ms ago
                    IE: Unknown: 00086D616179616E3034
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030103
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1603001300000000000000000000000000000000000000
                    IE: Unknown: DD090010180205F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3403001300000000000000000000000000000000000000

Well, I thought it doesn't work because(I don't know if this is the right place for this) I tried to use aircrack-ng, and when I'm typing: airmon-ng it says:

Interface    Chipset        Driver

wlan0        Unknown     rt2800pci - [phy0]

that the chipset is unknown, and when I went forward with the use of the program, it gave me an error that may cause because my chipset isn't recognized or fit.

---

### Post by chili555 on 2014-06-07
I know nothing about aircrack, airhack, airfoolishness and I don't want to know. If your device sees networks and connects, we're all done here.

---

### Post by spirox2 on 2014-06-07
Okay, I guess it's fine then. thanks again for your time

---

