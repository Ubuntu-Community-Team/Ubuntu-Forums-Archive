---
title: "Need help with 8192cu realtek driver, really high ping"
date: 2017-02-17
forum: Networking &amp; Wireless
---

### Post by tuman on 2017-02-17
Hi, i'm have problems with network stable work with my USB dongle.

lsusbBus 002 Device 002: ID 0b05:17ab ASUSTek Computer, Inc. USB-N13 802.11n Network Adapter (rev. B1) [Realtek RTL8192CU]

```
ping issues (on my phone or laptop these problems doesn't appear (avg ping):10 ms)
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=29.1 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=89.2 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=5798 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=4798 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=64 time=3798 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=64 time=2798 ms
64 bytes from 192.168.1.1: icmp_seq=7 ttl=64 time=1802 ms
64 bytes from 192.168.1.1: icmp_seq=8 ttl=64 time=802 ms
64 bytes from 192.168.1.1: icmp_seq=9 ttl=64 time=6.13 ms
64 bytes from 192.168.1.1: icmp_seq=10 ttl=64 time=8.28 ms
64 bytes from 192.168.1.1: icmp_seq=11 ttl=64 time=5.23 ms
64 bytes from 192.168.1.1: icmp_seq=12 ttl=64 time=5.45 ms
64 bytes from 192.168.1.1: icmp_seq=13 ttl=64 time=10.7 ms
64 bytes from 192.168.1.1: icmp_seq=14 ttl=64 time=1431 ms
64 bytes from 192.168.1.1: icmp_seq=15 ttl=64 time=424 ms
64 bytes from 192.168.1.1: icmp_seq=16 ttl=64 time=159 ms



I tried to install 8192cu-fixes from github: [COLOR=#006621][FONT=arial]https://[/FONT][/COLOR][B]github.com/pvaret/rtl[B]8192cu-fixes
[/B][/B]but, maybe i install other version of this driver, maybe something else, but:
tuman@montana:~$ dkms status | grep 8192cu
8192cu, 1.10, 4.2.0-27-generic, x86_64: installed (WARNING! Diff between built and installed module!)
What exactly does means that warning and how i can truly reinstall this module, when i install it, system writes that current version isn't bigger than installed, in /lib/modules/4.2.0-27-generic/kernel/drivers/net/wireless
8192cu was created at 2 may of 2016, but i build this fixes only today.
DKMS programm is required in arguments version of module, now its 1.10, but how i can to retrieve this information from .ko file?
I want to delete this version of 8192cu.ko and update it by downloaded srcs from github, but how i can understand this impossible with my skills). Plz answer how to rebuild modules in this type of dkms status msg.

Also i retrieve dmesg log
tuman@montana:~$ dmesg | grep 8192cu
[    7.161766] 8192cu: module verification failed: signature and/or required key missing - tainting kernel
[    7.317496] usbcore: registered new interface driver rtl8192cu
```
So, 1 of my purpose is to rebuild module for passing verification.
Also i dont fully understand what does second line of dmesg means: does rtl8192cu in this line corresponds to my 8192cu?
I blacklists rtl8192cu in /etc/modprobe.d directory, so how it can register?

Plz help me get the message of this questions and solve problems with high ping

---

### Post by wildmanne39 on 2017-02-17
You need to go into the bios and disable secure boot then if you installed that driver correctly it should load when you reboot, I use that driver myself and it works perfectly with the new driver you are trying to install.

You can install the driver after turning off secure boot if it did not install correctly by copying and pasting one line and a time into the terminal.
```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git 
git clone https://github.com/pvaret/rtl8192cu-fixes.git
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.10
```

---

### Post by wildmanne39 on 2017-02-17
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by tuman on 2017-02-17
> **wildmanne39 said:**
> You need to go into the bios and disable secure boot then if you installed that driver correctly it should load when you reboot, I use that driver myself and it works perfectly with the new driver you are trying to install.

You can install the driver after turning off secure boot if it did not install correctly by copying and pasting one line and a time into the terminal.
```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git 
git clone https://github.com/pvaret/rtl8192cu-fixes.git
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.10
```

Okay, but what can i do if i haven't secure boot in my bios settings? also my motherboard's bios isn't UEFI.
I log some strange behaviour:

```

[    7.867130] 8192cu: module verification failed: signature and/or required key missing - tainting kernel
[    8.055164] usbcore: registered new interface driver rtl8192cu
[  996.614256] usbcore: deregistering interface driver rtl8192cu
[ 1074.021982] usbcore: registered new interface driver rtl8192cu
[ 7507.484555] usbcore: deregistering interface driver rtl8192cu
[ 7525.972692] usbcore: registered new interface driver rtl8192cu
[ 7550.274857] usbcore: deregistering interface driver rtl8192cu
[ 7578.877807] usbcore: registered new interface driver rtl8192cu
tuman@montana:~$ dmesg modprobe -r 8192cu

```

After it usbcore logged that "interface driver rtl8192cu is deregistering", what does this means? 

