---
title: "My wifi not detected"
date: 2014-08-14
forum: Networking &amp; Wireless
---

### Post by simfomet on 2014-08-14
Hi, recently I installed lubuntu in my netbook with Broadcom BCM4313.When I want to connect to my wifi it detects a lot of wifis but not mine. I'm close to the router and another computers are perfectly connected. What's happening?
Im not an expert on linux...

---

### Post by chili555 on 2014-08-14
Which (probably wrong) driver is in use? Please open a terminal Ctrl+Alt+t and run and post:```
lsmod | grep -e wl -e brcmsmac
```Thanks.

---

### Post by simfomet on 2014-08-14
Thank for the answer. This is the result.

brcmsmac              529837  0 
cordic                 12518  1 brcmsmac
brcmutil               15066  1 brcmsmac
mac80211              546051  2 b43,brcmsmac
cfg80211              409394  3 b43,brcmsmac,mac80211
bcma                   42043  3 b43,brcmsmac

---

### Post by chili555 on 2014-08-14
Hmmm! The correct driver, actually. Does it see your router here?```
sudo iwlist wlan0 scan
```You needn't post all the results, just tell us if it's there.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, I have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. After making these changes, reboot the router.

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

We might also try blacklisting b43 which isn't helpful:```
sudo -i
echo "blacklist b43"  >>  /etc/modprobe.d/blacklist.conf
modprobe -r b43
exit
```Any change?

---

### Post by simfomet on 2014-08-14
The answer for sudo iwlist wlan0 scan is wlan0     Interface doesn't support scanning : Network is down, if I try wlan1 appears    Interface doesn't support scanning.

I use wpa2-psk AES
And if I try sudo iw reg get appears command not found

---

### Post by chili555 on 2014-08-14
> And if I try sudo iw reg get appears command not foundWow! What Ubuntu version do you have?```
lsb_release -d
```May I see:```
iwconfig
```

---

### Post by simfomet on 2014-08-15
I have Ubuntu 14.04.1 LTS and to iwconfig appears

 ```
wlan0     IEEE 802.11bgn  ESSID:<snip>
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:15:F2:F0:2A:F9   
          Bit Rate=48 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=62/70  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:34   Missed beacon:0
```

lo        no wireless extensions.

eth0      no wireless extensions.


But there's one reason for it. I have two routers (low quality I guess), Comtrend AR5387un and an older one Comtrend 536HG+. I always have better results with 536. I tried to connect to 536 and all is perfect. I'm posting with this wifi connection but as I said when I try to detect the other one show me a lot of wifis but not mine.

---

### Post by asellus2 on 2014-08-17
Last time I worked with lubuntu I use some routers (from huawei) and my laptor couldn't detect it. After that I tried several routers from dlink, zyxel and amplifiers from [http://www.wilsonamplifiers.com/](http://www.wilsonamplifiers.com/) and only with dlink it works OK. Amplifier didn't influnce network performance. Zyxel router wasn't detected at all...

---

### Post by varunendra on 2014-08-17
**@simfomet,**

Did you blacklist "b43"? If the problem still exists, Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

**@asellus2,**
First of all, Welcome to the forums!

If you need support for what you described above, I suggest you start your own thread with the description of the problem, and the wireless_script report I asked above. Feel free to post the link of your thread here so we can follow.

Wireless problems can be very subjective and may have different reasons, different solutions even if the symptoms appear to be the same.

---

### Post by simfomet on 2014-08-22
> **varunendra said:**
> **@simfomet,**

Did you blacklist "b43"? If the problem still exists, Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.


I don't know exactly what do you mean with *Did you blacklist b43*, sorry. This is the result of the wireless_script with the netbook connected to 536HG+ router

```

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

belen-Compaq-Mini-CQ10-500 3.13.0-34-generic i686,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Atom(TM) CPU N455   @ 1.66GHz
Memory : 990 MB
Uptime : 11:58:21 up 4 min,  2 users,  load average: 0,38, 0,48, 0,23


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 04)
    Subsystem: Hewlett-Packard Company Device [103c:148a]
    Kernel driver in use: r8169
