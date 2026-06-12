---
title: "Ubuntu 12.04 WiFi Missing"
date: 2014-04-18
forum: Networking &amp; Wireless
---

### Post by Stob on 2014-04-18
I downloaded and installed 12.04 desktop. I have no WiFi. The icon is blank. On bootup, error missing firmware file B43. Then it says to go to wireless.kernel.org and download the correct firmware for this driver.

I have been trying to sort this out since. In reading through WiFiDocs/Driver/bcm43xx, it says I need to install B43-fwcutter package before installing the firmware for the Broadcom bcm4318. I have both of these files in the home folder. The WiKi Docs says I can double click the B43-fwcutter and install it. Well, it looks good, but the "install" icon won't do annything when clicking it. So that's not working. And consequently I can't get the firmware installed.

I have access to a PC that I can download files to a USB stick to get things to Ubuntu, but I'm hitting a roadblock. Any help is appreciated.

---

### Post by praseodym on 2014-04-18
You need to install the package **linux-firmware-nonfree**, b43-fwcutter is outdated. Lets check the output of

**lspci -nnk **

for more information

---

### Post by Stob on 2014-04-18
What part of that search would you like to know? It's long and I don't have the ability to cut and paste off of that PC.

---

### Post by praseodym on 2014-04-18
**lspci -nnk | grep -iA2 net**

thats one line

---

### Post by Stob on 2014-04-18
It shows 
Display modes
Display options
Resolving of Device ID's
etc.

Not to ask a dumb question, but when you show a line, between the nnk and grep above, what is that? Did I type wrong?

---

### Post by praseodym on 2014-04-18
Please show the "Broadcom" entry. This "|" is a "pipe", here it is AltGr+<

---

### Post by Stob on 2014-04-18
I can't make the "pipe" on my American keyboard. Can I?

---

### Post by praseodym on 2014-04-18
Can you copy/paste that line into the terminal?

---

### Post by Stob on 2014-04-18
No Sir I can't. Any other way of getting the info?

---

### Post by praseodym on 2014-04-18
Ok, check

```
lspci -nnk
```

and show the Broadcom output for the device IDs and the model of the card (if shown)

---

### Post by Stob on 2014-04-18
BCM4318 [Airforce One 54g] 802.11g Wireless LAN Controler [14e4:4318] (rev 02)

Is that helpful? Anything else I should look for, there is a lot here.

---

### Post by Stob on 2014-04-18
Subsystem:Gemtek Technology Co. Ltd Device [17f9:0006]
Kernel driver in use: b43-PCI-bridge
K ernel modules: ssb

---

### Post by praseodym on 2014-04-18
You need this file:

[http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz)

save it in "Downloads" and install it via:

```
sudo tar xvf ~/Downloads/2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
sudo modprobe -rfv b43
sudo modprobe -v b43
sudo service network-manager restart 
```

---

### Post by baphomet2 on 2014-04-18
On an US keyboard layout the "pipe" symbol is on the backslash \ key.  Shift + \ = |

---

### Post by Stob on 2014-04-18
> **praseodym said:**
> You need this file:

[http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz)

save it in "Downloads" and install it via:

```
sudo tar xvf ~/Downloads/2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
sudo modprobe -rfv b43
sudo modprobe -v b43
sudo service network-manager restart 
```

Thank you Sir for your patience and help. Will this download do all that is needed? Anything else after? One more novice question. In your commands, you have 3 lines. Do I do one and enter, then the next and enter? Or do I type it all in at once?

---

### Post by praseodym on 2014-04-18
One after another

---

### Post by Stob on 2014-04-21
I'm trying to fix a wireless issue, and need to input commands in a terminal. I'm being asked for a sudo password. The only password I have is at login. it doesn't work. How do I do this?

---

### Post by lisati on 2014-04-21
By "doesn't work" do you mean that it doesn't show when you type it? This is perfectly normal.

---

### Post by Stob on 2014-04-21
Thanks, it went through, but, in the commands I got on a different thread here, were '/' and the terminal says it is an invalid option. Should the / be a post?

---

### Post by The Cog on 2014-04-21
> **Stob said:**
> Thanks, it went through, but, in the commands I got on a different thread here, were '/' and the terminal says it is an invalid option. Should the / be a post?
Sorry, I have no idea what you mean. '/' is not a command, it is just the root folder of the filesystem. Perhaps you could post a link to the commands you're trying to follow?

