---
title: "RTL8723BE Wireless – 'no networks found' in Ubuntu – but works in Windows 10!"
date: 2016-03-18
forum: Networking &amp; Wireless
---

### Post by lee-barber86 on 2016-03-18
I had this issue previously and installed Windows 10 - needed laptop for work, so it had to work! Now I don't need it for work so it has again become a play-thing... but the issue remains that while the wifi works fine in Windows OS no wireless networks are found in Ubuntu. This indicates to me that the card itself is fine so it must be a firmware/software/Ubuntu issue.

I ran the diagnostic code, output follows:

```

########## wireless info START ##########

Report from: 18 Mar 2016 20:19 GMT +0000

Booted last: 18 Mar 2016 20:16 GMT +0000

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.19.0-56-generic #62~14.04.1-Ubuntu SMP Fri Mar 11 11:03:15 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

GNOME

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Hewlett-Packard Company Device [103c:2235]
    Kernel driver in use: r8169

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Hewlett-Packard Company Device [103c:2231]
    Kernel driver in use: rtl8723be

##### lsusb #############################

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 04ca:704d Lite-On Technology Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 0bda:b001 Realtek Semiconductor Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8723be             143360  0 
btcoexist             184320  1 rtl8723be
rtl_pci                40960  1 rtl8723be
rtlwifi               102400  3 btcoexist,rtl_pci,rtl8723be
mac80211              712704  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              524288  2 mac80211,rtlwifi
hp_wmi                 16384  0 
sparse_keymap          16384  1 hp_wmi
wmi                    20480  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fda0:8d16:7ce9:8300:b4b8:810e:5704:a041/64 Scope:Global
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          inet6 addr: fda0:8d16:7ce9:8300:<IP6 'eth0' [IF]>/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1616 errors:0 dropped:0 overruns:0 frame:0
          TX packets:425 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:315171 (315.1 KB)  TX bytes:58955 (58.9 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search lan

##### network managers ##################

Installed:

    NetworkManager

Running:

root       848     1  0 20:16 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723be
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

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
    Address:         192.168.1.4
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

  IPv6 Settings:
    Address:         fda0:8d16:7ce9:8300:b4b8:810e:5704:a041
    Prefix:          64
    Gateway:         ::

    Address:         fda0:8d16:7ce9:8300:<IP6 'eth0' [IF]>
    Prefix:          64
    Gateway:         ::

    Address:         fe80::<IP6 'eth0' [IF]>
    Prefix:          64
    Gateway:         ::

    DNS:             fe80::1

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

##### iw reg get ########################

Region: Europe/London (based on set time zone)

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

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     No scan results

##### module infos ######################

[rtl8723be]
filename:       /lib/modules/3.19.0-56-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     00619764255210776FAB54D
depends:        rtlwifi,rtl_pci,btcoexist,mac80211
vermagic:       3.19.0-56-generic SMP mod_unload modversions 
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)
parm:           ant_sel:Set to 1 or 2 to force antenna number (default 0)
 (int)

[rtl_pci]
filename:       /lib/modules/3.19.0-56-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     8552A7BAFD0FCC2C41CF075
depends:        mac80211,rtlwifi
vermagic:       3.19.0-56-generic SMP mod_unload modversions 

[rtlwifi]
filename:       /lib/modules/3.19.0-56-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     990116D31097F1C4C1F7006
depends:        mac80211,cfg80211
vermagic:       3.19.0-56-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/3.19.0-56-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     1261743510839D352D1D895
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-56-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        0D:22:80:B1:1C:0F:54:77:D5:8C:80:D7:06:21:62:5D:AE:0F:BC:8D
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.19.0-56-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     EF182B558008C23DD85EF03
depends:        
intree:         Y
vermagic:       3.19.0-56-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        0D:22:80:B1:1C:0F:54:77:D5:8C:80:D7:06:21:62:5D:AE:0F:BC:8D
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8723be]
ant_sel: 0
debug: 1
disable_watchdog: N
fwlps: N
ips: N
msi: N
swenc: N
swlps: N

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
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

[/etc/modprobe.d/rtl8723be.conf]
options rtl8723be fwlps=N ips=N
/etc/modprobe.d/rtl8723be.conf (END)

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0xb723 (rtl8723be)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[    6.711924] r8169 0000:01:00.0 eth0: link down
[    6.711988] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    8.634282] rtlwifi: module verification failed: signature and/or  required key missing - tainting kernel
[    8.667389] Using firmware rtlwifi/rtl8723befw.bin
[    8.667681] rtlwifi: channel plan 0x20
[    8.667685] rtlwifi: country code 11
[    8.680819] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    8.681507] rtlwifi: wireless switch is on
[    9.211550] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  135.831153] r8169 0000:01:00.0 eth0: link up
[  135.831179] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

########## wireless info END ############


```

I have tried the following with no luck:

The first thing I tried was:
sudo rmmod rtl8723be && sudo modprobe rtl8723be 
No Result