--
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:145c]
    Kernel driver in use: bcma-pci-bridge


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 001 Device 002: ID 04f2:b1eb Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:"Metal_up_your_ass"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC C-01 Metal_up_your_ass>   
          Bit Rate=48 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-39 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:49   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface           Soft blocked  Hard blocked
0: hp-wifi: Wireless LAN      no            no
1: phy0: Wireless LAN         no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

brcmsmac              529837  0 
cordic                 12518  1 brcmsmac
brcmutil               15066  1 brcmsmac
b43                   356470  0 
mac80211              546051  2 b43,brcmsmac
cfg80211              409394  3 b43,brcmsmac,mac80211
ssb                    51854  1 b43
hp_wmi                 13702  0 
sparse_keymap          13708  1 hp_wmi
bcma                   42043  3 b43,brcmsmac
wmi                    18673  1 hp_wmi


module parameters ~~~~~~~~~~~~~~~~~~

b43          (10): allhwsupport=0 | bad_frames_preempt=0 | btcoex=1 | hwpctl=0 | hwtkip=0 | nohwcrypt=0 | pio=0 | qos=1 | verbose=2
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
============================o=============o==========o=============o=========o===========o==============o===========
 Interface & ID             | Type        | Driver   | State       | Default | Speed     | Support      | HW Addr   
============================o=============o==========o=============o=========o===========o==============o===========
 wlan0  [Metal_up_your_ass] | 802.11 WiFi | brcmsmac | connected   | yes     | 48 Mb/s   | WEP/WPA/WPA2 | <MAC wlan0>

    Orange-6F38:     Infra, <MAC C-12 Orange-6F38>, Freq 2457 MHz, Rate 54 Mb/s, Strength 52 WPA WPA2
    JAZZTEL_2085:    Infra, <MAC C-02 JAZZTEL_2085>, Freq 2412 MHz, Rate 54 Mb/s, Strength 50 WPA
    Orange-D98E:     Infra, <MAC C-16 Orange-D98E>, Freq 2417 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    JAZZTEL_23D7:    Infra, <MAC C-05 JAZZTEL_23D7>, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA
    JAZZTEL_BD7A:    Infra, <MAC C-03 JAZZTEL_BD7A>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA
    WLAN_B0F5:       Infra, <MAC C-07 WLAN_B0F5>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA
    vodafone76C0:    Infra, <MAC C-13 vodafone76C0>, Freq 2452 MHz, Rate 54 Mb/s, Strength 30 WPA
    JAZZTEL_A609:    Infra, <MAC C-09 JAZZTEL_A609>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    vodafoneEAD4:    Infra, <MAC C-06 vodafoneEAD4>, Freq 2422 MHz, Rate 54 Mb/s, Strength 24 WPA
    JAZZTEL_3429:    Infra, <MAC C-10 JAZZTEL_3429>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA
    *Metal_up_your_ass: Infra, <MAC C-01 Metal_up_your_ass>, Freq 2462 MHz, Rate 54 Mb/s, Strength 83 WPA2
    Galy1978:        Infra, <MAC C-08 Galy1978>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA
    WLAN_9E40:       Infra, <MAC C-04 WLAN_9E40>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA
    JAZZTEL_36:      Infra, <MAC C-17 JAZZTEL_36>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WEP
    WLAN_6A:         Infra, <MAC C-14 WLAN_6A>, Freq 2452 MHz, Rate 54 Mb/s, Strength 27 WEP
    iMolle.com_397E78: Infra, <MAC C-15 iMolle.com_397E78>, Freq 2452 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    WLAN_125D:       Infra, <MAC C-11 WLAN_125D>, Freq 2437 MHz, Rate 54 Mb/s, Strength 17 WPA

    Address:         192.168.1.4
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             192.168.1.1
----------------------------+-------------+----------+-------------+---------+-----------+--------------+-----------
 eth0                       | Wired       | r8169    | unavailable | no      |           |              | <MAC eth0>
----------------------------+-------------+----------+-------------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~

