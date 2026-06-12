---
title: "Wifi is unstable in my Ubuntu 14.04"
date: 2016-02-19
forum: Networking &amp; Wireless
---

### Post by prmnth on 2016-02-19
Hi I have used Ubuntu 14.04 in my Hp pavillion g6 notebook laptop when it was released. After my time with Arch Linux for a while I thought I could install Ubuntu again. So installed 14.04 and have done all the updates (NOT upgrade). My WIFI connection have been unstable after the updates. The wifi status show the device is connected all the time but I am unable to receive any data. It works for a minute and then it does not work for another 5 to 10 mins and the cycle repeats. I have observed the same in system monitor. When I am not receiving data I use to check the system monitor and there is periodic rise and drop in the Network History.

Please help me out. I have ran the script. Here is my output.

[ATTACH]267387[/ATTACH]

[ATTACH]267388[/ATTACH]
[SIZE=5][FONT=franklin gothic medium][B]
Edit:

[COLOR=#000000]My issue is resolved by deactivating the N-mode of the driver. Now, I have b and g mode selected. I did it by going to my router settings via 198.162.1.1 . Don't know how to do it from terminal for my wireless driver [[SIZE=3]Qualcomm Atheros AR9485 Wireless Network Adapter[/SIZE]]. If anyone knows how to do that, please update this thread, it will helpful for others. My sincere thanks to [/COLOR][/B][/FONT][/SIZE][[IMG]http://ubuntuforums.org/customavatars/avatar1599436_1.gif[/IMG]]("http://ubuntuforums.org/member.php?u=1599436")[COLOR=#000000][[COLOR=#000000]Hadaka[/COLOR]]("http://ubuntuforums.org/member.php?u=1599436") [/COLOR]
[COLOR=#000000][/COLOR][IMG]http://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-offline.png[/IMG][COLOR=#000000][/COLOR][COLOR=#000000]**Ubuntu addict and loving it**[/COLOR][SIZE=5][COLOR=#008000][FONT=comic sans ms]**You were really helpful.**[/FONT][/COLOR][/SIZE]

---

### Post by Hadaka on 2016-02-19
Hi, from a working wired connection please copy and paste
one line at a time..
```
sudo iw reg set IN
sudo sed -i 's/^REG.*=$/&IN/' /etc/default/crda
```
then do..
```
sudo modprobe -rfv ath9k
echo "options ath9k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath9k.conf
sudo modprobe -v ath9k
```
Next please access your router settings and remove the paramater TKIP
choose instead...WPA2/PSK or  WPA2 CCMP but not TKIP.
remove wired connection..boot and test wireless
thanks.

---

### Post by prmnth on 2016-02-19
> **Hadaka said:**
> Hi, from a working wired connection please copy and pasteone line at a time..```
sudo iw reg set INsudo sed -i 's/^REG.*=$/&IN/' /etc/default/crda
```then do..```
sudo modprobe -rfv ath9kecho "options ath9k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath9k.confsudo modprobe -v ath9k
```Next please access your router settings and remove the paramater TKIPchoose instead...WPA2/PSK or  WPA2 CCMP but not TKIP.remove wired connection..boot and test wirelessthanks.Hi, Thanks for the reply. I did as you have said but still my problem is not resolved. Help me. I ran the script again. Here it is.```
########## wireless info START ##########Report from: 20 Feb 2016 07:45 IST +0530Booted last: 20 Feb 2016 07:33 IST +0530Script from: 27 Sep 2015 00:34 UTC +0000##### release ###########################Distributor ID:	UbuntuDescription:	Ubuntu 14.04.3 LTSRelease:	14.04Codename:	trusty##### kernel ############################Linux 3.13.0-24-generic #47-Ubuntu SMP Fri May 2 23:30:00 UTC 2014 x86_64 x86_64 x86_64 GNU/LinuxParameters: ro, quiet, splash, nomodeset, vt.handoff=7##### desktop ###########################Ubuntu##### lspci #############################02:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)	Subsystem: Hewlett-Packard Company Device [103c:1785]	Kernel driver in use: ath9k03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 05)	Subsystem: Hewlett-Packard Company Device [103c:3567]	Kernel driver in use: r8169##### lsusb #############################Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hubBus 006 Device 002: ID 0cf3:311d Atheros Communications, Inc. Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hubBus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hubBus 005 Device 002: ID 046d:c018 Logitech, Inc. Optical Wheel MouseBus 005 Device 003: ID 413c:2107 Dell Computer Corp. Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hubBus 001 Device 002: ID 04f2:b249 Chicony Electronics Co., Ltd Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hubBus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub##### PCMCIA card info ####################### rfkill ############################0: phy0: Wireless LAN	Soft blocked: no	Hard blocked: no1: hci0: Bluetooth	Soft blocked: no	Hard blocked: no##### lsmod #############################ath3k                  13318  0 bluetooth             395423  23 bnep,ath3k,btusb,rfcommhp_wmi                 14062  0 sparse_keymap          13948  1 hp_wmiath9k                 164164  0 ath9k_common           13551  1 ath9kath9k_hw              453856  2 ath9k_common,ath9kath                    28698  3 ath9k_common,ath9k,ath9k_hwwmi                    19177  1 hp_wmimac80211              626489  1 ath9kcfg80211              484040  3 ath,ath9k,mac80211##### interfaces ########################auto loiface lo inet loopback##### ifconfig ##########################eth0      Link encap:Ethernet  HWaddr             UP BROADCAST MULTICAST  MTU:1500  Metric:1          RX packets:0 errors:0 dropped:0 overruns:0 frame:0          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0          collisions:0 txqueuelen:1000           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)wlan0     Link encap:Ethernet  HWaddr             inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0          inet6 addr: fe80::/64 Scope:Link          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1          RX packets:17645 errors:0 dropped:0 overruns:0 frame:0          TX packets:12479 errors:0 dropped:0 overruns:0 carrier:0          collisions:0 txqueuelen:1000           RX bytes:19509851 (19.5 MB)  TX bytes:1961597 (1.9 MB)##### iwconfig ##########################eth0      no wireless extensions.lo        no wireless extensions.wlan0     IEEE 802.11bgn  ESSID:"MBLAZE-EC315-1DE9"            Mode:Managed  Frequency:2.437 GHz  Access Point:              Bit Rate=65 Mb/s   Tx-Power=16 dBm             Retry  long limit:7   RTS thr:off   Fragment thr:off          Power Management:off          Link Quality=44/70  Signal level=-66 dBm            Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0          Tx excessive retries:0  Invalid misc:10   Missed beacon:0##### route #############################Kernel IP routing tableDestination     Gateway         Genmask         Flags Metric Ref    Use Iface0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0##### resolv.conf #######################nameserver 127.0.1.1##### network managers ##################Installed:	NetworkManagerRunning:root      1006     1  0 07:33 ?        00:00:00 NetworkManager##### NetworkManager info ###############NetworkManager ToolState: connected (global)- Device: eth0 -----------------------------------------------------------------  Type:              Wired  Driver:            r8169  State:             unavailable  Default:           no  HW Address:          Capabilities:    Carrier Detect:  yes  Wired Properties    Carrier:         off- Device: wlan0  [MBLAZE-EC315-1DE9] -------------------------------------------  Type:              802.11 WiFi  Driver:            ath9k  State:             connected  Default:           yes  HW Address:          Capabilities:    Speed:           65 Mb/s  Wireless Properties    WEP Encryption:  yes    WPA Encryption:  yes    WPA2 Encryption: yes  Wireless Access Points (* = current AP)    *MBLAZE-EC315-1DE9: Infra, , Freq 2437 MHz, Rate 54 Mb/s, Strength 51 WPA WPA2  IPv4 Settings:    Address:         192.168.1.100    Prefix:          24 (255.255.255.0)    Gateway:         192.168.1.1    DNS:             192.168.1.1##### NetworkManager.state ##############[main]NetworkingEnabled=trueWirelessEnabled=trueWWANEnabled=trueWimaxEnabled=true##### NetworkManager.conf ###############[main]plugins=ifupdown,keyfile,ofonodns=dnsmasq[ifupdown]managed=false##### NetworkManager profiles ###########[[/etc/NetworkManager/system-connections/MBLAZE-EC315-1DE9]] (600 root)[connection] id=MBLAZE-EC315-1DE9 | type=802-11-wireless[802-11-wireless] ssid=MBLAZE-EC315-1DE9 | mac-address= | mtu=1500[ipv4] method=auto[ipv6] method=auto##### iw reg get ########################Region: Asia/Kolkata (based on set time zone)country IN:	(2402 - 2482 @ 40), (N/A, 20)	(5170 - 5250 @ 40), (N/A, 20)	(5250 - 5330 @ 40), (N/A, 20), DFS	(5735 - 5835 @ 40), (N/A, 20)##### iwlist channels ###################eth0      no frequency information.lo        no frequency information.wlan0     13 channels in total; available frequencies :          Channel 01 : 2.412 GHz          Channel 02 : 2.417 GHz          Channel 03 : 2.422 GHz          Channel 04 : 2.427 GHz          Channel 05 : 2.432 GHz          Channel 06 : 2.437 GHz          Channel 07 : 2.442 GHz          Channel 08 : 2.447 GHz          Channel 09 : 2.452 GHz          Channel 10 : 2.457 GHz          Channel 11 : 2.462 GHz          Channel 12 : 2.467 GHz          Channel 13 : 2.472 GHz          Current Frequency:2.437 GHz (Channel 6)##### iwlist scan #######################eth0      Interface doesn't support scanning.lo        Interface doesn't support scanning.Channel occupancy:      1   APs on   Frequency:2.437 GHz (Channel 6)wlan0     Scan completed :          Cell 01 - Address:                     Channel:6                    Frequency:2.437 GHz (Channel 6)                    Quality=34/70  Signal level=-76 dBm                      Encryption key:on                    ESSID:"MBLAZE-EC315-1DE9"                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s                              24 Mb/s; 36 Mb/s; 54 Mb/s                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s                    Mode:Master                    Extra:tsf=000000002e8f4542                    Extra: Last beacon: 24ms ago                    IE: IEEE 802.11i/WPA2 Version 1                        Group Cipher : TKIP                        Pairwise Ciphers (2) : CCMP TKIP                        Authentication Suites (1) : PSK                    IE: WPA Version 1                        Group Cipher : TKIP                        Pairwise Ciphers (2) : CCMP TKIP                        Authentication Suites (1) : PSK##### module infos ######################[ath3k]filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/bluetooth/ath3k.kofirmware:       ath3k-1.fwlicense:        GPLversion:        1.0description:    Atheros AR30xx firmware driverauthor:         Atheros Communicationssrcversion:     98A5245588C09E5E41690D0depends:        bluetoothintree:         Yvermagic:       3.13.0-24-generic SMP mod_unload modversions signer:         Magrathea: Glacier signing keysig_key:        69:B0:D0:A7:9B:85:D9:06:21:70:6E:8D:06:60:4D:73:0B:35:9F:C0sig_hashalgo:   sha512[ath9k]filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.kolicense:        Dual BSD/GPLdescription:    Support for Atheros 802.11n wireless LAN cards.author:         Atheros Communicationssrcversion:     BAF225EEB618908380B28DAdepends:        ath9k_hw,mac80211,ath9k_common,cfg80211,athintree:         Yvermagic:       3.13.0-24-generic SMP mod_unload modversions signer:         Magrathea: Glacier signing keysig_key:        69:B0:D0:A7:9B:85:D9:06:21:70:6E:8D:06:60:4D:73:0B:35:9F:C0sig_hashalgo:   sha512parm:           debug:Debugging mask (uint)parm:           nohwcrypt:Disable hardware encryption (int)parm:           blink:Enable LED blink on activity (int)parm:           btcoex_enable:Enable wifi-BT coexistence (int)parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)parm:           ps_enable:Enable WLAN PowerSave (int)[ath9k_common]filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.kolicense:        Dual BSD/GPLdescription:    Shared library for Atheros wireless 802.11n LAN cards.author:         Atheros Communicationssrcversion:     696B00A6C59713EC0966997depends:        ath,ath9k_hwintree:         Yvermagic:       3.13.0-24-generic SMP mod_unload modversions signer:         Magrathea: Glacier signing keysig_key:        69:B0:D0:A7:9B:85:D9:06:21:70:6E:8D:06:60:4D:73:0B:35:9F:C0sig_hashalgo:   sha512[ath9k_hw]filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.kolicense:        Dual BSD/GPLdescription:    Support for Atheros 802.11n wireless LAN cards.author:         Atheros Communicationssrcversion:     4809F3842A0542CD6B556D3depends:        athintree:         Yvermagic:       3.13.0-24-generic SMP mod_unload modversions signer:         Magrathea: Glacier signing keysig_key:        69:B0:D0:A7:9B:85:D9:06:21:70:6E:8D:06:60:4D:73:0B:35:9F:C0sig_hashalgo:   sha512[ath]filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/ath/ath.kolicense:        Dual BSD/GPLdescription:    Shared library for Atheros wireless LAN cards.author:         Atheros Communicationssrcversion:     88A67C5359B02C5A710AFCFdepends:        cfg80211intree:         Yvermagic:       3.13.0-24-generic SMP mod_unload modversions signer:         Magrathea: Glacier signing keysig_key:        69:B0:D0:A7:9B:85:D9:06:21:70:6E:8D:06:60:4D:73:0B:35:9F:C0sig_hashalgo:   sha512[mac80211]filename:       /lib/modules/3.13.0-24-generic/kernel/net/mac80211/mac80211.kolicense:        GPLdescription:    IEEE 802.11 subsystemsrcversion:     C0F95BBF832E05DEFD722F4depends:        cfg80211intree:         Yvermagic:       3.13.0-24-generic SMP mod_unload modversions signer:         Magrathea: Glacier signing keysig_key:        69:B0:D0:A7:9B:85:D9:06:21:70:6E:8D:06:60:4D:73:0B:35:9F:C0sig_hashalgo:   sha512parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)[cfg80211]filename:       /lib/modules/3.13.0-24-generic/kernel/net/wireless/cfg80211.kodescription:    wireless configuration supportlicense:        GPLauthor:         Johannes Bergsrcversion:     8B3D642D1F2E6406EF33F74depends:        intree:         Yvermagic:       3.13.0-24-generic SMP mod_unload modversions signer:         Magrathea: Glacier signing keysig_key:        69:B0:D0:A7:9B:85:D9:06:21:70:6E:8D:06:60:4D:73:0B:35:9F:C0sig_hashalgo:   sha512parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)##### module parameters #################[ath9k]blink: 0bt_ant_diversity: 0btcoex_enable: 0nohwcrypt: 1ps_enable: 0[mac80211]beacon_loss_count: 7ieee80211_default_rc_algo: minstrel_htmax_nullfunc_tries: 2max_probe_tries: 5probe_wait_ms: 500[cfg80211]cfg80211_disable_40mhz_24ghz: Nieee80211_regdom: 00##### /etc/modules ######################lprtc##### modprobe options ##################[/etc/modprobe.d/ath9k.conf]options ath9k nohwcrypt=1options ath9k nohwcrypt=1[/etc/modprobe.d/blacklist-ath_pci.conf]blacklist ath_pci[/etc/modprobe.d/blacklist.conf]blacklist evbugblacklist usbmouseblacklist usbkbdblacklist eepro100blacklist de4x5blacklist eth1394blacklist snd_intel8x0mblacklist snd_aw2blacklist i2c_i801blacklist prism54blacklist bcm43xxblacklist garmin_gpsblacklist asus_acpiblacklist snd_pcspblacklist pcspkrblacklist amd76x_edac[/etc/modprobe.d/blacklist-rare-network.conf]alias net-pf-3 offalias net-pf-6 offalias net-pf-9 offalias net-pf-11 offalias net-pf-12 offalias net-pf-19 offalias net-pf-21 offalias net-pf-36 off[/etc/modprobe.d/iwlwifi.conf]remove iwlwifi \(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \&& /sbin/modprobe -r mac80211[/etc/modprobe.d/mlx4.conf]softdep mlx4_core post: mlx4_en##### rc.local ##########################exit 0##### pm-utils ##########################[/etc/pm/power.d/disable_wol] (777 root)CONFFILE=/etc/default/tlpLIBDIRS='/usr/lib /usr/lib64'for d in ${LIBDIRS}; do    if [ -d "${d}/pm-utils/power.d" ]; then        blocked="${d}/pm-utils/power.d/${0##*/}"        break    fidoneif [ -n "$blocked" ] && [ -x "$blocked" ]; then    # else nothing to disable -> don't read $CONFFILE    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then        # TLP is enabled -> disable $blocked        echo "Notice: '${blocked}' disabled by TLP."    else        exec "$blocked" $*    fifiexit 0[/etc/pm/power.d/laptop-mode] (777 root)CONFFILE=/etc/default/tlpLIBDIRS='/usr/lib /usr/lib64'for d in ${LIBDIRS}; do    if [ -d "${d}/pm-utils/power.d" ]; then        blocked="${d}/pm-utils/power.d/${0##*/}"        break    fidoneif [ -n "$blocked" ] && [ -x "$blocked" ]; then    # else nothing to disable -> don't read $CONFFILE    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then        # TLP is enabled -> disable $blocked        echo "Notice: '${blocked}' disabled by TLP."    else        exec "$blocked" $*    fifiexit 0[/etc/pm/power.d/pci_devices] (777 root)CONFFILE=/etc/default/tlpLIBDIRS='/usr/lib /usr/lib64'for d in ${LIBDIRS}; do    if [ -d "${d}/pm-utils/power.d" ]; then        blocked="${d}/pm-utils/power.d/${0##*/}"        break    fidoneif [ -n "$blocked" ] && [ -x "$blocked" ]; then    # else nothing to disable -> don't read $CONFFILE    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then        # TLP is enabled -> disable $blocked        echo "Notice: '${blocked}' disabled by TLP."    else        exec "$blocked" $*    fifiexit 0[/etc/pm/power.d/pcie_aspm] (777 root)CONFFILE=/etc/default/tlpLIBDIRS='/usr/lib /usr/lib64'for d in ${LIBDIRS}; do    if [ -d "${d}/pm-utils/power.d" ]; then        blocked="${d}/pm-utils/power.d/${0##*/}"        break    fidoneif [ -n "$blocked" ] && [ -x "$blocked" ]; then    # else nothing to disable -> don't read $CONFFILE    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then        # TLP is enabled -> disable $blocked        echo "Notice: '${blocked}' disabled by TLP."    else        exec "$blocked" $*    fifiexit 0[/etc/pm/power.d/sched-powersave] (777 root)CONFFILE=/etc/default/tlpLIBDIRS='/usr/lib /usr/lib64'for d in ${LIBDIRS}; do    if [ -d "${d}/pm-utils/power.d" ]; then        blocked="${d}/pm-utils/power.d/${0##*/}"        break    fidoneif [ -n "$blocked" ] && [ -x "$blocked" ]; then    # else nothing to disable -> don't read $CONFFILE    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then        # TLP is enabled -> disable $blocked        echo "Notice: '${blocked}' disabled by TLP."    else        exec "$blocked" $*    fifiexit 0[/etc/pm/power.d/usb_bluetooth] (777 root)CONFFILE=/etc/default/tlpLIBDIRS='/usr/lib /usr/lib64'for d in ${LIBDIRS}; do    if [ -d "${d}/pm-utils/power.d" ]; then        blocked="${d}/pm-utils/power.d/${0##*/}"        break    fidoneif [ -n "$blocked" ] && [ -x "$blocked" ]; then    # else nothing to disable -> don't read $CONFFILE    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then        # TLP is enabled -> disable $blocked        echo "Notice: '${blocked}' disabled by TLP."    else        exec "$blocked" $*    fifiexit 0[/etc/pm/power.d/wireless] (777 root)CONFFILE=/etc/default/tlpLIBDIRS='/usr/lib /usr/lib64'for d in ${LIBDIRS}; do    if [ -d "${d}/pm-utils/power.d" ]; then        blocked="${d}/pm-utils/power.d/${0##*/}"        break    fidoneif [ -n "$blocked" ] && [ -x "$blocked" ]; then    # else nothing to disable -> don't read $CONFFILE    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then        # TLP is enabled -> disable $blocked        echo "Notice: '${blocked}' disabled by TLP."    else        exec "$blocked" $*    fifiexit 0[/etc/pm/power.d/xfs_buffer] (777 root)CONFFILE=/etc/default/tlpLIBDIRS='/usr/lib /usr/lib64'for d in ${LIBDIRS}; do    if [ -d "${d}/pm-utils/power.d" ]; then        blocked="${d}/pm-utils/power.d/${0##*/}"        break    fidoneif [ -n "$blocked" ] && [ -x "$blocked" ]; then    # else nothing to disable -> don't read $CONFFILE    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then        # TLP is enabled -> disable $blocked        echo "Notice: '${blocked}' disabled by TLP."    else        exec "$blocked" $*    fifiexit 0##### udev rules ########################[/etc/udev/rules.d/70-persistent-net.rules]# PCI device 0x10ec:0x8136 (r8169)SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"# PCI device 0x168c:0x0032 (ath9k)SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"# USB device 0x:0x (cdc_ether)SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"##### dmesg #############################[   27.083030] wlan0: authenticated[   27.084519] wlan0: associate with  (try 1/3)[   27.088968] wlan0: RX AssocResp from  (capab=0x411 status=0 aid=1)[   27.089060] wlan0: associated[   27.089084] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready[   29.476354] wlan0: deauthenticating from  by local choice (reason=2)[   29.486189] wlan0: authenticate with [   29.503335] wlan0: send auth to  (try 1/3)[   29.506016] wlan0: authenticated[   29.513230] wlan0: associate with  (try 1/3)[   29.516913] wlan0: RX AssocResp from  (capab=0x411 status=0 aid=1)[   29.516999] wlan0: associated########## wireless info END ############
```[ATTACH]267389[/ATTACH]

---

### Post by Hadaka on 2016-02-19
Hi, The change to your wifi in the router settings still needs to be done to remove TKIP
```
Cell 01 - Address: <MAC 'MBLAZE-EC315-1DE9' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"MBLAZE-EC315-1DE9"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000002e8f4542
                    Extra: Last beacon: 24ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : [COLOR=#ff0000]TKIP[/COLOR]
                        Pairwise Ciphers (2) : CCMP [COLOR=#ff0000]TKIP[/COLOR]
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : [COLOR=#ff0000]TKIP[/COLOR]
                        Pairwise Ciphers (2) : CCMP [COLOR=#ff0000]TKIP[/COLOR]
                        Authentication Suites (1) : PSK
```
Then please configure your network IPv4...IPv6 settings like the attached..
[ATTACH=CONFIG]267390[/ATTACH][ATTACH=CONFIG]267391[/ATTACH]
thanks.

---

### Post by prmnth on 2016-02-19
How to remove [COLOR=#FF0000][FONT=Ubuntu Mono]TKIP ? should i do that in 192.168.1.1?


[/FONT][/COLOR]

---

### Post by prmnth on 2016-02-19
> **Hadaka said:**
> Hi, The change to your wifi in the router settings still needs to be done to remove TKIP
```
Cell 01 - Address: <MAC 'MBLAZE-EC315-1DE9' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"MBLAZE-EC315-1DE9"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000002e8f4542
                    Extra: Last beacon: 24ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : [COLOR=#ff0000]TKIP[/COLOR]
                        Pairwise Ciphers (2) : CCMP [COLOR=#ff0000]TKIP[/COLOR]
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : [COLOR=#ff0000]TKIP[/COLOR]
                        Pairwise Ciphers (2) : CCMP [COLOR=#ff0000]TKIP[/COLOR]
                        Authentication Suites (1) : PSK
```
Then please configure your network IPv4...IPv6 settings like the attached..
[ATTACH=CONFIG]267390[/ATTACH][ATTACH=CONFIG]267391[/ATTACH]
thanks.



I think I have made the changes. Will browse for sometime and let you know whether the issue is resolved. Thank you for your help. 

> wlan0     Scan completed :          Cell 01 - Address: <MAC 'MBLAZE-EC315-1DE9' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"MBLAZE-EC315-1DE9"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000002f57a9e6
                    Extra: Last beacon: 144ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

---

### Post by prmnth on 2016-02-19
[FONT=georgia][SIZE=4]**Still the issue is not resolved. Please Help**[/SIZE][/FONT]

---

### Post by Hadaka on 2016-02-20
hi, your signal from the router is weak, how far are you from the rounter?
```
Link Quality=32/70  Signal level=-78 dBm  
```
Please check your antenna connections, unscrew them and see if there is any
green coloring ,it should be shiney brass , clean with a que trip and alcohol then
make sure they are tight.
also ..please do..
```
sudo iw reg set BO
sudo iwconfig wlan0 txpower 20
```
if no improvement, post another wireless-info
thanks.

---

### Post by prmnth on 2016-02-20
> **Hadaka said:**
> hi, your signal from the router is weak, how far are you from the rounter?
```
Link Quality=32/70  Signal level=-78 dBm  
```
Please check your antenna connections, unscrew them and see if there is any
green coloring ,it should be shiney brass , clean with a que trip and alcohol then
make sure they are tight.
also ..please do..
```
sudo iw reg set BO
sudo iwconfig wlan0 txpower 20
```
if no improvement, post another wireless-info
thanks.

[FONT=georgia][B]There is little improvement but the problem is still there.  I did all the steps as you have told.  Here is my wireless info. 
[/B][/FONT]
[ATTACH]267392[/ATTACH]

---

### Post by Hadaka on 2016-02-20
ok, please do..
```
sudo iw reg set IN
sudo iwconfig wlan0 txpower 20
```
and i see this time you used a USB..
```
USB device 0x:0x (cdc_ether)
```
please dont plug in anything different as it effects diagnostics
also your wifi signal is still weak,if your computer is easy to reseat the wifi card
and check the antenna connection that would be great...i
I am running out of ideas as to why your signal is weak. please run the command,remove the usb,
check the wifi card and antenna connection if you can and post yet another wireless-info file
thanks.

---

### Post by prmnth on 2016-02-20
> **Hadaka said:**
> ok, please do..
```
sudo iw reg set IN
sudo iwconfig wlan0 txpower 20
```
and i see this time you used a USB..
```
USB device 0x:0x (cdc_ether)
```
please dont plug in anything different as it effects diagnostics
also your wifi signal is still weak,if your computer is easy to reseat the wifi card
and check the antenna connection that would be great...i
I am running out of ideas as to why your signal is weak. please run the command,remove the usb,
check the wifi card and antenna connection if you can and post yet another wireless-info file
thanks.

I did as you have told but not yet resolved. I am using a MTS USB datacard connected to a power source. Using wifi in my laptop I am accessing the MTS datacard. 
 
I also have Antergos Linux in my Laptop and it works fine there and in my Android mobile too. Before updating the Ubuntu there was no problem. I am encountering this problem from 16th onwards. I asked the datacard customer service, they say all are good from there side. 

Here is my wireless info 

[ATTACH]267393[/ATTACH]

---

