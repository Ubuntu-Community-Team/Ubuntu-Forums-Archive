---
title: "Patriot Wireless key inconsistent functionality"
date: 2013-09-13
forum: Networking &amp; Wireless
---

### Post by AliPM on 2013-09-13
Hi,

I have a Patriot pcusbw1150 11n wireless adapter, which I have tried using in Ubuntu 12.04 and Mint 15 (both off the Live USB) and encountered the same issue. Linux detects the device and lists available networks, allows me to enter my WPA key into my network, but then immediately after telling me it is connected, it disconnects.

However - I have tried running a Live linux environment 4 times, and the first time (in Mint) I had the above problem, the second time (in Ubu 12.04) it connected and stayed connected until I logged out, and the two times I have tried since then I've had the problem again.

The adapter works fine in Windows 7 and XP, just needed drivers to be installed.

If anyone could tell me how I could go about fixing this or creating an error report that would be great. Thanks in advance

---

### Post by varunendra on 2013-09-14
Do you have a installed version as well or only trying on Live sessions? Please do the following, preferably on the installed one if you have one -

1) Please follow the "Wireless Script" link in my signature, download the script and note down the instructions to manually run it (no internet method).

2) Do a fresh boot, plug-in the adapter, try to connect and let it fail (or succeed if it can).

3) As soon as it fails, run the wireless_script and post back the "wireless-info.txt" file it generates. (or if it connects, use it for a min. or two, then run the script).

And.. do you have a wired connection available? It may make things easier if we needed to install some packages to do the fix.

---

### Post by AliPM on 2013-09-14
Thanks for the quick reply!

Since posting, I  installed Mint, after which I couldn't get any wireless connectivity at all so I played around with some commands I found in a Linux Mint forum thread, but nothing worked. Then I installed Ubuntu 12.04, which was still very inconsistent yesterday.

Today, however, my wireless adapter has decided to spite me and work fine, so here's the output from your script (run a few minutes after plugging in):