Metal_up_your_ass    : ssid=Metal_up_your_ass | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 1.074/1.086/1.098/0.012 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.068/0.068/0.069/0.008 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "ca_ES.UTF-8")


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     11 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 11 (2.462 GHz)

          Current Frequency=2.462 GHz (Channel 11)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 Metal_up_your_ass>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-36 dBm  
                    Encryption key:on
                    ESSID:"Metal_up_your_ass"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000001ca05fd31
                    Extra: Last beacon: 32ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 JAZZTEL_2085>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"JAZZTEL_2085"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000359583888
                    Extra: Last beacon: 32ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 JAZZTEL_BD7A>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"JAZZTEL_BD7A"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004c89391e24
                    Extra: Last beacon: 32ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC C-04 WLAN_9E40>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"WLAN_9E40"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001f2f091de83
                    Extra: Last beacon: 32ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC C-05 JAZZTEL_23D7>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"JAZZTEL_23D7"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000005ce2d5639
                    Extra: Last beacon: 180ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC C-06 vodafoneEAD4>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"vodafoneEAD4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000c1054b539
                    Extra: Last beacon: 18244ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC C-07 WLAN_B0F5>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"WLAN_B0F5"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000003a0c5e616a1
                    Extra: Last beacon: 32ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC C-08 Galy1978>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"Galy1978"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000028e80dfe24c
                    Extra: Last beacon: 32ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC C-09 JAZZTEL_A609>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"JAZZTEL_A609"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000014359d306c
                    Extra: Last beacon: 32ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC C-10 JAZZTEL_3429>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"JAZZTEL_3429"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000363b0645e2d
                    Extra: Last beacon: 32ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC C-11 WLAN_125D>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"WLAN_125D"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000016b42ba191
                    Extra: Last beacon: 19136ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC C-12 Orange-6F38>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"Orange-6F38"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000003bb021c92
                    Extra: Last beacon: 32ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC C-13 vodafone76C0>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"vodafone76C0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001ea5b2f9057
                    Extra: Last beacon: 32ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC C-14 WLAN_6A>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"WLAN_6A"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000790d11c6
                    Extra: Last beacon: 18592ms ago
          Cell 15 - Address: <MAC C-15 iMolle.com_397E78>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"iMolle.com_397E78"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000035053f91d7
                    Extra: Last beacon: 652ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 16 - Address: <MAC C-16 Orange-D98E>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"Orange-D98E"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000a75dcd5002
                    Extra: Last beacon: 1596ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 17 - Address: <MAC C-17 JAZZTEL_36>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"JAZZTEL_36"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004b4f475186
                    Extra: Last beacon: 156ms ago
          Cell 18 - Address: <MAC C-18 MOVISTAR_E138>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"MOVISTAR_E138"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000796546d17c
                    Extra: Last beacon: 132ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/libpisock9.conf]
blacklist visor


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[brcmsmac]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
firmware:       brcm/bcm43xx_hdr-0.fw
firmware:       brcm/bcm43xx-0.fw
srcversion:     43D6897F7EB716081DF69BE
depends:        bcma,mac80211,brcmutil,cfg80211,cordic

[cordic]
filename:       /lib/modules/3.13.0-34-generic/kernel/lib/cordic.ko
srcversion:     810E6E73D80DD7F75AC5B42
depends:        

[brcmutil]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
srcversion:     E81EE4CBB6A7A689150D93D
depends:        

[b43]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
srcversion:     42BAE2DB9BADE3E7ECA2CC0
depends:        bcma,ssb,mac80211,cfg80211
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)

[mac80211]
filename:       /lib/modules/3.13.0-34-generic/kernel/net/mac80211/mac80211.ko
srcversion:     8ADA881D348148A3358334C
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-34-generic/kernel/net/wireless/cfg80211.ko
srcversion:     E786D076B61F97809B04B64
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ssb]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/ssb/ssb.ko
srcversion:     3DE188310F77C566C2E8CB3
depends:        

[hp_wmi]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/platform/x86/hp-wmi.ko
srcversion:     22DCD1B7DA09178B45B1068
depends:        wmi,sparse-keymap

