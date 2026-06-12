---
title: "Ubuntu Wifi not working- 14.04 (x64)"
date: 2014-07-20
forum: Networking &amp; Wireless
---

### Post by quiskter on 2014-07-20
Hello. I installed Ubuntu a few weeks ago on my laptop, and it has been working beautifully up until now. The internet light on my laptop has gone from its usual blue to the orange that is displayed when WiFi is off. In the drop down menu, the "Wi-Fi Networks" selection is grayed out, and underneath it, in grayed out letters, it says "Wi-Fi is disabled". My computer is a HP Pavilion 2000-412nr, and it has been upgraded to 6GB of RAM. I don't know much about my WiFi card except it's made by Ralink. I have tried looking in the WiFi settings and pressing the switch on my computer to no avail. Connecting the laptop directly to my ethernet port on the router works, and I can get on the internet that way. Help would be greatly appreciated. As stated in the title, I am running Ubuntu 14.04 on an x64 system.

---

### Post by varunendra on 2014-07-20
Welcome to the forums quiskter!

Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by quiskter on 2014-07-21
```

    
    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

LaptopOfShame 3.13.0-24-generic x86_64,  Ubuntu 14.04 LTS, trusty

CPU    : AMD E-300 APU with Radeon(tm) HD Graphics
Memory : 5570 MB
Uptime : 14:32:23 up 17:03,  3 users,  load average: 0.87, 0.50, 0.26


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:3577]
    Kernel driver in use: r8169
07:00.0 Network controller [0280]: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390]
    Subsystem: Hewlett-Packard Company U98Z077.00 Half-size Mini PCIe Card [103c:1636]
    Kernel driver in use: rt2800pci


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 004: ID 04f2:b249 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface           Soft blocked  Hard blocked
0: hp-wifi: Wireless LAN      yes           no
1: phy0: Wireless LAN         no            yes


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

rt2800pci              13606  0 
rt2800mmio             20986  1 rt2800pci
hp_wmi                 14062  0 
rt2800lib              89076  2 rt2800pci,rt2800mmio
sparse_keymap          13948  1 hp_wmi
rt2x00pci              13287  1 rt2800pci
rt2x00mmio             13603  2 rt2800pci,rt2800mmio
rt2x00lib              55307  5 rt2x00pci,rt2800lib,rt2800pci,rt2800mmio,rt2x00mmio
mac80211              626489  3 rt2x00lib,rt2x00pci,rt2800lib
cfg80211              484040  2 mac80211,rt2x00lib
eeprom_93cx6           13344  1 rt2800pci
crc_ccitt              12707  1 rt2800lib
wmi                    19177  1 hp_wmi


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
rt2800pci     (1): nohwcrypt=N
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
============================o=============o===========o==============o=========o===========o==============o===========
 Interface & ID             | Type        | Driver    | State        | Default | Speed     | Support      | HW Addr   
============================o=============o===========o==============o=========o===========o==============o===========
 wlan0                      | 802.11 WiFi | rt2800pci | unavailable  | no      |           | WEP/WPA/WPA2 | <MAC wlan0>
----------------------------+-------------+-----------+--------------+---------+-----------+--------------+-----------
 eth0  [Wired connection 1] | Wired       | r8169     | connected    | yes     | 100 Mb/s  |              | <MAC eth0>

    Address:         192.168.1.12
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             192.168.1.1
----------------------------+-------------+-----------+--------------+---------+-----------+--------------+-----------


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

Wi-Fi connection 1   : ssid=NETGEAR60 | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.487/0.591/0.696/0.107 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1000ms
rtt min/avg/max/mdev = 0.079/0.088/0.097/0.009 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     14 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 14 (2.484 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~



blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[rt2800pci]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
firmware:       rt2860.bin
version:        2.3.0
srcversion:     D876F002AA85529257D61EB
depends:        rt2x00lib,rt2800lib,rt2800mmio,rt2x00mmio,rt2x00pci,eeprom_93cx6
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2800mmio]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rt2x00/rt2800mmio.ko
version:        2.3.0
srcversion:     F196893F5F72140CA847345
depends:        rt2800lib,rt2x00lib,rt2x00mmio

[rt2800lib]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
version:        2.3.0
srcversion:     9BD0087B6943A41E7FD8EDA
depends:        rt2x00lib,mac80211,crc-ccitt

[rt2x00pci]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
version:        2.3.0
srcversion:     9B9D0D0D0F8571AF43705FD
depends:        rt2x00lib,mac80211

[rt2x00mmio]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko
version:        2.3.0
srcversion:     07530604F5CE4EF69872C75
depends:        rt2x00lib

[rt2x00lib]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
version:        2.3.0
srcversion:     C57F87A3569F5363E79FD42
depends:        mac80211,cfg80211

[mac80211]
filename:       /lib/modules/3.13.0-24-generic/kernel/net/mac80211/mac80211.ko
srcversion:     C0F95BBF832E05DEFD722F4
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-24-generic/kernel/net/wireless/cfg80211.ko
srcversion:     8B3D642D1F2E6406EF33F74
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[eeprom_93cx6]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/misc/eeprom/eeprom_93cx6.ko
version:        1.0
srcversion:     215D8C1284A3C33B4A5A1C5
depends:        

[crc_ccitt]
filename:       /lib/modules/3.13.0-24-generic/kernel/lib/crc-ccitt.ko
srcversion:     2294FCAD06D727386004EEB
depends:        


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x1814:0x5390 (rt2800pci)
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

BOOT_IMAGE=/vmlinuz-3.13.0-24-generic root=/dev/mapper/it--vg-root ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    1.626654] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.627703] audit: initializing netlink socket (disabled)
[    2.396586] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   13.346599] wmi: Mapper loaded
[   14.865027] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 5390, rev 0502 detected
[   14.915321] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 5390 detected
[   19.892645] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   23.176710] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

    ======== Done ========

```

