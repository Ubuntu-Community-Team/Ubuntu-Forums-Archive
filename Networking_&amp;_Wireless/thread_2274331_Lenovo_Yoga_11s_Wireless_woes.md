---
title: "Lenovo Yoga 11s Wireless woes"
date: 2015-04-19
forum: Networking &amp; Wireless
---

### Post by d-john on 2015-04-19
After attempting to follow numerous HOWTOs on the Internet and failing, I am throwing in the towel and asking for help.

I have a Lenovo Yoga 11s. I partitioned the SSD and installed Ubuntu 14.10 as a dual boot option using UEFI. So far so good.

The wireless chipset in this laptop is known to be problematic, from what I can tell. Some people were reporting that the issue was "fixed" with 14.10 or that the driver worked, although slowly. That was not my experience. Although I could see a list of wireless networks, and enter my credentials, it failed to connect every single time for me.

Following an online tutorial, I blacklisted the built-in driver, downloaded a new driver [here]("https://github.com/lwfinger/rtl8723au/archive/master.tar.gz"). Compiled it, and installed it. I used a old Dlink USB wireless adapter to connect to the Internet while I tried this.

As far as I can tell, it worked. I saw no error messages. I unplugged the Dlink. Connected via the internal wireless and surfed the Internet for about 10 minutes, whereupon I was disconnected and the laptop went straight back to failing to connect. 

I am a user, not a programmer or sysadmin. I am decent at following directions, but I do not pretend to understand a lot of what I am doing. Many of the directions I have found online fail to work as advertised. Can anyone help me get the built-in wireless to work?

I am attaching the output of the wireless_script as instructed by the stickied post in the sub-forum.