[bcma]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/bcma/bcma.ko
srcversion:     E41B811D88783DD5BC38565
depends:        

[wmi]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4727 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-34-generic root=UUID=2dd40ec9-591e-44bf-8607-5ef9d183927c ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    1.927898] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.928748] audit: initializing netlink socket (disabled)
[    2.573622] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.574439] r8169 0000:01:00.0 (unregistered net_device): unknown MAC, using family default
[   11.657575] bcma: bus0: Found chip with id 0x4313, rev 0x01 and package 0x08
[   11.657627] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x24, class 0x0)
[   11.657662] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x18, class 0x0)
[   11.657721] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x11, class 0x0)
[   11.662871] wmi: Mapper loaded
[   11.670538] bcma: bus0: Bus registered
[   14.196802] Support for cores revisions 0x17 and 0x18 disabled by module param allhwsupport=0. Try b43.allhwsupport=1
[   14.197094] b43: probe of bcma0:0 failed with error -524
[   14.886294] brcmsmac bcma0:0: mfg 4bf core 812 rev 24 class 0 irq 17
[   14.967110] ieee80211 phy0: registered radio enabled led device: brcmsmac-phy0:radio gpio: 243
[   15.770082] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   20.254779] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   20.254798] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[   20.255025] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.255880] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.614180] wlan0: authenticate with <MAC C-01 Metal_up_your_ass>
[   21.620069] wlan0: send auth to <MAC C-01 Metal_up_your_ass> (try 1/3)
[   21.642128] wlan0: authenticated
[   21.642620] brcmsmac bcma0:0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   21.642632] brcmsmac bcma0:0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   21.644482] wlan0: associate with <MAC C-01 Metal_up_your_ass> (try 1/3)
[   21.653560] wlan0: RX AssocResp from <MAC C-01 Metal_up_your_ass> (capab=0x411 status=0 aid=2)
[   21.654861] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[   21.654874] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   21.654901] wlan0: associated
[   21.654969] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   22.836784] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)

    ======== Done ========


