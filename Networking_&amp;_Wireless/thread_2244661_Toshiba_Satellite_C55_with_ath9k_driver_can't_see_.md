---
title: "Toshiba Satellite C55 with ath9k driver can't see wireless"
date: 2014-09-17
forum: Networking &amp; Wireless
---

### Post by r-friedman on 2014-09-17
[SIZE=2]i saw varunendra's nice answer to the Dell users ([/SIZE][SIZE=2][Qualcomm Atheros QCA9565 / AR9565 , Dell inspiron 5537 wir&#1077;less problems]("http://ubuntuforums.org/showthread.php?t=2190930")[/SIZE]), I am having a similar problem on Toshiba Satellite C55.
[SIZE=2] i wen[/SIZE]t thru the build and install procedure as he suggested, altho i am  on 12.04.4.  when i use modinfo, i see ath9k and the version is in the  kernel.
i do modprobe ath9k and it works, showing ath9k and its dependencies
but i still can't get wireless to come up, despite reboots
i tried rfkill and what is disturbing is that it didn't even list the pci port with the ath9k on it, just the bluetooth port
i tried the FN-F8 and FN-F12 ways of turning the wireless on or off with  no effect; wireless light stayed on; there were some errors relating to  the keyboard processor in dmesg.
any suggestions, i'd really appreciate some help

---

### Post by dave131 on 2014-09-18
You're sure you have that chipset, right?  I had a C55 series that worked "out of the box", but there is nothing to say they don't switch up the adapter.

Please post back the output of

lspci | grep Network

Once we can see it is that adapter, perhaps someone can help more.

Also, please follow the following for downloading/running a script that will tell us about your network adapters and post the output back here inside of code tags:

[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by r-friedman on 2014-10-13
Sorry to take so long getting back, I've been hammered at work.

Here is the lspci output:
02:00.0 Network controller: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01)

Here is the wireless script output. 
[ATTACH]257170[/ATTACH]

Thanks for your help.

---

### Post by Hadaka on 2014-10-13
Hi, you have a broadcom wireless driver loaded and not
athk9. and a couple other issues, let's see if we can fix
them. with a working wired connection please do..
Please COPY  and paste to avoid typos,1 line at a time.
```
sudo apt-get update
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/udev/rules.d/70-persistent-net.rules
sudo modprobe -rf ath9k
echo "ath9k" | sudo tee -a /etc/modules
sudo modprobe ath9k
```
boot

---

### Post by r-friedman on 2014-10-14
No joy, there is still no wireless connections area in the network window.
lspci gives same output.  Here is wireless script output. [ATTACH=CONFIG]257200[/ATTACH]
Thanks for the help

---

### Post by r-friedman on 2014-10-14
[ATTACH]257201[/ATTACH]
This is the new wireless script output, sorry.

---

### Post by naradezza on 2014-10-14
I think your driver is not compatible, have you been try with another type of driver???

---

