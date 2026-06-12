---
title: "WPA2 with an atheros wireless card (madwifi) in Ubuntu 7.10 - First, is it possible?"
date: 2008-01-14
forum: Networking &amp; Wireless
---

### Post by Milkensen on 2008-01-14
Prior to everything I have to say that wireless actually works, but not in the way I'd like to.
Previous to try to follow step by step the sticky how2 about this issue, I'd like to know if it is possible WPA2 with PSK with the madwifi driver in a Ubuntu system, that is, if someone have got it.
If not, I'd like to know, then I'd reconfigure my router to another way of encryption that be well-known to work.. 

Please, can anyone confirm that (starting) point?

---

### Post by zipperback on 2008-01-14
> **Milkensen said:**
> Prior to everything I have to say that wireless actually works, but not in the way I'd like to.
Previous to try to follow step by step the sticky how2 about this issue, I'd like to know if it is possible WPA2 with PSK with the madwifi driver in a Ubuntu system, that is, if someone have got it.
If not, I'd like to know, then I'd reconfigure my router to another way of encryption that be well-known to work.. 

Please, can anyone confirm that (starting) point?



Install Wicd.
[http://wicd.sourceforge.net](http://wicd.sourceforge.net)

I have an Acer Aspire 5050-3371 with the Atheros chipset.
I am using the ndiswrapper with the XP driver and wicd for my network management.
There is an option to use several different kinds of encryption methods.


I've included a screenshot.

- zipperback
:popcorn:

---

### Post by kevdog on 2008-01-14
Yes it should work,  try the thread connecting at the command line in my signature.  This should allow you to perform some tests to see if wpa2 is going to work for you.

---

### Post by Milkensen on 2008-01-17
Thank you both men, two days later, but actually I'm so busy these days, far away from my laptop, that I've just seen your replies a few minutes ago. 
Weeeeeeeeeeeeeeeeeeeeeeeell... I'll try first the easy way... wicd. Then we'll see...

Anyhow, thank you very much!! :-)

Daniel

---

### Post by Milkensen on 2008-01-22
Ops...!, I'm going on with the same or similar issue. I'd would appreciate any help very much, men, because I'm in a whole mess since the last few days...

I first installed wicd and actually things didn't work. It detected all networks indeed, and it could connect to my own router, at least it said that... but also said 0% signal, and actually no network.  
My router is configured for WPA2 with PSK, and I'd like it worked into that mannersince with another Linux distro it was able to do it.
Then, I removed all the wicd things, its own repo, etc. 

Problems continued when I realized that even into this new situation, my laptop was able to connect via wireless to any network over there, in particular to that one that was making me mad!... a open network, the only one in my neighbourhood that wasn't encrypted or password protected. My wireless card was workin automatically in the roaming mode, and despite I unchecked again and again that possibility as root administrator, it returned to that status without asking... bad :-(  
Is this last maybe a bug in Ubuntu?

The funny thing would come later, when I decided to remove _all the packages related with the wireless mode_  in the laptop: wpasupplicant, wireless-tools, madwifi-tools, linux-restricted-modules  (where is the madwifi driver between others), xsupplicant, networkmanager packages, hostapd, and other less importants. And... incredible!!! Reboot and the laptop still continued being able to connect via wireless to the damn open network that, since several days ago I hated deeply. 
How it could be possible? I thought that maybe the config files still remained there, and also I clean the cache of the donwload packages with the package manager. 
Then, eventually, no wireless network was detected any more, uf!. 

After that, I started installing carefully some essential wireless packages, like networkmanager madwifi, etc., avoiding to install everything related to, in prevention that they could interfere between them. Final result: I started to have new problems, now with the WIRED connection: for some reason the laptop was unable to connect to the router in spite of there was a valid configuration defined permanently as root admin. It was unbelievable for me! 
Then, after editing manually the file /etc/network/interfaces, etc. things became again acceptable, but I don't know even now, everytime I boot the laptop I must to do a sudo su first, and then a /etc/init.d/networking restart, if I want wired connection working OK, I do not understand it, but...
The config file, and the network is correctly configured, so...?

After this, I tried to follow step by step one of the how2 for WPA2 placed in Ubuntuforums, but  I am unable to do work it, in spite of following succesfully those steps.
Should I to resing? Hard to accept it..

Please, I'm claiming for help almost desperately..:-)

========================================================================
DATA & Info: 

What I have: 
Thinkpad T42 laptop, wireless card AR5212/AR5213, atheros chip. (Wired ethernet card, a Gigabit ethernet).
No DHCP. Static IP 192.168.1.x Router with gateway IP 192.168.1.1 configured. This router Comtrend ADSL2+ wireless. Configured for accepting ethernet connections from some static IP on a LAN, and configured its wireless for accept connections with WPA2,  PSK encryption.

What I'm sure: 
The wireless card in the laptop works, since it's able to detect all the networks around here, including my own router, of course. 
It is able to connect in roaming mode, it does it if the wireless is active, and it's without any notification..., to the only one open network that is in my neighbourhood.

What I'm unable: 
Connect the laptop to the router through WPA2 encryption and that it would really work. 

