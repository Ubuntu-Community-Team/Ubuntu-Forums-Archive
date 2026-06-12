---
title: "WIFI Adapter not working"
date: 2016-07-21
forum: Networking &amp; Wireless
---

### Post by doniv96 on 2016-07-21
Hi guys,
I'm new to ubuntu,I just installed MATE 16.04.I have issues with my wireless adapters.
Firstly I tried to get my NETGEAR WNA1000M to work and tried a lot of solutions posted throughout most of the forums,
It did not work and then I tried my friend's adapter,MEDIATEK 802.11n which is supposed to be supported but is also not working.
The connections always display Realtek or Mediatek based on the adapter but looks like it is disabled,I haveb een trying for a whole day to get a fix.
I'm afraid I messed up the etc folder with the tons of solutions I tried out,The information for the NETGEAR  adapter is
RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911 I.
Thanks in advance,

---

### Post by chili555 on 2016-07-21
>  looks like it is disabledLet's take a look. Please run and post:```
lsmod | grep -e wmi -e acpi
rfkill list all
```Next, let's concentrate on one and only one device. Insert it and run:```
lsusb
```Post the result.

---

### Post by doniv96 on 2016-07-21
```
invictus@invictus-PORTEGE-M800:~$ lsmod | grep -e wmi -e acpi
toshiba_acpi           40960  0
sparse_keymap          16384  1 toshiba_acpi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd                    81920  16 snd_hwdep,snd_timer,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
pata_acpi              16384  0
wmi                    20480  1 toshiba_acpi
video                  40960  2 i915,toshiba_acpi
invictus@invictus-PORTEGE-M800:~$ rfkill list all
0: Toshiba Bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
10: phy9: Wireless LAN
    Soft blocked: no
    Hard blocked: no
invictus@invictus-PORTEGE-M800:~\
```


This is what I get after running the first 2 codes mentioned.(NETGEAR adapter plugged in)

---

### Post by doniv96 on 2016-07-21
```
invictus@invictus-PORTEGE-M800:~$ lsusb
Bus 002 Device 004: ID 04f2:b008 Chicony Electronics Co., Ltd USB 2.0 Camera
Bus 002 Device 008: ID 0846:9041 NetGear, Inc. WNA1000M 802.11bgn [Realtek RTL8188CUS]
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:0024 Microsoft Corp. Trackball Explorer
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
invictus@invictus-PORTEGE-M800:~$ 

```

Result after running the lsusb code.
Thanks for helping out :)

---

### Post by chili555 on 2016-07-21
May I also see:```
lspci -nnk | grep 0280 -A2
```Those Toshibas are a bit tricky!

By the way, installing another *older* driver isn't going to solve this:> 1: phy0: Wireless LAN
Soft blocked: no
[COLOR="#FF0000"]Hard blocked: yes[/COLOR]I suspect you've pressed the wireless key combination, Fn+F12 or some such, about a thousand times with no change at all.

---

### Post by doniv96 on 2016-07-21
The wifi device(hardware inside the computer) was not working before,I had Windows 7 installed and started using the netgear device.
The repair centre said that the physical switch was damaged.Hence the netgear, which has been working well for 2 years.
I should have mentioned this before,sorry.
I ran the command,This is what I get

```

08:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
    Subsystem: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:1040]
    Kernel driver in use: iwl3945
invictus@invictus-PORTEGE-M800:~$

```

---

### Post by wildmanne39 on 2016-07-21
Please use code tags when posting code.
Thanks

---

### Post by chili555 on 2016-07-21
> **doniv96 said:**
> The wifi device(hardware inside the computer) was not working before,I had Windows 7 installed and started using the netgear device.
The repair centre said that the physical switch was damaged.Hence the netgear, which has been working well for 2 years.
I should have mentioned this before,sorry.
I ran the command,This is what I get


08:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
    Subsystem: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:1040]
    Kernel driver in use: iwl3945
invictus@invictus-PORTEGE-M800:~$Let's try blacklisting the internal and see if that helps coax the USB to life:```
sudo -i
echo "blacklist iwl3945"  >>  /etc/modprobe.d/blacklist.conf
exit
```Reboot and show us:```
rfkill list all
lsmod | grep rtl
iwconfig
```Thanks.

---

### Post by doniv96 on 2016-07-21
Here is what I got
```

