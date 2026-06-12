---
title: "wifi stops working"
date: 2014-09-02
forum: Networking &amp; Wireless
---

### Post by bertmung on 2014-09-02
I have 14.04 installed on a Lenovo X120e. I'm having the same problem with a Cisco WRT54G wireless router and the wireless modem from FairPoint that I use at another location. 

From time to time the wireless stops working. The frequency varies. Usually the quickest way to re establish the connection is to disable and re enable Wi-Fi. 

Usually, this is a minor annoyance, but sometimes I'm disabling and re enabling Wi-Fi everytime I navigate to a new link.

---

### Post by varunendra on 2014-09-04
Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by bertmung on 2014-09-04
Thanks Varun,

```


	======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

bert-ThinkPad-X120e 3.13.0-35-generic x86_64,  Ubuntu 14.04.1 LTS, trusty

CPU    : AMD E-350 Processor
Memory : 3551 MB
Uptime : 12:16:48 up  3:35,  2 users,  load average: 0.62, 0.63, 0.57


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
	Subsystem: Lenovo Device [17aa:21df]
	Kernel driver in use: r8169
04:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
	Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8195]
	Kernel driver in use: rtl8192ce


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 003: ID 5986:01a6 Acer, Inc Lenovo Integrated Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 062a:410c Creative Labs 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:"dolcevirus4"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC C-NA *dolcevirus4 1>   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=66/70  Signal level=-44 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2324   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

rtl8192ce              53550  0 
rtl_pci                26690  1 rtl8192ce
rtlwifi                63475  2 rtl_pci,rtl8192ce
rtl8192c_common        53172  1 rtl8192ce
mac80211              630653  3 rtl_pci,rtlwifi,rtl8192ce
cfg80211              484040  2 mac80211,rtlwifi
wmi                    19177  0 


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
rtl8192ce     (5): debug=0 | fwlps=Y | ips=Y | swenc=N | swlps=N
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
======================o=============o===========o=============o=========o===========o==============o===========
 Interface & ID       | Type        | Driver    | State       | Default | Speed     | Support      | HW Addr   
======================o=============o===========o=============o=========o===========o==============o===========
 wlan0  [dolcevirus4] | 802.11 WiFi | rtl8192ce | connected   | yes     | 18 Mb/s   | WEP/WPA/WPA2 | <MAC wlan0>

    Subway- Guest:   Infra, <MAC C-NA Subway- Guest 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 54
    *dolcevirus4:    Infra, <MAC C-NA *dolcevirus4 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 70 WPA
    sheepfarm:       Infra, <MAC C-NA sheepfarm 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA2
    BenDev4:         Infra, <MAC C-NA BenDev4 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27
    CableWiFi:       Infra, <MAC C-NA CableWiFi 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 4

    Address:         192.168.72.116
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.72.1
    DNS:             192.168.72.1
----------------------+-------------+-----------+-------------+---------+-----------+--------------+-----------
 eth0                 | Wired       | r8169     | unavailable | no      |           |              | <MAC eth0>
----------------------+-------------+-----------+-------------+---------+-----------+--------------+-----------


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
 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.72.1    0.0.0.0         UG    0      0        0 wlan0
192.168.72.0    0.0.0.0         255.255.255.0   U     9      0        0 wlan0

--- 192.168.72.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 2.480/3.265/4.050/0.785 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.078/0.082/0.087/0.010 ms


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

          Current Frequency:2.462 GHz (Channel 11)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

Aquiring of root rights failed.


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[rtl8192ce]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
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
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
srcversion:     D5E4890DC428FA5A1BF92DF
depends:        mac80211,rtlwifi

[rtlwifi]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
srcversion:     E1F4663325225EE8DBA54CA
depends:        mac80211,cfg80211

[rtl8192c_common]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
srcversion:     32F826C623BC49F764F7974
depends:        

[mac80211]
filename:       /lib/modules/3.13.0-35-generic/kernel/net/mac80211/mac80211.ko
srcversion:     D491AB7C521706DA5F4BE7C
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-35-generic/kernel/net/wireless/cfg80211.ko
srcversion:     C2478077E22138832B71659
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[wmi]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:0x8176 (rtl8192ce)
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

BOOT_IMAGE=/boot/vmlinuz-3.13.0-35-generic root=UUID=e45bf20b-13f2-4f6b-bd32-591c50340533 ro acpi_osi=Linux quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    2.204862] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    2.205613] audit: initializing netlink socket (disabled)
[    2.726260] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    8.549807] psmouse serio5: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   23.567205] wmi: Mapper loaded
[   24.230372] thinkpad_acpi: http://ibm-acpi.sf.net/
[   24.230939] thinkpad_acpi: Unsupported brightness interface, please contact ibm-acpi-devel@lists.sourceforge.net
[   24.588928] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[   24.891211] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   24.891717] rtlwifi: wireless switch is on
[   25.348564] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   28.769312] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.770436] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   30.946574] wlan0: authenticate with <MAC C-NA *dolcevirus4 1>
[   30.965588] wlan0: send auth to <MAC C-NA *dolcevirus4 1> (try 1/3)
[   30.988440] wlan0: authenticated
[   30.988969] rtl8192ce 0000:04:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[   30.992956] wlan0: associate with <MAC C-NA *dolcevirus4 1> (try 1/3)
[   30.995504] wlan0: RX AssocResp from <MAC C-NA *dolcevirus4 1> (capab=0x411 status=0 aid=2)
[   30.995720] wlan0: associated
[   30.995803] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   32.005006] wlan0: deauthenticating from <MAC C-NA *dolcevirus4 1> by local choice (reason=2)
[   32.006076] wlan0: authenticate with <MAC C-NA *dolcevirus4 1>
[   32.006291] wlan0: send auth to <MAC C-NA *dolcevirus4 1> (try 1/3)
[   32.012796] wlan0: authenticated
[   32.013564] rtl8192ce 0000:04:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[   32.016491] wlan0: associate with <MAC C-NA *dolcevirus4 1> (try 1/3)
[   32.019216] wlan0: RX AssocResp from <MAC C-NA *dolcevirus4 1> (capab=0x411 status=0 aid=2)
[   32.019426] wlan0: associated
[ 2939.752063] wlan0: deauthenticated from <MAC C-NA *dolcevirus4 1> (Reason: 7)
[ 2941.037344] wlan0: authenticate with <MAC C-NA *dolcevirus4 1>
[ 2941.037636] wlan0: send auth to <MAC C-NA *dolcevirus4 1> (try 1/3)
[ 2941.043977] wlan0: authenticated
[ 2941.044373] rtl8192ce 0000:04:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 2941.055671] wlan0: associate with <MAC C-NA *dolcevirus4 1> (try 1/3)
[ 2941.060168] wlan0: RX AssocResp from <MAC C-NA *dolcevirus4 1> (capab=0x411 status=0 aid=2)
[ 2941.060369] wlan0: associated
[ 3114.908028] wlan0: deauthenticating from <MAC C-NA *dolcevirus4 1> by local choice (reason=3)
[ 3118.338478] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3120.063281] wlan0: authenticate with <MAC C-NA *dolcevirus4 1>
[ 3120.076508] wlan0: send auth to <MAC C-NA *dolcevirus4 1> (try 1/3)
[ 3120.080178] wlan0: authenticated
[ 3120.080521] rtl8192ce 0000:04:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 3120.084143] wlan0: associate with <MAC C-NA *dolcevirus4 1> (try 1/3)
[ 3120.087669] wlan0: RX AssocResp from <MAC C-NA *dolcevirus4 1> (capab=0x411 status=0 aid=2)
[ 3120.087888] wlan0: associated
[ 3120.089389] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3121.110269] wlan0: deauthenticating from <MAC C-NA *dolcevirus4 1> by local choice (reason=2)
[ 3121.131981] wlan0: authenticate with <MAC C-NA *dolcevirus4 1>
[ 3121.132156] wlan0: send auth to <MAC C-NA *dolcevirus4 1> (try 1/3)
[ 3121.134969] wlan0: authenticated
[ 3121.135535] rtl8192ce 0000:04:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 3121.139571] wlan0: associate with <MAC C-NA *dolcevirus4 1> (try 1/3)
[ 3121.142201] wlan0: RX AssocResp from <MAC C-NA *dolcevirus4 1> (capab=0x411 status=0 aid=2)
[ 3121.142445] wlan0: associated
[10912.146288] wlan0: deauthenticated from <MAC C-NA *dolcevirus4 1> (Reason: 7)
[10913.429976] wlan0: authenticate with <MAC C-NA *dolcevirus4 1>
[10913.437324] wlan0: send auth to <MAC C-NA *dolcevirus4 1> (try 1/3)
[10913.440994] wlan0: authenticated
[10913.442821] rtl8192ce 0000:04:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[10913.445909] wlan0: associate with <MAC C-NA *dolcevirus4 1> (try 1/3)
[10913.449029] wlan0: RX AssocResp from <MAC C-NA *dolcevirus4 1> (capab=0x411 status=0 aid=2)
[10913.449242] wlan0: associated
[11092.364084] wlan0: deauthenticated from <MAC C-NA *dolcevirus4 1> (Reason: 7)
[11108.424004] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[11121.877379] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[11123.649835] wlan0: authenticate with <MAC C-NA *dolcevirus4 1>
[11123.660613] wlan0: send auth to <MAC C-NA *dolcevirus4 1> (try 1/3)
[11123.666337] wlan0: authenticated
[11123.666976] rtl8192ce 0000:04:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[11123.670687] wlan0: associate with <MAC C-NA *dolcevirus4 1> (try 1/3)
[11123.675122] wlan0: RX AssocResp from <MAC C-NA *dolcevirus4 1> (capab=0x411 status=0 aid=2)
[11123.675352] wlan0: associated
[11123.675446] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[11123.694126] wlan0: deauthenticating from <MAC C-NA *dolcevirus4 1> by local choice (reason=2)
[11123.698779] wlan0: authenticate with <MAC C-NA *dolcevirus4 1>
[11123.699058] wlan0: send auth to <MAC C-NA *dolcevirus4 1> (try 1/3)
[11123.700996] wlan0: authenticated
[11123.706347] rtl8192ce 0000:04:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[11123.706662] wlan0: associate with <MAC C-NA *dolcevirus4 1> (try 1/3)
[11123.711153] wlan0: RX AssocResp from <MAC C-NA *dolcevirus4 1> (capab=0x411 status=0 aid=2)
[11123.711309] wlan0: associated

	======== Done ========

```