-------------------------
Some outputs:
```

# lshw -C network

  *-network:0             
       description: Ethernet interface
       product: 82540EP Gigabit Ethernet Controller (Mobile)
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 03
       serial: 00:0d:60:f9:bb:90
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI duplex=full firmware=N/A ip=192.168.1.31 latency=64 link=yes mingnt=255 module=e1000 multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Wireless interface
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications, Inc.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: wifi0
       version: 01
       serial: 00:0e:9b:1b:0d:1a
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.3.2) latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
```

My own network: pn366a
The _hated_  opened network: casa
```

iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:14:7F:AC:AC:57
                    ESSID:"SpeedTouchD20A8B"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=3/70  Signal level=-92 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:wme_ie=dd180050f2020101080003a4000027a4000042435e0062322f00
          Cell 02 - Address: 00:01:38:79:5C:A9
                    ESSID:"WLAN_C4"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=8/70  Signal level=-87 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:wme_ie=dd180050f2020101000003a4000027a4000042435e0062322f00
          Cell 03 - Address: 00:01:38:79:25:F5
                    ESSID:"WLAN_FB"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=7/70  Signal level=-88 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:wme_ie=dd070050f202000100
          Cell 04 - Address: 00:03:C9:A4:75:01
                    ESSID:"Comtrend"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=8/70  Signal level=-87 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 05 - Address: 00:03:C9:D2:12:CA
                    ESSID:"pn366a"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=54/70  Signal level=-41 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : none TKIP
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
          Cell 06 - Address: 00:1A:2B:00:C7:F7
                    ESSID:"casa"
                    Mode:Master
                    Frequency:2.422 GHz (Channel 3)
                    Quality=16/70  Signal level=-79 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 07 - Address: 00:01:38:97:21:BE
                    ESSID:"WLAN_A0"
                    Mode:Master
                    Frequency:2.457 GHz (Channel 10)
                    Quality=12/70  Signal level=-83 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:wme_ie=dd180050f2020101000003a4000027a4000042435e0062322f00
          Cell 08 - Address: 00:16:38:89:3B:5E
                    ESSID:"WLAN_5F"
                    Mode:Master
                    Frequency:2.467 GHz (Channel 12)
                    Quality=3/70  Signal level=-92 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 09 - Address: 00:60:B3:FB:47:5D
                    ESSID:"WLAN_86"
                    Mode:Master
                    Frequency:2.452 GHz (Channel 9)
                    Quality=16/70  Signal level=-79 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
          Cell 10 - Address: 00:16:38:C4:7E:DF
                    ESSID:"Jazztel Wireless"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=7/70  Signal level=-88 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 11 - Address: 00:60:B3:F3:E2:96
                    ESSID:"WLAN_C3"
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Quality=11/70  Signal level=-84 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
          Cell 12 - Address: 00:19:CB:38:DD:22
                    ESSID:"WLAN_4B"
                    Mode:Master
                    Frequency:2.452 GHz (Channel 9)
                    Quality=8/70  Signal level=-87 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 13 - Address: 00:60:B3:D5:CB:82
                    ESSID:"WLAN_09"
                    Mode:Master
                    Frequency:2.452 GHz (Channel 9)
                    Quality=16/70  Signal level=-79 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
          Cell 14 - Address: 00:01:38:A2:5A:DF
                    ESSID:"WLAN_D8"
                    Mode:Master
                    Frequency:2.467 GHz (Channel 12)
                    Quality=163/70  Signal level=-188 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:wme_ie=dd070050f202000100
          Cell 15 - Address: 00:13:49:4B:21:62
                    ESSID:"TYC"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=5/70  Signal level=-90 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
          Cell 16 - Address: 00:11:F5:14:9C:BB
                    ESSID:"SpeedTouch76FDA0"
                    Mode:Master
                    Frequency:2.452 GHz (Channel 9)
                    Quality=25/70  Signal level=-70 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
          Cell 17 - Address: 00:17:3F:61:FF:99
                    ESSID:"Caralladas"
                    Mode:Master
                    Frequency:2.447 GHz (Channel 8)
                    Quality=6/70  Signal level=-89 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
          Cell 18 - Address: 00:11:F5:14:A1:8F
                    ESSID:"SpeedTouchE42F97"
                    Mode:Master
                    Frequency:2.452 GHz (Channel 9)
                    Quality=2/70  Signal level=-93 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
          Cell 19 - Address: 00:A0:C5:9C:D1:B1
                    ESSID:"Jesus"
                    Mode:Master
                    Frequency:2.457 GHz (Channel 10)
                    Quality=10/70  Signal level=-85 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
```


```
# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.422 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:17 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=-91 dBm  Noise level=-91 dBm
          Rx invalid nwid:182418  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

--------------

Could someone lead me step by step to configure from zero a WPA2 connection, please?

Thank you in advance,

Daniel Milkensen

---

### Post by Milkensen on 2008-01-24
I give up.
Concerning to me, actually it is impossible to get a wireless connection with Ubuntu 7.10 through WPA2 with PSK. 

I've followed two or more step-by-step howto's fixed here, in the Ubuntuforums, and nothing...

My /etc/network/interfaces file looks like to this:
```
auto lo
iface lo inet loopback