---

### Post by aysiu on 2014-04-21
What's the exact command you're trying to run?

---

### Post by Stob on 2014-04-21
Sudo tar ~/Downloads/2480236-Broadcom-Firmware.tar.gz -C /lib/firmware/

---

### Post by lisati on 2014-04-21
Threads merged.

---

### Post by Stob on 2014-04-21
It ended up that I had made an error in typing. My mistake and I have successfully gotten a wireless connection!

However, Firefox will not connect to anything. "Can't find server" on any website I try. What should I look for?

---

### Post by praseodym on 2014-04-21
Check in Firefox->Settings->Network if proxy is activated. Also check the system proxy settings.

Lets see afterwards:
```

route -n
cat /etc/resolv.conf
ifconfig -a
iwconfig
iwlist chan
sudo iwlist scan
```

---

### Post by Stob on 2014-04-21
Firefox is set at "use system proxy settings".

There is a lot of info after the commands you show, what are you looking for? Lot of "cells"

---

### Post by praseodym on 2014-04-21
Please show "your" cell

---

### Post by Stob on 2014-04-21
There are 13 cells. I have to type these out, so I'll show cell 1:

Address: 00:23:97:23:89:AF
Channel 6
Frequency: 2.437 ghz
Quality=64/70.  Signal level= -46 dbm
Encryption key On
ESSID: MVFD
Bid Rates: 1mb/s; 2mb/s; 5.5mb/s; 11 mb/s; 18mb/s; 24mb/s; 36mb/s; 54mb/s
Mode: Master
Extra: TSP=000000caae7b2732
Extra: Last beacon: 12ms ago
IE: unknown:000E4D6964646C65627572674D564644
IE: unknown:010882848B962430486C
IE: unknown:030106
IE: unknown:2A0104
IE: unknown:2F0104
IE: unknown:32040C121860
IE: unknown:DD090010180204F000000

---

### Post by praseodym on 2014-04-21
Is it the full entry for cell 1? Can you show the other outputs (copy them into a txt file)

---

### Post by Stob on 2014-04-21
Cells 1-4, more to follow:

