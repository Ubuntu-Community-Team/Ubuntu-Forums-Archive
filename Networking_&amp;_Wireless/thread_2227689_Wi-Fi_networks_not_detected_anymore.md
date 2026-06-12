---
title: "Wi-Fi networks not detected anymore"
date: 2014-06-03
forum: Networking &amp; Wireless
---

### Post by Taoma on 2014-06-03
Hi,

[B]My Wi-Fi networks are not detected anymore.
[/B]
**What triggered it : **My computer froze and I ended up having to restart it using the power switch. In case it could be relevant : it froze while I was using Calc, trying to drag and drop items (bug already filed in LibreOffice).

**What I have attempted to solve it :** I was under Kubuntu 13.10 when it happened, so I took this opportunity to reinstall the OS with Kubuntu 14.04 (no config files were kept), but it didn't solve it.

**"sudo iwlist wlan0 scan"** shows "wlan0 No scan results".

** /var/lib/NetworkManager/NetworkManager.state **shows :
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true
WiMAXEnabled=true

**Any idea what could I try ?** I would greatly appreciate any suggestion.

---

### Post by varunendra on 2014-06-05
Welcome to the forums Taoma!

Please post back the outputs of -
```
lspci -nnk | grep -iA2 net
lsusb
```

And if it is a PCMCIA card, then also the output of -
```
pccardctl info
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by Taoma on 2014-06-05
Thanks for this nice welcoming message, Varunendra.

Here are the results :

```

lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723AE PCIe Wireless Network Adapter [10ec:8723]
        Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0726]
        Kernel driver in use: rtl8723ae
--
03:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0a)
        Subsystem: CLEVO/KAPOK Computer Device [1558:0240]
        Kernel driver in use: r8169

```

```

lsusb
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 017: ID 19d2:1365 ZTE WCDMA Technologies MSM 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 0bda:8723 Realtek Semiconductor Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```

To be able to pick up the available Wi-Fi network and be connected to the internet, I am currenlty using my Firefox OS mobile as a modem, through one of my USB port.

No, I am not using a PCMCIA card.

---

### Post by varunendra on 2014-06-06
Is the output of 'lsusb' from when the mobile was connected via USB? The device "0bda:8723" is interesting.

While the mobile is plugged in, working as a modem, please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

### Post by Taoma on 2014-06-08
Here are the results :

```
    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

AirisKubi 3.13.0-27-generic i686,  Ubuntu 14.04 LTS, trusty

CPU    : Intel(R) Core(TM) i7-3630QM CPU @ 2.40GHz
Memory : 7986 MB
Uptime : 12:29:26 up 1 day, 13:36,  3 users,  load average: 0,02, 0,08, 0,07


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723AE PCIe Wireless Network Adapter [10ec:8723]
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0726]
    Kernel driver in use: rtl8723ae
--
03:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0a)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0240]
    Kernel driver in use: r8169


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 19d2:1365 ZTE WCDMA Technologies MSM 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 0bda:8723 Realtek Semiconductor Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
1: phy0: Wireless LAN      no            no
6: hci0: Bluetooth         no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

rtl8723ae              76459  0 
rtl8723_common         22417  1 rtl8723ae
rtl_pci                26314  1 rtl8723ae
rtlwifi                52835  2 rtl_pci,rtl8723ae
mac80211              546013  3 rtl_pci,rtlwifi,rtl8723ae
cfg80211              409394  2 mac80211,rtlwifi
wmi                    18673  0 


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
rtl8723ae     (5): debug=0 | fwlps=Y | ips=Y | swenc=N | swlps=N
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
============================o=============o============o==============o=========o===========o==============o===========
 Interface & ID             | Type        | Driver     | State        | Default | Speed     | Support      | HW Addr   
============================o=============o============o==============o=========o===========o==============o===========
 usb0  [Wired connection 2] | Wired       | rndis_host | connected    | yes     |           |              | <MAC ID removed>

    Address:         192.168.0.10
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1
    DNS:             192.168.0.1
----------------------------+-------------+------------+--------------+---------+-----------+--------------+-----------
 eth0                       | Wired       | r8169      | unavailable  | no      |           |              | <MAC eth0>
----------------------------+-------------+------------+--------------+---------+-----------+--------------+-----------
 wlan0                      | 802.11 WiFi | rtl8723ae  | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>
----------------------------+-------------+------------+--------------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true
WiMAXEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~
 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 usb0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 usb0