invictus@invictus-PORTEGE-M800:~$ rfkill list all
0: Toshiba Bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
invictus@invictus-PORTEGE-M800:~$ lsmod | grep rtl
rtl8xxxu               73728  0
rtl8192cu              69632  0
rtl_usb                20480  1 rtl8192cu
rtl8192c_common        53248  1 rtl8192cu
rtlwifi                77824  3 rtl_usb,rtl8192c_common,rtl8192cu
mac80211              737280  4 rtl8xxxu,rtl_usb,rtlwifi,rtl8192cu
cfg80211              565248  2 mac80211,rtlwifi
invictus@invictus-PORTEGE-M800:~$ iwconfig
enp7s0    no wireless extensions.

lo        no wireless extensions.

wlx04a1516bf8c5  IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
invictus@invictus-PORTEGE-M800:~$ 

```

---

### Post by chili555 on 2016-07-21
Looks pretty good! Do networks appear in Network Manager? Does it scan?```
sudo iwlist scan
```Any interesting clues in the log?```
dmesg | grep -e rtl -e wlx
```

---

### Post by doniv96 on 2016-07-21
Here it is,
```

invictus@invictus-PORTEGE-M800:~$ sudo iwlist scan
[sudo] password for invictus: 
enp7s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlx04a1516bf8c5  Scan completed :
          Cell 01 - Address: F4:F2:6D:46:94:4E
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption key:on
                    ESSID:"Veritas"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000015dd8f100b
                    Extra: Last beacon: 0ms ago
                    IE: Unknown: 000756657269746173
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030105
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6F111BFF00000000000000000000000100000000000000000000
                    IE: Unknown: 3D16050D0000000000000000000000000000000000000000
                    IE: Unknown: 7F080000000000000040
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DDA90050F204104A0001101044000102103B00010310470010000102030405060708090A0B0C0D0E0F1021000754502D4C494E4B10230014544C2D57523734304E2F544C2D57523734314E4410240003362E3010420003312E301054000800060050F20400011011001E576972656C65737320526F757465722057523734304E2F57523734314E44100800020086103C000101104900140024E26002000101600000020001600100020001
          Cell 02 - Address: C4:01:7C:67:24:A8
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:off
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000079745063c
                    Extra: Last beacon: 27892ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD180050F20201018F0003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C330C001BFFFF000000000000000000001000000000000000000000
                    IE: Unknown: 2D1A0C001BFFFF000000000000000000001000000000000000000000
                    IE: Unknown: DD1A00904C3406000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000000000000000000000000000000000000000000
                    IE: Unknown: 7F0400000000
                    IE: Unknown: DD080013920100018500
          Cell 03 - Address: 48:EE:0C:2B:95:68
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"LiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002c74f37187
                    Extra: Last beacon: 27380ms ago
                    IE: Unknown: 00044C694669
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6E181FFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B000000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A00B400C800140005001900
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336E181FFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B000000000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020160
                    IE: Unknown: DD1D0050F204104A0001101044000102103C0001031049000600372A000120
          Cell 04 - Address: 14:82:5B:E3:EC:0C
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"xperio_E3EC0D"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000d19275cb8
                    Extra: Last beacon: 0ms ago
                    IE: Unknown: 000D78706572696F5F453345433044
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC191FFFFF000000000000000000000000000000001804810000
                    IE: Unknown: 3D1601000000000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33AC191FFFFF000000000000000000000000000000001804810000
                    IE: Unknown: DD1A00904C3401000000000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020160

invictus@invictus-PORTEGE-M800:~$ dmesg | grep -e rtl -e wlx
[   17.892355] rtl8192cu: Chip version 0x10
[   17.974213] rtl8192cu: MAC address: 04:a1:51:6b:f8:c5
[   17.974220] rtl8192cu: Board Type 0
[   17.974458] rtl_usb: rx_max_size 15360, rx_urb_num 8, in_ep 1
[   17.974505] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[   18.156460] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   18.156812] usbcore: registered new interface driver rtl8192cu
[   18.235656] usbcore: registered new interface driver rtl8xxxu
[   18.239012] rtl8192cu 2-1:1.0 wlx04a1516bf8c5: renamed from wlan0
[   29.219003] IPv6: ADDRCONF(NETDEV_UP): wlx04a1516bf8c5: link is not ready
[   29.220965] rtl8192cu: MAC auto ON okay!
[   29.253711] rtl8192cu: Tx queue select: 0x05
[   29.657752] IPv6: ADDRCONF(NETDEV_UP): wlx04a1516bf8c5: link is not ready
[   30.774741] IPv6: ADDRCONF(NETDEV_UP): wlx04a1516bf8c5: link is not ready
invictus@invictus-PORTEGE-M800:~$ 