After i re stick dongle in usb port, usbcore also notes that new interface driver was registered and 
```
lsmod|grep 8192cu
``` 
giving output that 8192cu was loaded, also when i manually drop it from mods list
 
(```
modprobe -r 8192cu
```) 
it isn't lists by previous command , until i re stick dongle...

So, does driver 8192cu corresponds to interface driver rtl8192cu? Maybe that msg about verification doesn't means that driver wasn't  load and all is okay? 

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git 
git clone https://github.com/pvaret/rtl8192cu-fixes.git
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.10
```
When i try this, DKMS says that this version was already installed. But output of DKMS status isn't change from my last post (WARNING about diff between built and installed)

I'm fully confused)

---

### Post by wildmanne39 on 2017-02-17
Click on the wireless script in my signature and follow the directions for running it and posting the file it creates here using code tags.

I suspect the kernel tainted error can be ignored, is the wifi working good now?

---

### Post by tuman on 2017-02-18
> **wildmanne39 said:**
> Click on the wireless script in my signature and follow the directions for running it and posting the file it creates here using code tags.

I suspect the kernel tainted error can be ignored, is the wifi working good now?


Now wifi sometimes works good, sometimes not, ping is very unstable, but on other devices all is okay, here is current ping probe to router:
```

tuman@montana:/etc$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=4819 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=3838 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=2830 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=1822 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=64 time=814 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=64 time=17.6 ms
64 bytes from 192.168.1.1: icmp_seq=7 ttl=64 time=10.4 ms
64 bytes from 192.168.1.1: icmp_seq=8 ttl=64 time=239 ms
64 bytes from 192.168.1.1: icmp_seq=9 ttl=64 time=5.92 ms
64 bytes from 192.168.1.1: icmp_seq=10 ttl=64 time=1372 ms
64 bytes from 192.168.1.1: icmp_seq=11 ttl=64 time=365 ms
64 bytes from 192.168.1.1: icmp_seq=12 ttl=64 time=44.0 ms
64 bytes from 192.168.1.1: icmp_seq=13 ttl=64 time=62.8 ms
64 bytes from 192.168.1.1: icmp_seq=14 ttl=64 time=6.76 ms
64 bytes from 192.168.1.1: icmp_seq=15 ttl=64 time=11.8 ms
64 bytes from 192.168.1.1: icmp_seq=16 ttl=64 time=85.5 ms
64 bytes from 192.168.1.1: icmp_seq=17 ttl=64 time=17.6 ms
64 bytes from 192.168.1.1: icmp_seq=18 ttl=64 time=2034 ms
64 bytes from 192.168.1.1: icmp_seq=19 ttl=64 time=1034 ms
64 bytes from 192.168.1.1: icmp_seq=20 ttl=64 time=34.3 ms
64 bytes from 192.168.1.1: icmp_seq=21 ttl=64 time=34.0 ms
64 bytes from 192.168.1.1: icmp_seq=22 ttl=64 time=6.98 ms
64 bytes from 192.168.1.1: icmp_seq=23 ttl=64 time=12.3 ms
64 bytes from 192.168.1.1: icmp_seq=24 ttl=64 time=45.9 ms
64 bytes from 192.168.1.1: icmp_seq=25 ttl=64 time=649 ms
^C
--- 192.168.1.1 ping statistics ---
31 packets transmitted, 25 received, 19% packet loss, time 30098ms
rtt min/avg/max/mdev = 5.929/808.592/4819.004/1285.639 ms, pipe 5



```

Here is my iwconfig:
```

tuman@montana:/etc$ iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:"Jack_Daniels"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.422 GHz  Access Point: **:**:**:**:**:**  
          Bit Rate:144.4 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=88/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



```
I masked some values, but here iwlist wlan0
```

Cell 04 - Address: **:**:**:**:**:**
                    ESSID:"Jack_Daniels"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.422 GHz (Channel 3)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=DATA
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: Data
                    Quality=100/100  Signal level=91/100 

```
Okay, also i'm used network-manager and problem with high ping was occured, so i installed wicd manager, but cant connect to my AP from it), now i connect to my AP by wpa_supplicant and dhclient programms
And here is your script wireless-info:
```



########## wireless info START ##########


Report from: 18 Feb 2017 08:22 MSK +0400


Booted last: 17 Feb 2017 23:28 MSK +0400


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 4.2.0-27-generic #32~14.04.1-Ubuntu SMP Fri Jan 22 15:32:26 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8121/AR8113/AR8114 Gigabit or Fast Ethernet [1969:1026] (rev b0)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8226]
    Kernel driver in use: ATL1E


##### lsusb #############################


Bus 002 Device 040: ID 0b05:5571 ASUSTek Computer, Inc. 
Bus 002 Device 042: ID 0b05:17ab ASUSTek Computer, Inc. USB-N13 802.11n Network Adapter (rev. B1) [Realtek RTL8192CU]
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 09da:054f A4 Tech Co., Ltd 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 005: ID 04f2:0111 Chicony Electronics Co., Ltd KU-9908 Keyboard
Bus 007 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


##### rfkill ############################


##### lsmod #############################