---

### Post by varunendra on 2014-09-05
> **bertmung said:**
> ```
iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

[COLOR="#FF0000"]Aquiring of root rights failed.[/COLOR]
```

Did you not supply your login password when asked by the script? It is required to run "iwlist scan" command with root access, so that it can show live results. Otherwise it'll just show buffered/leftover results (I don't know what "leftover" means here, but the man page of "iwlist" says so). The sudo password, once supplied, is also used (in this script, not the regular one that is in the sticky) to grep saved connection profiles (filtering out sensitive parts).

Anyway, none of the above looks so important for now, so I guess we can proceed with what we have now.

Please try changing the encryption in your router to WPA2-PSK with AES (CCMP) if it supports that. Currently it is using WPA (1) which essentially requires 'TKIP' which is older, inferior and inefficient compared to 'AES', and can be problematic sometimes. Reboot the router after saving the change.

Additionally, if required, please try some driver parameters in Ubuntu -
```
echo "options rtl8192ce fwlps=N ips=N" | sudo tee /etc/modprobe.d/rtl8192ce.conf
```
Reboot for the above to take effect. (usually we try above in temporary mode, and don't require a reboot, but I have recently started doubting that method (thanks to the intel driver)..., feel free to consider me paranoid if you wish :p).

---

### Post by skymandr-gmail on 2014-12-19
Hi! I'm having a very simliar issue, and since Bertmung hasn't replied, perhaps I can jump in? :)