```

---

### Post by varunendra on 2014-08-22
> **simfomet said:**
> I don't know exactly what do you mean with *Did you blacklist b43*, sorry.
Something that dr. chili555 earlier told you to do -
> **chili555 said:**
> We might also try blacklisting b43 which isn't helpful:```
sudo -i
echo "blacklist b43"  >>  /etc/modprobe.d/blacklist.conf
modprobe -r b43
exit
```
..and what you evidently haven't done -
> **simfomet said:**
> ```
lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
....
**[COLOR="#FF0000"]b43[/COLOR]**                   356470  0 
mac80211              546051  2 **[COLOR="#FF0000"]b43[/COLOR]**,brcmsmac
cfg80211              409394  3 **[COLOR="#FF0000"]b43[/COLOR]**,brcmsmac,mac80211
....
bcma                   42043  3 **[COLOR="#FF0000"]b43[/COLOR]**,brcmsmac
```
..and no blacklist entry for "b43" captured by the script, means it doesn't exist.

Please do that now, and hopefully that would be all you need.

---

### Post by simfomet on 2014-08-25
No good results. I,m connected with cable to the router that I have the problem.I tried everything that chili555 mentioned again and:
sudo iwlist wlan0 scan
```
wlan0     Scan completed :
          Cell 01 - Address: 38:72:C0:B2:20:85
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"JAZZTEL_2085"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000005e0d176e9
                    Extra: Last beacon: 24ms ago
                    IE: Unknown: 000C4A415A5A54454C5F32303835
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601000400000000000000000000000000000000000000
                    IE: Unknown: DD090010180201F02C0000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: 38:72:C0:ED:BD:7A
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"JAZZTEL_BD7A"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000041e0f08a7d
                    Extra: Last beacon: 24ms ago
                    IE: Unknown: 000C4A415A5A54454C5F42443741
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601000400000000000000000000000000000000000000
                    IE: Unknown: DD090010180203F02C0000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: DC:0B:1A:9C:B0:F6
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"WLAN_B0F5"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000003e6b070557f
                    Extra: Last beacon: 24ms ago
                    IE: Unknown: 0009574C414E5F42304635
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000400000000000000000000000000000000000000
                    IE: Unknown: DD7B0050F204104A00011010440001021041000100103B0001031047001064CC8C770540FC4A833DCAA3701B589F1021000842726F6164636F6D1023000842726F6164636F6D1024000631323334353610420004313233341054000800060050F20400011011000A42726F6164636F6D4150100800020084103C000101
                    IE: Unknown: DD090010180201F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 04 - Address: 6A:E8:7B:1B:76:C0
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"vodafone76C0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000230447dbf3a
                    Extra: Last beacon: 188ms ago
                    IE: Unknown: 000C766F6461666F6E6537364330
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030109
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A8E1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1609000600000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DDA20050F204104A0001101044000102103B00010310470010BC329E001DD811B286016AE87B1B76C01021001D48756177656920546563686E6F6C6F6769657320436F2E2C204C74642E1023001C48756177656920576972656C6573732041636365737320506F696E74102400065254323836301042000831323334353637381054000800060050F204000110110009487561776569415053100800020084103C000100
                    IE: Unknown: 0B05020046127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706455320010D10
                    IE: Unknown: DD1E00904C338E1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3409000600000000000000000000000000000000000000
          Cell 05 - Address: 62:A8:E4:CB:A8:24
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"Galy1978"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002d46b4ec939
                    Extra: Last beacon: 24ms ago
                    IE: Unknown: 000847616C7931393738
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A8E1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D160B070600000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0504001D127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706455320010D10
                    IE: Unknown: DD1E00904C338E1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C340B070600000000000000000000000000000000000000
          Cell 06 - Address: 38:72:C0:C4:34:29
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"JAZZTEL_3429"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000003a999f23183
                    Extra: Last beacon: 19316ms ago
                    IE: Unknown: 000C4A415A5A54454C5F33343239
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000400000000000000000000000000000000000000
                    IE: Unknown: DD090010180202F02C0000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 07 - Address: F8:8B:86:A6:E1:41
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"MOVISTAR_E138"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000bf4eb3717c
                    Extra: Last beacon: 19124ms ago
                    IE: Unknown: 000D4D4F5649535441525F45313338
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6C1817FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B000000000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336C1817FFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B000000000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020160
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 08 - Address: 30:39:F2:85:12:5E
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"WLAN_125D"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005c9fc7a19b
                    Extra: Last beacon: 368ms ago
                    IE: Unknown: 0009574C414E5F31323544
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000400000000000000000000000000000000000000
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180202F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 09 - Address: 40:4A:03:DB:73:4E
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"WLAN_98"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000009780ab872
```

sudo iw reg get

```
command not found
```

gksudo gedit /etc/default/crda and nothing happens and I have gedit

In 
```
sudo -i
echo "blacklist b43"  >>  /etc/modprobe.d/blacklist.conf
modprobe -r b43
exit
```
nothing happens and my wifi is not detected as usual

---

### Post by varunendra on 2014-08-25
Do you not see your access-point in the "iwlist scan" results above? By the way, none of the ones listed have the recommended WPA2-AES encryption. Strange enough, almost all of them have WPA(1)-AES, which is a non-standard combination, and most probably not mutually compatible as well. It was WPA2 that started supporting AES, WPA(1) didn't originally have that capability.

Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

### Post by simfomet on 2014-08-26
> **varunendra said:**
> Do you not see your access-point in the "iwlist scan" results above? By the way, none of the ones listed have the recommended WPA2-AES encryption. Strange enough, almost all of them have WPA(1)-AES, which is a non-standard combination, and most probably not mutually compatible as well. It was WPA2 that started supporting AES, WPA(1) didn't originally have that capability.

Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

First of all thanks for your help and sorry about my english, it's not my mother tongue. As you will see on my iwlist scan don-t recognize my wifi called In_Metal_We_Trust

Yes I use AES,this is an image of the settings in my router
[[IMG]http://s23.postimg.org/ndo0f76mv/Wireless_advanced.jpg[/IMG]]("http://postimg.org/image/ndo0f76mv/")

[[IMG]http://s27.postimg.org/vum05g7xr/Wireless_security.jpg[/IMG]]("http://postimg.org/image/vum05g7xr/")

And this is the result of the script

```
======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