8192cu                528384  0 
mxm_wmi                16384  1 nouveau
wmi                    20480  2 mxm_wmi,nouveau


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:7
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF2]>  
          inet addr:192.168.1.43  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF2]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27465 errors:0 dropped:1049 overruns:0 frame:0
          TX packets:21656 errors:0 dropped:3 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:28141132 (28.1 MB)  TX bytes:4499372 (4.4 MB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"Jack_Daniels"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.422 GHz  Access Point: <MAC 'Jack_Daniels' [AC1]>   
          Bit Rate:144.4 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=95/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0


##### resolv.conf #######################


nameserver 192.168.1.1


##### network managers ##################


Installed:


    Wicd


Running:


    None found.


##### NetworkManager info ###############


NetworkManager is not installed (package "network-manager").


##### NetworkManager.state ##############


[main]
NetworkingEnabled=false
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/Jack_Daniels]] (600 root)
[connection] id=Jack_Daniels | type=802-11-wireless
[802-11-wireless] ssid=Jack_Daniels | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=ignore


##### iw reg get ########################


Region: Europe/Moscow (based on set time zone)


country 00:
    (2402 - 2472 @ 40), (6, 20)
    (2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN
    (2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN
    (5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN
    (5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (6, 20), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0)


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


wlan0     13 channels in total; available frequencies :
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
          Current Frequency:2.422 GHz (Channel 3)


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      2   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.422 GHz (Channel 3)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.442 GHz (Channel 7)
      5   APs on   Frequency:2.462 GHz (Channel 11)


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Jack_Daniels' [AC1]>
                    ESSID:"Jack_Daniels"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.422 GHz (Channel 3)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=100/100  Signal level=96/100  
          Cell 02 - Address: <MAC 'MGTS_GPON_FC7E' [AC2]>
                    ESSID:"MGTS_GPON_FC7E"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:130 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=100/100  Signal level=60/100  
          Cell 03 - Address: <MAC 'PON5 11/1-79' [AC3]>
                    ESSID:"PON5 11/1-79"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:130 Mb/s
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Quality=50/100  Signal level=44/100  
          Cell 04 - Address: <MAC 'beeline-76' [AC4]>
                    ESSID:"beeline-76"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra:wpa_ie=dd160050f20101000050f20201000050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30140100000fac020100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=100/100  Signal level=84/100  
          Cell 05 - Address: <MAC 'PON26 11/1-80' [AC5]>
                    ESSID:"PON26 11/1-80"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:130 Mb/s
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Quality=0/100  Signal level=58/100  
          Cell 06 - Address: <MAC 'Inet75' [AC6]>
                    ESSID:"Inet75"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=0/100  Signal level=58/100  
          Cell 07 - Address: <MAC 'PON5 11/1-71' [AC7]>
                    ESSID:"PON5 11/1-71"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:130 Mb/s
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Quality=36/100  Signal level=78/100  
          Cell 08 - Address: <MAC 'MGTS_GPON_62D6' [AC8]>
                    ESSID:"MGTS_GPON_62D6"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:130 Mb/s
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Quality=20/100  Signal level=57/100  
          Cell 09 - Address: <MAC 'MGTS' [AC9]>
                    ESSID:"MGTS"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=36/100  Signal level=55/100  
          Cell 10 - Address: <MAC 'dimo4a' [AC10]>
                    ESSID:"dimo4a"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:130 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=54/100  Signal level=23/100  
          Cell 11 - Address: <MAC 'SSID4' [AC11]>
                    ESSID:"SSID4"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra:wpa_ie=dd180050f20101000050f20201000050f20201000050f2020000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Quality=56/100  Signal level=23/100  


##### module infos ######################


[8192cu]
filename:       /lib/modules/4.2.0-27-generic/kernel/drivers/net/wireless/8192cu.ko
version:        v4.0.2_9000.20130911
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     340C0C60435AA0500D61BF0
depends:        
vermagic:       4.2.0-27-generic SMP mod_unload modversions 
parm:           rtw_ips_mode:The default IPS mode (int)
parm:           ifname:The default name to allocate for first interface (charp)
parm:           if2name:The default name to allocate for second interface (charp)
parm:           rtw_initmac:charp
parm:           rtw_channel_plan:int
parm:           rtw_chip_version:int
parm:           rtw_rfintfs:int
parm:           rtw_lbkmode:int
parm:           rtw_network_mode:int
parm:           rtw_channel:int
parm:           rtw_mp_mode:int
parm:           rtw_wmm_enable:int
parm:           rtw_vrtl_carrier_sense:int
parm:           rtw_vcs_type:int
parm:           rtw_busy_thresh:int
parm:           rtw_ht_enable:int
parm:           rtw_cbw40_enable:int
parm:           rtw_ampdu_enable:int
parm:           rtw_rx_stbc:int
parm:           rtw_ampdu_amsdu:int
parm:           rtw_lowrate_two_xmit:int
parm:           rtw_rf_config:int
parm:           rtw_power_mgnt:int
parm:           rtw_low_power:int
parm:           rtw_wifi_spec:int
parm:           rtw_special_rf_path:int
parm:           rtw_antdiv_cfg:int
parm:           rtw_enusbss:int
parm:           rtw_hwpdn_mode:int
parm:           rtw_hwpwrp_detect:int
parm:           rtw_hw_wps_pbc:int
parm:           rtw_max_roaming_times:The max roaming times to try (uint)
parm:           rtw_force_iol:Force to enable IOL (bool)
parm:           rtw_mc2u_disable:int
parm:           rtw_mac_phy_mode:int
parm:           rtw_80211d:int
parm:           rtw_notch_filter:0:Disable, 1:Enable, 2:Enable only for P2P (uint)


##### module parameters #################


[8192cu]
if2name: wlan%d
ifname: wlan%d
rtw_80211d: 0
rtw_ampdu_amsdu: 0
rtw_ampdu_enable: 1
rtw_antdiv_cfg: 2
rtw_busy_thresh: 40
rtw_cbw40_enable: 3
rtw_channel: 1
rtw_channel_plan: 65
rtw_chip_version: 0
rtw_enusbss: 0
rtw_force_iol: N
rtw_ht_enable: 1
rtw_hwpdn_mode: 2
rtw_hwpwrp_detect: 0
rtw_hw_wps_pbc: 1
rtw_initmac: (null)
rtw_ips_mode: 1
rtw_lbkmode: 0
rtw_low_power: 0
rtw_lowrate_two_xmit: 1
rtw_mac_phy_mode: 0
rtw_max_roaming_times: 2
rtw_mc2u_disable: 0
rtw_mp_mode: 0
rtw_network_mode: 0
rtw_notch_filter: 0
rtw_power_mgnt: 1
rtw_rf_config: 5
rtw_rfintfs: 2
rtw_rx_stbc: 1
rtw_special_rf_path: 0
rtw_vcs_type: 1
rtw_vrtl_carrier_sense: 2
rtw_wifi_spec: 0
rtw_wmm_enable: 1


##### /etc/modules ######################


rtc
8192cu
coretemp
w83627ehf


##### modprobe options ##################


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
blacklist rtl8192cu
blacklist rtl8192c_common
blacklist rtlwifi


[/etc/modprobe.d/blacklist-native-rtl8192.conf]
install rtl8192cu /bin/false
install rtl8192c_common /bin/false
install rtlwifi /bin/false
install rtl8xxxu /bin/false


[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x1969:0x1026 (ATL1E)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF2]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[ 6735.599989] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6735.670614] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 6737.981040] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 7014.550055] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7020.413372] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 7509.090716] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 7526.557547] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7531.357043] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 7579.461592] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7584.124290] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 7591.306164] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7595.514175] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