I've been having the problem with wifi disconnecting frequently since 13.04 on my Lenovo TP Edge, and sometimes it turns horribly slow, as if hanging by a package. I was hoping 14.04 would solve it, but no, and now I've finally grown tired of it. As stated above the quickest fix is usually to restart the disable and enable wifi. I have two further observations, that may be anecdotal and I have yet to confirm properly: It seems that the wifi stays alive better when I e.g. stream video, whereas disconnect happens most frequently when leave the computer, browse the internet or write forum posts (such as now). I also seem to experience the problems more at home, using my Linksys WRT54GL Router than at other places, but other computers in my household don't have this problem with the router in question.

Here is the output from the (old version of the) wireless_script:

[ATTACH=CONFIG]258684[/ATTACH]

And here is a snippet from my Kernel log of an disconnection event, showing three disassociation events, the third of which did not reassociate.

```
Dec 18 22:37:43 Colin kernel: [169259.401945] wlan0: deauthenticated from theMACaddress (Reason: 7)
Dec 18 22:37:43 Colin kernel: [169259.429654] cfg80211: Calling CRDA to update world regulatory domain
Dec 18 22:37:43 Colin kernel: [169259.437068] cfg80211: World regulatory domain updated:
Dec 18 22:37:43 Colin kernel: [169259.437078] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Dec 18 22:37:43 Colin kernel: [169259.437085] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 18 22:37:43 Colin kernel: [169259.437091] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 18 22:37:43 Colin kernel: [169259.437097] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Dec 18 22:37:43 Colin kernel: [169259.437102] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 18 22:37:43 Colin kernel: [169259.437108] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 18 22:37:44 Colin kernel: [169260.687567] wlan0: authenticate with theMACaddress
Dec 18 22:37:44 Colin kernel: [169260.695934] wlan0: send auth to theMACaddress (try 1/3)
Dec 18 22:37:44 Colin kernel: [169260.697748] wlan0: authenticated
Dec 18 22:37:44 Colin kernel: [169260.698193] rtl8192ce 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
Dec 18 22:37:44 Colin kernel: [169260.698202] rtl8192ce 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
Dec 18 22:37:44 Colin kernel: [169260.701628] wlan0: associate with theMACaddress (try 1/3)
Dec 18 22:37:44 Colin kernel: [169260.703798] wlan0: RX AssocResp from theMACaddress (capab=0x411 status=0 aid=3)
Dec 18 22:37:44 Colin kernel: [169260.703955] wlan0: associated
Dec 18 22:38:44 Colin kernel: [169320.485102] wlan0: deauthenticated from theMACaddress (Reason: 7)
Dec 18 22:38:44 Colin kernel: [169320.507202] cfg80211: Calling CRDA to update world regulatory domain
Dec 18 22:38:44 Colin kernel: [169320.515484] cfg80211: World regulatory domain updated:
Dec 18 22:38:44 Colin kernel: [169320.515494] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Dec 18 22:38:44 Colin kernel: [169320.515501] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 18 22:38:44 Colin kernel: [169320.515508] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 18 22:38:44 Colin kernel: [169320.515513] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Dec 18 22:38:44 Colin kernel: [169320.515519] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 18 22:38:44 Colin kernel: [169320.515524] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 18 22:38:44 Colin kernel: [169320.535618] wlan0: authenticate with theMACaddress
Dec 18 22:38:44 Colin kernel: [169320.535856] wlan0: send auth to theMACaddress (try 1/3)
Dec 18 22:38:44 Colin kernel: [169320.537550] wlan0: authenticated
Dec 18 22:38:44 Colin kernel: [169320.537947] rtl8192ce 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
Dec 18 22:38:44 Colin kernel: [169320.537960] rtl8192ce 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
Dec 18 22:38:44 Colin kernel: [169320.539178] wlan0: associate with theMACaddress (try 1/3)
Dec 18 22:38:44 Colin kernel: [169320.543045] wlan0: RX AssocResp from theMACaddress (capab=0x411 status=0 aid=3)
Dec 18 22:38:44 Colin kernel: [169320.543224] wlan0: associated
Dec 18 22:39:43 Colin kernel: [169379.515076] wlan0: deauthenticated from theMACaddress (Reason: 7)
Dec 18 22:39:43 Colin kernel: [169379.556625] cfg80211: Calling CRDA to update world regulatory domain
Dec 18 22:39:43 Colin kernel: [169379.563224] cfg80211: World regulatory domain updated:
Dec 18 22:39:43 Colin kernel: [169379.563234] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Dec 18 22:39:43 Colin kernel: [169379.563238] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 18 22:39:43 Colin kernel: [169379.563242] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 18 22:39:43 Colin kernel: [169379.563245] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Dec 18 22:39:43 Colin kernel: [169379.563248] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 18 22:39:43 Colin kernel: [169379.563252] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 18 22:39:58 Colin kernel: [169394.689598] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

Cheers,
Andreas Skyman

---

### Post by jeremy31 on 2014-12-19
This info from Varun's post is relevant to you

[COLOR=#000000][INDENT]Please try changing the encryption in your router to WPA2-PSK with AES (CCMP) if it supports that. Currently it is using WPA (1) which essentially requires 'TKIP' which is older, inferior and inefficient compared to 'AES', and can be problematic sometimes. Reboot the router after saving the change.

Additionally, if required, please try some driver parameters in Ubuntu -
Code:
echo "options rtl8192ce fwlps=N ips=N" | sudo tee /etc/modprobe.d/rtl8192ce.conf
Reboot for the above to take effect. (usually we try above in temporary mode, and don't require a reboot, but I have recently started doubting that method (thanks to the intel driver)..., feel free to consider me paranoid if you wish :razz:).[/INDENT]
[/COLOR]
[INDENT]**[Varun]("https://wiki.ubuntu.com/Varunendra")**
[/INDENT]

---