```
Scan completed : 
          Cell 01 - Address: 00:23:97:23:89:AF 
                    Channel:6 
                    Frequency:2.437 GHz (Channel 6) 
                    Quality=64/70  Signal level=-46 dBm   
                    Encryption key:on 
                    ESSID:"MiddleburgMVFD" 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 
                              24 Mb/s; 36 Mb/s; 54 Mb/s 
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s 
                    Mode:Master 
                    Extra:tsf=000000caae7b2732 
                    Extra: Last beacon: 12ms ago 
                    IE: Unknown: 000E4D6964646C65627572674D564644 
                    IE: Unknown: 010882848B962430486C 
                    IE: Unknown: 030106 
                    IE: Unknown: 2A0104 
                    IE: Unknown: 2F0104 
                    IE: Unknown: 32040C121860 
                    IE: Unknown: DD090010180204F0000000 
          Cell 02 - Address: 58:16:26:AE:E6:D3 
                    Channel:1 
                    Frequency:2.412 GHz (Channel 1) 
                    Quality=49/70  Signal level=-61 dBm   
                    Encryption key:on 
                    ESSID:"COL_Public" 
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s 
                              36 Mb/s; 48 Mb/s; 54 Mb/s 
                    Bit Rates:6 Mb/s; 9 Mb/s 
                    Mode:Master 
                    Extra:tsf=00000174fbbc968d 
                    Extra: Last beacon: 12ms ago 
                    IE: Unknown: 000A434F4C5F5075626C6963 
                    IE: Unknown: 01088B9618243048606C 
                    IE: Unknown: 030101 
                    IE: Unknown: 0706555320010B1E 
                    IE: Unknown: 2A0104 
                    IE: Unknown: 2F0104 
                    IE: IEEE 802.11i/WPA2 Version 1 
                        Group Cipher : CCMP 
                        Pairwise Ciphers (1) : CCMP 
                        Authentication Suites (1) : PSK 
                    IE: Unknown: 32020C12 
                    IE: Unknown: 0B050300100000 
                    IE: Unknown: 7F03000008 
                    IE: Unknown: 46050200010001 
                    IE: Unknown: DD09001018020300050000 
                    IE: Unknown: DD180050F202010180000364000027A4000042435E0062322F00 
                    IE: Unknown: DD0A0002BC01581626AEE6C0 
          Cell 03 - Address: 58:16:26:AE:E6:D0 
                    Channel:1 
                    Frequency:2.412 GHz (Channel 1) 
                    Quality=49/70  Signal level=-61 dBm   
                    Encryption key:on 
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00" 
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s 
                              36 Mb/s; 48 Mb/s; 54 Mb/s 
                    Bit Rates:6 Mb/s; 9 Mb/s 
                    Mode:Master 
                    Extra:tsf=00000174fbbbf104 
                    Extra: Last beacon: 4796ms ago 
                    IE: Unknown: 000C000000000000000000000000 
                    IE: Unknown: 01088B9618243048606C 
                    IE: Unknown: 030101 
                    IE: Unknown: 050400030000 
                    IE: Unknown: 0706555320010B1E 
                    IE: Unknown: 2A0104 
                    IE: Unknown: 2F0104 
                    IE: IEEE 802.11i/WPA2 Version 1 
                        Group Cipher : CCMP 
                        Pairwise Ciphers (1) : CCMP 
                        Authentication Suites (1) : 802.1x 
                       Preauthentication Supported 
                    IE: Unknown: 32020C12 
                    IE: Unknown: 0B050300100000 
                    IE: Unknown: 7F03000008 
                    IE: Unknown: 46050200010001 
                    IE: Unknown: DD09001018020300050000 
                    IE: Unknown: DD180050F202010180000364000027A4000042435E0062322F00 
                    IE: Unknown: DD0A0002BC01581626AEE6C0 
          Cell 04 - Address: 58:16:26:AE:E6:D1 
                    Channel:1 
                    Frequency:2.412 GHz (Channel 1) 
                    Quality=51/70  Signal level=-59 dBm   
                    Encryption key:on 
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00" 
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s 
                              36 Mb/s; 48 Mb/s; 54 Mb/s 
                    Bit Rates:6 Mb/s; 9 Mb/s 
                    Mode:Master 
                    Extra:tsf=00000174fbbbf2de 
                    Extra: Last beacon: 4796ms ago 
                    IE: Unknown: 000B0000000000000000000000 
                    IE: Unknown: 01088B9618243048606C 
                    IE: Unknown: 030101 
                    IE: Unknown: 050400030000 
                    IE: Unknown: 0706555320010B1E 
                    IE: Unknown: 2A0104 
                    IE: Unknown: 2F0104 
                    IE: IEEE 802.11i/WPA2 Version 1 
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK 
                    IE: Unknown: 32020C12 
                    IE: Unknown: 0B050300100000 
                    IE: Unknown: 7F03000008 
                    IE: Unknown: 46050200010001 
                    IE: Unknown: DD09001018020300050000 
                    IE: Unknown: DD180050F202010180000364000027A4000042435E0062322F00 
                    IE: Unknown: DD0A0002BC01581626AEE6C0
```

---