2[SUP]nd[/SUP]:
sudo make install the driver from this repo: [https://github.com/lwfinger/rtlwifi_new](https://github.com/lwfinger/rtlwifi_new)
No Result


3[SUP]rd[/SUP]:
echo "options rtl8723be fwlps=0" | sudo tee /etc/modprobe.d/rtl8723be.conf
No Result


4[SUP]th[/SUP]:
options rtl8723be fwlps=N ips=N added to /etc/modprobe.d/rtl8723be.conf
No Result


I'm literally at my wits' end with this issue - if a permanent fix is found, the provider wil have my never-ending gratitude!!

---

### Post by jeremy31 on 2016-03-18
```
sudo rm /etc/modprobe.d/rtl8723be.conf
sudo modprobe -r rtl8723be
sudo modprobe rtl8723be fwlps=N ant_sel=1
iwlist scan | egrep -i 'ssid|quality'
```
If it finds something in the scan compare it to the next result
```
sudo modprobe -r rtl8723be
sudo modprobe rtl8723be fwlps=N ant_sel=2
iwlist scan | egrep -i 'ssid|quality'
```

Which setting works better, if any?

---

### Post by ajgreeny on 2016-03-18
I have moved your original post from general view.
In future if the title needs changing you can use the Report Post button at bottom left and we can edit that for you to what you wish it to be..

---

### Post by lee-barber86 on 2016-03-19
@jeremy31: Thanks for the reply. The output from the first block of your code is below.

```

lee@lee-HP-ProBook-455-G2:~$ sudo rm /etc/modprobe.d/rtl8723be.conf
[sudo] password for lee: 
lee@lee-HP-ProBook-455-G2:~$ sudo modprobe -r rtl8723be
lee@lee-HP-ProBook-455-G2:~$ sudo modprobe rtl8723be fwlps=N ant_sel=1
lee@lee-HP-ProBook-455-G2:~$ iwlist scan | egrep -i 'ssid|quality'
eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

```

Output of 2nd block follows:

```

lee@lee-HP-ProBook-455-G2:~$ sudo modprobe -r rtl8723belee@lee-HP-ProBook-455-G2:~$ sudo modprobe rtl8723be fwlps=N ant_sel=2
lee@lee-HP-ProBook-455-G2:~$ iwlist scan | egrep -i 'ssid|quality'
eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

```

Unfortunately, no luck! It really is a puzzle - I've had an on/off relationship with Linux since I bought this laptop purely due to this problem.

---

### Post by lee-barber86 on 2016-03-19
@ajgreeny: Thanks for letting me know, will remember in future :)

---

### Post by lee-barber86 on 2016-03-19
It might help to know that this problem exist no matter the flavour of Ubuntu *or* Linux. i.e. whether I have Xubuntu/Ubuntu/Mint etc, or whether I have Arch/Suse/Fedora etc.

---

### Post by jeremy31 on 2016-03-19
> **lee-barber86 said:**
> It might help to know that this problem exist no matter the flavour of Ubuntu *or* Linux. i.e. whether I have Xubuntu/Ubuntu/Mint etc, or whether I have Arch/Suse/Fedora etc.

I figured you had the single antenna issue that is common for HP laptops now, let's see if Chili555's idea helps

[COLOR=#000000] I recommend that your regulatory domain be set explicitly. Check yours[/COLOR][COLOR=#000000]
```
sudo iw reg get
```[/COLOR]
[COLOR=#000000]If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [/COLOR][http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2)[COLOR=#000000] Then set it temporarily:[/COLOR][COLOR=#000000]
```
sudo iw reg set IS
```[/COLOR]
[COLOR=#000000]Of course, substitute your country code if not Iceland. Set it permanently:[/COLOR][COLOR=#000000]
```
gksudo gedit /etc/default/crda
```[/COLOR]
[COLOR=#000000]Use nano or kate or leafpad if you don't have the text editor gedit.[/COLOR]

[COLOR=#000000]Change the last line to read[/COLOR][COLOR=#000000]
```
REGDOMAIN=IS
```[/COLOR]
[COLOR=#000000]Proofread carefully, save and close the text editor.[/COLOR]

---

### Post by lee-barber86 on 2016-03-24
@Jeremy31: thanks for the solution, but it doesn't seem to have had any effect - aside from changing my regdomain for sure! 

I'm personally at the end of my knowledge... so I'll react to any suggestion of a hint of a solution...

---

### Post by jeremy31 on 2016-03-24
Run ```
./wireless-info
```

Post the new wireless-info.txt

---

### Post by chili555 on 2016-03-24
I suggest you try the suggestion at post #52  here: [http://ubuntuforums.org/showthread.php?t=2304607&page=6&highlight=8723be](http://ubuntuforums.org/showthread.php?t=2304607&page=6&highlight=8723be)

---

### Post by chili555 on 2016-03-25
> 2nd:
sudo make install the driver from this repo: [https://github.com/lwfinger/rtlwifi_new](https://github.com/lwfinger/rtlwifi_new)
No Result
I have been advised that the rtlwifi_new suite has been updated in the last ten days. If your installation of rtlwifi_new is older, I'd re-clone, recompile and reboot.

---