### Post by jeremy31 on 2014-10-14
Did you enter this one in terminal ```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
``` as per post by Hadaka as the file still exists and what does```
modinfo wl | grep -i 168c
```[COLOR=#000000][FONT=Ubuntu Mono]

[/FONT][/COLOR]

---

### Post by Hadaka on 2014-10-14
Hi, you keep loading the wl driver..
02:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
    Subsystem: XAVi Technologies Corp. Device [1b9a:28a4]
    Kernel modules: wl**[COLOR=#ff0000]<-[/COLOR]**
please re run the commands and  do not accept additional driver when offered
say no
post the output of..
```
modinfo ath9k | grep 168C
```
Thanks

---

### Post by r-friedman on 2014-10-14
@jeremy
yes i ran the delete
here's the modinfo output: ERROR: modinfo: could not find module wl
@hadaka
never was offered additional drivers
here's the modinfo output:
alias:          pci:v0000168Cd00000037sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000033sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000030sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Esv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
maybe I still have the wrong script output up there
[FONT=courier new]##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL
8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Toshiba America Info Systems Device [1179:f91b]
    Kernel driver in use: r8169

02:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Ne
twork Adapter [168c:0036] (rev 01)
    Subsystem: XAVi Technologies Corp. Device [1b9a:28a4]

03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Exp
ress Card Reader [10ec:5229] (rev 01)

##### lsusb #############################

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 003: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 004 Device 002: ID 0bc2:5031 Seagate RSS LLC FreeAgent GoFlex USB 3.0
Bus 001 Device 003: ID 04f2:b446 Chicony Electronics Co., Ltd 
Bus 001 Device 004: ID 0930:0227 Toshiba Corp. 

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ath9k                 117460  0 
mac80211              436493  1 ath9k
ath9k_common           13781  1 ath9k
ath9k_hw              391626  2 ath9k,ath9k_common
ath                    19387  3 ath9k,ath9k_common,ath9k_hw
cfg80211              178877  3 ath9k,mac80211,ath
wmi                    18744  1 toshiba_acpi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.79  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::faa9:63ff:fece:289f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:878 errors:0 dropped:0 overruns:0 frame:0
          TX packets:691 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:362147 (362.1 KB)  TX bytes:78066 (78.0 KB)
          Interrupt:42 Base address:0x8000 

##### iwconfig ##########################

lo        no wireless extensions.
eth0      no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.0.1
search attlocal.net

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.79
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

<snip>

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

##### module infos ######################

[ath9k]
filename:       /lib/modules/3.2.0-70-generic-pae/kernel/drivers/net/wireless/at
h/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     DAE1627B8BFAFE91C008E84
depends:        ath9k_hw,ath9k_common,mac80211,cfg80211,ath
intree:         Y
vermagic:       3.2.0-70-generic-pae SMP mod_unload modversions 686 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           ps_enable:Enable WLAN PowerSave (int)

[mac80211]
filename:       /lib/modules/3.2.0-70-generic-pae/kernel/net/mac80211/mac80211.k
o
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     1944D882391CC5F32CA6325
depends:        cfg80211
intree:         Y
vermagic:       3.2.0-70-generic-pae SMP mod_unload modversions 686 
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac
80211 to use (charp)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnectin
g (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason
 4). (int)
arm:           probe_wait_ms:Maximum time(ms) to wait for probe response before
 disconnecting (reason 4). (int)

[ath9k_common]
filename:       /lib/modules/3.2.0-70-generic-pae/kernel/drivers/net/wireless/at
h/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     87C8338518A200F45D72110
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.2.0-70-generic-pae SMP mod_unload modversions 686 

[ath9k_hw]
filename:       /lib/modules/3.2.0-70-generic-pae/kernel/drivers/net/wireless/at
h/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     E360040A6B724E8079E71E5
depends:        ath
intree:         Y
vermagic:       3.2.0-70-generic-pae SMP mod_unload modversions 686 
parm:           force_new_ani:Force new ANI for AR5008, AR9001, AR9002 (int)

[ath]
filename:       /lib/modules/3.2.0-70-generic-pae/kernel/drivers/net/wireless/at
h/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     8B429DBE4586F4065E2EA2E
depends:        cfg80211
intree:         Y
vermagic:       3.2.0-70-generic-pae SMP mod_unload modversions 686 

[cfg80211]
filename:       /lib/modules/3.2.0-70-generic-pae/kernel/net/wireless/cfg80211.k
o
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     A289A224DC04F871A44431D
depends:        
intree:         Y
vermagic:       3.2.0-70-generic-pae SMP mod_unload modversions 686 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz
 band (bool)

##### module parameters #################

[ath9k]
blink: 0
btcoex_enable: 0
nohwcrypt: 0
ps_enable: 0

[mac80211]
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[ath9k_hw]
force_new_ani: 0

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
ath9k

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
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
ath9k

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



[/FONT]

---

### Post by Hadaka on 2014-10-14
ok, go here -> [http://ubuntuforums.org/showthread.php?t=2190930](http://ubuntuforums.org/showthread.php?t=2190930)
post #4 .when you load the back port pay attention to the number for the
files you need to run.Its going to be 3.17 rc3 make sure you change it to
that in the instructions...if you dont understand please do not do anything
stop and ask for help.
thanks.

---

### Post by r-friedman on 2014-10-19
OK, now posting over wireless.
Thanks Hadaka, I am off to the market to get you your squid.

---

### Post by Hadaka on 2014-10-19
.Great !

please do,
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