########## wireless info END ############



```

---

### Post by wildmanne39 on 2017-02-18
I can not really help you or any one else will be able to either if you keep changing things without being asked too, you have so many things changed it will take a while to undo them.

Before we proceed is your connection working good now that you are not using network manager or wicd?

Did you set all those parameters for the new driver that it shows in the file?

Did you run:
```
sudo cp ./rtl8192cu-fixes/8192cu-disable-power-management.conf /etc/modprobe.d/
``` 
after you installed them new driver if not please do so now and see if that fixes the issue please.
If the issue continue all I need to see is a new script file each time it has all the information in it.

---

### Post by tuman on 2017-02-18
> **wildmanne39 said:**
> I can not really help you or any one else will be able to either if you keep changing things without being asked too, you have so many things changed it will take a while to undo them.

Before we proceed is your connection working good now that you are not using network manager or wicd?

Did you set all those parameters for the new driver that it shows in the file?

Did you run:
```
sudo cp ./rtl8192cu-fixes/8192cu-disable-power-management.conf /etc/modprobe.d/
``` 
after you installed them new driver if not please do so now and see if that fixes the issue please.
If the issue continue all I need to see is a new script file each time it has all the information in it.

Now i'm not using them both, and when i started this thread i dont use them, i didn't change something after created this topic. Okay i understood you.

my connection is good, better than with network-manager, with network-manager i have big problems with reconnect to the a.p.
No, I didn't set them.

No, now i run, and yes ping become more better and connect come more stable, not fully sure in it, but hope that this problem is solved), here is my ping, now:

```

