---
title: "Acer S7 392 with Intel Corporation Wireless 7260 Lagging Ubuntu 13.10"
date: 2014-02-08
forum: Networking &amp; Wireless
---

### Post by Kwakkiezalf on 2014-02-08
Hi,

I got my new Acer Aspire S7392 running on ubuntu 13.10,but get bad performance on my wifi. I am sure it is related to my pc and not the network. I get lag peaks during onlinegaming which I only got with this config.

Anyone have any clue if it could be related to some driver not working ?

Looking forward to some reply.

Cheers

---

### Post by praseodym on 2014-02-08
Hi, there's a bug with the N-mode of the driver, deactivate it via:
```

echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```

---

### Post by Kwakkiezalf on 2014-02-08
Thx praseodym. First code, runs fine but responce on [COLOR=#000000][FONT=Ubuntu Mono]sudo modprobe -rfv iwlwifi is: 
[/FONT][/COLOR]
FATAL: Module iwlwifi is in use
[COLOR=#000000][FONT=Ubuntu Mono]
Any clue for that?[/FONT][/COLOR]

I did follow it up with the 3rd code...with now error to follow.

lag still remains
[COLOR=#000000][FONT=Ubuntu Mono]



[/FONT][/COLOR]

---

### Post by praseodym on 2014-02-08
Reboot.

---

### Post by Kwakkiezalf on 2014-02-09
[[COLOR=#000000]praseodym[/COLOR]]("http://ubuntuforums.org/member.php?u=1411497")[COLOR=#000000] ,[/COLOR]

[COLOR=#000000]Even after the reboot the issue remained. I have dual boot, and in windows the issue does not occur. Somehow it must be related to Ubuntu.[/COLOR]

[COLOR=#000000]Any alternatives?[/COLOR]

---

### Post by praseodym on 2014-02-09
Lets check:
```

ifconfig -a
iwconfig
cat /etc/resolv.conf
iwlist chan
sudo iwlist scan
dmesg | grep iwl
```

---

### Post by chili555 on 2014-02-09
@praseodym--

There is a new and improved firmware available that I suggest OP try: [https://git.kernel.org/cgit/linux/kernel/git/egrumbach/linux-firmware.git/plain/iwlwifi-7260-7.ucode](https://git.kernel.org/cgit/linux/kernel/git/egrumbach/linux-firmware.git/plain/iwlwifi-7260-7.ucode)

---

### Post by praseodym on 2014-02-09
The package "linux-firmware" does already contain it in 13.10:

[http://packages.ubuntu.com/saucy/all/linux-firmware/filelist](http://packages.ubuntu.com/saucy/all/linux-firmware/filelist)

---

### Post by chili555 on 2014-02-09
> **praseodym said:**
> The package "linux-firmware" does already contain it in 13.10:

[http://packages.ubuntu.com/saucy/all/linux-firmware/filelist](http://packages.ubuntu.com/saucy/all/linux-firmware/filelist)linux-firmware-nonfree contains the older file, not the new and improved. The one in linux-firmware-nonfree is 682892 bytes and the new and improved is 683236.> $ ls -al /lib/firmware | grep 7260
-rw-r--r--  1 root root  683236 Jan 17 11:34 iwlwifi-7260-7.ucode
-rw-r--r--  1 root root  682892 Jul 10  2013 iwlwifi-7260-7.ucode.bak

---

### Post by praseodym on 2014-02-09
In 13.10 "-nonfree" does not contain the file:

[http://packages.ubuntu.com/saucy/all/linux-firmware-nonfree/filelist](http://packages.ubuntu.com/saucy/all/linux-firmware-nonfree/filelist)

I just installed both of the saucy packages on 12.04:
```

ls -al /lib/firmware | grep 7260
-rw-r--r--  1 root root  682892 Jul 10  2013 iwlwifi-7260-7.ucode
dpkg -l linux-firmware | grep ii
ii  linux-firmware                                  1.116                                      Firmware for Linux kernel drivers
dpkg -l linux-firmware-nonfree | grep ii
ii  linux-firmware-nonfree                          1.14ubuntu1                                Non-free firmware for Linux kernel drivers
```
We'll see when (and if) we have more information ;)

---

### Post by Kwakkiezalf on 2014-02-09
Praseodym,

Thank you for your support so far. This is what i got back:

ifconfig -a:
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:144 errors:0 dropped:0 overruns:0 frame:0
          TX packets:144 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15299 (15.2 KB)  TX bytes:15299 (15.2 KB)


wlan0     Link encap:Ethernet  HWaddr 5c:51:4f:5d:a3:c2  
          inet addr:192.168.0.108  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::5e51:4fff:fe5d:a3c2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:752 errors:0 dropped:0 overruns:0 frame:0
          TX packets:589 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:445534 (445.5 KB)  TX bytes:74210 (74.2 KB)



iwconfig:

lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"Midas 5.0"  
          Mode:Managed  Frequency:5.18 GHz  Access Point: 00:0C:F6:E2:DE:D4   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:25   Missed beacon:0


cat /etc/resolv.conf:
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search XXXXX

---

### Post by Kwakkiezalf on 2014-02-09
iwlist chan:
lo        no frequency information.


wlan0     32 channels in total; available frequencies :
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
          Current Frequency:5.18 GHz (Channel 36)

---

### Post by Kwakkiezalf on 2014-02-09
sudo iwlist scan:


lo Interface doesn't support scanning.


wlan0 Scan completed :
Cell 01 - Address: 00:0C:F6:E2E4
Channel:36
Frequency:5.18 GHz (Channel 36)
Quality=59/70 Signal level=-51 dBm 
Encryption keyn
ESSID:"Midas 5.0"
Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=00000512f0b2e93f
Extra: Last beacon: 8ms ago
IE: Unknown: 00094D6964617320352E30
IE: Unknown: 01088C129824B048606C
IE: Unknown: 030124
IE: Unknown: 3C0401162400
IE: Unknown: 2D1AEE0117FFFF0000010000000000000000000000000C1846470900
IE: Unknown: 3D1624050700000000000000000000000000000000000000
IE: Unknown: 3E0100
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : PSK
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : PSK
IE: Unknown: DD180050F2020101060003A4000027A4000042435E0062322F00
IE: Unknown: 0B05020001127A
IE: Unknown: DD07000C4304000000
IE: Unknown: 200103
IE: Unknown: 0706474220240410
IE: Unknown: DD8B0050F204104A0001101044000102103B000103104700102880288028801880A880000CF6E2DED41021000753697465636F6D1023000E53697465636F6D20526F757465721024000E574C522D353030302F76323030311042000831323334353637381054000800060050F20400011011000E53697465636F6D20526F75746572100800020084103C000102
Cell 02 - Address: 50:7E:5D:7F:A7:EF
Channel:10
Frequency:2.457 GHz (Channel 10)
Quality=49/70 Signal level=-61 dBm 
Encryption keyn
ESSID:"VGV75197FA7EF"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
18 Mb/s; 36 Mb/s; 54 Mb/s
Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
Mode:Master
Extra:tsf=000000a7c6dcfcbb
Extra: Last beacon: 8ms ago
IE: Unknown: 000D56475637353139374641374546
IE: Unknown: 010882848B961224486C
IE: Unknown: 03010A
IE: Unknown: 2A0104
IE: Unknown: 32040C183060
IE: Unknown: 2D1A6C0017FFFF0000000000000000000000000000000C0000000000
IE: Unknown: 3D160A000000000000000000000000000000000000000000
IE: Unknown: 3E0100
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (1) : TKIP
Authentication Suites (1) : PSK
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : PSK
IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
IE: Unknown: 0B05000022127A
IE: Unknown: 7F0101
IE: Unknown: DD8F0050F204104A00011010440001021041000100103B0001031047001000000000000000030000507E5D7FA7EF1021000B436F72706F726174696F6E1023000B564756373531394B5732321024000930322E30302E3132341042000A4A3234323037303637311054000800060050F204000110110014576972656C65737320526F757465722857464129100800020084
IE: Unknown: 07064E4C20010D10
Cell 03 - Address: 00:0C:F6:E2E0
Channel:11
Frequency:2.462 GHz (Channel 11)
Quality=65/70 Signal level=-45 dBm 
Encryption keyn
ESSID:"Midas 2.4"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
18 Mb/s; 36 Mb/s; 54 Mb/s
Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
Mode:Master
Extra:tsf=00000512f06c53e0
Extra: Last beacon: 8ms ago
IE: Unknown: 00094D6964617320322E34
IE: Unknown: 010882848B961224486C
IE: Unknown: 03010B
IE: Unknown: 2A0104
IE: Unknown: 32040C183060
IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
IE: Unknown: 3D160B070700000000000000000000000000000000000000
IE: Unknown: 3E0100
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : PSK
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : PSK
IE: Unknown: DD180050F2020101860003A4000027A4000042435E0062322F00
IE: Unknown: 0B05020094127A
IE: Unknown: DD07000C4304000000
IE: Unknown: 0706474220010D10
IE: Unknown: DD8B0050F204104A0001001044000102103B00010310470010BC329E001DD811B28601000CF6E2DED01021000753697465636F6D1023000E53697465636F6D20526F757465721024000E574C522D353030302F76323030311042000831323334353637381054000800060050F20400011011000E53697465636F6D20526F75746572100800020004103C000101
Cell 04 - Address: CC:AF:78:53:3F6
Channel:11
Frequency:2.462 GHz (Channel 11)
Quality=39/70 Signal level=-71 dBm 
Encryption keyn
ESSID:"Ziggo5B44C"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
24 Mb/s; 36 Mb/s; 54 Mb/s
Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
Mode:Master
Extra:tsf=000000fb29cc720b
Extra: Last beacon: 8ms ago
IE: Unknown: 000A5A6967676F3542343443
IE: Unknown: 010882848B962430486C
IE: Unknown: 03010B
IE: Unknown: 2A0104
IE: Unknown: 2F0104
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: Unknown: 32040C121860
IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
IE: Unknown: 3D160B081500000000000000000000000000000000000000
IE: Unknown: 4A0E14000A002C01C800140005001900
IE: Unknown: 7F0101
IE: Unknown: DD770050F204104A0001101044000102103B00010310470010714B1E979A7690F725A01A7D19844840102100045562656510230004556265651024000631323334353610420007303030303030311054000800060050F204000110110006556265654150100800022008103C0001011049000600372A000120
IE: Unknown: DD090010180206F02C0000
IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
Cell 05 - Address: CE:AF:78:53:3F7
Channel:11
Frequency:2.462 GHz (Channel 11)
Quality=40/70 Signal level=-70 dBm 
Encryption keyn
ESSID:"Ziggo"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
24 Mb/s; 36 Mb/s; 54 Mb/s
Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
Mode:Master
Extra:tsf=000000fb29cc7f0b
Extra: Last beacon: 8ms ago
IE: Unknown: 00055A6967676F
IE: Unknown: 010882848B962430486C
IE: Unknown: 03010B
IE: Unknown: 2A0104
IE: Unknown: 2F0104
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : 802.1x
IE: Unknown: 32040C121860
IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
IE: Unknown: 3D160B081100000000000000000000000000000000000000
IE: Unknown: 4A0E14000A002C01C800140005001900
IE: Unknown: 7F0101
IE: Unknown: DD090010180201F02C0000
IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

dmesg | grep iwl:
[ 1.654389] iwlwifi 0000:01:00.0: can't disable ASPM; OS doesn't have ASPM control
[ 1.654439] iwlwifi 0000:01:00.0: irq 60 for MSI/MSI-X
[ 1.678889] iwlwifi 0000:01:00.0: loaded firmware version 22.1.7.0 op_mode iwlmvm
[ 1.698158] iwlwifi 0000:01:00.0: Detected Intel(R) Dual Band Wireless N 7260, REV=0x144
[ 1.698210] iwlwifi 0000:01:00.0: L1 Disabled; Enabling L0S
[ 1.698354] iwlwifi 0000:01:00.0: L1 Disabled; Enabling L0S
[ 1.906933] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[ 3.662876] iwlwifi 0000:01:00.0: L1 Disabled; Enabling L0S
[ 3.663020] iwlwifi 0000:01:00.0: L1 Disabled; Enabling L0S

Thx so far, hope this helps

For now i did not do anything with the other point brought up with regard to the [COLOR=#000000]"linux-firmware"  brought up by chilli555. This may be the next step?[/COLOR]

cheers kwakkie

---

### Post by praseodym on 2014-02-09
Change the encryption mode to pure WPA2-AES (CCMP) and the ESSID to sth. without blank

---

### Post by Kwakkiezalf on 2014-02-09
Praseodym,

Thx for your fast reply. No idea where and how to do that. Could you helpme out here? "WPA2 personal / WPA2 enterprise" i can find in the connection settings , but no specific"pure" or CCMP there.
Where can i find the ESSID ?

---

### Post by praseodym on 2014-02-09
You need to enter the router settings for all of that. Check the manual. Enter the IP address of your router into the URL-line of your browser. Login/PW are normally sticked on the router

---

### Post by Kwakkiezalf on 2014-02-11
Praseodym,

Changed the settings in the router...no effect. I watched the netgraph in game, while loading the system at a very low level, and than lag pikes occur. Looks like some reoccurring thing.

No idea

Cheers kwakkie

---

### Post by Kwakkiezalf on 2014-02-18
Chilli555 & Praseodym,

I also chekedthe file Chilli made reference to and I already have the newer one installed (iwlwifi-7260-7.ucode, 683236 bytes). I'm lost here and have no clue to why my network keeps lagging. The same router I have no issue with a different computer. So it must be related to my hardware/software config of my pc Acer S7 392.

Anyone any more hints/tricks?

cheers kwakkie

---

### Post by chili555 on 2014-02-18
@praseodym--

You might try kernel 3.13 and the even newer firmware:  [http://ubuntuforums.org/showthread.php?t=2178873&p=12932157#post12932157](http://ubuntuforums.org/showthread.php?t=2178873&p=12932157#post12932157)

---

### Post by Kwakkiezalf on 2014-03-12
Solved,

Issue was related to the beacon pulse rate and package size of router

Thx for the help all!


kwakkie

---