### Post by Stob on 2014-04-21
Cell 5-9
```

  Cell 05 - Address: 58:16:26:AE:E6:D2 
                    Channel:1 
                    Frequency:2.412 GHz (Channel 1) 
                    Quality=51/70  Signal level=-59 dBm   
                    Encryption key:on 
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00" 
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s 
                              36 Mb/s; 48 Mb/s; 54 Mb/s 
                    Bit Rates:6 Mb/s; 9 Mb/s 
                    Mode:Master 
                    Extra:tsf=00000174fbbbf4bd 
                    Extra: Last beacon: 4796ms ago 
                    IE: Unknown: 000D00000000000000000000000000 
                    IE: Unknown: 01088B9618243048606C 
                    IE: Unknown: 030101 
                    IE: Unknown: 050400030100 
                    IE: Unknown: 0706555320010B1E 
                    IE: Unknown: 2A0104 
                    IE: Unknown: 2F0104 
                    IE: IEEE 802.11i/WPA2 Version 1 
                        Group Cipher : CCMP 
                        Pairwise Ciphers (1) : CCMP 
                        Authentication Suites (1) : 802.1x 
                       Preauthentication Supported 
                    IE: Unknown: 32020C12 
                    IE: Unknown: 0B050300100000 
                    IE: Unknown: 7F03000008 
                    IE: Unknown: 46050200010001 
                    IE: Unknown: DD09001018020300050000 
                    IE: Unknown: DD180050F202010180000364000027A4000042435E0062322F00 
                    IE: Unknown: DD0A0002BC01581626AEE6C0 
          Cell 06 - Address: FC:15:B4:B0:5B:4C 
                    Channel:6 
                    Frequency:2.437 GHz (Channel 6) 
                    Quality=64/70  Signal level=-46 dBm   
                    Encryption key:on 
                    ESSID:"HP-Print-4C-Photosmart 7520" 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s 
                              11 Mb/s; 12 Mb/s; 18 Mb/s 
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s 
                    Mode:Master 
                    Extra:tsf=000002945bd848f0 
                    Extra: Last beacon: 12ms ago 
                    IE: Unknown: 001B48502D5072696E742D34432D50686F746F736D6172742037353230 
                    IE: Unknown: 010802040B0C12161824 
                    IE: Unknown: 030106 
                    IE: Unknown: 2A0100 
                    IE: Unknown: 2D1A0055010200050039010400580200007B01040058020000330102 
                    IE: IEEE 802.11i/WPA2 Version 1 
                        Group Cipher : CCMP 
                        Pairwise Ciphers (1) : CCMP 
                        Authentication Suites (1) : PSK 
                    IE: Unknown: 32043048606C 
                    IE: Unknown: 3D1606000100000000000000000000000000000000000000 
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00 
                    IE: Unknown: DD7708000900040000000701020100020178031650686F746F736D617274203735323020736572696573040F37353230000000000000000F54483405105448343149373131355230355959000006101C852A4DB8001F08ABCDFC15B4B05B4C0704C0A8012D080200D4090200080A04000000010B0400000000 
          Cell 07 - Address: 58:16:26:AF:51:F0 
                    Channel:6 
                    Frequency:2.437 GHz (Channel 6) 
                    Quality=38/70  Signal level=-72 dBm   
                    Encryption key:on 
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00" 
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s 
                              36 Mb/s; 48 Mb/s; 54 Mb/s 
                    Bit Rates:6 Mb/s; 9 Mb/s 
                    Mode:Master 
                    Extra:tsf=00000174fb17e0e8 
                    Extra: Last beacon: 224ms ago 
                    IE: Unknown: 000C000000000000000000000000 
                    IE: Unknown: 01088B9618243048606C 
                    IE: Unknown: 030106 
                    IE: Unknown: 050400030000 
                    IE: Unknown: 0706555320010B1E 
                    IE: Unknown: 2A0100 
                    IE: Unknown: 2F0100 
                    IE: IEEE 802.11i/WPA2 Version 1 
                        Group Cipher : CCMP 
                        Pairwise Ciphers (1) : CCMP 
                        Authentication Suites (1) : 802.1x 
                       Preauthentication Supported 
                    IE: Unknown: 32020C12 
                    IE: Unknown: 0B050000130000 
                    IE: Unknown: 7F03000008 
                    IE: Unknown: 46050200010001 
                    IE: Unknown: DD09001018020000050000 
                    IE: Unknown: DD180050F202010180000364000027A4000042435E0062322F00 
                    IE: Unknown: DD0A0002BC01581626AF51E0 
          Cell 08 - Address: 58:16:26:AF:51:F1 
                    Channel:6 
                    Frequency:2.437 GHz (Channel 6) 
                    Quality=40/70  Signal level=-70 dBm   
                    Encryption key:on 
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00" 
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s 
                              36 Mb/s; 48 Mb/s; 54 Mb/s 
                    Bit Rates:6 Mb/s; 9 Mb/s 
                    Mode:Master 
                    Extra:tsf=00000174fb17e2d5 
                    Extra: Last beacon: 224ms ago 
                    IE: Unknown: 000B0000000000000000000000 
                    IE: Unknown: 01088B9618243048606C 
                    IE: Unknown: 030106 
                    IE: Unknown: 050400030000 
                    IE: Unknown: 0706555320010B1E 
                    IE: Unknown: 2A0100 
                    IE: Unknown: 2F0100 
                    IE: IEEE 802.11i/WPA2 Version 1 
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK 
                    IE: Unknown: 32020C12 
                    IE: Unknown: 0B050000130000 
                    IE: Unknown: 7F03000008 
                    IE: Unknown: 46050200010001 
                    IE: Unknown: DD09001018020000050000 
                    IE: Unknown: DD180050F202010180000364000027A4000042435E0062322F00 
                    IE: Unknown: DD0A0002BC01581626AF51E0 
          Cell 09 - Address: 58:16:26:AF:51:F2 
                    Channel:6 
                    Frequency:2.437 GHz (Channel 6) 
                    Quality=42/70  Signal level=-68 dBm   
                    Encryption key:on 
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00" 
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s 
                              36 Mb/s; 48 Mb/s; 54 Mb/s 
                    Bit Rates:6 Mb/s; 9 Mb/s 
                    Mode:Master 
                    Extra:tsf=00000174fb17e4bd 
                    Extra: Last beacon: 224ms ago 
                    IE: Unknown: 000D00000000000000000000000000 
                    IE: Unknown: 01088B9618243048606C 
                    IE: Unknown: 030106 
                    IE: Unknown: 050400030000 
                    IE: Unknown: 0706555320010B1E 
                    IE: Unknown: 2A0100 
                    IE: Unknown: 2F0100 
                    IE: IEEE 802.11i/WPA2 Version 1 
                        Group Cipher : CCMP 
                        Pairwise Ciphers (1) : CCMP 
                        Authentication Suites (1) : 802.1x 
                       Preauthentication Supported 
                    IE: Unknown: 32020C12 
                    IE: Unknown: 0B050000130000 
                    IE: Unknown: 7F03000008 
                    IE: Unknown: 46050200010001 
                    IE: Unknown: DD09001018020000050000 
                    IE: Unknown: DD180050F202010180000364000027A4000042435E0062322F00 
                    IE: Unknown: DD0A0002BC01581626AF51E0
```