auto eth0
iface eth0 inet static
address 192.168.1.31
netmask 255.255.255.0
gateway 192.168.1.1


auto ath0
iface ath0 inet static
address 192.168.1.31
gateway 192.168.1.1
dns-nameservers 62.14.2.1 
netmask 255.255.255.0
wpa-driver madwifi
wpa-ssid pn366a
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk 69883c023e8013886c79241afc7add294fabf7b28e47ca404c21a6fa7250aefa

```
I've tried some little variations over it, but unfortunately without results. 

Also, I created the /etc/wpa_supplicant.conf file, there I've tried with this config:
```

ap_scan=1
ctrl_interface=/var/run/wpa_supplicant

network={
	ssid="pn366a"
	scan_ssid=0
	proto=RSN
	key_mgmt=WPA-PSK
	psk="69883c023e8013886c79241afc7add294fabf7b28e47ca404c21a6fa7250aefa"
	pairwise=CCMP
	group=CCMP

}

```

Over this, I've tried commenting out the first line (ap_scan=1), with the same results: zero.

Of course.., restarting the network, and rebooting the system were done, but that didn't solve anything.

Anyone could suggest me to try something different maybe?

---

### Post by kevdog on 2008-01-24
Those threads that you have read are accurate, however the interfaces file is used by network manager, whereas the wpa_supplicant.conf file is only used if it is called either from the command line or from the interfaces file itself.  By itself it does nothing.

Again I would at first try connecting from the command line.  Its the most basic approach -- the only thing it relies upon is the linux wireless tools package and the dhclient package -- both which are installed.

---

### Post by Milkensen on 2008-01-25
I entered the following commands from the CLI, after a "sudo su":
```

 ifconfig ath0 down
 ifconfig ath0 192.168.1.31 netmask 255.255.255.0 up
 route add default gw 192.168.1.1
 wpa_supplicant -w -Dmadwifi -iath0 -c/etc/wpa_supplicant.conf -dd

```
The reply from the CLI has been:


 ```
wpa_supplicant -w -Dmadwifi -iath0 -c/etc/wpa_supplicant.conf -dd
Initializing interface 'ath0' conf '/etc/wpa_supplicant.conf' driver 'madwifi' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ap_scan=1
ctrl_interface='/var/run/wpa_supplicant'
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=6):
     70 6e 33 36 36 61                                 pn366a          
scan_ssid=0 (0x0)
proto: 0x2
key_mgmt: 0x2
Line 9: Invalid passphrase length 64 (expected: 8..63) '69883c023e8013886c79241afc7add294fabf7b28e47ca404c21a6fa7250aefa"'.
Line 9: failed to parse psk '"69883c023e8013886c79241afc7add294fabf7b28e47ca404c21a6fa7250aefa"'.
pairwise: 0x10
group: 0x10
Line 13: WPA-PSK accepted for key management, but no PSK configured.
Line 13: failed to parse network block.
Failed to read or parse configuration '/etc/wpa_supplicant.conf'.
Failed to add interface ath0
Cancelling scan request
Cancelling authentication timeout
```

Also, I've taped this last command before  those which define and coming up the network, but the output is the same.

What's wrong with the passphrase? 
I've checked looking for blank spaces, but there aren't.

---

### Post by Milkensen on 2008-01-25
Well, I've found out via Google that the following string from the output:
```

Invalid passphrase length 64 (expected: 8..63)
```

is appearing in some dozens of cases over there, but much of the people try to remove the quotes from the hexadecimal key in the /etc/wpa_supplicant.conf, without results. Other people just abandon and configure their router for another protocol of encryption and try it... Some people are talking about a bug, in the madwifi driver, reported since the first days January 2008, related with the management of the hex keys. 

I changed in the /etc/wpa_supplicant.conf file this line, leaving it as follows:

```
scan_ssid=1
```

Before there was a 0 there, but since actually I do not what it means, and comparing with the equivalent line in /etc/network/interfaces.conf, I decided to change it. This is the line I'm refering to now:
```
wpa-ap-scan 1
```

I have no idea if they both must to be set to the same value or not. 
I'm just trying things, since there are no much clues..

The output now, after the sequence of commands from the previous post, is below (I had to stop it with Ctrl+C since the scanning was running and running endless). 

```

10: 00:1a:2b:00:c7:f7 ssid='casa' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
No suitable AP found.
[COLOR="Red"]Setting scan request: 5 sec 0 usec
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=6):
     70 6e 33 36 36 61                                 pn366a          
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b1a len=14
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b19 len=8
Received 2417 bytes of scan results (11 BSSes)
Scan results: 11
Selecting BSS from priority group 0[/COLOR]
[COLOR="Red"]Try to find WPA-enabled AP
0: 00:03:c9:d2:12:ca ssid='pn366a' wpa_ie_len=0 rsn_ie_len=22 caps=0x11
   skip RSN IE - PTK cipher mismatch[/COLOR]
