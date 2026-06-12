---
title: "No wireless networks found"
date: 2013-10-29
forum: Networking &amp; Wireless
---

### Post by darkloader on 2013-10-29
Hello, I have searched through many forums and googled for almost half a day now. I cannot find the solutions to my problem.

I have come down to the forums to start a thread in hopes that one of the experts here can help me with my issue!

I have just installed a new linux distribution, kernel version 3.7 ~ amd64 architecture.

I just cannot seem to get the wireless driver to work. I am currently connected to eth0 and ethernet is working just fine

Though, when I try to look for wlan0 it just says that the driver does not exist! Here is some information about my machine that will be valuable!
```

int@0x8:~# lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Device 9900
00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI Trinity HDMI Audio Controller
00:02.0 PCI bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Root Port
00:04.0 PCI bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Root Port
00:07.0 PCI bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Root Port
00:10.0 USB controller: Advanced Micro Devices [AMD] FCH USB XHCI Controller (rev 03)
00:10.1 USB controller: Advanced Micro Devices [AMD] FCH USB XHCI Controller (rev 03)
00:11.0 SATA controller: Advanced Micro Devices [AMD] FCH SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] FCH USB OHCI Controller (rev 11)
00:12.2 USB controller: Advanced Micro Devices [AMD] FCH USB EHCI Controller (rev 11)
00:13.0 USB controller: Advanced Micro Devices [AMD] FCH USB OHCI Controller (rev 11)
00:13.2 USB controller: Advanced Micro Devices [AMD] FCH USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices [AMD] FCH SMBus Controller (rev 14)
00:14.2 Audio device: Advanced Micro Devices [AMD] FCH Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] FCH LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] FCH PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices [AMD] FCH USB OHCI Controller (rev 11)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 5
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Whistler LE [AMD Radeon HD 6625M Graphics]
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8723
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)

int@0x8:~# iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

```

Here are also some links that I followed throughout the day in hopes of solving this issue (none of the solutions worked)...