---

### Post by Stob on 2014-04-21
Cell 10-13, this is all of it:```


 Cell 10 - Address: 58:16:26:AF:51:F3 
                    Channel:6 
                    Frequency:2.437 GHz (Channel 6) 
                    Quality=42/70  Signal level=-68 dBm   
                    Encryption key:on 
                    ESSID:"COL_Public" 
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s 
                              36 Mb/s; 48 Mb/s; 54 Mb/s 
                    Bit Rates:6 Mb/s; 9 Mb/s 
                    Mode:Master 
                    Extra:tsf=00000174fae9cf38 
                    Extra: Last beacon: 12ms ago 
                    IE: Unknown: 000A434F4C5F5075626C6963 
                    IE: Unknown: 01088B9618243048606C 
                    IE: Unknown: 030106 
                    IE: Unknown: 0706555320010B1E 
                    IE: Unknown: 2A0100 
                    IE: Unknown: 2F0100 
                    IE: IEEE 802.11i/WPA2 Version 1 
                        Group Cipher : CCMP 
                        Pairwise Ciphers (1) : CCMP 
                        Authentication Suites (1) : PSK 
                    IE: Unknown: 32020C12 
                    IE: Unknown: 0B050000100000 
                    IE: Unknown: 7F03000008 
                    IE: Unknown: 46050200010001 
                    IE: Unknown: DD09001018020000050000 
                    IE: Unknown: DD180050F202010180000364000027A4000042435E0062322F00 
                    IE: Unknown: DD0A0002BC01581626AF51E0 
          Cell 11 - Address: 58:16:26:AF:60:73 
                    Channel:11 
                    Frequency:2.462 GHz (Channel 11) 
                    Quality=70/70  Signal level=-39 dBm   
                    Encryption key:on 
                    ESSID:"COL_Public" 
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s 
                              36 Mb/s; 48 Mb/s; 54 Mb/s 
                    Bit Rates:6 Mb/s; 9 Mb/s 
                    Mode:Master 
                    Extra:tsf=00000174fb4c972a 
                    Extra: Last beacon: 12ms ago 
                    IE: Unknown: 000A434F4C5F5075626C6963 
                    IE: Unknown: 01088B9618243048606C 
                    IE: Unknown: 03010B 
                    IE: Unknown: 0706555320010B1E 
                    IE: Unknown: 2A0100 
                    IE: Unknown: 2F0100 
                    IE: IEEE 802.11i/WPA2 Version 1 
                        Group Cipher : CCMP 
                        Pairwise Ciphers (1) : CCMP 
                        Authentication Suites (1) : PSK 
                    IE: Unknown: 32020C12 
                    IE: Unknown: 0B0500000F0000 
                    IE: Unknown: 7F03000008 
                    IE: Unknown: 46050200010001 
                    IE: Unknown: 33030C0B0B 
                    IE: Unknown: DD09001018020000050000 
                    IE: Unknown: DD180050F202010180000364000027A4000042435E0062322F00 
                    IE: Unknown: DD0A0002BC01581626AF6060 
          Cell 12 - Address: 58:16:26:AF:00:93 
                    Channel:11 
                    Frequency:2.462 GHz (Channel 11) 
                    Quality=48/70  Signal level=-62 dBm   
                    Encryption key:on 
                    ESSID:"COL_Public" 
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s 
                              36 Mb/s; 48 Mb/s; 54 Mb/s 
                    Bit Rates:6 Mb/s; 9 Mb/s 
                    Mode:Master 
                    Extra:tsf=00000174faa9a778 
                    Extra: Last beacon: 12ms ago 
                    IE: Unknown: 000A434F4C5F5075626C6963 
                    IE: Unknown: 01088B9618243048606C 
                    IE: Unknown: 03010B 
                    IE: Unknown: 0706555320010B1E 
                    IE: Unknown: 2A0100 
                    IE: Unknown: 2F0100 
                    IE: IEEE 802.11i/WPA2 Version 1 
                        Group Cipher : CCMP 
                        Pairwise Ciphers (1) : CCMP 
                        Authentication Suites (1) : PSK 
                    IE: Unknown: 32020C12 
                    IE: Unknown: 0B050000160000 
                    IE: Unknown: 7F03000008 
                    IE: Unknown: 46050200010001 
                    IE: Unknown: 33030C0B0B 
                    IE: Unknown: DD09001018020000050000 
                    IE: Unknown: DD180050F202010180000364000027A4000042435E0062322F00 
                    IE: Unknown: DD0A0002BC01581626AF0080 
          Cell 13 - Address: 58:16:26:AF:17:33 
                    Channel:11 
                    Frequency:2.462 GHz (Channel 11) 
                    Quality=42/70  Signal level=-68 dBm   
                    Encryption key:on 
                    ESSID:"COL_Public" 
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s 
                              36 Mb/s; 48 Mb/s; 54 Mb/s 
                    Bit Rates:6 Mb/s; 9 Mb/s 
                    Mode:Master 
                    Extra:tsf=00000174fb50afb4 
                    Extra: Last beacon: 12ms ago 
                    IE: Unknown: 000A434F4C5F5075626C6963 
                    IE: Unknown: 01088B9618243048606C 
                    IE: Unknown: 03010B 
                    IE: Unknown: 0706555320010B1E 
                    IE: Unknown: 2A0100 
                    IE: Unknown: 2F0100 
                    IE: IEEE 802.11i/WPA2 Version 1 
                        Group Cipher : CCMP 
                        Pairwise Ciphers (1) : CCMP 
                        Authentication Suites (1) : PSK 
                    IE: Unknown: 32020C12 
                    IE: Unknown: 0B0500000E0000 
                    IE: Unknown: 7F03000008 
                    IE: Unknown: 46050200010001 
                    IE: Unknown: 33030C0B0B 
                    IE: Unknown: DD09001018020000050000 
                    IE: Unknown: DD180050F202010180000364000027A4000042435E0062322F00 
                    IE: Unknown: DD0A0002BC01581626AF1720 
lo        Interface doesn't support scanning. 
eth0      Interface doesn't support scanning.
```