1: 00:11:f5:14:9c:bb ssid='SpeedTouch76FDA0' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:11:f5:14:a1:8f ssid='SpeedTouchE42F97' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
3: 00:13:49:4b:21:62 ssid='TYC' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
4: 00:60:b3:f3:e2:96 ssid='WLAN_C3' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
5: 00:01:38:97:21:be ssid='WLAN_A0' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
6: 00:01:38:79:5c:a9 ssid='WLAN_C4' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
7: 00:60:b3:d7:28:99 ssid='WLAN_D4' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
8: 00:01:38:79:25:f5 ssid='WLAN_FB' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
9: 00:14:7f:ac:ac:57 ssid='SpeedTouchD20A8B' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
10: 00:1a:2b:00:c7:f7 ssid='casa' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
[COLOR="Red"]Try to find non-WPA AP
0: 00:03:c9:d2:12:ca ssid='pn366a' wpa_ie_len=0 rsn_ie_len=22 caps=0x11
   skip - non-WPA network not allowed[/COLOR]
1: 00:11:f5:14:9c:bb ssid='SpeedTouch76FDA0' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:11:f5:14:a1:8f ssid='SpeedTouchE42F97' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
3: 00:13:49:4b:21:62 ssid='TYC' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
4: 00:60:b3:f3:e2:96 ssid='WLAN_C3' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
5: 00:01:38:97:21:be ssid='WLAN_A0' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
6: 00:01:38:79:5c:a9 ssid='WLAN_C4' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
7: 00:60:b3:d7:28:99 ssid='WLAN_D4' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
8: 00:01:38:79:25:f5 ssid='WLAN_FB' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
9: 00:14:7f:ac:ac:57 ssid='SpeedTouchD20A8B' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
10: 00:1a:2b:00:c7:f7 ssid='casa' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b1a len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b19 len=8
Received 2397 bytes of scan results (11 BSSes)
Scan results: 11
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:03:c9:d2:12:ca ssid='pn366a' wpa_ie_len=0 rsn_ie_len=22 caps=0x11
   skip RSN IE - PTK cipher mismatch
1: 00:11:f5:14:9c:bb ssid='SpeedTouch76FDA0' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:11:f5:14:a1:8f ssid='SpeedTouchE42F97' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
3: 00:60:b3:d5:cb:82 ssid='WLAN_09' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
4: 00:60:b3:f3:e2:96 ssid='WLAN_C3' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
5: 00:01:38:97:21:be ssid='WLAN_A0' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
6: 00:01:38:79:5c:a9 ssid='WLAN_C4' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
7: 00:60:b3:d7:28:99 ssid='WLAN_D4' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
8: 00:01:38:79:25:f5 ssid='WLAN_FB' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
9: 00:14:7f:ac:ac:57 ssid='SpeedTouchD20A8B' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
10: 00:1a:2b:00:c7:f7 ssid='casa' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
[COLOR="Red"]Try to find non-WPA AP
0: 00:03:c9:d2:12:ca ssid='pn366a' wpa_ie_len=0 rsn_ie_len=22 caps=0x11
   skip - non-WPA network not allowed[/COLOR]
1: 00:11:f5:14:9c:bb ssid='SpeedTouch76FDA0' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:11:f5:14:a1:8f ssid='SpeedTouchE42F97' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
3: 00:60:b3:d5:cb:82 ssid='WLAN_09' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
4: 00:60:b3:f3:e2:96 ssid='WLAN_C3' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
5: 00:01:38:97:21:be ssid='WLAN_A0' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
6: 00:01:38:79:5c:a9 ssid='WLAN_C4' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
7: 00:60:b3:d7:28:99 ssid='WLAN_D4' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
8: 00:01:38:79:25:f5 ssid='WLAN_FB' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
9: 00:14:7f:ac:ac:57 ssid='SpeedTouchD20A8B' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
10: 00:1a:2b:00:c7:f7 ssid='casa' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=6):
     70 6e 33 36 36 61                                 pn366a          
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b1a len=14
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b19 len=8
Received 2431 bytes of scan results (11 BSSes)
Scan results: 11
Selecting BSS from priority group 0
[COLOR="Red"]Try to find WPA-enabled AP
0: 00:03:c9:d2:12:ca ssid='pn366a' wpa_ie_len=0 rsn_ie_len=22 caps=0x11
   skip RSN IE - PTK cipher mismatch[/COLOR]
1: 00:11:f5:14:9c:bb ssid='SpeedTouch76FDA0' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:11:f5:14:a1:8f ssid='SpeedTouchE42F97' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
3: 00:60:b3:d5:cb:82 ssid='WLAN_09' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
4: 00:60:b3:f3:e2:96 ssid='WLAN_C3' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
5: 00:01:38:97:21:be ssid='WLAN_A0' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
6: 00:01:38:79:5c:a9 ssid='WLAN_C4' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
7: 00:60:b3:d7:28:99 ssid='WLAN_D4' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
8: 00:01:38:79:25:f5 ssid='WLAN_FB' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
9: 00:14:7f:ac:ac:57 ssid='SpeedTouchD20A8B' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
10: 00:1a:2b:00:c7:f7 ssid='casa' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
[COLOR="Red"]Try to find non-WPA AP
0: 00:03:c9:d2:12:ca ssid='pn366a' wpa_ie_len=0 rsn_ie_len=22 caps=0x11
   skip - non-WPA network not allowed[/COLOR]