```

---

### Post by doniv96 on 2016-07-21
The device looks like it is working,the blue light has been turned on and now I am connected to the network,
However I tried reconnecting it to another one and then back again,now it cannot seem to connect.

---

### Post by chili555 on 2016-07-21
I suggest you reboot, connect and then, in a terminal:```
sudo add-apt-repository ppa:hanipouspilot/rtlwifi
sudo apt-get update
sudo apt-get install rtl8192cu-dkms
```Reboot once more and let us know if it is working as expected.

---

### Post by doniv96 on 2016-07-22
Looks like there are some problems,
```

invictus@invictus-PORTEGE-M800:~$ sudo add-apt-repository ppa:hanipouspilot/rtlwifi
[sudo] password for invictus: 
 This is ppa for Realtek drivers from Larry Finger's github.

rtl8192eu is packaged from the Realtek site with some compat patches.
 More info: https://launchpad.net/~hanipouspilot/+archive/ubuntu/rtlwifi
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmp9ztbkbu5/secring.gpg' created
gpg: keyring `/tmp/tmp9ztbkbu5/pubring.gpg' created
gpg: requesting key 2F22E44A from hkp server keyserver.ubuntu.com
gpgkeys: key A31B1FE775FD7643D79B75107036069A2F22E44A can't be retrieved
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
gpg: keyserver communications error: keyserver helper general error
gpg: keyserver communications error: unknown pubkey algorithm
gpg: keyserver receive failed: unknown pubkey algorithm
invictus@invictus-PORTEGE-M800:~$ sudo add-apt-repository ppa:hanipouspilot/rtlwifi
 This is ppa for Realtek drivers from Larry Finger's github.

rtl8192eu is packaged from the Realtek site with some compat patches.
 More info: https://launchpad.net/~hanipouspilot/+archive/ubuntu/rtlwifi
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmp9qg51vp4/secring.gpg' created
gpg: keyring `/tmp/tmp9qg51vp4/pubring.gpg' created
gpg: requesting key 2F22E44A from hkp server keyserver.ubuntu.com
gpgkeys: key A31B1FE775FD7643D79B75107036069A2F22E44A can't be retrieved
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
gpg: keyserver communications error: keyserver helper general error
gpg: keyserver communications error: unknown pubkey algorithm
gpg: keyserver receive failed: unknown pubkey algorithm
invictus@invictus-PORTEGE-M800:~$ sudo apt-get update
Hit:1 http://in.archive.ubuntu.com/ubuntu xenial InRelease                     
Get:2 http://security.ubuntu.com/ubuntu xenial-security InRelease [94.5 kB]    
Get:3 http://ppa.launchpad.net/hanipouspilot/rtlwifi/ubuntu xenial InRelease [18.1 kB]
Hit:4 http://in.archive.ubuntu.com/ubuntu xenial-updates InRelease             
Hit:5 http://in.archive.ubuntu.com/ubuntu xenial-backports InRelease           
Ign:3 http://ppa.launchpad.net/hanipouspilot/rtlwifi/ubuntu xenial InRelease   
Hit:6 http://ppa.launchpad.net/ubuntu-mate-dev/welcome/ubuntu xenial InRelease 
Get:7 http://ppa.launchpad.net/hanipouspilot/rtlwifi/ubuntu xenial/main amd64 Packages [624 B]
Get:8 http://ppa.launchpad.net/hanipouspilot/rtlwifi/ubuntu xenial/main i386 Packages [624 B]
Get:9 http://ppa.launchpad.net/hanipouspilot/rtlwifi/ubuntu xenial/main Translation-en [216 B]
Fetched 114 kB in 2s (43.4 kB/s)       
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net/hanipouspilot/rtlwifi/ubuntu xenial InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7036069A2F22E44A
W: The repository 'http://ppa.launchpad.net/hanipouspilot/rtlwifi/ubuntu xenial InRelease' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
invictus@invictus-PORTEGE-M800:~$ sudo apt-get install rtl8192cu-dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package rtl8192cu-dkms
invictus@invictus-PORTEGE-M800:~$ 

```

---

### Post by doniv96 on 2016-07-22
Update
If I replug the device,erase the settings for one network and try to connect to another network,it will not connect immediately.However if i replug it it will connect without a glitch.And the MediaTek device is working flawlessly.I can connect and reconnect to networks without plugging it in and out multiple times.
Thanks a lot for the continuous help chili555.

---

### Post by Pilot6 on 2016-07-22
Regarding problem with the key of my ppa:hanipouspilot/rtlwifi

I lost the password for my pgp key and submitted a new one. I guess you need to remove the old key and install a new one.

---

### Post by Pilot6 on 2016-07-22
I just checked that

sudo add-apt-repository ppa:hanipouspilot/rtlwifi

works

---

### Post by chili555 on 2016-07-22
Please try the sequence again, @doniv96.

---

### Post by doniv96 on 2016-07-22
Again some errors occurred,
```
invictus@invictus-PORTEGE-M800:~$ sudo add-apt-repository ppa:hanipouspilot/rtlwifi[sudo] password for invictus: 
Sorry, try again.
[sudo] password for invictus: 
 This is ppa for Realtek drivers from Larry Finger's github.