---

### Post by praseodym on 2014-04-21
There are a lot of networks with the same ESSID but different AP-MAC-addresses. Choose one of them, e.g. Cell 10

```
Cell 10 - Address: [COLOR="#FF0000"]58:16:26:AF:51:F3[/COLOR]
Channel:6
Frequency:2.437 GHz (Channel 6)
Quality=42/70 Signal level=-68 dBm
Encryption keyn
ESSID:"COL_Public" 
```
and add the respective MAC-address in the field **BSSID** of your profile

---

### Post by Stob on 2014-04-21
I need to use the Cell 1  wireless. The Cell 10 is a network wireless that I don't have access to. So can I input the cell 1 info?

Where do I find the **BSSID** of my profile?

---

### Post by praseodym on 2014-04-21
For Cell 01 it is:
```

Scan completed :
Cell 01 - Address: [COLOR="#FF0000"]00:23:97:23:89:AF[/COLOR]
Channel:6
Frequency:2.437 GHz (Channel 6)
Quality=64/70 Signal level=-46 dBm
Encryption keyn
ESSID:"MiddleburgMVFD" 
```
Its only WEP encrypted!

---

### Post by Stob on 2014-04-21
It's the only one I have access to. I found the BSSID in Network/Wireless/Edit, entered the address. There still isn't a connection. There is an open field for "Cloned MAC address". Should there be something filled in there?