tuman@montana:~/webdrivers$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=30.3 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=14.4 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=7.48 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=6.46 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=64 time=6.09 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=64 time=5.48 ms
64 bytes from 192.168.1.1: icmp_seq=7 ttl=64 time=5.58 ms
64 bytes from 192.168.1.1: icmp_seq=8 ttl=64 time=1709 ms
64 bytes from 192.168.1.1: icmp_seq=9 ttl=64 time=1198 ms
64 bytes from 192.168.1.1: icmp_seq=10 ttl=64 time=199 ms
64 bytes from 192.168.1.1: icmp_seq=11 ttl=64 time=205 ms
64 bytes from 192.168.1.1: icmp_seq=12 ttl=64 time=8.38 ms
64 bytes from 192.168.1.1: icmp_seq=13 ttl=64 time=161 ms
64 bytes from 192.168.1.1: icmp_seq=14 ttl=64 time=6.73 ms
64 bytes from 192.168.1.1: icmp_seq=15 ttl=64 time=9.17 ms
64 bytes from 192.168.1.1: icmp_seq=16 ttl=64 time=5.47 ms
64 bytes from 192.168.1.1: icmp_seq=17 ttl=64 time=5.46 ms
64 bytes from 192.168.1.1: icmp_seq=18 ttl=64 time=3724 ms
64 bytes from 192.168.1.1: icmp_seq=19 ttl=64 time=2715 ms
64 bytes from 192.168.1.1: icmp_seq=20 ttl=64 time=1707 ms
64 bytes from 192.168.1.1: icmp_seq=21 ttl=64 time=699 ms
64 bytes from 192.168.1.1: icmp_seq=22 ttl=64 time=298 ms
64 bytes from 192.168.1.1: icmp_seq=23 ttl=64 time=12.4 ms
64 bytes from 192.168.1.1: icmp_seq=24 ttl=64 time=5.58 ms
^C
--- 192.168.1.1 ping statistics ---
24 packets transmitted, 24 received, 0% packet loss, time 23056ms
rtt min/avg/max/mdev = 5.468/531.281/3724.221/966.884 ms, pipe 4



```
What can cause this strange delay? Other devices disconnected from this network. Or maybe its normal behaviour?
Thanks you with help! By increasingly i think this problem is solved!
```

########## wireless info START ##########


Report from: 18 Feb 2017 09:09 MSK +0400


Booted last: 18 Feb 2017 09:03 MSK +0400


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 4.2.0-27-generic #32~14.04.1-Ubuntu SMP Fri Jan 22 15:32:26 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8121/AR8113/AR8114 Gigabit or Fast Ethernet [1969:1026] (rev b0)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8226]
    Kernel driver in use: ATL1E


##### lsusb #############################


Bus 002 Device 006: ID 04f2:0111 Chicony Electronics Co., Ltd KU-9908 Keyboard
Bus 002 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 003: ID 0b05:5571 ASUSTek Computer, Inc. 
Bus 002 Device 002: ID 0b05:17ab ASUSTek Computer, Inc. USB-N13 802.11n Network Adapter (rev. B1) [Realtek RTL8192CU]
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 09da:054f A4 Tech Co., Ltd 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


##### rfkill ############################


##### lsmod #############################


8192cu                528384  0 
mxm_wmi                16384  1 nouveau
wmi                    20480  2 mxm_wmi,nouveau


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF2]>  
          inet addr:192.168.1.43  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF2]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7937 errors:0 dropped:394 overruns:0 frame:0
          TX packets:8078 errors:0 dropped:3 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6808186 (6.8 MB)  TX bytes:1640021 (1.6 MB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"Jack_Daniels"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.422 GHz  Access Point: <MAC 'Jack_Daniels' [AC1]>   
          Bit Rate:144.4 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=92/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0


##### resolv.conf #######################


nameserver 192.168.1.1


##### network managers ##################


Installed:


    Wicd


Running:


    None found.


##### NetworkManager info ###############


NetworkManager is not installed (package "network-manager").


##### NetworkManager.state ##############


[main]
NetworkingEnabled=false
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/Jack_Daniels]] (600 root)
[connection] id=Jack_Daniels | type=802-11-wireless
[802-11-wireless] ssid=Jack_Daniels | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=ignore


##### iw reg get ########################


Region: Europe/Moscow (based on set time zone)


