---
title: "Can't connect to home wifi"
date: 2015-04-14
forum: Networking &amp; Wireless
---

### Post by kashei on 2015-04-14
HI im a newbie to linux (ubuntu 14.04)
i just installed netgear 3100 v2  (took me awhile, had to try 3 diff drivers ) anyway it finely worked. 
wifi showed up.
 im able to connect to my android  (wifi tether) but cant connect to home wifi 
please help
thank you

---

### Post by michi1983 on 2015-04-15
A little bit more info would be helpful ;)
What you mean with you can't connect to your home wifi? 
Can you connect with other clients (your android phone) to your home wifi?
Did it work earlier with your computer? 
Do you get any log files from your Ubuntu machine?

---

### Post by kashei on 2015-04-15
i have att dsl and when im hard line to it, it works perfectly....but not wifi.  
when im trying to connect, its asking me for password,  i put it in its trying to connect and then few seconds later its asking for password again.
but when im connecting to my android phone it connects rideway......

 i just installed ubuntu on this machine 
umm i dont think i get any log files,,,,well maybe i do but its not showing them



```
kashei@kashei1:~$ iwconfigeth0      no wireless extensions.


wlan0     IEEE 802.11g  ESSID:"AndroidA"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 5C:0A:5B:F9:08:46   
          Bit Rate=72 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:75/100  Signal level:-48 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:205  Invalid misc:1644619   Missed beacon:0


lo        no wireless extensions.



```

---

### Post by michi1983 on 2015-04-15
what kind of security are you using on the wifi router? can you change it for testing?

---

### Post by kashei on 2015-04-15
its wpa/wpa2......yeah i've tried open,  wep, wpa,  and can't connect with any of them

---

### Post by michi1983 on 2015-04-15
even if you disable it completely?

---

### Post by kashei on 2015-04-15
yup

---

### Post by michi1983 on 2015-04-15
Hm, sorry, but this does't make sense at all :/
I guess you will have to wait for the real 'pros', they might have an idea ;)

---

### Post by Vladlenin5000 on 2015-04-15
No, "pros" won't have clue unless there are enough information to work with.
What I can say right now is twofold: 
1. Always use WPA2-AES, nothing else is good.
2. Assuming that even with a open network it doesn't connect properly then you surely have a problem with the driver.

"Stickies" are there for a reason, like the ["Before posting in Networking & Wireless"]("http://ubuntuforums.org/showthread.php?t=370108") <- This is what you should do in order to get help.
And, according to [this]("https://wikidevi.com/wiki/Netgear_WNDA3100v2"), your Netgear WNDA3100 v2 has a Broadcom chipset so, again, a sticky, this time specifically about those [Broadcom chipsets]("http://ubuntuforums.org/showthread.php?t=2214110").

---

### Post by kashei on 2015-04-15
Vladlenin i always use WPA2, open network i was just trying if i could connect without password.......my problem is that i can connect to some networks like my phone, but cant connect to regular modem/router
if its wrong driver then why i can connect to some and not the other?

---

### Post by Vladlenin5000 on 2015-04-15
Exactly because of that it might be the wrong driver... Or it could be something else, we don't know... Will you please read the links I posted?

---

### Post by kashei on 2015-04-15
i think i know that the problem 
it shows that i have to network "cards"  one build in and usb netgear  
i've tried to blacklist build in one but it didnt work  


```
Ubuntu


##### lspci #############################


03:08.0 Ethernet controller [0200]: Intel Corporation NM10/ICH7 Family LAN Controller [8086:27dc] (rev 01)
	Subsystem: Dell Device [1028:01ab]
	Kernel driver in use: e100


##### lsusb #############################


Bus 001 Device 004: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]
Bus 001 Device 002: ID 0644:0200 TEAC Corp. All-In-One Multi-Card Reader CA200/B/S
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


##### rfkill ############################


##### lsmod #############################



```

---

### Post by Vladlenin5000 on 2015-04-15
Have you used the wireless script mentioned in one of the links? If so what you posted is incomplete. Please paste the complete results.
And no, considering only what you posted so far, you don't have two wireless devices. Internal ones would have been listed with lspci and yet it only shows the Ethernet, as expected. And it's a Dell... Desktop or notebook? Model, etc....

---