[http://ubuntuforums.org/showthread.php?t=1780662](http://ubuntuforums.org/showthread.php?t=1780662)
[http://ubuntuforums.org/showthread.php?t=798485&page=17](http://ubuntuforums.org/showthread.php?t=798485&page=17) (madwifi svn/website is gone)
[http://ubuntuforums.org/showthread.php?t=1362439](http://ubuntuforums.org/showthread.php?t=1362439) 
[http://askubuntu.com/questions/96775/wlan0-does-not-show-up-on-iwconfig](http://askubuntu.com/questions/96775/wlan0-does-not-show-up-on-iwconfig)
[http://www.linuxquestions.org/questions/linux-wireless-networking-41/wicd-no-wireless-networks-found-906227/](http://www.linuxquestions.org/questions/linux-wireless-networking-41/wicd-no-wireless-networks-found-906227/) (it's important to note that I deleted NetworkManager, and installed wicd(I read that the two conflict eachother))
[http://forums.debian.net/viewtopic.php?f=10&t=103573](http://forums.debian.net/viewtopic.php?f=10&t=103573)
[http://forums.debian.net/viewtopic.php?f=30&t=92910](http://forums.debian.net/viewtopic.php?f=30&t=92910)
[http://community.linuxmint.com/tutorial/view/1122](http://community.linuxmint.com/tutorial/view/1122)
[http://ubuntuforums.org/showthread.php?t=2017622&page=5](http://ubuntuforums.org/showthread.php?t=2017622&page=5)
[http://ubuntuforums.org/showthread.php?t=2139074](http://ubuntuforums.org/showthread.php?t=2139074)
[http://forums.opensuse.org/english/get-technical-help-here/wireless/477285-rtl8723ae-realtek-wirless-driver-hell-2.html](http://forums.opensuse.org/english/get-technical-help-here/wireless/477285-rtl8723ae-realtek-wirless-driver-hell-2.html)

^ Also, to anyone that has the same issue, and is reading this thread. Be sure to check those links above to see if any of them solve YOUR problem.

Thanks again, ANY help is appreciated!

Sincerly,
int0x8

---

### Post by chili555 on 2013-10-29
Wicd and Network Manager and madwifi and all those circa 2009 forum threads aren't going to solve your problem. Getting a proper driver installed is the only thing that will help. You have given us a very difficult task:> I have just installed a new linux distribution, kernel version 3.7 ~ amd64 architecture.Is your 'new linux distribution' based on Debian/Ubuntu and therefor uses .deb files or is it based on Red Hat and uses rpm? Can you download packages from an official repository or how do you install things? There are a lot of tough questions here.

Here is what I'd do if it were Ubuntu. With a working ethernet connection, I suggest you download this to your desktop: [http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.11-rc3/backports-3.11-rc3-1.tar.bz2](http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.11-rc3/backports-3.11-rc3-1.tar.bz2) Right-click it and select 'Extract Here.' Now open a terminal and do:```
sudo apt-get install build-essential linux-headers-generic
cd Desktop/backports-3.11-rc3-1/
make defconfig-rtlwifi
make
sudo make install
sudo modprobe rtl8723ae
```How this works outside of Ubuntu is anybody's guess. Good luck.

---

### Post by darkloader on 2013-10-29
Doctor, I applied your patch with the code you gave me, then I rebooted my machine as suggested at the end of the installer.

modprobe rtl8723ae didnt respond with an error, so I guess it installed correctly. After my reboot, I still do not have wireless internet. WICD doesn't pick it up either, and the wlan0 still does not exist.

Sorry about earlier though for not giving enough information about my kernel. I am using Debian. I do use .deb files. Here is the output of uname -r: 3.7-trunk-amd64 

I am using the latest build of kali linux with the 3.7 kernel, amd64 architecture.

Thanks again!

Sincerly,
int0x8

---

### Post by chili555 on 2013-10-29
What is the result of:```
sudo modprobe rtl8723ae
dmesg | grep -i rtl
iwconfig
```

---

### Post by darkloader on 2013-10-29
The output of the code you gave me is as follows:

```

int@0x8:~# sudo modprobe rtl8723ae

int@0x8:~# dmesg | grep -i rtl
[    4.392995] eth%d: RTL8101E at 0xffffc90000c7e000, 4c:72:b9:51:b5:58, IRQ 40
[    4.393806] eth0: Identified chip type is 'RTL8105E'.
[   13.384896] rtl8723ae: Using firmware rtlwifi/rtl8723fw_B.bin
[   13.746572] rtl8723ae 0000:02:00.0: firmware: agent aborted loading rtlwifi/rtl8723fw_B.bin (not found?)
[   13.746821] rtlwifi: Firmware rtlwifi/rtl8723fw_B.bin not available

int@0x8:~# iwconfig
eth0      no wireless extensions.

lo        no wireless extensions. 

```

---

### Post by chili555 on 2013-10-29
No firmware, eh? I think I'd try to install this: [http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.106_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.106_all.deb)

Then unload the driver:```
sudo modprobe -r rtl8723ae
```And reload it so it sees the shiny new firmware:```
sudo modprobe rtl8723ae
```

---

### Post by darkloader on 2013-10-29
Sorry, back up on that:

```

int@0x8:~/Desktop# sudo dpkg --install linux-firmware_1.106_all.deb
dpkg: considering removing amd64-microcode in favour of linux-firmware ...
dpkg: yes, will remove amd64-microcode in favour of linux-firmware
dpkg: considering removing atmel-firmware in favour of linux-firmware ...
dpkg: yes, will remove atmel-firmware in favour of linux-firmware
(Reading database ... 302814 files and directories currently installed.)
Unpacking linux-firmware (from linux-firmware_1.106_all.deb) ...
dpkg: error processing linux-firmware_1.106_all.deb (--install):
 trying to overwrite '/lib/firmware/agere_ap_fw.bin', which is also in package firmware-linux-nonfree 0.37
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 linux-firmware_1.106_all.deb

```

What did I do wrong?

---

### Post by chili555 on 2013-10-29
Nothing, probably, except trying to put a newer Ubuntu package on Kali. As I said above, from here on, it's anyone's guess!

Let's try a different way. Download this file to your desktop. [https://dl.dropboxusercontent.com/u/58267392/rtlwifi.zip](https://dl.dropboxusercontent.com/u/58267392/rtlwifi.zip)

Right-click the file and select 'Extract Here.' Now open a terminal and do:```
sudo mkdir /lib/firmware/rtlwifi
```It may report that the file exists; that's fine, just continue:```
sudo cp Desktop/rtlwifi/*  /lib/firmware/rtlwifi
sudo modprobe -r rtl8723ae
sudo modprobe rtl8723ae
```How about now?

---

### Post by darkloader on 2013-10-29
Okay doctor, that seems to have done the trick, but WICD still does not see any wireless networks:

```

int@0x8:~/Desktop# sudo cp Desktop/rtlwifi/*  /lib/firmware/rtlwifi
cp: cannot stat `Desktop/rtlwifi/*': No such file or directory
int@0x8:~/Desktop# ls
backports-3.11-rc3-1  knock.py  rtlwifi  silvertunnel.org_browser
int@0x8:~/Desktop# sudo cp ~/Desktop/rtlwifi/*  /lib/firmware/rtlwifi
int@0x8:~/Desktop# ls
backports-3.11-rc3-1  knock.py  rtlwifi  silvertunnel.org_browser
int@0x8:~/Desktop# sudo modprobe -r rtl8723ae
int@0x8:~/Desktop# sudo modprobe rtl8723ae
int@0x8:~/Desktop# ls
backports-3.11-rc3-1  knock.py  rtlwifi  silvertunnel.org_browser
int@0x8:~/Desktop# iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:on
          

```

Thanks

---

### Post by chili555 on 2013-10-29
> int@0x8:~/Desktop# sudo cp Desktop/rtlwifi/*  /lib/firmware/rtlwifi
cp: cannot stat `Desktop/rtlwifi/*': No such file or directoryAre you sure? You were already in Desktop:> int@0x8:~/[COLOR="#FF0000"]Desktop[/COLOR]#Therefor, when you asked to copy Desktop/rtlwifi/*, you were really asking to copy from ~/Desktop/Desktop/rtlwifi...which there isn't. Let's check. Reboot and show us:```
dmesg | grep -i rtl
ls /lib/firmware/rtlwifi
sudo iwlist wlan0 scan
```

---

### Post by darkloader on 2013-10-29
The only reason I entered the ~/ was because I was running the root terminal.

So after I rebooted my computer, I entered your code and I ran ```
sudo ifconfig wlan0 up
``` alongside. The output was:

```

int@0x8:~# dmesg | grep -i rtl
[    4.264266] eth%d: RTL8101E at 0xffffc90000c7c000, 4c:72:b9:51:b5:58, IRQ 40
[    4.278960] eth0: Identified chip type is 'RTL8105E'.
[   11.295226] rtl8723ae: Using firmware rtlwifi/rtl8723fw_B.bin
[   11.420791] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   11.421027] rtlwifi: wireless switch is on
int@0x8:~# ls /lib/firmware/rtlwifi
rtl8192cfw.bin  rtl8192cfwU_B.bin  rtl8192cfwU.bin  rtl8192cufw.bin  rtl8192defw.bin  rtl8192sefw.bin  rtl8712u.bin  rtl8723fw_B.bin  rtl8723fw.bin
int@0x8:~# sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning : Network is down
int@0x8:~# sudo ifconfig wlan0 up
int@0x8:~# ls
Desktop  madwifi.sh  rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012
int@0x8:~# sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: D8:5D:4C:F5:40:62
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"TP-LINK_F54062"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000016b2aec62
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 000E54502D4C494E4B5F463534303632
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101860003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401051B00000000000000000000000000000000000000
                    IE: Unknown: 3D1601051B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010006004000
                    IE: Unknown: DD850050F204104A0001101044000102103B0001031047001000000000000010000000D85D4CF540621021000754502D4C494E4B1023000B544C2D5752313034334E4410240003312E3010420003312E301054000800060050F20400011011001B576972656C65737320526F7574657220544C2D5752313034334E44100800020086103C000101
          Cell 02 - Address: 20:AA:4B:24:3B:FC
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-20 dBm  
                    Encryption key:on
                    ESSID:"Geeve"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000024d3a4cb92f
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 00054765657665
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD7F0050F204104A00011010440001021041000100103B00010310470010E0A77D1AB0C71C90FA131C66BF6015A510210005436973636F1023000D4C696E6B7379732045323530301024000776312E302E30331042000234321054000800060050F20400011011000D4C696E6B737973204532353030100800020084103C000103
                    IE: Unknown: DD090010180201F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: 64:70:02:B0:42:96
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"alex61"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f76f9a585
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 0006616C65783631
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101860003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34040D0800000000000000000000000000000000000000
                    IE: Unknown: 3D16040D0800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010006004000
                    IE: Unknown: DD850050F204104A0001101044000101103B0001031047001000000000000010000000647002B042961021000754502D4C494E4B1023000B544C2D5752313034334E4410240003312E3010420003312E301054000800060050F20400011011001B576972656C65737320526F7574657220544C2D5752313034334E44100800020086103C000101
          Cell 04 - Address: E8:40:F2:E7:AB:B4
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=12/70  Signal level=-98 dBm  
                    Encryption key:on
                    ESSID:"LEE FAMILY"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000243b429b51b
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 000A4C45452046414D494C59
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080400000000000000000000000000000000000000
                    IE: Unknown: DD6F0050F204104A0001101044000102103B000103104700104D73C5C27E6B5243D6440AAB1719670B10210005436973636F10230005436973636F1024000631323334353610420007303030303030311054000800060050F204000110110006313364306133100800020088103C000101
                    IE: Unknown: DD090010180202F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 05 - Address: EA:40:F2:E7:AB:B5
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000243b429aa02
                    Extra: Last beacon: 552ms ago
                    IE: Unknown: 000A00000000000000000000
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080400000000000000000000000000000000000000
                    IE: Unknown: DD090010180202F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 06 - Address: 02:2F:AF:07:20:07
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:off
                    ESSID:"HPJ610a.08B680"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=0000017eebdb4226
                    Extra: Last beacon: 384ms ago
                    IE: Unknown: 000E48504A363130612E303842363830
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 06020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
          Cell 07 - Address: 00:22:2D:11:62:94
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:off
                    ESSID:"WLAN"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000017eeb2d6a83
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 0004574C414E
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
          Cell 08 - Address: BC:14:01:24:B7:B8
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"BAYIT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master


```

To my surprise, wicd still says that there are no wireless networks found!

---

### Post by chili555 on 2013-10-29
I am not at all familiar with Wicd. Is there somewhere in Wicd that you need to select or type in 'wlan0?' Is Network Manager installed or removed? What does this tell us?```
dmesg | grep wlan

```

---

### Post by darkloader on 2013-10-29
This is the output of the code:

```

int@0x8:~# dmesg | grep wlan
[  275.180198] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

And this is what my wicd screen looks like:
[http://oi42.tinypic.com/1zdus0z.jpg](http://oi42.tinypic.com/1zdus0z.jpg)    (The image is too large to insert into here, just click the hyperlink)|

Doctor, you still there?

---

### Post by chili555 on 2013-10-29
> Doctor, you still there? Not for 24 hours; they do drag me away for meals and sleep once or twice a day! 

Is there any improvement if you type in wlan0 in the wireless interface box and click OK? And what about Network Manager? Is it installed or removed...or what?

---

### Post by darkloader on 2013-10-30
No no, I have network manager, I just don't use it.
Wow! I typed wlan0 into the wireless interface box, and it worked.

Though now another problem has submerged, whenever I try to connect to a wireless network it says: "This network requires encryption to be enabled."

---

### Post by chili555 on 2013-10-30
>      whenever I try to connect to a wireless network it says: "This network requires encryption to be enabled." Can you select 'Advanced Settings' and fill in the encryption key? Please see: [http://img6.imageshack.us/img6/7857/advancedsettings.png](http://img6.imageshack.us/img6/7857/advancedsettings.png)

---

### Post by darkloader on 2013-11-06
Yea, but whenever I fill it in, it either just doesnt connect or says 'validation failed'

---

### Post by chili555 on 2013-11-07
And you are sure the WPA password is correct? Any clues here?```
cat /var/log/syslog | grep -e wlan -e etwork | tail -n20
```

---