belen-Compaq-Mini-CQ10-500 3.13.0-34-generic i686,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Atom(TM) CPU N455   @ 1.66GHz
Memory : 990 MB
Uptime : 17:56:25 up 7 min,  2 users,  load average: 0,76, 0,68, 0,37


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 04)
    Subsystem: Hewlett-Packard Company Device [103c:148a]
    Kernel driver in use: r8169
--
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:145c]
    Kernel driver in use: bcma-pci-bridge


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 001 Device 003: ID 04f2:b1eb Chicony Electronics Co., Ltd 
Bus 001 Device 004: ID 1977:0824 T-Logic 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0458:0036 KYE Systems Corp. (Mouse Systems) Pocket Mouse LE
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface           Soft blocked  Hard blocked
0: hp-wifi: Wireless LAN      no            no
1: phy0: Wireless LAN         no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

brcmsmac              529837  0 
cordic                 12518  1 brcmsmac
brcmutil               15066  1 brcmsmac
mac80211              546051  1 brcmsmac
hp_wmi                 13702  0 
cfg80211              409394  2 brcmsmac,mac80211
sparse_keymap          13708  1 hp_wmi
bcma                   42043  2 brcmsmac
wmi                    18673  1 hp_wmi


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
============================o=============o==========o==============o=========o===========o==============o===========
 Interface & ID             | Type        | Driver   | State        | Default | Speed     | Support      | HW Addr   
============================o=============o==========o==============o=========o===========o==============o===========
 wlan0                      | 802.11 WiFi | brcmsmac | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>

    JAZZTEL_2085:    Infra, <MAC C-01 JAZZTEL_2085>, Freq 2412 MHz, Rate 54 Mb/s, Strength 60 WPA
    Galy1978:        Infra, <MAC C-04 Galy1978>, Freq 2462 MHz, Rate 54 Mb/s, Strength 57 WPA
    WLAN_B0F5:       Infra, <MAC C-02 WLAN_B0F5>, Freq 2437 MHz, Rate 54 Mb/s, Strength 54 WPA
    vodafone76C0:    Infra, <MAC C-03 vodafone76C0>, Freq 2452 MHz, Rate 54 Mb/s, Strength 37 WPA
    WLAN_9E40:       Infra, <MAC C-NA WLAN_9E40 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA
    iMolle.com_397E78: Infra, <MAC C-NA iMolle.com_397E78 1>, Freq 2452 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    WLAN_6A:         Infra, <MAC C-NA WLAN_6A 1>, Freq 2452 MHz, Rate 54 Mb/s, Strength 20 WEP
    Orange-D98E:     Infra, <MAC C-NA Orange-D98E 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    JAZZTEL_3429:    Infra, <MAC C-NA JAZZTEL_3429 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 15 WPA
    MOVISTAR_E138:   Infra, <MAC C-NA MOVISTAR_E138 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA
    WLAN_96A1:       Infra, <MAC C-NA WLAN_96A1 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 17 WPA
    JAZZTEL_BD7A:    Infra, <MAC C-NA JAZZTEL_BD7A 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA
    WLAN_09:         Infra, <MAC C-NA WLAN_09 1>, Freq 2442 MHz, Rate 54 Mb/s, Strength 17 WEP
    JAZZTEL_23D7:    Infra, <MAC C-06 JAZZTEL_23D7>, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA
    WLAN_98:         Infra, <MAC C-NA WLAN_98 1>, Freq 2452 MHz, Rate 54 Mb/s, Strength 29 WEP
----------------------------+-------------+----------+--------------+---------+-----------+--------------+-----------
 eth0  [Wired connection 1] | Wired       | r8169    | connected    | yes     | 100 Mb/s  |              | <MAC eth0>

    Address:         192.168.1.4
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             87.216.1.65
    DNS:             87.216.1.66
----------------------------+-------------+----------+--------------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~