```

*************** info trace ***************

***** uname -a *****

Linux ali-laptop-ubu 3.8.0-30-generic #44~precise1-Ubuntu SMP Fri Aug 23 18:32:41 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise

***** lspci *****

00:07.0 Bridge [0680]: NVIDIA Corporation MCP61 Ethernet [10de:03ef] (rev a2)
    Subsystem: ASUSTeK Computer Inc. M4N68T series motherboard [1043:83a4]
    Kernel driver in use: forcedeth

***** lsusb *****

Bus 001 Device 005: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN
Bus 001 Device 004: ID 0951:1689 Kingston Technology 
Bus 002 Device 002: ID 13ba:0018 Unknown 
Bus 002 Device 004: ID 1c4f:0003 SiGma Micro HID controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11bgn  ESSID:"UPC968593"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC address removed>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=69/70  Signal level=-41 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


***** rfkill *****

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** lsmod *****

rtl8192cu              72751  0 
rtl8192c_common        49561  1 rtl8192cu
rtlwifi                81225  1 rtl8192cu
mac80211              630977  3 rtl8192cu,rtl8192c_common,rtlwifi
cfg80211              525244  2 rtlwifi,mac80211

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: wlan0  [UPC968593] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192cu
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Internet:        Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 80 WPA2
    www.irongatenet.net-7.3: Infra, <MAC address removed>, Freq 2462 MHz, Rate 11 Mb/s, Strength 94
    www.irongatenet.net-7.2: Infra, <MAC address removed>, Freq 2462 MHz, Rate 11 Mb/s, Strength 92
    www.irongatenet.net-7.1: Infra, <MAC address removed>, Freq 2462 MHz, Rate 11 Mb/s, Strength 92
    www.irongatenet.net-7.0: Infra, <MAC address removed>, Freq 2462 MHz, Rate 11 Mb/s, Strength 90
    www.irongatenet.net-7.4: Infra, <MAC address removed>, Freq 2462 MHz, Rate 11 Mb/s, Strength 90
    www.irongatenet.net-7.5: Infra, <MAC address removed>, Freq 2462 MHz, Rate 11 Mb/s, Strength 89
    *UPC968593:      Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 79 WPA2

  IPv4 Settings:
    Address:         192.168.1.13
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             213.46.172.36
    DNS:             213.46.172.37


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off



***** NetworkManager.state *****

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

auto lo
iface lo inet loopback


***** iwlist *****

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=67/70  Signal level=-43 dBm  
                    Encryption key:on
                    ESSID:"UPC968593"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000bc1325822
                    Extra: Last beacon: 32ms ago
                    IE: Unknown: 0009555043393638353933
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080400000000000000000000000000000000000000
                    IE: Unknown: DD790050F204104A0001101044000102103B00010310470010F26E98CB14E0E0BA5644BD9D928F4F5510210005436973636F10230005436973636F1024000631323334353610420007303030303030311054000800060050F204000110110006393638353933100800022008103C0001011049000600372A000120
                    IE: Unknown: DD090010180202F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00


***** resolv.conf *****

nameserver 127.0.0.1

***** blacklist *****

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

***** modinfo *****

filename:       /lib/modules/3.8.0-30-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
firmware:       rtlwifi/rtl8192cufw.bin
description:    Realtek 8192C/8188C 802.11n USB wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
srcversion:     B60B278C1942CBFF27FC8A0
alias:          usb:v7392p7822d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2357p0100d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v20F4p624Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB2Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p330Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3309d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3307d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0019d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0061d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8186d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p17ABd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p9021d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p8178d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07AAp0056d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0586p341Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp2103d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp2102d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp1004d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019p1201d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFFCd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFFBd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFF8d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFFAd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFF9d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFF7d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp317Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v9846p9041d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v4855p0091d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v4855p0090d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3359d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3358d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p7811d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v20F4p648Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pED17d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB2Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB2Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019p4902d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3308d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3357d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v103Cp1629d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v4856p0091d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0EB0p9071d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p005Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0052d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp5088d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p9041d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p8189d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p8188d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v06F8pE033d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp11F2d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp1102d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp817Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8178d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8754d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp819Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp818Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp817Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp817Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp817Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp817Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp817Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8177d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8176d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8170d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp018Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8191d*dc*dsc*dp*ic*isc*ip*in*
depends:        rtlwifi,mac80211,rtl8192c-common
intree:         Y
vermagic:       3.8.0-30-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

filename:       /lib/modules/3.8.0-30-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     E6FCDEDFF185E90DD643BE4
depends:        mac80211
intree:         Y
vermagic:       3.8.0-30-generic SMP mod_unload modversions 

filename:       /lib/modules/3.8.0-30-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     FA8C819FC50E5EFF6562FED
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.8.0-30-generic SMP mod_unload modversions 


***** udev rules *****

# PCI device 0x10de:/sys/devices/pci0000:00/0000:00:07.0 (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# USB device 0x0bda:0x8176 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[  361.947319] rtl8192cu: Chip version 0x10
[  362.040420] rtl8192cu: MAC address: <MAC address removed>
[  362.040429] rtl8192cu: Board Type 0
[  362.040666] rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
[  362.040715] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw.bin
[  362.081756] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[  362.082736] rtlwifi: wireless switch is on
[  362.137273] rtl8192cu: MAC auto ON okay!
[  362.169980] rtl8192cu: Tx queue select: 0x05
[  362.531439] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  362.531771] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  364.864148] wlan0: authenticate with <MAC address removed>
[  364.892540] wlan0: send auth to <MAC address removed> (try 1/3)
[  364.904332] wlan0: authenticated
[  364.907128] wlan0: associate with <MAC address removed> (try 1/3)
[  364.936177] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)rt 
[  364.936265] wlan0: associated
[  364.936343] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

****************** done ******************


```

I am experiencing lots of unexpected errors using Ubuntu today (with the add-apt-repository command and virtualbox) which I don't understand. Does this report give you any indication of why that might be?

I can connect to a wired connection if necessary.

FYI: When the wireless connection went down yesterday, it also caused the other computers on the network to  lose their wireless connections.

Thanks again

---

### Post by varunendra on 2013-09-14
> **AliPM said:**
> so here's the output from your script
Not my script, it's a courtesy of Wild Man and others who helped (Krytarik, anewguy, chili555, llua). I'm just using it frequently :P

