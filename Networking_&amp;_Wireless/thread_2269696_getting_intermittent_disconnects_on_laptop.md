---
title: "getting intermittent disconnects on laptop"
date: 2015-03-17
forum: Networking &amp; Wireless
---

### Post by sam_baker2 on 2015-03-17
hi,
I have just installed xubuntu 14.04.2 on my laptop, and now i am getting
disconnected from the wifi after 10 minutes or so. I can uncheck the 
"enable wifi" tab, then check it back, then I can I can reconnect. But
after some minutes, I get disconnected again.
I had 12.04 on this laptop, and had absolutely no problem with the
connection. It has an intel chip in it.

I found a few commands from the forum, here they are:


here is the result of iwconfig:
```

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

```

here is lspci -nnk | grep -iA2 net

```

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Lenovo Device [17aa:21e2]
    Kernel driver in use: r8169
--
08:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8195]
    Kernel driver in use: rtl8192ce

```

here is cat /etc/modprobe.d/iwlwifi.conf

```

# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

```


thanks for any help

---

### Post by kc1di on 2015-03-17
The answer at Ask Ubuntu here may be of help - that wireless card seems to have been problematic for quite a while now. 
[http://askubuntu.com/questions/482564/realtek-rtl8188ce-desconects-randomly-and-features-slow-connections]("http://askubuntu.com/questions/482564/realtek-rtl8188ce-desconects-randomly-and-features-slow-connections")

---

### Post by sam_baker2 on 2015-03-17
thnks for reply kc1di,
I will try some of the sugestions on that link but it might take
some time, as the laptop may sit for 20-30 minutes before
it acts up.

---

### Post by wildmanne39 on 2015-03-17
If that does not help you can install the backported driver that works better, I am not sure of your kernel verson but this one should work if you have kernel 3.13 - 3.16.

Install the dependencies required to compile the driver:

    ```
sudo apt-get install --reinstall linux-headers-generic linux-headers-$(uname -r) build-essential dkms

```
Click on the link below to download the newest driver to your computer then right click and extract here.

Then compile the driver using the directions below.

```
cd ~/Downloads/backports-3.16-rc1-1
make defconfig-rtlwifi
make
sudo make install
```
Reboot    
When you have an upgrade to the kernel you will need to do:

```
cd ~/Downloads/backports-3.16-rc1-1
make clean
make defconfig-rtlwifi
make
sudo make install
```
Reboot




  [1]: [https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.16-rc1/backports-3.16-rc1-1.tar.xz](https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.16-rc1/backports-3.16-rc1-1.tar.xz)

---

### Post by sam_baker2 on 2015-03-17
thks for reply Wild Man
I am going through the suggestions given on the link
[http://askubuntu.com/questions/482564/realtek-rtl8188ce-desconects-randomly-and-features-slow-connections](http://askubuntu.com/questions/482564/realtek-rtl8188ce-desconects-randomly-and-features-slow-connections)
one by one, and have to wait awhile to see if and which any particular one will fix the problem,
then, if this doesn't work, will try your post.

also uname -r is 
```

3.16.0-31-generic

```

---

### Post by sam_baker2 on 2015-03-17
I had no luck Wild Man.
I tried to set the router to only "B" mode, set the channel to 11, then I installed 
the "backports-3.16-rc1-1" per your post, but I still get disconnected after about 
10 minutes.
I tried turning the router & modem off for a minute or so, then back on, as well as
turning the laptop off, then on.
~also, I set the encryption to "AES" only.

---

### Post by wildmanne39 on 2015-03-17
Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

---

### Post by sam_baker2 on 2015-03-17
here is the text from the script wild man

```



########## wireless info START ##########

Report from: 17 Mar 2015 22:34 CDT -0500

Booted last: 17 Mar 2015 20:00 CDT -0500

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.16.0-31-generic #43~14.04.1-Ubuntu SMP Tue Mar 10 20:13:38 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Xubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Lenovo Device [17aa:21e2]
    Kernel driver in use: r8169

08:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8195]
    Kernel driver in use: rtl8192ce

##### lsusb #############################

Bus 002 Device 003: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 5986:03b3 Acer, Inc 
Bus 001 Device 003: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8192ce              75561  0 
rtl_pci                35587  1 rtl8192ce
rtlwifi                91289  2 rtl_pci,rtl8192ce
rtl8192c_common        70973  1 rtl8192ce
mac80211              549421  3 rtl_pci,rtlwifi,rtl8192ce
cfg80211              498251  2 mac80211,rtlwifi
compat                 13139  4 cfg80211,mac80211,rtlwifi,rtl8192ce

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::62d8:19ff:fecb:6442/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3909 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3712 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3403349 (3.4 MB)  TX bytes:596692 (596.6 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Router2"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'Router2' [AC1]>   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-14 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:21   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: wlan0  [Router2] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           18 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    McCURDY:         Infra, <MAC 'McCURDY' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 80 WPA2
    CISCO814:        Infra, <MAC 'CISCO814' [AN2]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    CISCO814-guest:  Infra, <MAC 'CISCO814-guest' [AN3]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27
    *Router2:        Infra, <MAC 'Router2' [AC1]>, Freq 2462 MHz, Rate 11 Mb/s, Strength 88 WPA2

  IPv4 Settings:
    Address:         192.168.1.101
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             156.154.70.1
    DNS:             156.154.71.1

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
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

[[/etc/NetworkManager/system-connections/Router2]] (600 root)
[connection] id=Router2 | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=Router2 | mac-address=<MAC 'wlan0' [IF]> | mtu=1500
[ipv4] method=auto
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/TGM]] (600 root)
[connection] id=TGM | type=802-11-wireless
[802-11-wireless] ssid=TGM | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Chicago (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

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
          Current Frequency:2.462 GHz (Channel 11)

##### iwlist scan #######################

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      5   APs on   Frequency:2.462 GHz (Channel 11)

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Router2' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:on
                    ESSID:"Router2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=000000022f069d7f
                    Extra: Last beacon: 60ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'McCURDY' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"McCURDY"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000264064a8ee0
                    Extra: Last beacon: 60ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'TGM' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-36 dBm  
                    Encryption key:on
                    ESSID:"TGM"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000018201c967c7
                    Extra: Last beacon: 60ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC '

```

---

### Post by wildmanne39 on 2015-03-17
There is a lot of information missing from that file, can you try agin? 
Thanks

---

### Post by sam_baker2 on 2015-03-18
that was from the pastebin file, this is the 21k downloaded textfile:
```



########## wireless info START ##########

Report from: 17 Mar 2015 22:34 CDT -0500

Booted last: 17 Mar 2015 20:00 CDT -0500

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.16.0-31-generic #43~14.04.1-Ubuntu SMP Tue Mar 10 20:13:38 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Xubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Lenovo Device [17aa:21e2]
    Kernel driver in use: r8169

08:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8195]
    Kernel driver in use: rtl8192ce

##### lsusb #############################

Bus 002 Device 003: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 5986:03b3 Acer, Inc 
Bus 001 Device 003: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8192ce              75561  0 
rtl_pci                35587  1 rtl8192ce
rtlwifi                91289  2 rtl_pci,rtl8192ce
rtl8192c_common        70973  1 rtl8192ce
mac80211              549421  3 rtl_pci,rtlwifi,rtl8192ce
cfg80211              498251  2 mac80211,rtlwifi
compat                 13139  4 cfg80211,mac80211,rtlwifi,rtl8192ce

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::62d8:19ff:fecb:6442/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3909 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3712 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3403349 (3.4 MB)  TX bytes:596692 (596.6 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Router2"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'Router2' [AC1]>   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-14 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:21   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: wlan0  [Router2] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           18 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    McCURDY:         Infra, <MAC 'McCURDY' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 80 WPA2
    CISCO814:        Infra, <MAC 'CISCO814' [AN2]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    CISCO814-guest:  Infra, <MAC 'CISCO814-guest' [AN3]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27
    *Router2:        Infra, <MAC 'Router2' [AC1]>, Freq 2462 MHz, Rate 11 Mb/s, Strength 88 WPA2

  IPv4 Settings:
    Address:         192.168.1.101
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             156.154.70.1
    DNS:             156.154.71.1

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
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

[[/etc/NetworkManager/system-connections/Router2]] (600 root)
[connection] id=Router2 | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=Router2 | mac-address=<MAC 'wlan0' [IF]> | mtu=1500
[ipv4] method=auto
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/TGM]] (600 root)
[connection] id=TGM | type=802-11-wireless
[802-11-wireless] ssid=TGM | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Chicago (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

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
          Current Frequency:2.462 GHz (Channel 11)

##### iwlist scan #######################

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      5   APs on   Frequency:2.462 GHz (Channel 11)

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Router2' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:on
                    ESSID:"Router2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=000000022f069d7f
                    Extra: Last beacon: 60ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'McCURDY' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"McCURDY"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000264064a8ee0
                    Extra: Last beacon: 60ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'TGM' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-36 dBm  
                    Encryption key:on
                    ESSID:"TGM"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000018201c967c7
                    Extra: Last beacon: 60ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC '\00\00\00\00\00' [AC4]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000018201cf6176
                    Extra: Last beacon: 368ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC '\00\00\00\00\00' [AC5]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-36 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000018201cac0de
                    Extra: Last beacon: 632ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC '\00\00\00\00\00' [AC6]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; lo        Interface doesn't support scanning.

5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000018201b1c606
                    Extra: Last beacon: 2332ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8192ce]
filename:       /lib/modules/3.16.0-31-generic/updates/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
version:        backported from Linux (v3.16-rc1-0-g7171511) using backports v3.16-rc1-1-0-g04d6077
firmware:       rtlwifi/rtl8192cfwU_B.bin
firmware:       rtlwifi/rtl8192cfwU.bin
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     BE372FB24A1F38A5218DAA0
depends:        rtlwifi,rtl_pci,rtl8192c-common,compat,mac80211
vermagic:       3.16.0-31-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl_pci]
filename:       /lib/modules/3.16.0-31-generic/updates/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     2A841709EF6A38E777CCD34
depends:        mac80211,rtlwifi
vermagic:       3.16.0-31-generic SMP mod_unload modversions 

[rtlwifi]
filename:       /lib/modules/3.16.0-31-generic/updates/drivers/net/wireless/rtlwifi/rtlwifi.ko
version:        backported from Linux (v3.16-rc1-0-g7171511) using backports v3.16-rc1-1-0-g04d6077
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     AEDBFD2C2F64D9D545BF951
depends:        mac80211,compat,cfg80211
vermagic:       3.16.0-31-generic SMP mod_unload modversions 

[rtl8192c_common]
filename:       /lib/modules/3.16.0-31-generic/updates/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     A279C50E29ED7F277EAF738
depends:        
vermagic:       3.16.0-31-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/3.16.0-31-generic/updates/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
version:        backported from Linux (v3.16-rc1-0-g7171511) using backports v3.16-rc1-1-0-g04d6077
srcversion:     9CD4BA60E3E8E32D406EF8E
depends:        cfg80211,compat
vermagic:       3.16.0-31-generic SMP mod_unload modversions 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.16.0-31-generic/updates/net/wireless/cfg80211.ko
version:        backported from Linux (v3.16-rc1-0-g7171511) using backports v3.16-rc1-1-0-g04d6077
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     1481A68D59D8001BEE4C696
depends:        compat
vermagic:       3.16.0-31-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8192ce]
debug: 0
fwlps: Y
ips: Y
swenc: N
swlps: N

[mac80211]
beacon_loss_count: 7
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

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

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0x8176 (rtl8192ce)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   15.844346] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   54.599337] wlan0: authenticate with <MAC 'Router2' [AC1]>
[   54.619170] wlan0: send auth to <MAC 'Router2' [AC1]> (try 1/3)
[   54.621515] wlan0: authenticated
[   54.621694] rtl8192ce 0000:08:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   54.621698] rtl8192ce 0000:08:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   54.622639] wlan0: associate with <MAC 'Router2' [AC1]> (try 1/3)
[   54.625033] wlan0: RX AssocResp from <MAC 'Router2' [AC1]> (capab=0x11 status=0 aid=1)
[   54.625192] wlan0: associated
[   54.625203] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  266.211470] wlan0: deauthenticated from <MAC 'Router2' [AC1]> (Reason: 7=CLASS3_FRAME_FROM_NONASSOC_STA)
[  266.233605] wlan0: authenticate with <MAC 'Router2' [AC1]>
[  266.243792] wlan0: send auth to <MAC 'Router2' [AC1]> (try 1/3)
[  266.247881] wlan0: authenticated
[  266.248070] rtl8192ce 0000:08:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  266.248074] rtl8192ce 0000:08:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  266.249209] wlan0: associate with <MAC 'Router2' [AC1]> (try 1/3)
[  266.255432] wlan0: RX AssocResp from <MAC 'Router2' [AC1]> (capab=0x11 status=0 aid=1)
[  266.255601] wlan0: associated
[  427.690137] wlan0: deauthenticated from <MAC 'Router2' [AC1]> (Reason: 7=CLASS3_FRAME_FROM_NONASSOC_STA)
[  427.738564] wlan0: authenticate with <MAC 'Router2' [AC1]>
[  427.748731] wlan0: send auth to <MAC 'Router2' [AC1]> (try 1/3)
[  427.753006] wlan0: authenticated
[  427.753201] rtl8192ce 0000:08:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  427.753206] rtl8192ce 0000:08:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  427.754337] wlan0: associate with <MAC 'Router2' [AC1]> (try 1/3)
[  427.757054] wlan0: RX AssocResp from <MAC 'Router2' [AC1]> (capab=0x11 status=0 aid=1)
[  427.757220] wlan0: associated
[  548.893691] wlan0: deauthenticated from <MAC 'Router2' [AC1]> (Reason: 7=CLASS3_FRAME_FROM_NONASSOC_STA)
[ 9186.765853] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9191.627156] wlan0: authenticate with <MAC 'Router2' [AC1]>
[ 9191.637365] wlan0: send auth to <MAC 'Router2' [AC1]> (try 1/3)
[ 9191.639997] wlan0: authenticated
[ 9191.640128] rtl8192ce 0000:08:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 9191.640132] rtl8192ce 0000:08:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 9191.643128] wlan0: associate with <MAC 'Router2' [AC1]> (try 1/3)
[ 9191.646058] wlan0: RX AssocResp from <MAC 'Router2' [AC1]> (capab=0x11 status=0 aid=1)
[ 9191.646215] wlan0: associated
[ 9191.646241] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

########## wireless info END ############



```

---

### Post by wildmanne39 on 2015-03-18
Change IEEE 802.11bgn to IEEE 802.11bg in your router and set your channel on 6 or one for know because several people are using channel 11 already but nly on is using 1 and no one is using 6.
Reboot computer.
Thanks

---

### Post by sam_baker2 on 2015-03-18
I only have these choices in my (linksys) router:
disabled, mixed, B only, G only.

The channel was originally set to 1, but I changed it to 11.
I will change it to 6
I looked at the text list and it also looks like someone is using channel 1

---

### Post by wildmanne39 on 2015-03-18
I have to go to bed for tonight, I have to get up early and work late.

---

### Post by sam_baker2 on 2015-03-18
me too, I will check it out tomorrow when I 
have more time to let it run

thanks

---

### Post by sam_baker2 on 2015-03-21
I got my networking to work now without intermittently disconnecting after a few minutes.
 For the record, I have  rtl8192ce driver in my laptop.

  I went to this forum link:
[http://ubuntuforums.org/showthread.php?t=2262957](http://ubuntuforums.org/showthread.php?t=2262957)
and used Pilot6's solution. Downloaded the new driver, compiled
it, and so far it is working ok.

---