```


########## wireless info START ##########


Report from: 19 Apr 2015 12:44 PDT -0700


Booted last: 19 Apr 2015 12:42 PDT -0700


Script from: 06 Apr 2015 17:23 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.10
Release:    14.10
Codename:    utopic


##### kernel ############################


Linux 3.16.0-34-generic #47-Ubuntu SMP Fri Apr 10 18:02:58 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


##### lsusb #############################


Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 006: ID 03eb:8814 Atmel Corp. 
Bus 002 Device 005: ID 2047:0855 Texas Instruments 
Bus 002 Device 004: ID 0bda:1724 Realtek Semiconductor Corp. 
Bus 002 Device 003: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 002 Device 002: ID 5986:053d Acer, Inc 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


##### lsmod #############################


cfg80211              510218  0 
snd_soc_rt5640         93042  0 
snd_soc_rl6231         13037  1 snd_soc_rt5640
snd_soc_core          200204  1 snd_soc_rt5640
snd_pcm               104102  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:2 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


##### iwconfig ##########################


lo        no wireless extensions.


wlan0     unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=2.417 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


##### resolv.conf #######################


##### NetworkManager info ###############


NetworkManager Tool


State: connecting


- Device: wlan0  [Biznerds] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723au
  State:             connecting (configuring)
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 
    EWCP ADMIN:      Infra, <MAC 'EWCP ADMIN' [AC7]>, Freq 2437 MHz, Rate 16 Mb/s, Strength 47 WPA WPA2
    HOME-A6D2-2.4:   Infra, <MAC 'HOME-A6D2-2.4' [AN2]>, Freq 2437 MHz, Rate 16 Mb/s, Strength 46 WPA WPA2
    ATT4p5k5X7:      Infra, <MAC 'ATT4p5k5X7' [AC2]>, Freq 2412 MHz, Rate 16 Mb/s, Strength 10 WPA WPA2
    WLCP ADMIN:      Infra, <MAC 'WLCP ADMIN' [AN4]>, Freq 2462 MHz, Rate 16 Mb/s, Strength 43 WPA WPA2
    EWCP ADMIN:      Infra, <MAC 'EWCP ADMIN' [AC9]>, Freq 2462 MHz, Rate 16 Mb/s, Strength 43 WPA WPA2
    HOME-4942:       Infra, <MAC 'HOME-4942' [AN6]>, Freq 2437 MHz, Rate 2 Mb/s, Strength 10 WPA WPA2
    EWCP ADMIN:      Infra, <MAC 'EWCP ADMIN' [AN7]>, Freq 2412 MHz, Rate 16 Mb/s, Strength 10 WPA WPA2
    SureWest-84:     Infra, <MAC 'SureWest-84' [AC6]>, Freq 2422 MHz, Rate 16 Mb/s, Strength 10 WPA WPA2
    ATT843:          Infra, <MAC 'ATT843' [AN9]>, Freq 2437 MHz, Rate 2 Mb/s, Strength 7 WPA WPA2
    WLCP Guest:      Infra, <MAC 'WLCP Guest' [AN10]>, Freq 2462 MHz, Rate 16 Mb/s, Strength 43
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AC3]>, Freq 2437 MHz, Rate 2 Mb/s, Strength 1
    2WIRE934:        Infra, <MAC '2WIRE934' [AN12]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    2WIRE308:        Infra, <MAC '2WIRE308' [AN13]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 23 WPA WPA2
    XFBSECA7HE6H:    Infra, <MAC 'XFBSECA7HE6H' [AN14]>, Freq 2462 MHz, Rate 16 Mb/s, Strength 7 WPA2 Enterprise
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AN15]>, Freq 2462 MHz, Rate 16 Mb/s, Strength 42
    CableWiFi:       Infra, <MAC 'CableWiFi' [AN16]>, Freq 2462 MHz, Rate 16 Mb/s, Strength 23
    WLCP ADMIN:      Infra, <MAC 'WLCP ADMIN' [AN17]>, Freq 2437 MHz, Rate 16 Mb/s, Strength 26 WPA WPA2
    Jennifer Quan Shrestha's Network: Infra, <MAC 'Jennifer Quan Shrestha's Network' [AC4]>, Freq 2462 MHz, Rate 16 Mb/s, Strength 7 WPA2
    WLCP ADMIN:      Infra, <MAC 'WLCP ADMIN' [AN19]>, Freq 2462 MHz, Rate 16 Mb/s, Strength 10 WPA WPA2
    SureWest-1D:     Infra, <MAC 'SureWest-1D' [AN20]>, Freq 2462 MHz, Rate 16 Mb/s, Strength 10 WPA WPA2
    WLCP Guest:      Infra, <MAC 'WLCP Guest' [AN21]>, Freq 2437 MHz, Rate 16 Mb/s, Strength 25
    2WIRE017:        Infra, <MAC '2WIRE017' [AN22]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 7 WPA WPA2
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AN23]>, Freq 2462 MHz, Rate 16 Mb/s, Strength 23
    CableWiFi:       Infra, <MAC 'CableWiFi' [AN24]>, Freq 2462 MHz, Rate 16 Mb/s, Strength 23
    2WIRE723:        Infra, <MAC '2WIRE723' [AN25]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 7 WPA WPA2
    Jennifer Quan Guest network: Infra, <MAC 'Jennifer Quan Guest network' [AC8]>, Freq 2462 MHz, Rate 16 Mb/s, Strength 7 WPA2
    ATTdU6kRCI:      Infra, <MAC 'ATTdU6kRCI' [AN27]>, Freq 2412 MHz, Rate 16 Mb/s, Strength 0 WPA WPA2
    Biznerds:        Infra, <MAC 'Biznerds' [AC1]>, Freq 2417 MHz, Rate 44 Mb/s, Strength 71 WPA WPA2


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


[[/etc/NetworkManager/system-connections/Biznerds]] (600 root)
[connection] id=Biznerds | type=802-11-wireless
[802-11-wireless] ssid=Biznerds | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/Los_Angeles (based on set time zone)


country 00: DFS-UNSET
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), NO-IR
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, NO-IR
    (5170 - 5250 @ 40), (3, 20), NO-IR
    (5735 - 5835 @ 40), (3, 20), NO-IR


##### iwlist channels ###################


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
          Current Frequency:2.417 GHz (Channel 2)


##### iwlist scan #######################


Channel occupancy:


      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.417 GHz (Channel 2)
      1   APs on   Frequency:2.422 GHz (Channel 3)
      1   APs on   Frequency:2.427 GHz (Channel 4)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      3   APs on   Frequency:2.462 GHz (Channel 11)


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Biznerds' [AC1]>
                    ESSID:"Biznerds"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.417 GHz (Channel 2)
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2040050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Quality=92/100  Signal level=72/100  
          Cell 02 - Address: <MAC 'ATT4p5k5X7' [AC2]>
                    ESSID:"ATT4p5k5X7"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:wpa_ie=dd1c0050f20101000050f20202000050f2040050f20201000050f2020c00
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Quality=0/100  Signal level=19/100  
          Cell 03 - Address: <MAC 'xfinitywifi' [AC3]>
                    ESSID:"xfinitywifi"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:130 Mb/s
                    Quality=0/100  Signal level=10/100  
          Cell 04 - Address: <MAC 'Jennifer Quan Shrestha's Network' [AC4]>
                    ESSID:"Jennifer Quan Shrestha's Network"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=0/100  Signal level=7/100  
          Cell 05 - Address: <MAC '' [AC5]>
                    ESSID:""
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.427 GHz (Channel 4)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=0/100  Signal level=7/100  
          Cell 06 - Address: <MAC 'SureWest-84' [AC6]>
                    ESSID:"SureWest-84"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.422 GHz (Channel 3)
                    Encryption key:on
                    Bit Rates:14lo        Interface doesn't support scanning.


4 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2040050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Quality=0/100  Signal level=23/100  
          Cell 07 - Address: <MAC 'EWCP ADMIN' [AC7]>
                    ESSID:"EWCP ADMIN"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:wpa_ie=dd160050f20101000050f20401000050f20401000050f202
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=0/100  Signal level=42/100  
          Cell 08 - Address: <MAC 'Jennifer Quan Guest network' [AC8]>
                    ESSID:"Jennifer Quan Guest network"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=0/100  Signal level=7/100  
          Cell 09 - Address: <MAC 'EWCP ADMIN' [AC9]>
                    ESSID:"EWCP ADMIN"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:wpa_ie=dd160050f20101000050f20401000050f20401000050f202
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=0/100  Signal level=10/100  


##### module infos ######################


[cfg80211]
filename:       /lib/modules/3.16.0-34-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     4A525D9D32B0C6D120CA547
depends:        
intree:         Y
vermagic:       3.16.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        72:0F:95:EA:B0:EA:3A:33:B3:BE:DE:E1:EE:3A:E7:88:F5:1C:AE:26
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


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
blacklist r8723au


[/etc/modprobe.d/blacklist-ideapad_laptop.conf]
blacklist ideapad_laptop


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
# USB device 0x:0x (rtl8723au)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


##### dmesg #############################


########## wireless info END ############



```