Metal_up_your_ass    : ssid=Metal_up_your_ass | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1
search Home


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.427/0.453/0.479/0.026 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.067/0.070/0.073/0.003 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "ca_ES.UTF-8")


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     11 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 11 (2.462 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 JAZZTEL_2085>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"JAZZTEL_2085"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000156e066fd2
                    Extra: Last beacon: 28ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 WLAN_B0F5>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"WLAN_B0F5"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000003f63da4aefc
                    Extra: Last beacon: 28ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 vodafone76C0>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"vodafone76C0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000023fd2d0ec12
                    Extra: Last beacon: 28ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC C-04 Galy1978>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"Galy1978"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002e3f87ef510
                    Extra: Last beacon: 28ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC C-05 Orange-6F38>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"Orange-6F38"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000619b6c007
                    Extra: Last beacon: 544ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC C-06 JAZZTEL_23D7>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"JAZZTEL_23D7"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000aced56183
                    Extra: Last beacon: 84ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist b43
blacklist b43

[/etc/modprobe.d/libpisock9.conf]
blacklist visor


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[brcmsmac]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
firmware:       brcm/bcm43xx_hdr-0.fw
firmware:       brcm/bcm43xx-0.fw
srcversion:     43D6897F7EB716081DF69BE
depends:        bcma,mac80211,brcmutil,cfg80211,cordic

[cordic]
filename:       /lib/modules/3.13.0-34-generic/kernel/lib/cordic.ko
srcversion:     810E6E73D80DD7F75AC5B42
depends:        

[brcmutil]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
srcversion:     E81EE4CBB6A7A689150D93D
depends:        

[mac80211]
filename:       /lib/modules/3.13.0-34-generic/kernel/net/mac80211/mac80211.ko
srcversion:     8ADA881D348148A3358334C
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[hp_wmi]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/platform/x86/hp-wmi.ko
srcversion:     22DCD1B7DA09178B45B1068
depends:        wmi,sparse-keymap

[cfg80211]
filename:       /lib/modules/3.13.0-34-generic/kernel/net/wireless/cfg80211.ko
srcversion:     E786D076B61F97809B04B64
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[bcma]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/bcma/bcma.ko
srcversion:     E41B811D88783DD5BC38565
depends:        

[wmi]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4727 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-34-generic root=UUID=2dd40ec9-591e-44bf-8607-5ef9d183927c ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    1.411637] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.412500] audit: initializing netlink socket (disabled)
[    2.053161] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.053472] r8169 0000:01:00.0 (unregistered net_device): unknown MAC, using family default
[   13.158298] wmi: Mapper loaded
[   13.356746] bcma: bus0: Found chip with id 0x4313, rev 0x01 and package 0x08
[   13.356793] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x24, class 0x0)
[   13.356826] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x18, class 0x0)
[   13.356880] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x11, class 0x0)
[   13.410117] bcma: bus0: Bus registered
[   14.852199] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.746215] brcmsmac bcma0:0: mfg 4bf core 812 rev 24 class 0 irq 17
[   17.044582] ieee80211 phy0: registered radio enabled led device: brcmsmac-phy0:radio gpio: 243
[   19.362448] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   19.362473] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[   19.362722] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.363721] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

    ======== Done ========


```

---

### Post by varunendra on 2014-08-27
The **channel** in your first screenshot is set to '**13**', while your card seems to support only channels 1 to 11. Please change the channel in the router/access-point to **1 or 11** > save > reboot the router > delete the previously saved connection profile from Network Manager in Ubuntu > reboot the laptop as well > see if it can detect your access-point and connect to it.

---

### Post by simfomet on 2014-08-27
It's working!!!!!!!! I thought it could be controllers thing or whatever and it have been just changing wifi channel;);)

Thank you!!!!!

---

### Post by varunendra on 2014-08-28
Congrats!

Just remember NOT to install the "STA" driver (or "wl", package name "bcmwl-kernel-source") that the updates/Additional-Drivers program may offer - that is not a good driver for your card. In short, you need _nothing_ to make your card work. It is supported natively, and will work out-of-box with Ubuntu.

---