---

### Post by praseodym on 2014-04-21
Please show

```
dmesg | egrep '[W]lan|b43|[F]irm|key'
```

---

### Post by Stob on 2014-04-21
dmesg | egrep '[W]lan|b43|[F]irm|key' 
[    0.837056] Asymmetric key parser 'x509' registered 
[    1.061175] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 8d304f11d631e8152aa9fb1b909ef288f0069efb' 
[    1.247415] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4 
[   11.083775] b43-phy0: Broadcom 4318 WLAN found (core revision 9) 
[   11.124042] b43-phy0: Found PHY: Analog 3, Type 2 (G), Revision 7 
[   20.040055] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10) 
[   23.515431] b43 ssb0:0 wlan0: disabling HT/VHT due to WEP/TKIP use 
[   23.515439] b43 ssb0:0 wlan0: disabling HT as WMM/QoS is not supported by the AP 
[   23.515443] b43 ssb0:0 wlan0: disabling VHT as WMM/QoS is not supported by the AP

---

### Post by praseodym on 2014-04-21
```
 [ 23.515431] b43 ssb0:0 wlan0: disabling HT/VHT due to WEP/TKIP use 
```

Are you sure the key is correct? Did you chose WEP in the NM profile?

---

### Post by Stob on 2014-04-21
The key is correct, the wifi icon shows good signal and that it is connected. The security was set at WEP 40/128-bit key, I changed it to WEP 128-bit-passphrase and there is still no internet connection.

I have used this same wireless on another laptop, same key, and worked fine. So I know the network works OK.

---

### Post by praseodym on 2014-04-21
Please check these options:
```

echo "options b43 pio=1 qos=0" | sudo tee /etc/modprobe.d/b43.conf
sudo modprobe -rfv b43
sudo modprobe -v b43
sudo service network-manage restart
dmesg | grep b43
iwconfig
```

---

### Post by Stob on 2014-04-21
This disconnected the laptop from the wireless network. But here are the results from the above.