1: 00:11:f5:14:9c:bb ssid='SpeedTouch76FDA0' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:11:f5:14:a1:8f ssid='SpeedTouchE42F97' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
3: 00:60:b3:d5:cb:82 ssid='WLAN_09' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
4: 00:60:b3:f3:e2:96 ssid='WLAN_C3' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
5: 00:01:38:97:21:be ssid='WLAN_A0' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
6: 00:01:38:79:5c:a9 ssid='WLAN_C4' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
7: 00:60:b3:d7:28:99 ssid='WLAN_D4' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
8: 00:01:38:79:25:f5 ssid='WLAN_FB' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
9: 00:14:7f:ac:ac:57 ssid='SpeedTouchD20A8B' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
10: 00:1a:2b:00:c7:f7 ssid='casa' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b1a len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b19 len=8
Received 3030 bytes of scan results (14 BSSes)
Scan results: 14
Selecting BSS from priority group 0
[COLOR="Red"]Try to find WPA-enabled AP
0: 00:03:c9:d2:12:ca ssid='pn366a' wpa_ie_len=0 rsn_ie_len=22 caps=0x11
   skip RSN IE - PTK cipher mismatch[/COLOR]
1: 00:11:f5:14:9c:bb ssid='SpeedTouch76FDA0' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:11:f5:14:a1:8f ssid='SpeedTouchE42F97' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
3: 00:13:49:4b:21:62 ssid='TYC' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
4: 00:17:3f:61:ff:99 ssid='Caralladas' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
5: 00:60:b3:d5:cb:82 ssid='WLAN_09' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
6: 00:60:b3:f3:e2:96 ssid='WLAN_C3' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
7: 00:01:38:97:21:be ssid='WLAN_A0' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
8: 00:01:38:79:5c:a9 ssid='WLAN_C4' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
9: 00:60:b3:d7:28:99 ssid='WLAN_D4' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
10: 00:01:38:79:25:f5 ssid='WLAN_FB' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
11: 00:14:7f:ac:ac:57 ssid='SpeedTouchD20A8B' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
12: 00:16:38:89:3b:5e ssid='WLAN_5F' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
13: 00:1a:2b:00:c7:f7 ssid='casa' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
Try to find non-WPA AP
[COLOR="Red"]0: 00:03:c9:d2:12:ca ssid='pn366a' wpa_ie_len=0 rsn_ie_len=22 caps=0x11
   skip - non-WPA network not allowed[/COLOR]
1: 00:11:f5:14:9c:bb ssid='SpeedTouch76FDA0' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:11:f5:14:a1:8f ssid='SpeedTouchE42F97' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
3: 00:13:49:4b:21:62 ssid='TYC' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
4: 00:17:3f:61:ff:99 ssid='Caralladas' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
5: 00:60:b3:d5:cb:82 ssid='WLAN_09' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
6: 00:60:b3:f3:e2:96 ssid='WLAN_C3' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
7: 00:01:38:97:21:be ssid='WLAN_A0' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
8: 00:01:38:79:5c:a9 ssid='WLAN_C4' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
9: 00:60:b3:d7:28:99 ssid='WLAN_D4' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
10: 00:01:38:79:25:f5 ssid='WLAN_FB' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
11: 00:14:7f:ac:ac:57 ssid='SpeedTouchD20A8B' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
12: 00:16:38:89:3b:5e ssid='WLAN_5F' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
13: 00:1a:2b:00:c7:f7 ssid='casa' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
No suitable AP found.
[COLOR="Red"]Setting scan request: 5 sec 0 usec
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=6):
     70 6e 33 36 36 61                                 pn366a          
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b1a len=14
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b19 len=8
Received 3030 bytes of scan results (14 BSSes)
Scan results: 14
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:03:c9:d2:12:ca ssid='pn366a' wpa_ie_len=0 rsn_ie_len=22 caps=0x11
   skip RSN IE - PTK cipher mismatch[/COLOR]
1: 00:11:f5:14:9c:bb ssid='SpeedTouch76FDA0' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:11:f5:14:a1:8f ssid='SpeedTouchE42F97' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
3: 00:13:49:4b:21:62 ssid='TYC' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
4: 00:17:3f:61:ff:99 ssid='Caralladas' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
5: 00:60:b3:d5:cb:82 ssid='WLAN_09' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
6: 00:60:b3:f3:e2:96 ssid='WLAN_C3' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
7: 00:01:38:97:21:be ssid='WLAN_A0' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
8: 00:01:38:79:5c:a9 ssid='WLAN_C4' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
9: 00:60:b3:d7:28:99 ssid='WLAN_D4' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
10: 00:01:38:79:25:f5 ssid='WLAN_FB' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
11: 00:14:7f:ac:ac:57 ssid='SpeedTouchD20A8B' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
12: 00:16:38:89:3b:5e ssid='WLAN_5F' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
13: 00:1a:2b:00:c7:f7 ssid='casa' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
[COLOR="Red"]Try to find non-WPA AP
0: 00:03:c9:d2:12:ca ssid='pn366a' wpa_ie_len=0 rsn_ie_len=22 caps=0x11
   skip - non-WPA network not allowed[/COLOR]