country 00:
    (2402 - 2472 @ 40), (6, 20)
    (2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN
    (2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN
    (5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN
    (5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (6, 20), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0)


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


wlan0     13 channels in total; available frequencies :
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
          Current Frequency:2.422 GHz (Channel 3)


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.422 GHz (Channel 3)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.442 GHz (Channel 7)
      3   APs on   Frequency:2.462 GHz (Channel 11)


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Jack_Daniels' [AC1]>
                    ESSID:"Jack_Daniels"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.422 GHz (Channel 3)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=100/100  Signal level=93/100  
          Cell 02 - Address: <MAC 'MGTS_GPON_FC7E' [AC2]>
                    ESSID:"MGTS_GPON_FC7E"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:130 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=100/100  Signal level=56/100  
          Cell 03 - Address: <MAC 'Inet75' [AC3]>
                    ESSID:"Inet75"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=0/100  Signal level=74/100  
          Cell 04 - Address: <MAC 'PON26 11/1-80' [AC4]>
                    ESSID:"PON26 11/1-80"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:130 Mb/s
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Quality=88/100  Signal level=47/100  
          Cell 05 - Address: <MAC 'beeline-76' [AC5]>
                    ESSID:"beeline-76"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra:wpa_ie=dd160050f20101000050f20201000050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30140100000fac020100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=100/100  Signal level=84/100  
          Cell 06 - Address: <MAC 'PON5 11/1-71' [AC6]>
                    ESSID:"PON5 11/1-71"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:130 Mb/s
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Quality=36/100  Signal level=77/100  
          Cell 07 - Address: <MAC 'MGTS_GPON_62D6' [AC7]>
                    ESSID:"MGTS_GPON_62D6"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:130 Mb/s
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Quality=20/100  Signal level=50/100  
          Cell 08 - Address: <MAC 'MGTS' [AC8]>
                    ESSID:"MGTS"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=20/100  Signal level=57/100  


##### module infos ######################


[8192cu]
filename:       /lib/modules/4.2.0-27-generic/kernel/drivers/net/wireless/8192cu.ko
version:        v4.0.2_9000.20130911
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     340C0C60435AA0500D61BF0
depends:        
vermagic:       4.2.0-27-generic SMP mod_unload modversions 
parm:           rtw_ips_mode:The default IPS mode (int)
parm:           ifname:The default name to allocate for first interface (charp)
parm:           if2name:The default name to allocate for second interface (charp)
parm:           rtw_initmac:charp
parm:           rtw_channel_plan:int
parm:           rtw_chip_version:int
parm:           rtw_rfintfs:int
parm:           rtw_lbkmode:int
parm:           rtw_network_mode:int
parm:           rtw_channel:int
parm:           rtw_mp_mode:int
parm:           rtw_wmm_enable:int
parm:           rtw_vrtl_carrier_sense:int
parm:           rtw_vcs_type:int
parm:           rtw_busy_thresh:int
parm:           rtw_ht_enable:int
parm:           rtw_cbw40_enable:int
parm:           rtw_ampdu_enable:int
parm:           rtw_rx_stbc:int
parm:           rtw_ampdu_amsdu:int
parm:           rtw_lowrate_two_xmit:int
parm:           rtw_rf_config:int
parm:           rtw_power_mgnt:int
parm:           rtw_low_power:int
parm:           rtw_wifi_spec:int
parm:           rtw_special_rf_path:int
parm:           rtw_antdiv_cfg:int
parm:           rtw_enusbss:int
parm:           rtw_hwpdn_mode:int
parm:           rtw_hwpwrp_detect:int
parm:           rtw_hw_wps_pbc:int
parm:           rtw_max_roaming_times:The max roaming times to try (uint)
parm:           rtw_force_iol:Force to enable IOL (bool)
parm:           rtw_mc2u_disable:int
parm:           rtw_mac_phy_mode:int
parm:           rtw_80211d:int
parm:           rtw_notch_filter:0:Disable, 1:Enable, 2:Enable only for P2P (uint)


##### module parameters #################


[8192cu]
if2name: wlan%d
ifname: wlan%d
rtw_80211d: 0
rtw_ampdu_amsdu: 0
rtw_ampdu_enable: 1
rtw_antdiv_cfg: 2
rtw_busy_thresh: 40
rtw_cbw40_enable: 3
rtw_channel: 1
rtw_channel_plan: 65
rtw_chip_version: 0
rtw_enusbss: 0
rtw_force_iol: N
rtw_ht_enable: 1
rtw_hwpdn_mode: 2
rtw_hwpwrp_detect: 0
rtw_hw_wps_pbc: 1
rtw_initmac: (null)
rtw_ips_mode: 1
rtw_lbkmode: 0
rtw_low_power: 0
rtw_lowrate_two_xmit: 1
rtw_mac_phy_mode: 0
rtw_max_roaming_times: 2
rtw_mc2u_disable: 0
rtw_mp_mode: 0
rtw_network_mode: 0
rtw_notch_filter: 0
rtw_power_mgnt: 0
rtw_rf_config: 5
rtw_rfintfs: 2
rtw_rx_stbc: 1
rtw_special_rf_path: 0
rtw_vcs_type: 1
rtw_vrtl_carrier_sense: 2
rtw_wifi_spec: 0
rtw_wmm_enable: 1


##### /etc/modules ######################


rtc
8192cu
coretemp
w83627ehf


##### modprobe options ##################


[/etc/modprobe.d/8192cu-disable-power-management.conf]
options 8192cu rtw_power_mgnt=0 rtw_enusbss=0


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
blacklist rtl8192cu
blacklist rtl8192c_common
blacklist rtlwifi


[/etc/modprobe.d/blacklist-native-rtl8192.conf]
install rtl8192cu /bin/false
install rtl8192c_common /bin/false
install rtlwifi /bin/false
install rtl8xxxu /bin/false


[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x1969:0x1026 (ATL1E)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF2]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[    7.464046] 8192cu: module verification failed: signature and/or required key missing - tainting kernel
[   33.168885] init: network-manager main process (838) terminated with status 127
[   33.168894] init: network-manager main process ended, respawning
[   46.445584] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   51.018497] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  127.508306] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


########## wireless info END ############



```

---

### Post by wildmanne39 on 2017-02-18
Let's set your country code for your router and that may help further:
```
sudo iw reg set RU
sudo sed -i 's/^REG.*=$/&RU/' /etc/default/crda
```
It is very late here, if you need more help after you change the country code I will help you tomorrow if someone does not beat me to it.

---

### Post by tuman on 2017-02-18
> **wildmanne39 said:**
> Let's set your country code for your router and that may help further:
```
sudo iw reg set RU
sudo sed -i 's/^REG.*=$/&RU/' /etc/default/crda
```
It is very late here, if you need more help after you change the country code I will help you tomorrow if someone does not beat me to it.
I'm set this, but delays are still occure, yes, some help with delays will be nice, okay), will see you tomorrow
Here wireless-info
```

########## wireless info START ##########


Report from: 18 Feb 2017 10:07 MSK +0400


Booted last: 18 Feb 2017 09:03 MSK +0400


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.4 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 4.2.0-27-generic #32~14.04.1-Ubuntu SMP Fri Jan 22 15:32:26 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8121/AR8113/AR8114 Gigabit or Fast Ethernet [1969:1026] (rev b0)
	Subsystem: ASUSTeK Computer Inc. Device [1043:8226]
	Kernel driver in use: ATL1E


##### lsusb #############################


Bus 002 Device 010: ID 04f2:0111 Chicony Electronics Co., Ltd KU-9908 Keyboard
Bus 002 Device 009: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 003: ID 0b05:5571 ASUSTek Computer, Inc. 
Bus 002 Device 002: ID 0b05:17ab ASUSTek Computer, Inc. USB-N13 802.11n Network Adapter (rev. B1) [Realtek RTL8192CU]
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 09da:054f A4 Tech Co., Ltd 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


##### rfkill ############################


##### lsmod #############################


cfg80211              540672  0 
8192cu                528384  0 
mxm_wmi                16384  1 nouveau
wmi                    20480  2 mxm_wmi,nouveau


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF2]>  
          inet addr:192.168.1.43  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF2]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1234 errors:0 dropped:1561 overruns:0 frame:0
          TX packets:1358 errors:0 dropped:10 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:27533703 (27.5 MB)  TX bytes:9032110 (9.0 MB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"Jack_Daniels"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.422 GHz  Access Point: <MAC 'Jack_Daniels' [AC1]>   
          Bit Rate:144.4 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=86/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0


##### resolv.conf #######################


nameserver 192.168.1.1


##### network managers ##################


Installed:


	Wicd


Running:


	None found.


##### NetworkManager info ###############


NetworkManager is not installed (package "network-manager").


##### NetworkManager.state ##############


[main]
NetworkingEnabled=false
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/Jack_Daniels]] (600 root)
[connection] id=Jack_Daniels | type=802-11-wireless
[802-11-wireless] ssid=Jack_Daniels | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=ignore