### Post by kashei on 2015-04-15
```
######### wireless info START ##########

Report from: 15 Apr 2015 13:53 EDT -0400


Booted last: 14 Apr 2015 18:20 EDT -0400


Script from: 06 Apr 2015 17:23 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.2 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.16.0-34-generic #47~14.04.1-Ubuntu SMP Fri Apr 10 17:49:16 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


03:08.0 Ethernet controller [0200]: Intel Corporation NM10/ICH7 Family LAN Controller [8086:27dc] (rev 01)
	Subsystem: Dell Device [1028:01ab]
	Kernel driver in use: e100


##### lsusb #############################


Bus 001 Device 004: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]
Bus 001 Device 002: ID 0644:0200 TEAC Corp. All-In-One Multi-Card Reader CA200/B/S
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


##### rfkill ############################


##### lsmod #############################


cfg80211              494362  0 
ndiswrapper           283985  0 
mxm_wmi                13021  1 nouveau
wmi                    19193  2 mxm_wmi,nouveau


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet6 addr: fe80::213:72ff:fed2:f7c3/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:6820 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4465 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7474385 (7.4 MB)  TX bytes:480108 (480.1 KB)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.43.223  Bcast:192.168.43.255  Mask:255.255.255.0
          inet6 addr: fe80::224e:7fff:fee5:9a9c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:203303 errors:0 dropped:0 overruns:0 frame:0
          TX packets:164870 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:232922098 (232.9 MB)  TX bytes:27631024 (27.6 MB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11g  ESSID:"AndroidA"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'AndroidA' [AC1]>   
          Bit Rate=72 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:78/100  Signal level:-46 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:384  Invalid misc:1704866   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.43.1    0.0.0.0         UG    0      0        0 wlan0
192.168.43.0    0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e100
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         off


- Device: wlan0  [AndroidA] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ndiswrapper
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           72 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    ATT7000:         Infra, <MAC 'ATT7000' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA2
    wifi unavailable:Infra, <MAC 'wifi unavailable:Infra, <MAC address>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA2' [AN2]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA2
    NETGEAR51:       Infra, <MAC 'NETGEAR51' [AC2]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA2
    *AndroidA:       Infra, <MAC 'AndroidA' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 78 WPA2
    wifi available:  Infra, <MAC 'wifi available' [AN5]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA2


  IPv4 Settings:
    Address:         192.168.43.223
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.43.1


    DNS:             192.168.43.1


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


[[/etc/NetworkManager/system-connections/ATT7000]] (600 root)
[connection] id=ATT7000 | type=802-11-wireless
[802-11-wireless] ssid=ATT7000 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ATT7000 1]] (600 root)
[connection] id=ATT7000 1 | type=802-11-wireless
[802-11-wireless] ssid=ATT7000 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/NETGEAR51]] (600 root)
[connection] id=NETGEAR51 | type=802-11-wireless
[802-11-wireless] ssid=NETGEAR51 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/AndroidA]] (600 root)
[connection] id=AndroidA | type=802-11-wireless
[802-11-wireless] ssid=AndroidA | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/New_York (based on set time zone)


country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


wlan0     14 channels in total; available frequencies :
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
          Channel 14 : 2.484 GHz
          Current Frequency:2.437 GHz (Channel 6)


##### iwlist scan #######################


Channel occupancy:


      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.462 GHz (Channel 11)


eth0      Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'AndroidA' [AC1]>
                    ESSID:"AndroidA"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:73/100  Signal level:-49 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'NETGEAR51' [AC2]>
                    ESSID:"NETGEAR51"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality:90/100  Signal level:-38 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'ATT7000' [AC3]>
                    ESSID:"ATT7000"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:84/100  Signal level:-42 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IElo        Interface doesn't support scanning.


: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


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
sig_key:        80:21:14:84:DC:DA:08:06:05:39:31:B7:EE:AA:DE:22:EA:7E:C2:62
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[ndiswrapper]
filename:       /lib/modules/3.16.0-34-generic/updates/dkms/ndiswrapper.ko
license:        GPL
version:        1.59
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     DC1EFD919FDF2DB80D424C6
depends:        
vermagic:       3.16.0-34-generic SMP mod_unload modversions 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)


##### module parameters #################


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


grep: /sys/module/ndiswrapper/parameters/debug: Permission denied
grep: /sys/module/ndiswrapper/parameters/hangcheck_interval: Permission denied
grep: /sys/module/ndiswrapper/parameters/if_name: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_gid: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_uid: Permission denied
grep: /sys/module/ndiswrapper/parameters/utils_version: Permission denied
[ndiswrapper]


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


[/etc/modprobe.d/ndiswrapper.conf]
alias usb:v050Dp6050d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v050Dp615Ad*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v050Dp825Cd*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0846p9011d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0846p9020d*dc*dsc*dp*ic*isc*ip* ndiswrapper


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x27dc (e100)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (ndiswrapper)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[62290.714919] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[62311.420856] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[62430.181997] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[62450.816293] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[70201.935667] ndiswrapper (iw_set_freq:436): setting configuration failed (00010003)


########## wireless info END ############



```

---

### Post by Vladlenin5000 on 2015-04-15
```
[70201.935667] ndiswrapper (iw_set_freq:436): setting configuration failed (00010003)
```

1. No, you don't have any additional WiFi device, internal or otherwise.
2. You couldn't have picked a WORSE WiFi USB dongle.
3. There's no Linux support for that chipset and never will be; resorting to *ndiswrapper* is your only chance and
4. *ndiswrapper* requires the use of one specific Windows driver and only one. It requires Windows **XP** drivers according to the architecture, 32 or 64-bit.

So...
If you already used the aforementioned Windows driver with the wrapper then there's little to nothing you can do about it. The wrapper is a "hack" and, even when it was a "new thing", it worked poorly (when it worked...).
I suggest you sell that PoS, old and lousy dongle (or give it or trow it away for good). New fully supported WiFi dongles can cost as little as $10. How much does you time worth?

---

### Post by kashei on 2015-04-15
thanks Vlad, but u dont mind if i'll get a 2nd opinion, do you???

---

### Post by Vladlenin5000 on 2015-04-15
Not at all... :p

@chili555 - Can you please give your opinion? Thank you...

(chilli555 is the resident expert; I'm just slightly above average).

---

### Post by kashei on 2015-04-15
Hhmmm this is weird ..... did a lil bit more research and found that sometimes all you have to do i change a password 
thats what i did and it worked!!!!!!!!
?????????????

---

### Post by Vladlenin5000 on 2015-04-15
Change the WiFi password? Yes, it's plausible... The emulated driver might not work properly with some characters or something like that...
Anyway, glad it's working. You can now mark this one as solved using the thread tools so others in the future may benefit of that wierd yet simple solution.

---

