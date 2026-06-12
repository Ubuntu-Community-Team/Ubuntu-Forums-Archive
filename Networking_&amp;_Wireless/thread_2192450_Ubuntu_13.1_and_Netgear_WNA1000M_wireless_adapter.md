---
title: "Ubuntu 13.1 and Netgear WNA1000M wireless adapter"
date: 2013-12-07
forum: Networking &amp; Wireless
---

### Post by btubolino on 2013-12-07
Hello,

Im a new Linux convert and so far very impressed, I downloaded 13.1 and erased Windows. I am having trouble with wireless though. I read that Netgear WNA1000M has out of the box plug and play so I purchased and it worked immediately. However after several minutes of flawless connection it would stop transmitting however not disconnect. I would unplug the adapter and then plug it back it to get another 5 to 10 minutes of activity. I have been doing this for the past couple of days while searching for a remedy. Obviously this isn't a sustainable method of wireless connection.

I have looked for many solutions to this but have not come across anything that works. This version of Ubuntu has the carl1790 firmware so there must be another issue. 

I am new to Linux and not too knowledgeable about code but I learn quickly.

Thanks in advance for any help.

---

### Post by praseodym on 2013-12-08
Please open a terminal (CTRL+ALT+T) and show the outputs of these commands:
```

lsusb
lsmod
cat /etc/resolv.conf
ifconfig -a
iwconfig
sudo iwlist scan
```

---

### Post by btubolino on 2013-12-08
Here is what I got:

dci@DCI:~$ lsusb
Bus 001 Device 002: ID 0846:9041 NetGear, Inc. WNA1000M802.11bgn [Realtek RTL8188CUS]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 roothub
Bus 005 Device 002: ID 045e:0745 Microsoft Corp. NanoTransceiver v1.0 for Bluetooth
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 roothub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 roothub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 roothub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 roothub
dci@DCI:~$ lsmod
Module                 Size  Used by
joydev                17377  0
hid_generic           12548  0
usbhid                53014  0
hid                  101512  2 hid_generic,usbhid
rfcomm                69070  0
bnep                  19564  2
bluetooth            371874  10 bnep,rfcomm
arc4                  12608  2
rtl8192cu             67723  0
rtl_usb               18448  1 rtl8192cu
rtlwifi               63229  2 rtl_usb,rtl8192cu
rtl8192c_common       48877  1 rtl8192cu
mac80211             596969  3rtl_usb,rtlwifi,rtl8192cu
cfg80211             479757  2 mac80211,rtlwifi
ppdev                 17671  0
dcdbas                14847  0
microcode             23518  0
snd_intel8x0          38104  2
snd_ac97_codec       130236  1 snd_intel8x0
ac97_bus              12730  1 snd_ac97_codec
snd_pcm              102033  2snd_ac97_codec,snd_intel8x0
snd_page_alloc        18710  2 snd_intel8x0,snd_pcm
snd_seq_midi          13324  0
snd_seq_midi_event    14899  1 snd_seq_midi
snd_rawmidi           30095  1 snd_seq_midi
snd_seq               61560  2snd_seq_midi_event,snd_seq_midi
snd_seq_device        14497  3snd_seq,snd_rawmidi,snd_seq_midi
snd_timer             29433  2 snd_pcm,snd_seq
psmouse                97626  0
serio_raw             13413  0
i915                 655752  3
video                 19318  1 i915
snd                   69141  12snd_ac97_codec,snd_intel8x0,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_seq_device,snd_seq_midi
lpc_ich               21080  0
drm_kms_helper        52651  1 i915
drm                  296739  4 i915,drm_kms_helper
soundcore             12680  1 snd
i2c_algo_bit          13413  1 i915
parport_pc            32701  1
mac_hid               13205  0
lp                    17759  0
parport               42299  3 lp,ppdev,parport_pc
tg3                  162230  0
ptp                   18580  1 tg3
pps_core              19027  1 ptp
floppy                69370  0

---