---

### Post by varunendra on 2014-07-22
Please check the BIOS to make sure the wireless adapter is not disabled from there. If it is not a UEFI based installation, also try resetting the BIOS.

I have found the wifi switches in HP models to be quite often buggy - they may take many seconds before responding to a touch/press, so also make sure you give it proper time to change its state (can be upto 20-30 seconds at most) after touching/pressing it. Although I know you must have already tried that before posting here, but just to be sure.

---

### Post by Bucky Ball on 2014-07-22
*Thread moved to **Networking & Wireless**.*

Welcome. Though you're a beginner, the networking experts hang here and they will be gentle. ;)

This is your wifi card and the driver it's using, as reported by your wireless info:
```

07:00.0 Network controller [0280]: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390]
    Subsystem: Hewlett-Packard Company U98Z077.00 Half-size Mini PCIe Card [103c:1636]
    Kernel driver in use: rt2800pci
```

From varun's response and from what I can see in your info, it does look like the card is simply switched off. At a glance I can't see anything glaringly obvious that's preventing things driver-wise. This has me curious, but it reads like this possibly just because the card is switched off:

```
 Interface           Soft blocked  Hard blocked
0: hp-wifi: Wireless LAN      yes           no
1: phy0: Wireless LAN         no            yes
```

Then there's this:

```
nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
============================o=============o===========o==============o=========o===========o==============o===========
 Interface & ID             | Type        | Driver    | State        | Default | Speed     | Support      | HW Addr   
============================o=============o===========o==============o=========o===========o==============o===========
 wlan0                      | 802.11 WiFi | rt2800pci | unavailable  | no      |           | WEP/WPA/WPA2 | <MAC wlan0>
```

.. where the wireless is not the default, which makes me think: do you have an ethernet cable plugged in when trying this? If so, unplug and reboot and see if that cranks up the card. Some lappy's defer to the cable if there's one plugged in. Finally, this:

```
resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1
```

Should that be 127.0.0.1? Varunendra?

---

### Post by praseodym on 2014-07-22
Please check:
```

echo "options hp_wmi wireless=1" | sudo tee /etc/modprobe.d/hp.conf
```
Reboot and check the buttons, plus
```

iwconfig
rfkill list
```

---

### Post by quiskter on 2014-07-22
The Wireless Adapter was not disabled in the BIOS, however, I tried turning it off and on again with no luck. I never would've thought to do a hard rest on the BIOS, but ultimately, that solved the problem. Thank you all for providing input, as well as a welcoming first encounter with the Ubuntu Forums.

---

### Post by varunendra on 2014-07-23
> **quiskter said:**
> I never would've thought to do a hard rest on the BIOS, but ultimately, that solved the problem.
Glad it worked.

It would be very nice if you can confirm whether the on/off switch also started working after this. Some times it is a stuck firmware code that causes such troubles. A BIOS reset is most often able to fix that, but in some cases, we sometimes also need to perform a complete power-cycle (disconnect AC power, battery, even motherboard battery in extreme cases > push power button to completely drain power from circuits > leave it for a few hours > reconnect battery, power and bingo!).

But a buggy on/off switch can make this problem frequent and I still need a confirmation if this trick can also fix that (I believe it can).

> **Bucky Ball said:**
> ```
resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1
```

Should that be 127.0.0.1? Varunendra?
That's fine as long as the /etc/NetworkManager/NetworkManager.conf file has this section -
```
[main]
plugins=ifupdown,keyfile,ofono
**dns=[COLOR="#0000CD"]dnsmasq[/COLOR]**
```
I can't explain this accurately, but the **dnsmasq** technique uses the local host address as a proxy which then redirects the DNS requests to the actual DNS server(s) that is/are reflected in the output of "**nm-too**l" (and can be manually read from "/run/nm-dns-dnsmasq.conf" file).

---

### Post by Bucky Ball on 2014-07-23
Good news. Enjoy! ;)

And thanks for the explanation, varunendra.

---