---

### Post by chili555 on 2015-04-19
Does it spring to life if you do:```
sudo modprobe 8723au
```We'll proceed once we have your response.

---

### Post by d-john on 2015-04-19
That did appear to do the trick. That step was part of the instructions that I followed before. But it didn't appear to "stick."

---

### Post by chili555 on 2015-04-19
Let's just put another nail in it. Please open a terminal and do:```
sudo -i
depmod -a
echo 8723au  >>  /etc/modules
exit
```You should be all set.

---

### Post by d-john on 2015-04-19
Results:

```
sudo modprobe 8723au
```

This made it work again for another 10-20 minutes. Then it decided it did not love me anymore. I tried entering it again, as if it was a magic phrase that solved all problems. No dice. I had to plug the Dlink to get back online and continue the conversation.

Moved on to Step 2 

```
sudo -i
depmod -a
echo 8723au  >>  /etc/modules
exit
```

Entered it. Unplugged Dlink. it refused to connect again. I rebooted the PC. Still refused to connect. Plugged Dlink back in. Now I am back here.

---

### Post by chili555 on 2015-04-19
Any informative messages?```
dmesg | grep 8723
rfkill list all
```Please detach the Dlink before you run these diagnostics.

---

### Post by d-john on 2015-04-19
Went through another bout of it working correctly again. Then, although I was showing that I was still connected to the Internet, I was getting this error message when I tried to pull up pages in Chrome.

```
DNS_PROBE_FINISHED_NO_INTERNET
```

Here's the result of "**dmesg | grep 8723**"

```