### Post by btubolino on 2013-12-08
dci@DCI:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generatedby resolvconf(8)
#     DO NOT EDIT THISFILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
dci@DCI:~$ ifconfig -a
eth0      Linkencap:Ethernet  HWaddr00:12:3f:c6:8a:d1  
          UP BROADCASTMULTICAST  MTU:1500  Metric:1
          RX packets:0errors:0 dropped:0 overruns:0 frame:0
          TX packets:0errors:0 dropped:0 overruns:0 carrier:0
          collisions:0txqueuelen:1000
          RX bytes:0(0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16
 
lo        Linkencap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr:::1/128 Scope:Host
          UP LOOPBACKRUNNING  MTU:65536  Metric:1
          RX packets:63errors:0 dropped:0 overruns:0 frame:0
          TX packets:63errors:0 dropped:0 overruns:0 carrier:0
          collisions:0txqueuelen:0
          RX bytes:6640(6.6 KB)  TX bytes:6640 (6.6 KB)
 
wlan0     Linkencap:Ethernet  HWaddr28:c6:8e:f4:3e:21  
          inetaddr:192.168.1.12 Bcast:192.168.1.255 Mask:255.255.255.0
          inet6 addr:fe80::2ac6:8eff:fef4:3e21/64 Scope:Link
          UP BROADCASTRUNNING MULTICAST  MTU:1500  Metric:1
          RXpackets:454 errors:0 dropped:0 overruns:0 frame:0
          TX packets:95errors:0 dropped:0 overruns:0 carrier:0
          collisions:0txqueuelen:1000
          RXbytes:29972 (29.9 KB)  TX bytes:14540(14.5 KB)
 
dci@DCI:~$ iwconfig
eth0      no wirelessextensions.
 
lo        no wirelessextensions.
 
wlan0     IEEE802.11bgn ESSID:"NETGEAR16"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: 84:1B:5E:EC:D7:D6   
          Bit Rate=72.2Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7  RTS thr=2347 B   Fragment thr:off
          PowerManagement:off
          LinkQuality=69/70  Signal level=-41 dBm  
          Rx invalidnwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessiveretries:0  Invalid misc:3   Missed beacon:0

---

### Post by btubolino on 2013-12-08
dci@DCI:~$ sudo iwlist scan
[sudo] password for dci:
Sorry, try again.
[sudo] password for dci:
eth0      Interfacedoesn't support scanning.
 
lo        Interfacedoesn't support scanning.
 
wlan0     Scancompleted :
          Cell 01 -Address: 84:1B:5E:EC:D7:D6
                   Channel:8
                   Frequency:2.447 GHz (Channel 8)
                   Quality=69/70  Signal level=-41dBm  
                   Encryption key:on
                   ESSID:"NETGEAR16"
                    BitRates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                             24 Mb/s; 36 Mb/s; 54 Mb/s
                    BitRates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                   Mode:Master
                    Extra:tsf=000002463aaff61b
                   Extra: Last beacon: 88ms ago
                    IE:Unknown: 00094E4554474541523136
                    IE:Unknown: 010882840B162430486C
                    IE:Unknown: 030108
                    IE: Unknown: 2A0104
                    IE:Unknown: 2F0104
                    IE:IEEE 802.11i/WPA2 Version 1
                       Group Cipher : CCMP
                       Pairwise Ciphers (1) : CCMP
                       Authentication Suites (1) : PSK
                    IE:Unknown: 32040C121860
                    IE:Unknown: 2D1AFC181FFFFF000000000000000000000000000000000000000000
                    IE:Unknown: 3D1608001700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE:Unknown: 7F0101
                    IE:Unknown:DD7F0050F204104A0001101044000102103B00010310470010CF7F5FFBF003DFFDF0EBF9396F2A551B1021000D4E4554474541522C20496E632E1023000A574E44523334303076321024000A574E44523334303076321042000230311054000800060050F20400011011000A574E4452333430307632100800020004103C000103
                    IE:Unknown: DD090010180207F0040000
                    IE:Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 -Address: 00:26:50:76:5A:29
                   Channel:1
                   Frequency:2.412 GHz (Channel 1)
                   Quality=70/70  Signal level=-40dBm  
                   Encryption key:on
                   ESSID:"2WIRE893"
                    BitRates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                             11 Mb/s; 12 Mb/s; 18 Mb/s
                    BitRates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                   Mode:Master
                   Extra:tsf=0000002ad86c1e49
                   Extra: Last beacon: 1700ms ago
                    IE:Unknown: 00083257495245383933
                    IE:Unknown: 010882848B0C12961824
                    IE:Unknown: 030101
                    IE:Unknown: 0706555320010B1B
                    IE:WPA Version 1
                       Group Cipher : TKIP
                       Pairwise Ciphers (1) : TKIP
                       Authentication Suites (1) : PSK
                    IE:Unknown: 2A0100
                    IE: Unknown: 32043048606C
          Cell 03 -Address: 74:9D:DC:87:B4:31
                   Channel:6
                   Frequency:2.437 GHz (Channel 6)
                   Quality=70/70  Signal level=-40dBm  
                   Encryption key:on
                   ESSID:"2WIRE999"
                    BitRates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                             11 Mb/s; 12 Mb/s; 18 Mb/s
                    BitRates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                   Mode:Master
                   Extra:tsf=000006e5d16d6db7
                   Extra: Last beacon: 148ms ago
                    IE:Unknown: 00083257495245393939
                    IE:Unknown: 010882848B0C12961824
                    IE:Unknown: 030106
                    IE:Unknown: 0706555320010B1B
                    IE:IEEE 802.11i/WPA2 Version 1
                       Group Cipher : TKIP
                       Pairwise Ciphers (2) : CCMP TKIP
                       Authentication Suites (1) : PSK
                    IE:WPA Version 1
                       Group Cipher : TKIP
                       Pairwise Ciphers (2) : CCMP TKIP
                       Authentication Suites (1) : PSK
                    IE:Unknown: 2A0100
                    IE:Unknown: 32043048606C
          Cell 04 -Address: 86:1B:5E:EC:D7:D7
                   Channel:8
                   Frequency:2.447 GHz (Channel 8)
                   Quality=69/70  Signal level=-41dBm  
                   Encryption key:on
                    ESSID:"NETGEAR-Guest"
                    BitRates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                             24 Mb/s; 36 Mb/s; 54 Mb/s
                    BitRates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                   Mode:Master
                   Extra:tsf=000002463ab002b6
                   Extra: Last beacon: 84ms ago
                    IE:Unknown: 000D4E4554474541522D4775657374
                    IE:Unknown: 010882840B162430486C
                    IE: Unknown: 030108
                    IE:Unknown: 2A0104
                    IE:Unknown: 2F0104
                    IE:IEEE 802.11i/WPA2 Version 1
                       Group Cipher : CCMP
                       Pairwise Ciphers (1) : CCMP
                       Authentication Suites (1) : PSK
                    IE:Unknown: 32040C121860
                    IE:Unknown: 2D1AFC181FFFFF000000000000000000000000000000000000000000
                    IE:Unknown: 3D1608001700000000000000000000000000000000000000
                    IE:Unknown: 4A0E14000A002C01C800140005001900
                    IE:Unknown: 7F0101
                    IE:Unknown: DD090010180207F0040000
                    IE:Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 05 -Address: B8:E6:25:2C:2B:D9
                   Channel:3
                   Frequency:2.422 GHz (Channel 3)
                    Quality=70/70  Signal level=10 dBm  
                   Encryption key:on
                   ESSID:"2WIRE336"
                    BitRates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                             11 Mb/s; 12 Mb/s; 18 Mb/s
                    BitRates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                   Mode:Master
                   Extra:tsf=0000000b53cd3729
                   Extra: Last beacon: 1376ms ago
                    IE:Unknown: 00083257495245333336
                    IE:Unknown: 010882848B0C12961824
                    IE:Unknown: 030103
                    IE: Unknown: 0706555320010B1B
                    IE:IEEE 802.11i/WPA2 Version 1
                       Group Cipher : TKIP
                       Pairwise Ciphers (2) : CCMP TKIP
                       Authentication Suites (1) : PSK
                    IE:WPA Version 1
                       Group Cipher : TKIP
                       Pairwise Ciphers (2) : CCMP TKIP
                       Authentication Suites (1) : PSK
                    IE:Unknown: 2A0100
                    IE: Unknown: 32043048606C

---

### Post by praseodym on 2013-12-08
Update/change the driver via:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git
git clone https://github.com/pvaret/rtl8192cu-fixes.git
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.7
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf   
```
Reboot.

---

### Post by btubolino on 2013-12-08
Thanks,

Here is what I get. I rebooted but still spotty connection. 

dci@DCI:~$ sudo apt-get install --reinstalllinux-headers-$(uname -r) linux-headers-generic build-essential dkms git
Reading package lists... Done
Building dependency tree      
Reading state information... Done
0 upgraded, 0 newly installed, 5 reinstalled, 0 to remove and144 not upgraded.
Need to get 0 B/9,182 kB of archives.
After this operation, 0 B of additional disk space will beused.
(Reading database ... 194455 files and directories currentlyinstalled.)
Preparing to replace build-essential 11.6ubuntu5 (using.../build-essential_11.6ubuntu5_amd64.deb) ...
Unpacking replacement build-essential ...
Preparing to replace dkms 2.2.0.3-1.1ubuntu4 (using.../dkms_2.2.0.3-1.1ubuntu4_all.deb) ...
Unpacking replacement dkms ...
Preparing to replace git 1:1.8.3.2-1 (using.../git_1%3a1.8.3.2-1_amd64.deb) ...
Unpacking replacement git ...
Preparing to replace linux-headers-3.11.0-14-generic3.11.0-14.21 (using .../linux-headers-3.11.0-14-generic_3.11.0-14.21_amd64.deb)...
Unpacking replacement linux-headers-3.11.0-14-generic ...
Preparing to replace linux-headers-generic 3.11.0.14.15(using .../linux-headers-generic_3.11.0.14.15_amd64.deb) ...
Unpacking replacement linux-headers-generic ...
Processing triggers for man-db ...
Setting up build-essential (11.6ubuntu5) ...
Setting up dkms (2.2.0.3-1.1ubuntu4) ...
Setting up git (1:1.8.3.2-1) ...
Setting up linux-headers-3.11.0-14-generic (3.11.0-14.21) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms3.11.0-14-generic /boot/vmlinuz-3.11.0-14-generic
Setting up linux-headers-generic (3.11.0.14.15) ...

---

### Post by praseodym on 2013-12-08
It's ok, go on...

---

### Post by btubolino on 2013-12-08
it seems to just stall there. Is there a step I missed?

---

### Post by praseodym on 2013-12-08
Continue with the "git" line

---

### Post by btubolino on 2013-12-08
Gotcha, each code needs to run seperate... I entered each line and rebooted. The wireless doesn't work at all now. The light on the adapter is off now too.

---

### Post by btubolino on 2013-12-08
OK, I didnt reboot with the netgear in the usb drive. Just rebooted with it in and now it seems to be working perfectly. Thanks so much.

---