1: 00:11:f5:14:9c:bb ssid='SpeedTouch76FDA0' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:11:f5:14:a1:8f ssid='SpeedTouchE42F97' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
3: 00:13:49:4b:21:62 ssid='TYC' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
4: 00:17:3f:61:ff:99 ssid='Caralladas' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
5: 00:60:b3:d5:cb:82 ssid='WLAN_09' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
6: 00:60:b3:f3:e2:96 ssid='WLAN_C3' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
7: 00:01:38:97:21:be ssid='WLAN_A0' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
8: 00:01:38:79:5c:a9 ssid='WLAN_C4' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
9: 00:60:b3:d7:28:99 ssid='WLAN_D4' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
10: 00:01:38:79:25:f5 ssid='WLAN_FB' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
11: 00:14:7f:ac:ac:57 ssid='SpeedTouchD20A8B' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
12: 00:16:38:89:3b:5e ssid='WLAN_5F' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
13: 00:1a:2b:00:c7:f7 ssid='casa' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b1a len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b19 len=8
Received 2986 bytes of scan results (14 BSSes)
Scan results: 14
Selecting BSS from priority group 0
[COLOR="Red"]Try to find WPA-enabled AP
0: 00:03:c9:d2:12:ca ssid='pn366a' wpa_ie_len=0 rsn_ie_len=22 caps=0x11
   skip RSN IE - PTK cipher mismatch
1: 00:11:f5:14:9c:bb ssid='SpeedTouch76FDA0' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch[/COLOR]
2: 00:11:f5:14:a1:8f ssid='SpeedTouchE42F97' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
3: 00:13:49:4b:21:62 ssid='TYC' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
4: 00:17:3f:61:ff:99 ssid='Caralladas' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
5: 00:60:b3:d5:cb:82 ssid='WLAN_09' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
6: 00:60:b3:f3:e2:96 ssid='WLAN_C3' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
7: 00:01:38:97:21:be ssid='WLAN_A0' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
8: 00:60:b3:d7:28:99 ssid='WLAN_D4' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
9: 00:01:38:79:5c:a9 ssid='WLAN_C4' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
10: 00:01:38:79:25:f5 ssid='WLAN_FB' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
11: 00:16:38:89:3b:5e ssid='WLAN_5F' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
12: 00:80:5a:49:c6:38 ssid='Virus' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
13: 00:1a:2b:00:c7:f7 ssid='casa' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
[COLOR="Red"]Try to find non-WPA AP
0: 00:03:c9:d2:12:ca ssid='pn366a' wpa_ie_len=0 rsn_ie_len=22 caps=0x11
   skip - non-WPA network not allowed[/COLOR]
1: 00:11:f5:14:9c:bb ssid='SpeedTouch76FDA0' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:11:f5:14:a1:8f ssid='SpeedTouchE42F97' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
3: 00:13:49:4b:21:62 ssid='TYC' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
4: 00:17:3f:61:ff:99 ssid='Caralladas' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
5: 00:60:b3:d5:cb:82 ssid='WLAN_09' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
6: 00:60:b3:f3:e2:96 ssid='WLAN_C3' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
7: 00:01:38:97:21:be ssid='WLAN_A0' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
8: 00:60:b3:d7:28:99 ssid='WLAN_D4' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
9: 00:01:38:79:5c:a9 ssid='WLAN_C4' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
10: 00:01:38:79:25:f5 ssid='WLAN_FB' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
11: 00:16:38:89:3b:5e ssid='WLAN_5F' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
12: 00:80:5a:49:c6:38 ssid='Virus' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
13: 00:1a:2b:00:c7:f7 ssid='casa' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 5 sec 0 usec
[COLOR="Red"]Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=6):
     70 6e 33 36 36 61                                 pn366a          
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b1a len=14
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b19 len=8
Received 2952 bytes of scan results (14 BSSes)
Scan results: 14
Selecting BSS from priority group 0[/COLOR]
[COLOR="Red"]Try to find WPA-enabled AP
0: 00:03:c9:d2:12:ca ssid='pn366a' wpa_ie_len=0 rsn_ie_len=22 caps=0x11
   skip RSN IE - PTK cipher mismatch[/COLOR]
1: 00:11:f5:14:9c:bb ssid='SpeedTouch76FDA0' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:11:f5:14:a1:8f ssid='SpeedTouchE42F97' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
3: 00:13:49:4b:21:62 ssid='TYC' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
4: 00:17:3f:61:ff:99 ssid='Caralladas' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
5: 00:60:b3:d5:cb:82 ssid='WLAN_09' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
6: 00:60:b3:f3:e2:96 ssid='WLAN_C3' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
7: 00:01:38:97:21:be ssid='WLAN_A0' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
8: 00:60:b3:d7:28:99 ssid='WLAN_D4' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
9: 00:01:38:79:5c:a9 ssid='WLAN_C4' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
10: 00:01:38:79:25:f5 ssid='WLAN_FB' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
11: 00:16:38:89:3b:5e ssid='WLAN_5F' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
12: 00:80:5a:49:c6:38 ssid='Virus' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
13: 00:1a:2b:00:c7:f7 ssid='casa' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
[COLOR="Red"]Try to find non-WPA AP
0: 00:03:c9:d2:12:ca ssid='pn366a' wpa_ie_len=0 rsn_ie_len=22 caps=0x11
   skip - non-WPA network not allowed[/COLOR]