[    1.858999] 8723au: module verification failed: signature and/or  required key missing - tainting kernel
[    1.862002] usbcore: registered new interface driver rtl8723au
[    3.720094] RTL8723AU: ERROR indicate disassoc
[    3.745703] RTL8723AU: ERROR set bssid:00:00:00:00:00:00
[    3.745760] RTL8723AU: ERROR set ssid [g\xffffffc6isQ\xffffffffJ\xffffffec)&#890;\xffffffab\xfffffff2\xfffffffb\xffffffe3F|\xffffffc2T\xfffffff8xffffffe8\xffffffe7\xffffff8dvZ.c3\xffffff9f&#602;a\xffffffc8fA] fw_state=0x00000008
[    6.367541] RTL8723AU: ERROR set ssid [Biznerds] fw_state=0x00000008
[    6.367577] RTL8723AU: ERROR set bssid:fc:75:16:c6:e3:b8
[    6.455169] RTL8723AU: ERROR start auth
[    6.458770] RTL8723AU: ERROR auth success, start assoc
[    6.468650] RTL8723AU: ERROR assoc success
[    6.491945] RTL8723AU: ERROR send eapol packet
[    6.508916] RTL8723AU: ERROR send eapol packet
[    6.508956] RTL8723AU: ERROR set pairwise key to hw: alg:4(WEP40-1 WEP104-5 TKIP-2 AES-4) camid:4
[    6.509487] RTL8723AU: ERROR set ssid [Biznerds] fw_state=0x00000009
[    6.509501] RTL8723AU: ERROR indicate disassoc
[    6.509535] RTL8723AU: ERROR set bssid:fc:75:16:c6:e3:b8
[    6.509651] RTL8723AU: ERROR set group key to hw: alg:2(WEP40-1 WEP104-5 TKIP-2 AES-4) keyid:2
[    6.510221] RTL8723AU: ERROR set group key to hw: alg:2(WEP40-1 WEP104-5 TKIP-2 AES-4) keyid:0
[    6.510777] RTL8723AU: ERROR set group key to hw: alg:2(WEP40-1 WEP104-5 TKIP-2 AES-4) keyid:2
[    6.511336] RTL8723AU: ERROR set group key to hw: alg:2(WEP40-1 WEP104-5 TKIP-2 AES-4) keyid:0
[    6.525102] RTL8723AU: ERROR sta recv deauth reason code(6) sta:fc:75:16:c6:e3:b8
[    6.528339] RTL8723AU: ERROR indicate disassoc
[    9.729952] RTL8723AU: ERROR nolinked power save enter
[   30.348806] RTL8723AU: ERROR nolinked power save leave
[   31.650989] RTL8723AU: ERROR set ssid [Biznerds] fw_state=0x00000008
[   31.651008] RTL8723AU: ERROR set bssid:fc:75:16:c6:e3:b8
[   31.739181] RTL8723AU: ERROR start auth
[   31.744866] RTL8723AU: ERROR auth success, start assoc
[   31.759767] RTL8723AU: ERROR assoc success
[   31.813493] RTL8723AU: ERROR send eapol packet
[   31.823072] RTL8723AU: ERROR send eapol packet
[   31.823115] RTL8723AU: ERROR set pairwise key to hw: alg:4(WEP40-1 WEP104-5 TKIP-2 AES-4) camid:4
[   31.823682] RTL8723AU: ERROR set group key to hw: alg:2(WEP40-1 WEP104-5 TKIP-2 AES-4) keyid:2
[  937.573411] RTL8723AU: ERROR set group key to hw: alg:2(WEP40-1 WEP104-5 TKIP-2 AES-4) keyid:1
[  937.573468] RTL8723AU: ERROR send eapol packet

```

---

### Post by chili555 on 2015-04-20
Let's have a look at:```
lsmod | grep 8723
cat /etc/modprobe.d/blacklist.conf | tail -n5
```Thanks.

---

### Post by d-john on 2015-04-20
OK. Once more into the breach. I assume these will run fine with the Dlink still plugged in. Here are the results.

lsmod | grep 8723

```
8723au                903256  0
```


cat /etc/modprobe.d/blacklist.conf | tail -n5 
```
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist r8723au