Okay, so the driver your card uses is one of the many others which don't cooperate well with the newer kernels. So I don't yet know of a well tested fix. Let's try a few trivial things first, which can be done (and undone, if required) easily :

```

***** iwlist *****

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (**Channel 6**)
                    Quality=67/70  Signal level=-43 dBm  
                    Encryption key:on
                    ESSID:"UPC968593"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000bc1325822
                    Extra: Last beacon: 32ms ago
                    IE: Unknown: 0009555043393638353933
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        **Group Cipher : [COLOR="#FF0000"]TKIP[/COLOR]**
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

```
Are you using TKIP for group cipher (or algorithm)? Try changing it to AES (WPA2-PSK, AES). TKIP is rather inefficient and doesn't work well with many linux drivers.

> FYI: When the wireless connection went down yesterday, it also caused the other computers on the network to  lose their wireless connections.
Is N-channel enabled on your router? Do other computers get the benefit of speeds higher than 54 Mb/s?

I'd suggest to try disabling the N-channel on the router, permanently if you can, or at least temporarily for a test. Does it help improving performance on Ubuntu?

One more change you should try in the router is to change the channel from 6 to 1 or 11. If it doesn't help even the slightest, you may change it back.

In Ubuntu, please do (you may try this before above changes) -
```
echo "options rtl8192cu swenc=Y" | sudo tee /etc/modprobe.d/rtl8192cu.conf
sudo modprobe -rfv rtl8192cu
sudo modprobe -v rtl8192cu
```
The first command will permanently set the parameter swenc=Y for the driver. Most often it helps, especially in conjunction with the changes I asked above. Even if it doesn't help, it won't hurt the performance and can be reverted (if required) by deleting the /etc/modprobe.d/rtl8192.conf file that we created.

For now, please try these and report back.

And whenever the connection starts acting funny again, do a fresh boot, try to connect and let it fail, and run the script again to generate a fresh report. Post it back.

---

### Post by AliPM on 2013-09-14
Awesome, thanks for the tips. I inputted the terminal commands and so far all I have done is change the encrytion to AES. Haven't made any more of your changes yet.

What does the -f operator do with modprobe? Not sure I understand why the module needs to be removed and then reactivated.

N channel is enabled at the moment. Speed is reported as 72 Mb/s in Win7 and Linux. Connection speeds all seem pretty good so I won't disable it just yet.

Interesting that you said that these drivers aren't compatible with new drivers, because I plugged the adapter into my previous 10.04 box and it didn't recognise it (therefore I assumed it wasn't supported).

Another dumb question - would all of the above commands have the same effect in Mint? I'm guessing they would.

I will keep you posted if it stops working again. Thanks a bunch

---

### Post by varunendra on 2013-09-14
Awesome indeed ! (at least for now, hope it's permanent).

> **AliPM said:**
> What does the -f operator do with modprobe?
Thanks for bringing this up, it proved to be an eye opener question for me. I was about to answer - "to force unload the module" but thought let's take a look at its man page, and it turned out to be a "**force**" option, but for **loading**, not removing modules. My previous understanding was biased by the -f option in "rmmod" which is indeed for "force unloading" a module.

> Not sure I understand why the module needs to be removed and then reactivated.
We removed it so that we can reload it again with the option we set with the first command - "swenc=Y". It will be automatically loaded with that option from next boot.

> Interesting that you said that these drivers aren't compatible with new drivers, because I plugged the adapter into my previous 10.04 box and it didn't recognise it (therefore I assumed it wasn't supported).
The driver rtl8192cu always existed in the kernel (or at least since I know it), maybe the support for your device would have been added later (I believe since kernel 2.8 or 3..). However, many wireless drivers got broken due to some critical changes since kernel 3.5.something, and most of them are still suffering from various bugs, this one included.

> Another dumb question - would all of the above commands have the same effect in Mint? I'm guessing they would.
The commands I suggested so far - yes. There is probably no difference between Ubuntu and Mint on how the modules and related scripts, configurations etc. are handled.

---