1: 00:11:f5:14:9c:bb ssid='SpeedTouch76FDA0' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:11:f5:14:a1:8f ssid='SpeedTouchE42F97' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
3: 00:13:49:4b:21:62 ssid='TYC' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
4: 00:17:3f:61:ff:99 ssid='Caralladas' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
5: 00:60:b3:d5:cb:82 ssid='WLAN_09' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
6: 00:60:b3:f3:e2:96 ssid='WLAN_C3' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
7: 00:01:38:97:21:be ssid='WLAN_A0' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
8: 00:60:b3:d7:28:99 ssid='WLAN_D4' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
9: 00:01:38:79:5c:a9 ssid='WLAN_C4' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
10: 00:01:38:79:25:f5 ssid='WLAN_FB' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
11: 00:16:38:89:3b:5e ssid='WLAN_5F' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
12: 00:80:5a:49:c6:38 ssid='Virus' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
13: 00:1a:2b:00:c7:f7 ssid='casa' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 5 sec 0 usec
CTRL-EVENT-TERMINATING - signal 2 received
Removing interface ath0
State: SCANNING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_madwifi_set_drop_unencrypted: enabled=0
wpa_driver_madwifi_set_countermeasures: enabled=0
No keys have been configured - skip key clearing
Cancelling scan request
Cancelling authentication timeout
WEXT: Operstate: linkmode=0, operstate=6



```

It gives us some extra info about the network it should connect, my router: pnn366a; but I am not able to interpret it... after a few seconds, the scanning just continues over another networks.

Milkensen

---

### Post by Milkensen on 2008-01-27
No one for help? 

Anyone have got WPA2 in Ubuntu 7.10 with an atheros wireless chipset?

:confused:

---

### Post by kevdog on 2008-01-27
can you post your wpa_supplicant.conf file?

---

### Post by Milkensen on 2008-01-27
It's already posted. 

The only one line that currently is changed is:

```
scan_ssid=1
```

instead of 0, but I don't know if this matters anything...

Also, as I've already said, I've tried without quotes in the hex key, but nothing..

---

### Post by kevdog on 2008-01-27
Just for the record, does wpa(1) work?

---

### Post by mandrill on 2008-01-27
I got it. I run it. No problems. PM me.

---

### Post by Milkensen on 2008-01-28
> **kevdog said:**
> Just for the record, does wpa(1) work?

I've never tried it. I'd have to reconfigure the router for it, then I would see... Ubuntu 7.10 is my first Ubuntu. Before, with another Linux distro this issue worked OK, I mean WPA2. 

Probably I'll do it some evening, since it seem that I no have many options any more..

---

### Post by fosheezy05 on 2008-01-28
I have a Fujitsu S2110 Lifebook with the Atheros AR5006X card, and WPA (not WPA2) works fine on it.  I'm running Ubuntu 7.10 for the AMD 64 bit processors.  I had a lot of trouble trying to get it to work under 7.04, so I upgraded and was able to connect using the included network utility with no problem.

Wayne

---

### Post by kevdog on 2008-01-28
fosh

Thanks for the input, however your chipset revision number is slightly different than Mikensen's.  I think that is part of the problem here.

---

### Post by Milkensen on 2008-01-29
Well, well, well... Good news!

I've just got the wireless to work through WPA, no WPA2, but at least this is working at the moment. 

I'll try other combinations little by little when I have time. I think that some of the comments here could be useful to other people.

First, I had to change the whole wireless configuration in my router, a Comtrend CT-536+ which I had  updated its software some time ago, I didn't remember that point, until I got into a old folder with some files in a folder backup. I usually do not update software from routers and other accesory devices unless it's really neccesary. It was, but I don't remember the reason any more...:-)


[COLOR="DarkOrange"]
IN MY ROUTER:[/COLOR]
[COLOR="DarkOrange"]-----------------------------------------------------------------------------------------------------------[/COLOR]

 * Network Authentication: WPA-PSK

* WPA Pre-Shared Key: 24 characters, including things like % \ . / [ { } * : ) $ ... Really!
  The router accepts  strings longer that 24, but  the network-admin utility in the Gnome desktop doesn't, so 24 would be the longest.

* WPA Encryption: AES

WEP Encryption: Disabled

No Mac filter at the moment

AP mode: Access point (no bridges here)

Other advanced wireless configurations: untouched, and irrelevants here.

-[COLOR="DarkOrange"]-------------------------------------------------------------------------------------------------------------[/COLOR]

Please, notice that I could choice TKIP in the WPA encryption way, but I wanted to try with AES, despite according with several how2's it seems that it should associated to WPA2, but actually it hasn't to. 

Then, the WEP encryption is set to OFF. My router gives me the possibility of enabling it... if somebody could remark me briefly what's the difference, please... I mean, apart from this WPA PSK active, what would sum the WEP enabled here?

Please, have a look at the four attachments about the possibilities of this router. 

[COLOR="DarkOrange"]
IN THE LAPTOP[/COLOR]
[COLOR="DarkOrange"]----------------------------------------------------------------------------------------[/COLOR]

/etc/network/interfaces file:
```