rtl8192eu is packaged from the Realtek site with some compat patches.
 More info: https://launchpad.net/~hanipouspilot/+archive/ubuntu/rtlwifi
Press [ENTER] to continue or ctrl-c to cancel adding it


gpg: keyring `/tmp/tmpk4fyeoz3/secring.gpg' created
gpg: keyring `/tmp/tmpk4fyeoz3/pubring.gpg' created
gpg: requesting key 2F22E44A from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpk4fyeoz3/trustdb.gpg: trustdb created
gpg: key 2F22E44A: public key "Launchpad PPA for Pilot6" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
invictus@invictus-PORTEGE-M800:~$ sudo apt-get update
Ign:1 http://dl.google.com/linux/chrome/deb stable InRelease                   
Hit:2 http://archive.canonical.com/ubuntu xenial InRelease                     
Hit:3 http://dl.google.com/linux/chrome/deb stable Release                     
Hit:4 http://in.archive.ubuntu.com/ubuntu xenial InRelease                     
Get:5 http://security.ubuntu.com/ubuntu xenial-security InRelease [94.5 kB]    
Hit:6 http://ppa.launchpad.net/hanipouspilot/rtlwifi/ubuntu xenial InRelease   
Get:7 http://in.archive.ubuntu.com/ubuntu xenial-updates InRelease [95.7 kB]   
Hit:9 http://ppa.launchpad.net/me-davidsansome/clementine/ubuntu xenial InRelease
Hit:10 http://ppa.launchpad.net/ubuntu-mate-dev/welcome/ubuntu xenial InRelease
Hit:11 http://in.archive.ubuntu.com/ubuntu xenial-backports InRelease          
Fetched 190 kB in 6s (30.6 kB/s)                                               
Reading package lists... Done
invictus@invictus-PORTEGE-M800:~$ sudo apt-get install rtl8192cu-dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package rtl8192cu-dkms
invictus@invictus-PORTEGE-M800:~$ 

```

---

### Post by Pilot6 on 2016-07-22
I see that the issue with the key has been fixed. Now the problem is that I never amde a package rtl8192cu for Xenial.
Try to install this one

```
wget https://launchpad.net/~hanipouspilot/+archive/ubuntu/rtlwifi/+files/rtl8192cu-dkms_0.2_all.deb
sudo dpkg -i  rtl8192cu-dkms_0.2_all.deb
```

---

### Post by doniv96 on 2016-07-23
Here is what i got,
```

invictus@invictus-PORTEGE-M800:~$ sudo dpkg -i  rtl8192cu-dkms_0.2_all.deb
[sudo] password for invictus: 
Selecting previously unselected package rtl8192cu-dkms.
(Reading database ... 240052 files and directories currently installed.)
Preparing to unpack rtl8192cu-dkms_0.2_all.deb ...
Unpacking rtl8192cu-dkms (0.2) ...
dpkg: dependency problems prevent configuration of rtl8192cu-dkms:
 rtl8192cu-dkms depends on dkms (>= 1.95); however:
  Package dkms is not installed.


dpkg: error processing package rtl8192cu-dkms (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 rtl8192cu-dkms
invictus@invictus-PORTEGE-M800:~$ sudo dpkg -i  rtl8192cu-dkms_0.2_all.deb(Reading database ... 240229 files and directories currently installed.)
Preparing to unpack rtl8192cu-dkms_0.2_all.deb ...
Unpacking rtl8192cu-dkms (0.2) over (0.2) ...
dpkg: dependency problems prevent configuration of rtl8192cu-dkms:
 rtl8192cu-dkms depends on dkms (>= 1.95); however:
  Package dkms is not installed.


dpkg: error processing package rtl8192cu-dkms (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 rtl8192cu-dkms
invictus@invictus-PORTEGE-M800:~$ 

```

---

### Post by Pilot6 on 2016-07-23
If you are connected to internet, run

sudo apt-get install -f

and the issue will be fixed. The command will install dkms and the rtl8192cu-dkms package.

---

### Post by doniv96 on 2016-08-03
Thanks guys,
Everything is working fine now.

---