##### iw reg get ########################


Region: Europe/Moscow (based on set time zone)


country RU:
	(2402 - 2482 @ 40), (N/A, 20)
	(5735 - 5835 @ 20), (N/A, 30)


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


wlan0     13 channels in total; available frequencies :
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
          Current Frequency:2.422 GHz (Channel 3)


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      2   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.422 GHz (Channel 3)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.442 GHz (Channel 7)
      3   APs on   Frequency:2.462 GHz (Channel 11)


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Jack_Daniels' [AC1]>
                    ESSID:"Jack_Daniels"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.422 GHz (Channel 3)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=100/100  Signal level=86/100  
          Cell 02 - Address: <MAC 'MGTS_GPON_96AD' [AC2]>
                    ESSID:"MGTS_GPON_96AD"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:130 Mb/s
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Quality=84/100  Signal level=44/100  
          Cell 03 - Address: <MAC 'MGTS_GPON_FC7E' [AC3]>
                    ESSID:"MGTS_GPON_FC7E"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:130 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=99/100  Signal level=54/100  
          Cell 04 - Address: <MAC 'PON26 11/1-80' [AC4]>
                    ESSID:"PON26 11/1-80"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:130 Mb/s
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Quality=100/100  Signal level=56/100  
          Cell 05 - Address: <MAC 'Inet75' [AC5]>
                    ESSID:"Inet75"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=100/100  Signal level=64/100  
          Cell 06 - Address: <MAC 'beeline-76' [AC6]>
                    ESSID:"beeline-76"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra:wpa_ie=dd160050f20101000050f20201000050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30140100000fac020100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=20/100  Signal level=76/100  
          Cell 07 - Address: <MAC 'PON5 11/1-71' [AC7]>
                    ESSID:"PON5 11/1-71"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:130 Mb/s
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Quality=48/100  Signal level=68/100  
          Cell 08 - Address: <MAC 'MGTS_GPON_62D6' [AC8]>
                    ESSID:"MGTS_GPON_62D6"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:130 Mb/s
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Quality=36/100  Signal level=49/100  
          Cell 09 - Address: <MAC 'MGTS' [AC9]>
                    ESSID:"MGTS"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=48/100  Signal level=47/100  


##### module infos ######################