auto lo
iface lo inet loopback


auto eth0
iface eth0 inet static
address 192.168.1.31
netmask 255.255.255.0
gateway 192.168.1.1


auto ath0
iface ath0 inet static
wireless-essid pn366a
address 192.168.1.31
netmask 255.255.255.0
dns-nameservers 62.14.2.1
gateway 192.168.1.1
wpa-driver madwifi
wpa-ssid pn366a
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
####wpa-psk 69883c023e8013886c79241afc7add294fabf7b28e47ca404c21a6fa7250aefa
wpa-psk 4e5e805a9310c3ba273fd14ef5b861430b0295a546f82b666bdaaea0e35e67c5


```

Please, notice the CCMP (that is... AES) option. 
And the "new" wpa-psk :-) See below at the bottom of this post. 


/etc/wpa_supplicant.conf file:
```
ap_scan=1
ctrl_interface=/var/run/wpa_supplicant

network={
	ssid="pn366a"
	scan_ssid=1
	proto=WPA
	key_mgmt=WPA-PSK
	##psk="69883c023e8013886c79241afc7add294fabf7b28e47ca404c21a6fa7250aefa"
	psk="4e5e805a9310c3ba273fd14ef5b861430b0295a546f82b666bdaaea0e35e67c5"
	pairwise=CCMP
	group=CCMP

}


```

Then I ran the sequence of commands posted below, according with the kevdog how2, but addapted to an static IP address in the LAN:
```

ifconfig ath0 down
 ifconfig ath0 192.168.1.31 netmask 255.255.255.0 up
route add default gw 192.168.1.1
 iwconfig ath0 essid "pn366a"
 wpa_supplicant -w Dmadwifi -iath0 -c/etc/wpa_supplicant.conf
```

Nothing happened, so I tried...
```

 /etc/init.d/networking restart
```
...and still nothing either.
So, I decided to reboot. The ethernet cord was unplugged, of course (as it was during all these moments). 
Log in.. and voila! Network working. 
To confirm that the roaming mode was not running, nor the laptop were connected to some neighbourhood's opened wireless, like "casa" (arrgggggggg...), I launched wifi-radar, it discarded  such options, and confirmed the result: connected to my network, protected. 
[COLOR="DarkOrange"]
-------------------------------------------------------------------------------------------------------------[/COLOR]

Last point for now: Why I changed the hex key?
I didn't, actually. I mean, I didn't change the ascII key (my 24 secret string of characters, weird/not usual ones included, of course..)
I just followed instructions from wieman01 (fixed how2) to get it. 
But this time instead of quoting the asc key with these ones..."..., I had to put the single quotes...' ..., and being the same asc string, the resulting hexadecimal key was different now!!
So, how to interpret that? Maybe..  was the first quote (")  taken as a symbol belonging to the string previously? :confused:
Have a look to this CLI outputs, and compare please (the first one is the key just without any kind of quotes, then the bash output complains about forbidden symbols in the CLI, it's normal):

 ```

#wpa_passphrase pn366a %\%\.../]{Jc}$:)e$t0*e$*
bash: error de sintaxis cerca de token no esperado `)'

#wpa_passphrase pn366a '%\%\.../]{Jc}$:)e$t0*e$*'
network={
        ssid="pn366a"
        #psk="%\%\.../]{Jc}$:)e$t0*e$*"
        psk=4e5e805a9310c3ba273fd14ef5b861430b0295a546f82b666bdaaea0e35e67c5
}

l# wpa_passphrase pn366a "%\%\.../]{Jc}$:)e$t0*e$*"
network={
        ssid="pn366a"
        #psk="%\%\.../]{Jc}$:)e*e"
        psk=69883c023e8013886c79241afc7add294fabf7b28e47ca404c21a6fa7250aefa
}

```

As we can see, the last one (which I've been using these days...) I think it's wrong. It doesn't belong to the whole string I invented, but a shorter one, as we can see.
Specifically, the following string chunks were deleted by the bash in the bad key:  "$t0" and then "$*".

Now, I'd have to check again if WPA2 works considering this matter. But this will be into another moment..

Regards

---

### Post by mandrill on 2008-01-29
Congratulations! The one portion of this whole thing that I can give feedback on quickly, is that WEP is worthless - it can be cracked in less than a minute by "pros". WPA was the next step in encryption, but you had to deal with all that hexadecimal stuff - WPA2/ PSK makes the router do the assignation of the hexadecimals, with stronger encryption, - and all you need to do is activate your machine with a password. Virtually invulnerable to invasion. Give your ssid an innocuous name, (let it broadcast, doesn't matter) and change the password access to the router. I believe AES (I could be wrong) is intended for enterprise applications, so stick with WPA2/ PSK. (Assuming your equipment can do it)

Haven't got time right now to go over the rest, but good job and good luck!

---