```

---

### Post by chili555 on 2015-04-20
It seems you have a choice to make:

*A driver that works --sort of; the original r8723au; or

*A driver that doesn't work at all; the compiled 8723au; or

*Purchase a cheap working USB wireless.

I really have no solution or suggestion for the git version. If you'd like to try to troubleshoot the native version, I'll be happy to try. I regret that I haven't a ready solution.

---

### Post by d-john on 2015-04-20
Hmm. I am disappointed. I read a few reviews online from people who reported they got this to work using a downloaded driver.

So is there hope that the original driver can be fixed? Or would I be better off getting a $10 nano wireless adapter and using up one of my USB ports?

Adding a wireless adapter seems inelegant, but I don't want to take up too much of your time.

---

### Post by chili555 on 2015-04-20
I think the hope is on the low side; yours is a relatively new device with a very new Linux driver. My usual process is to load the driver, try to connect and then look at *dmesg *for clues as to what going on or, more precisely, what's going wrong. I Google the errors and warnings and hope that someone has a solution. In some cases, a driver parameter can help:```
options r8723au some_parameter=Y 
```There are many available for this driver:```
modinfo r8723au
<snip>
parm:           rtw_ips_mode:The default IPS mode (int)
parm:           rtw_regulatory_id:int
parm:           ifname:The default name to allocate for first interface (charp)
parm:           if2name:The default name to allocate for second interface (charp)
parm:           rtw_channel_plan:int
parm:           rtw_chip_version:int
parm:           rtw_rfintfs:int
parm:           rtw_channel:int
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
parm:           rtw_smart_ps:int
parm:           rtw_low_power:int
parm:           rtw_wifi_spec:int
parm:           rtw_antdiv_cfg:int
parm:           rtw_enusbss:int
parm:           rtw_hwpdn_mode:int
parm:           rtw_hwpwrp_detect:int
parm:           rtw_hw_wps_pbc:int
parm:           rtw_max_roaming_times:The max roaming times to try (uint)
parm:           rtw_80211d:Enable 802.11d mechanism (int)
parm:           rtw_btcoex_enable:Enable BT co-existence mechanism (int)
parm:           rtw_notch_filter:0:Disable, 1:Enable, 2:Enable only for P2P (uint)
parm:           debug:Set debug level (1-9) (default 1) (int)

```The trouble is that there is no documentation that I've been able to find that tells us what each parameter does or undoes.

I suggest you try the process I outlined above and let's see what we see.```
sudo modprobe -r 8723au
sudo modprobe r8723au
dmesg | tail -n20
```I think the driver will improve; a few kernel versions from now, we'll laugh at these bad old days! When that may be, I can't predict. In the meantime, an inelegant USB can tide you over.

Don't worry about my time; I've been here for years and I'll be here for many more.

---

### Post by d-john on 2015-04-20
Results:

```

[46236.196747] RTL8723AU: ERROR indicate disassoc
[46240.257271] ACPI Error: [\_SB_.PCI0.LPCB.EC0_.ECRD] Namespace lookup failure, AE_NOT_FOUND (20140424/psargs-359)
[46240.257279] ACPI Error: Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_.TSKN._TMP] (Node ffff88015a868c08), AE_NOT_FOUND (20140424/psparse-536)
[46244.256711] ACPI Error: [\_SB_.PCI0.LPCB.EC0_.ECRD] Namespace lookup failure, AE_NOT_FOUND (20140424/psargs-359)
[46244.256732] ACPI Error: Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_.TSKN._TMP] (Node ffff88015a868c08), AE_NOT_FOUND (20140424/psparse-536)
[46248.259968] ACPI Error: [\_SB_.PCI0.LPCB.EC0_.ECRD] Namespace lookup failure, AE_NOT_FOUND (20140424/psargs-359)
[46248.259976] ACPI Error: Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_.TSKN._TMP] (Node ffff88015a868c08), AE_NOT_FOUND (20140424/psparse-536)
[46252.259953] ACPI Error: [\_SB_.PCI0.LPCB.EC0_.ECRD] Namespace lookup failure, AE_NOT_FOUND (20140424/psargs-359)
[46252.259960] ACPI Error: Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_.TSKN._TMP] (Node ffff88015a868c08), AE_NOT_FOUND (20140424/psparse-536)
[46255.089656] r8723au: module is from the staging directory, the quality is unknown, you have been warned.
[46255.159892] usbcore: registered new interface driver rtl8723au
[46255.198014] rtl8723au: Loading firmware rtlwifi/rtl8723aufw_B.bin
[46255.199789] RTL8723AU: Firmware Version 33, SubVersion 0, Signature 0x2302
[46255.619190] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[46255.623385] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[46259.173993] ACPI Error: [\_SB_.PCI0.LPCB.EC0_.ECRD] Namespace lookup failure, AE_NOT_FOUND (20140424/psargs-359)
[46259.174001] ACPI Error: Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_.TSKN._TMP] (Node ffff88015a868c08), AE_NOT_FOUND (20140424/psparse-536)
[46259.632013] RTL8723AU: ERROR nolinked power save enter
[46263.176656] ACPI Error: [\_SB_.PCI0.LPCB.EC0_.ECRD] Namespace lookup failure, AE_NOT_FOUND (20140424/psargs-359)
[46263.176664] ACPI Error: Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_.TSKN._TMP] (Node ffff88015a868c08), AE_NOT_FOUND (20140424/psparse-536)