[cfg80211]
filename:       /lib/modules/4.2.0-27-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     7982686FBE8064A87E02753
depends:        
intree:         Y
vermagic:       4.2.0-27-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        73:6E:2F:9E:A1:B4:72:8A:15:AC:16:9B:18:69:26:7E:11:28:D6:E8
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[8192cu]
filename:       /lib/modules/4.2.0-27-generic/kernel/drivers/net/wireless/8192cu.ko
version:        v4.0.2_9000.20130911
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     340C0C60435AA0500D61BF0
depends:        
vermagic:       4.2.0-27-generic SMP mod_unload modversions 
parm:           rtw_ips_mode:The default IPS mode (int)
parm:           ifname:The default name to allocate for first interface (charp)
parm:           if2name:The default name to allocate for second interface (charp)
parm:           rtw_initmac:charp
parm:           rtw_channel_plan:int
parm:           rtw_chip_version:int
parm:           rtw_rfintfs:int
parm:           rtw_lbkmode:int
parm:           rtw_network_mode:int
parm:           rtw_channel:int
parm:           rtw_mp_mode:int
parm:           rtw_wmm_enable:int
parm:           rtw_vrtl_carrier_sense:int
parm:           rtw_vcs_type:int
parm:           rtw_busy_thresh:int
parm:           rtw_ht_enable:int
parm:           rtw_cbw40_enable:int
parm:           rtw_ampdu_enable:int
parm:           rtw_rx_stbc:int
parm:           rtw_ampdu_amsdu:int
parm:           rtw_lowrate_two_xmit:int
parm:           rtw_rf_config:int
parm:           rtw_power_mgnt:int
parm:           rtw_low_power:int
parm:           rtw_wifi_spec:int
parm:           rtw_special_rf_path:int
parm:           rtw_antdiv_cfg:int
parm:           rtw_enusbss:int
parm:           rtw_hwpdn_mode:int
parm:           rtw_hwpwrp_detect:int
parm:           rtw_hw_wps_pbc:int
parm:           rtw_max_roaming_times:The max roaming times to try (uint)
parm:           rtw_force_iol:Force to enable IOL (bool)
parm:           rtw_mc2u_disable:int
parm:           rtw_mac_phy_mode:int
parm:           rtw_80211d:int
parm:           rtw_notch_filter:0:Disable, 1:Enable, 2:Enable only for P2P (uint)


##### module parameters #################


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


[8192cu]
if2name: wlan%d
ifname: wlan%d
rtw_80211d: 0
rtw_ampdu_amsdu: 0
rtw_ampdu_enable: 1
rtw_antdiv_cfg: 2
rtw_busy_thresh: 40
rtw_cbw40_enable: 3
rtw_channel: 1
rtw_channel_plan: 65
rtw_chip_version: 0
rtw_enusbss: 0
rtw_force_iol: N
rtw_ht_enable: 1
rtw_hwpdn_mode: 2
rtw_hwpwrp_detect: 0
rtw_hw_wps_pbc: 1
rtw_initmac: (null)
rtw_ips_mode: 1
rtw_lbkmode: 0
rtw_low_power: 0
rtw_lowrate_two_xmit: 1
rtw_mac_phy_mode: 0
rtw_max_roaming_times: 2
rtw_mc2u_disable: 0
rtw_mp_mode: 0
rtw_network_mode: 0
rtw_notch_filter: 0
rtw_power_mgnt: 0
rtw_rf_config: 5
rtw_rfintfs: 2
rtw_rx_stbc: 1
rtw_special_rf_path: 0
rtw_vcs_type: 1
rtw_vrtl_carrier_sense: 2
rtw_wifi_spec: 0
rtw_wmm_enable: 1


##### /etc/modules ######################


rtc
8192cu
coretemp
w83627ehf


##### modprobe options ##################


[/etc/modprobe.d/8192cu-disable-power-management.conf]
options 8192cu rtw_power_mgnt=0 rtw_enusbss=0


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
blacklist rtl8192cu
blacklist rtl8192c_common
blacklist rtlwifi


[/etc/modprobe.d/blacklist-native-rtl8192.conf]
install rtl8192cu /bin/false
install rtl8192c_common /bin/false
install rtlwifi /bin/false
install rtl8xxxu /bin/false


[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x1969:0x1026 (ATL1E)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF2]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[   33.168885] init: network-manager main process (838) terminated with status 127
[   33.168894] init: network-manager main process ended, respawning
[   46.445584] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   51.018497] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  127.508306] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3396.226385] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[ 3396.335229] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 3418.673549] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 3 times)
[ 3482.198289] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


########## wireless info END ############



```

---

### Post by wildmanne39 on 2017-02-18
The only thing I see that we can do is to change to the google nameserver which is faster in most cases then the IP'S.
```
echo "nameserver 8.8.8.8" | sudo tee /etc/resolv.conf . /dev/null
```
You can still set the router channel to 1, 6, or 11 ans see if that cuts down on interference.

---

### Post by tuman on 2017-02-19
Thx, I changed nameserver and requests come little faster, switching the channels dont change something in better direction

---

### Post by wildmanne39 on 2017-02-19
That was the last thing that I see to try from the information in the file by the wireless script everything looks good.

If you are satisfied that it is working a lot better then before please use thread tools to mark the thread as solved.

---

