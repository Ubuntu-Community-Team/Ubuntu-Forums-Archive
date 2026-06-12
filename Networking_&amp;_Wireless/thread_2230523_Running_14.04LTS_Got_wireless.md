---
title: "Running 14.04LTS? Got wireless?"
date: 2014-06-19
forum: Networking &amp; Wireless
---

### Post by mbott on 2014-06-19
I've been struggling with a Netis WF2113 (RTL8192CE) for quite some time now. And for the last couple of days, I've been researching the posts of chili555, praseodym, varunendra and others who have attempted to help many people with similar issues to what I've encountered.  I've had no joy.  So, I'd rather switch than fight.  

I would really like to hear of what wireless cards people are running that are not having issues, either slow speeds, intermittent connections, etc.  So if you are running 14.04 and have a good wireless connection, what are you using?

Thanks!

-- 
Mike

---

### Post by TheFu on 2014-06-20
I have an Acer C720 chromebook - 14.04 and wifi works great - well - as good as wifi ever works. Connects to portable travel routers, older G and newer N routers, plus every wifi hotspot I've come across. Nothing replaces a wired GigE connection yet.

AR9462 Wireless Network Adapter
ath9k is the driver.

---

### Post by mbott on 2014-07-19
Well, this was a bust. Not that I expected a slew of positive responses here where people are looking for assistance, but I did hope for a couple. :(

-- 
Mike

---

### Post by kurt18947 on 2014-07-19
There are a few wifi adapters that I've had pretty good luck with.  One is a USB distant cousin of the device TheFu mentions -- Netgear WNA 1100.  It's an N150 device using an Atheros chipset so not the fastest but it seems pretty reliable.  A somewhat faster adapter is TrendNet TEW-649UB.  It uses a RealTek 8192SU chipset and has been plug 'n' play for a few years.  There are other adapters using the same chipsets that should function equally well though I don't know them by brand or model.  A risk with recommending specific models is that manufacturers will change chipsets without changing model designations, instead adding a ver. 2 or ver. B or something like that.  Linux wifi drivers support chipsets, not manufacturer model designations so a model that worked great 6 mos. ago may not work as well or at all today.  A resource I find useful with wifi compatibility questions is wikidevi.com.  It's a site dedicated to linux & wifi hardware/chipsets.  

I also agree with TheFu about wired ethernet being *so* much simpler when it's practical.  I've developed a fondness for Verizon's MoCA implementation.  It's pretty inexpensive using old repurposed Verizon FiOS routers to have an ethernet switch at every TV coax outlet if I so choose up to 8 MoCA devices total, I believe.

---

### Post by varunendra on 2014-07-21
Not much can be tried with rtl8192ce driver in the latest kernels until this bug is fixed : [https://bugs.launchpad.net/bugs/1342703](https://bugs.launchpad.net/bugs/1342703)

But to let us see if some tweaking can be possible with the existing driver to optimize performance, I think you should post a report of wireless_script. Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

### Post by mbott on 2014-07-21
[http://ubuntuforums.org/showthread.php?t=2216871&p=12987742#post12987742](http://ubuntuforums.org/showthread.php?t=2216871&p=12987742#post12987742)

---

### Post by varunendra on 2014-07-21
A line on what you want us to do with that link would have been very nice.

But no comments is probably even better, just made me realize that I should be short of time too, got some important things to take care of..

---

### Post by chili555 on 2014-07-21
Not a single issue at all for my Intel Corporation Centrino Advanced-N 6200.> wlan0     IEEE 802.11abgn  ESSID:"GBR1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: xx:D7:19:41:54:xx   
          Bit Rate=86.7 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=54/70  Signal level=-56 dBm  
By the way, usually people with no problems don't come here.

---

### Post by mbott on 2014-07-21
> **chili555 said:**
> Not a single issue at all for my Intel Corporation Centrino Advanced-N 6200.By the way, usually people with no problems don't come here.

And I believe I pointed that out myself.

> **mbott said:**
> Well, this was a bust. Not that I expected a slew of positive responses here where people are looking for assistance, but I did hope for a couple. :(

-- 
Mike

;)

---

### Post by mbott on 2014-07-21
Here is the script results:

> 
	======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

mdesktop 3.13.0-32-generic x86_64,  Ubuntu 14.04 LTS, trusty

CPU    : Intel(R) Core(TM) i5-4670K CPU @ 3.40GHz
Memory : 15735 MB
Uptime : 18:21:07 up 1 day, 10:06,  2 users,  load average: 0.09, 0.17, 0.13


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
	Subsystem: ASUSTeK Computer Inc. Device [1043:8554]
	Kernel driver in use: r8169
--
06:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192CE PCIe Wireless Network Adapter [10ec:8178] (rev 01)
	Subsystem: Realtek Semiconductor Co., Ltd. RTL8192CE PCIe Wireless Network Adapter [10ec:8178]
	Kernel driver in use: rtl8192ce


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 003 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:"cz_2075"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC C-01 >   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=62/70  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

rtl8192ce              53550  0 
rtl_pci                26690  1 rtl8192ce
rtlwifi                63475  2 rtl_pci,rtl8192ce
rtl8192c_common        53172  1 rtl8192ce
mac80211              630653  3 rtl_pci,rtlwifi,rtl8192ce
eeepc_wmi              13151  0 
asus_wmi               24191  1 eeepc_wmi
sparse_keymap          13948  1 asus_wmi
cfg80211              484040  2 mac80211,rtlwifi
wmi                    19177  1 asus_wmi
video                  19476  2 i915,asus_wmi


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
eeepc_wmi     (1): hotplug_wireless=N
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
rtl8192ce     (5): debug=0 | fwlps=Y | ips=Y | swenc=N | swlps=N
video         (3): allow_duplicates=N | brightness_switch_enabled=Y | use_native_backlight=-1
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
===============================o=============o===========o==============o=========o===========o==============o===========
 Interface & ID                | Type        | Driver    | State        | Default | Speed     | Support      | HW Addr   
===============================o=============o===========o==============o=========o===========o==============o===========
 wlan0  [cz_2075]              | 802.11 WiFi | rtl8192ce | connected    | no      | 1 Mb/s    | WEP/WPA/WPA2 | <MAC wlan0>

    *cz_2075:        Infra, <MAC C-01 >, Freq 2437 MHz, Rate 54 Mb/s, Strength 72 WPA2

    Address:         192.168.2.19
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1
    DNS:             192.168.2.1
-------------------------------+-------------+-----------+--------------+---------+-----------+--------------+-----------
 eth0  [Ethernet connection 1] | Wired       | r8169     | connected    | yes     | 100 Mb/s  |              | <MAC eth0>

    Address:         192.168.2.18
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1
    DNS:             192.168.2.1
-------------------------------+-------------+-----------+--------------+---------+-----------+--------------+-----------


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

no-auto-default=<MAC eth0>,

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~

cz_2075              : ssid=cz_2075 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

--- 192.168.2.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.513/0.519/0.525/0.006 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.020/0.027/0.035/0.009 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")
country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)

          Current Frequency:2.437 GHz (Channel 6)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 >
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=26 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000c71a9b3d1
                    Extra: Last beacon: 300ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-01 >
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-2 dBm  
                    Encryption key:on
                    ESSID:"cz_2075"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000c6f15f458
                    Extra: Last beacon: 43120ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[rtl8192ce]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfwU_B.bin
firmware:       rtlwifi/rtl8192cfwU.bin
firmware:       rtlwifi/rtl8192cfw.bin
srcversion:     EF063698748457BBEDB4633
depends:        rtlwifi,rtl_pci,rtl8192c-common,mac80211
parm:           swenc:Set to 1 for software crypto (default 0)
parm:           ips:Set to 0 to not use link power save (default 1)
parm:           swlps:Set to 1 to use SW control power save (default 0)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl_pci]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
srcversion:     D5E4890DC428FA5A1BF92DF
depends:        mac80211,rtlwifi

[rtlwifi]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
srcversion:     E1F4663325225EE8DBA54CA
depends:        mac80211,cfg80211

[rtl8192c_common]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
srcversion:     32F826C623BC49F764F7974
depends:        

[mac80211]
filename:       /lib/modules/3.13.0-32-generic/kernel/net/mac80211/mac80211.ko
srcversion:     8ADA881D348148A3358334C
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-32-generic/kernel/net/wireless/cfg80211.ko
srcversion:     E786D076B61F97809B04B64
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:0x8178 (rtl8192ce)
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

BOOT_IMAGE=/boot/vmlinuz-3.13.0-32-generic root=UUID=03224d01-2b46-430c-86ce-0adb9655871f ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.397565] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.397728] audit: initializing netlink socket (disabled)
[    0.687529] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   13.102520] wmi: Mapper loaded
[   13.639153] asus_wmi: ASUS WMI generic driver loaded
[   13.661378] asus_wmi: Initialization: 0x0
[   13.661390] asus_wmi: BIOS WMI version: 0.9
[   13.661410] asus_wmi: SFUN value: 0x0
[   13.661576] input: Eee PC WMI hotkeys as /devices/platform/eeepc-wmi/input/input5
[   13.662028] asus_wmi: Backlight controlled by ACPI video driver
[   14.009114] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[   14.226248] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   14.226359] rtlwifi: wireless switch is on
[   17.490674] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.713756] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.713925] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[122813.203539] wlan0: authenticate with <MAC C-01 >
[122813.213641] wlan0: send auth to <MAC C-01 > (try 1/3)
[122813.217453] wlan0: authenticated
[122813.217556] rtl8192ce 0000:06:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[122813.217558] rtl8192ce 0000:06:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[122813.218866] wlan0: associate with <MAC C-01 > (try 1/3)
[122813.220908] wlan0: RX AssocResp from <MAC C-01 > (capab=0x411 status=0 aid=4)
[122813.221014] wlan0: associated
[122813.221026] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[122813.366966] WARNING: CPU: 0 PID: 0 at /build/buildd/linux-3.13.0/net/mac80211/rate.c:526 ieee80211_get_tx_rates+0x273/0x7f0 [mac80211]()
[122813.366969] Modules linked in: ctr ccm joydev rfcomm bnep bluetooth binfmt_misc snd_hda_codec_hdmi snd_hda_codec_realtek arc4 rtl8192ce x86_pkg_temp_thermal intel_powerclamp rtl_pci coretemp rtlwifi rtl8192c_common kvm_intel snd_hda_intel kvm i915 snd_hda_codec mac80211 eeepc_wmi asus_wmi snd_hwdep sparse_keymap snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq snd_seq_device parport_pc snd_timer mei_me ppdev crct10dif_pclmul lp crc32_pclmul cfg80211 drm_kms_helper drm parport mei ghash_clmulni_intel aesni_intel snd aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd soundcore serio_raw wmi video i2c_algo_bit mac_hid lpc_ich hid_logitech_dj usbhid hid usb_storage r8169 ahci psmouse libahci mii
[122813.367075]  [<ffffffffa03cd3ad>] ? rtl_is_special_data+0x2d/0x110 [rtlwifi]

	======== Done ========