```
echo "options b43 pio=1 qos=0" | sudo tee /etc/modprobe.d/b43.config 
[sudo] password for wayne: 
options b43 pio=1 qos=0 
[EMAIL="wayne@wayne-MX6128:~$"]wayne@wayne-MX6128:~$[/EMAIL] sudo modprobe -rfv b43 
WARNING: All config files need .conf: /etc/modprobe.d/b43.config, it will be ignored in a future release. 
rmmod /lib/modules/3.11.0-15-generic/kernel/drivers/net/wireless/b43/b43.ko 
rmmod /lib/modules/3.11.0-15-generic/kernel/net/mac80211/mac80211.ko 
rmmod /lib/modules/3.11.0-15-generic/kernel/net/wireless/cfg80211.ko 
rmmod /lib/modules/3.11.0-15-generic/kernel/drivers/ssb/ssb.ko 
rmmod /lib/modules/3.11.0-15-generic/kernel/drivers/bcma/bcma.ko 
[EMAIL="wayne@wayne-MX6128:~$"]wayne@wayne-MX6128:~$[/EMAIL] sudo modprobe -v b43 
WARNING: All config files need .conf: /etc/modprobe.d/b43.config, it will be ignored in a future release. 
insmod /lib/modules/3.11.0-15-generic/kernel/drivers/bcma/bcma.ko 
insmod /lib/modules/3.11.0-15-generic/kernel/drivers/ssb/ssb.ko 
insmod /lib/modules/3.11.0-15-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.11.0-15-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.11.0-15-generic/kernel/drivers/net/wireless/b43/b43.ko pio=1 qos=0 
[EMAIL="wayne@wayne-MX6128:~$"]wayne@wayne-MX6128:~$[/EMAIL] sudo service network-manager restart 
network-manager stop/waiting 
network-manager start/running, process 4624 
[EMAIL="wayne@wayne-MX6128:~$"]wayne@wayne-MX6128:~$[/EMAIL] dmesg | grep b43 
[   11.083775] b43-phy0: Broadcom 4318 WLAN found (core revision 9) 
[   11.124042] b43-phy0: Found PHY: Analog 3, Type 2 (G), Revision 7 
[   20.040055] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10) 
[   23.515431] b43 ssb0:0 wlan0: disabling HT/VHT due to WEP/TKIP use 
[   23.515439] b43 ssb0:0 wlan0: disabling HT as WMM/QoS is not supported by the AP 
[   23.515443] b43 ssb0:0 wlan0: disabling VHT as WMM/QoS is not supported by the AP 
[ 4519.251707] b43-phy0: Broadcom 4318 WLAN found (core revision 9) 
[ 4519.300094] b43-phy0: Found PHY: Analog 3, Type 2 (G), Revision 7 
[ 4519.556130] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10) 
[ 4519.576173] b43-phy0 warning: Forced PIO by use_pio module parameter. This should not be needed and will result in lower performance. 
[ 4522.632418] b43 ssb0:0 wlan0: disabling HT/VHT due to WEP/TKIP use 
[ 4522.632426] b43 ssb0:0 wlan0: disabling HT as WMM/QoS is not supported by the AP 
[ 4522.632430] b43 ssb0:0 wlan0: disabling VHT as WMM/QoS is not supported by the AP 
[ 4552.360102] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10) 
[ 4552.380207] b43-phy0 warning: Forced PIO by use_pio module parameter. This should not be needed and will result in lower performance. 
[ 4555.511784] b43 ssb0:0 wlan0: disabling HT/VHT due to WEP/TKIP use 
[ 4555.511793] b43 ssb0:0 wlan0: disabling HT as WMM/QoS is not supported by the AP 
[ 4555.511797] b43 ssb0:0 wlan0: disabling VHT as WMM/QoS is not supported by the AP 
[EMAIL="wayne@wayne-MX6128:~$"]wayne@wayne-MX6128:~$[/EMAIL] iwconfig 
wlan0     IEEE 802.11bg  ESSID:"MiddleburgMVFD"   
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:23:97:23:89:AF    
          Bit Rate=54 Mb/s   Tx-Power=20 dBm    
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 
          Link Quality=66/70  Signal level=-44 dBm   
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:4  Invalid misc:0   Missed beacon:0 
lo        no wireless extensions. 
eth0      no wireless extensions. 
[EMAIL="wayne@wayne-MX6128:~$"]wayne@wayne-MX6128:~$[/EMAIL]
```

---

### Post by praseodym on 2014-04-21
Looks like you are connected now?!
```

ifconfig wlan0
cat /etc/resolv.conf
route -n
iwlist wlan0 chan
```

---

### Post by Stob on 2014-04-21
The **wireless is connected**, but Firefox still will not recognize the connection. I cannot load any webpage. Thunderbird is not connected.

---

### Post by praseodym on 2014-04-21
Can you install packages?

```
ping -c 2 $(route -n | grep UG | awk {'print $2'})
ping -c 2 www.ubuntuusers.de
ping -c 2 213.95.41.11 
```

---

### Post by Stob on 2014-04-21
I did the commands. The ping -c 2 [www.ubuntuusers.de]("http://www.ubuntuusers.de") returned ping: unknown host [www.ubuntuusers.de](www.ubuntuusers.de)

Otherwise, the first says 2 packets transmitted, 2 received. What do I do?

---

### Post by praseodym on 2014-04-21
This means you can ping the router but nothing outside. Lets try:
```

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee /etc/resolv.conf
sudo service network-manager restart
```

---

### Post by Stob on 2014-04-22
Upon restarting in the morning, the wireless is connected and Firefox OS on line! Thank You! So far, so good!

---