--- 192.168.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 0.592/0.803/1.015/0.213 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.032/0.036/0.040/0.004 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : fr_FR.UTF-8)
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     No scan results


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[rtl8723ae]
filename:       /lib/modules/3.13.0-27-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723ae/rtl8723ae.ko
firmware:       rtlwifi/rtl8723fw_B.bin
firmware:       rtlwifi/rtl8723fw.bin
srcversion:     17B20EFB163E8FE9251294F
depends:        rtlwifi,rtl8723-common,rtl_pci,mac80211
parm:           swenc:Set to 1 for software crypto (default 0)
parm:           ips:Set to 0 to not use link power save (default 1)
parm:           swlps:Set to 1 to use SW control power save (default 0)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl8723_common]
filename:       /lib/modules/3.13.0-27-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko
srcversion:     D1807280DBDC9B8A7EBDAB7
depends:        

[rtl_pci]
filename:       /lib/modules/3.13.0-27-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
srcversion:     9B7F19319428FF0EFE7E350
depends:        mac80211,rtlwifi

[rtlwifi]
filename:       /lib/modules/3.13.0-27-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
srcversion:     27E91755814596D634B7709
depends:        mac80211,cfg80211

[mac80211]
filename:       /lib/modules/3.13.0-27-generic/kernel/net/mac80211/mac80211.ko
srcversion:     B09A94F74DCA60EBD06A6B6
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-27-generic/kernel/net/wireless/cfg80211.ko
srcversion:     8B3D642D1F2E6406EF33F74
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:0x8723 (rtl8723ae)
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

BOOT_IMAGE=/boot/vmlinuz-3.13.0-27-generic root=UUID=a45e3421-77c5-4b9c-b7a9-df0024b7eb1f ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    2.421066] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    2.421354] audit: initializing netlink socket (disabled)
[    3.041669] wmi: Mapper loaded
[    3.050199] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    4.950930] rtl8723ae: Using firmware rtlwifi/rtl8723fw_B.bin
[    4.968223] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    4.968445] rtlwifi: wireless switch is on
[    5.123417] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    5.546769] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    5.547132] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2029.208019] rtlwifi: wireless switch is on
[27002.289283] rtlwifi: wireless switch is on
[27430.310985] rtlwifi: wireless switch is on
[29478.170324] rtlwifi: wireless switch is on
[38897.411139] rtlwifi: wireless switch is on

    ======== Done ========


```

Refering to my previous post, the usb line corresponding to my mobile phone is this one :
```
Bus 001 Device 017: ID 19d2:1365 ZTE WCDMA Technologies MSM 
```

I don't know what the line you found interesting corresponds to, since I don't have anything else plugged in :
```
Bus 003 Device 002: ID 0bda:8723 Realtek Semiconductor Corp. 
``` Why is it more unusual than the other lines ?

Thanks again, Varunendra, for taking the time to look into my network issue.

---

### Post by varunendra on 2014-06-11
Posting in a hurry, so I may have missed something, but in a quick glance I couldn't notice anything wrong with whatever is in the script report (maybe the 'Wrong' part is what does not exist in it - the wireless networks!).

Did you try with the pci wifi alone? No ethernet cable, no usb devices (adapter or mobile phones).

About this -
> **Taoma said:**
> I don't know what the line you found interesting corresponds to, since I don't have anything else plugged in :
```
Bus 003 Device 002: ID 0bda:8723 Realtek Semiconductor Corp. 
``` Why is it more unusual than the other lines ?

It was nothing, I was simply confused by seeing '8723' in both lspci and lsusb. The lsusb one is simply the integrated bluetooth part of the card, and I had missed that point in confusion, so nothing wrong or surprising there.

---

### Post by Taoma on 2014-06-13
Thanks for getting back to me, Varun.

Yes, I tried the pci wifi alone, without USB or Ethernet cable, and no WiFi network is detected.

---

### Post by varunendra on 2014-06-15
If it is not a UEFI based setup, please try resetting the BIOS to defaults. Did you reboot after the problem occurred? The last report you posted showed the system to be running from more than a day. I won't be surprised if you, like I used to, keep even laptops continuously running for weeks or months.. :p

**PS:**
I don't know why this driver scares me a bit, but can we see a fresh report of wireless_script generated within 5 - 10 minutes after a reboot?

---

### Post by Taoma on 2014-06-16
I restarted my computer and resetted my BIOS settings to the default ones, but it didn't solve it. And I couldn't see any difference in the the new "wireless-info" generated, beside the uptime. I made further research however, since I realised it was more a hardware issue than a software one, and someone had resolved a similar WiFi network issue by unplugging the charger and removing the battery before putting it back to reboot the computer. And that's what worked for me too : I can now detect all the WiFi networks again :)

Thanks again, Varun, for the time you took looking into my issue. It is always easier to carry on looking for answers when someone else is also looking into it and makes useful suggestions.

---