---

### Post by WinEunuchs2Unix on 2014-07-21
> **chili555 said:**
> Not a single issue at all for my Intel Corporation Centrino Advanced-N 6200.By the way, usually people with no problems don't come here.

Yup should have ordered that one instead of Advanced-N 6235.  Apparently hindsight is not only 20/20 but chilli555 :D

---

### Post by mbott on 2014-10-08
> **WinEunuchs2Unix said:**
> Yup should have ordered that one instead of Advanced-N 6235.  Apparently hindsight is not only 20/20 but chilli555 :D

Finally got around to dumping the Netis WF-2113 and replaced it with a TP-Link TL-WN951N which is Atheros based (AR922X Wireless Network Adapter (rev 01)). Took about 5 minutes to put in service and wireless is well again.

All smiles here.

-- 
Mike

---

### Post by Hamburgian on 2014-10-20
Hi mbott,

Glad to hear you've struck lucky with your WN951N wifi card. I wasn't so lucky, but I guess this is a motherboard thing. I'm using an MSI K9N neo and I can't get this card to work properly. I've also followed chili555, praseodym, varunendra and hundreds of other posts. The card often connects, but just as often not. When it is connected, it drops out for no apparent reason and is also painfully slow. I've been at it  for 7 weeks now and have significantly shortened my hard drive's life. The spin-up/down count stood at 1143 when I began my saga, and now stands at 1506 - some 250+ pointless reboots after applying the suggested changes. So I've given up and gone down the power-line road.

---