```

---

### Post by chili555 on 2015-04-20
We have two issues going on here. First, we see:> RTL8723AU: ERROR indicate disassocAnd a Google search finds this: [https://github.com/lwfinger/rtl8723au/issues/17](https://github.com/lwfinger/rtl8723au/issues/17) The exact same error is quoted and the issue is discussed by the driver's author! He suggests:> You might try loading the driver with a 'rtw_power_mgnt=0' option. As I read the code, that should disable power management.Let's try that:```
sudo -i
echo "options r8723au rtw_power_mgnt=0  >  /etc/modprobe.d/r8723au.conf
exit
```And then reboot.

Next, we see:> [46240.257271] ACPI Error: [\_SB_.PCI0.LPCB.EC0_.ECRD] Namespace lookup failure, AE_NOT_FOUND (20140424/psargs-359)
[46240.257279] ACPI Error: Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_.TSKN._TMP] (Node ffff88015a868c08), AE_NOT_FOUND (20140424/psparse-536)
[46244.256711] ACPI Error: [\_SB_.PCI0.LPCB.EC0_.ECRD] Namespace lookup failure, AE_NOT_FOUND (20140424/psargs-359)
[46244.256732] ACPI Error: Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_.TSKN._TMP] (Node ffff88015a868c08), AE_NOT_FOUND (20140424/psparse-536)
[46248.259968] ACPI Error: [\_SB_.PCI0.LPCB.EC0_.ECRD] Namespace lookup failure, AE_NOT_FOUND (20140424/psargs-359)This is, as far as I know, not caused by wireless, however, it may have an impact on wireless. I am inexperienced in ACPI matters but I suggest you both Google and ask here: [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)  I suspect (with little or no knowledge to support it!) that either a change in the BIOS or an updated BIOS may help.

---

### Post by d-john on 2015-04-20
Did your first suggestion. It worked just long enough to make me excited -- then it stopped. Again. I ca't get it to connect again now. Even after a few reboots.

I'll ask about the ACPI error. Can't be BIOS because this is a UEFI machine. I checked for an update on the manufacturers website and got nothing.

I could jump to 15.04, I suppose. It has a new kernel. Perhaps it contains updated drivers that will make everything work like magic...

---

### Post by chili555 on 2015-04-21
> **d-john said:**
> 

I could jump to 15.04, I suppose. It has a new kernel. Perhaps it contains updated drivers that will make everything work like magic...You could certainly download and try a live session. 

...or you could get a US$10 USB wireless and wait a few months for the driver to evolve.

---

### Post by d-john on 2015-04-21
The $10 USB adapter was my original thought -- but I thought you wanted one more go at this. I'm pretty much ready to throw in the towel and buy an adapter at this point.

---

### Post by d-john on 2015-04-21
I'm ready to  throw in the towel I think. 15.04 is getting released this month, right? So improvements are on the way. I'm going to order my adapter.

---

### Post by chili555 on 2015-04-21
> 15.04 is getting released this month, right?That's correct, April 23; however, you can download and try the Beta 2 right now. I have it installed on an old Thinkpad now and I haven't found a problem yet.

I generally download and install a few days *prior* to any official release date because wireless and networking questions will come hot and heavy release morning and because the download mirrors are clogged like crazy on release morning and for several days thereafter.

[http://releases.ubuntu.com/15.04/](http://releases.ubuntu.com/15.04/)

---

