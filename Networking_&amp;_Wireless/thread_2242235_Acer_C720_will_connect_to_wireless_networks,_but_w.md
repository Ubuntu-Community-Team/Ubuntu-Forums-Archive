---
title: "Acer C720 will connect to wireless networks, but won't load web pages from majority"
date: 2014-08-31
forum: Networking &amp; Wireless
---

### Post by c720 on 2014-08-31
Hey all,

I have an Acer C720 Chromebook, running a dual boot of Chrome OS and Ubuntu 14.04.

When using Chrome OS, I can connect to and use private and public wireless networks with no problems. With Ubuntu, I can also connect to all networks, but with the vast majority of networks I have tried, I cannot use the internet; the standard 'Server Not Found' screen appears when trying to load up web pages, for example.

I find it strange that I **can **use certain networks with no problems, but not others. The only difference I have noticed is that one which worked was WPA protected, while others are WEP (this may be an irrelevant point).

Here is the result of my wireless script.

Thanks in advance!

```

[FONT=arial]======== Wireless-Info START ========[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]System-Info ~~~~~~~~~~~~~~~~~~~~~~~~[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]chrubuntu 3.13.0-34-generic x86_64,  Ubuntu 14.04.1 LTS, trusty[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]CPU    : Intel(R) Celeron(R) 2955U @ 1.40GHz[/FONT]
[FONT=arial]Memory : 1875 MB[/FONT]
[FONT=arial]Uptime : 20:27:47 up 3 min,  2 users,  load average: 0.40, 0.39, 0.17[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]01:00.0 Network controller [0280]: Qualcomm Atheros AR9462 Wireless Network Adapter [168c:0034] (rev 01)[/FONT]
[FONT=arial]    Subsystem: Foxconn International, Inc. Device [105b:e058][/FONT]
[FONT=arial]    Kernel driver in use: ath9k[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Bus 001 Device 002: ID 8087:8000 Intel Corp. [/FONT]
[FONT=arial]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT]
[FONT=arial]Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub[/FONT]
[FONT=arial]Bus 002 Device 007: ID 05e3:0727 Genesys Logic, Inc. microSD Reader/Writer[/FONT]
[FONT=arial]Bus 002 Device 005: ID 13ee:0001 MosArt [/FONT]
[FONT=arial]Bus 002 Device 006: ID 0489:e056 Foxconn / Hon Hai [/FONT]
[FONT=arial]Bus 002 Device 002: ID 1bcf:2c67 Sunplus Innovation Technology Inc. [/FONT]
[FONT=arial]Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]wlan0     IEEE 802.11abgn  ESSID:"BTHomeHub-CCA7"  [/FONT]
[FONT=arial]          Mode:Managed  Frequency:2.442 GHz  Access Point: <MAC C-01 BTHomeHub-CCA7>   [/FONT]
[FONT=arial]          Bit Rate=36 Mb/s   Tx-Power=16 dBm   [/FONT]
[FONT=arial]          Retry  long limit:7   RTS thr:off   Fragment thr:off[/FONT]
[FONT=arial]          Power Management:off[/FONT]
[FONT=arial]          Link Quality=53/70  Signal level=-57 dBm  [/FONT]
[FONT=arial]          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0[/FONT]
[FONT=arial]          Tx excessive retries:0  Invalid misc:27   Missed beacon:0[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]      Interface        Soft blocked  Hard blocked[/FONT]
[FONT=arial]0: phy0: Wireless LAN      no            no[/FONT]
[FONT=arial]1: hci0: Bluetooth         no            no[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]ath9k                 164164  0 [/FONT]
[FONT=arial]ath9k_common           13551  1 ath9k[/FONT]
[FONT=arial]ath9k_hw              453856  2 ath9k_common,ath9k[/FONT]
[FONT=arial]ath                    28698  3 ath9k_common,ath9k,ath9k_hw[/FONT]
[FONT=arial]mac80211              630653  1 ath9k[/FONT]
[FONT=arial]cfg80211              484040  3 ath,ath9k,mac80211[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]module parameters ~~~~~~~~~~~~~~~~~~[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]ath9k         (5): blink=0 | bt_ant_diversity=0 | btcoex_enable=0 | nohwcrypt=0 | ps_enable=0[/FONT]
[FONT=arial]cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00[/FONT]
[FONT=arial]mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]State: connected (global)[/FONT]
[FONT=arial]===========================o=============o========o===========o=========o===========o==============o===========[/FONT]
[FONT=arial] Interface & ID            | Type        | Driver | State     | Default | Speed     | Support      | HW Addr   [/FONT]
[FONT=arial]===========================o=============o========o===========o=========o===========o==============o===========[/FONT]
[FONT=arial] wlan0  [BTHomeHub-CCA7 1] | 802.11 WiFi | ath9k  | connected | yes     | 36 Mb/s   | WEP/WPA/WPA2 | <MAC wlan0>[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]  [/FONT]
[FONT=arial]    *BTHomeHub-CCA7: Infra, <MAC C-01 BTHomeHub-CCA7>, Freq 2442 MHz, Rate 54 Mb/s, Strength 57 WEP[/FONT]
[FONT=arial]  [/FONT]
[FONT=arial]    Address:         192.168.1.69[/FONT]
[FONT=arial]    Prefix:          24 (255.255.255.0)[/FONT]
[FONT=arial]    Gateway:         192.168.1.254[/FONT]
[FONT=arial]    DNS:             192.168.1.254[/FONT]
[FONT=arial]---------------------------+-------------+--------+-----------+---------+-----------+--------------+-----------[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]NetworkManager.state ~~~~~~~~~~~~~~~[/FONT]
[FONT=arial][main][/FONT]
[FONT=arial]NetworkingEnabled=true[/FONT]
[FONT=arial]WirelessEnabled=true[/FONT]
[FONT=arial]WWANEnabled=true[/FONT]
[FONT=arial]WimaxEnabled=true[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]NetworkManager.conf ~~~~~~~~~~~~~~~~[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial][main][/FONT]
[FONT=arial]plugins=ifupdown,keyfile,ofono[/FONT]
[FONT=arial]dns=dnsmasq[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial][ifupdown][/FONT]
[FONT=arial]managed=false[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]BTHomeHub-CCA7       : ssid=BTHomeHub-CCA7 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto [/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]# interfaces(5) file used by ifup(8) and ifdown(8)[/FONT]
[FONT=arial]# Include files from /etc/network/interfaces.d:[/FONT]
[FONT=arial]source-directory /etc/network/interfaces.d[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]nameserver 192.168.200.1[/FONT]
[FONT=arial]search intern.[/FONT]
[FONT=arial]options single-request timeout:1 attempts:5[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Kernel IP routing table[/FONT]
[FONT=arial]Destination     Gateway         Genmask         Flags Metric Ref    Use Iface[/FONT]
[FONT=arial]0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0[/FONT]
[FONT=arial]192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]--- 192.168.1.254 ping statistics ---[/FONT]
[FONT=arial]2 packets transmitted, 2 received, 0% packet loss, time 1002ms[/FONT]
[FONT=arial]rtt min/avg/max/mdev = 1.946/2.391/2.836/0.445 ms[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]--- 192.168.200.1 ping statistics ---[/FONT]
[FONT=arial]2 packets transmitted, 0 received, 100% packet loss, time 1008ms[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial](Region : "POSIX")[/FONT]
[FONT=arial]country 00:[/FONT]
[FONT=arial]    (2402 - 2472 @ 40), (3, 20)[/FONT]
[FONT=arial]    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS[/FONT]
[FONT=arial]    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS[/FONT]
[FONT=arial]    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS[/FONT]
[FONT=arial]    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]wlan0     32 channels in total; available frequencies :[/FONT]
[FONT=arial]          Channel 01 (2.412 GHz) - 13 (2.472 GHz)[/FONT]
[FONT=arial]          Channel 36 (5.18 GHz)[/FONT]
[FONT=arial]          Channel 40 (5.2 GHz)[/FONT]
[FONT=arial]          Channel 44 (5.22 GHz)[/FONT]
[FONT=arial]          Channel 48 (5.24 GHz)[/FONT]
[FONT=arial]          Channel 52 (5.26 GHz)[/FONT]
[FONT=arial]          Channel 56 (5.28 GHz)[/FONT]
[FONT=arial]          Channel 60 (5.3 GHz)[/FONT]
[FONT=arial]          Channel 64 (5.32 GHz)[/FONT]
[FONT=arial]          Channel 100 (5.5 GHz)[/FONT]
[FONT=arial]          Channel 104 (5.52 GHz)[/FONT]
[FONT=arial]          Channel 108 (5.54 GHz)[/FONT]
[FONT=arial]          Channel 112 (5.56 GHz)[/FONT]
[FONT=arial]          Channel 116 (5.58 GHz)[/FONT]
[FONT=arial]          Channel 120 (5.6 GHz)[/FONT]
[FONT=arial]          Channel 124 (5.62 GHz)[/FONT]
[FONT=arial]          Channel 128 (5.64 GHz)[/FONT]
[FONT=arial]          Channel 132 (5.66 GHz)[/FONT]
[FONT=arial]          Channel 136 (5.68 GHz)[/FONT]
[FONT=arial]          Channel 140 (5.7 GHz)[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]          Current Frequency:2.442 GHz (Channel 7)[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]wlan0     Scan completed :[/FONT]
[FONT=arial]          Cell 01 - Address: <MAC C-01 BTHomeHub-CCA7>[/FONT]
[FONT=arial]                    Channel:7[/FONT]
[FONT=arial]                    Frequency:2.442 GHz (Channel 7)[/FONT]
[FONT=arial]                    Quality=48/70  Signal level=-62 dBm  [/FONT]
[FONT=arial]                    Encryption key:on[/FONT]
[FONT=arial]                    ESSID:"BTHomeHub-CCA7"[/FONT]
[FONT=arial]                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s[/FONT]
[FONT=arial]                              24 Mb/s; 36 Mb/s; 54 Mb/s[/FONT]
[FONT=arial]                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s[/FONT]
[FONT=arial]                    Mode:Master[/FONT]
[FONT=arial]                    Extra:tsf=0000001629a07b1b[/FONT]
[FONT=arial]                    Extra: Last beacon: 60ms ago[/FONT]

[FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial][/etc/modprobe.d/blacklist-ath_pci.conf][/FONT]
[FONT=arial]blacklist ath_pci[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial][ath9k][/FONT]
[FONT=arial]filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko[/FONT]
[FONT=arial]srcversion:     7EAAD420ADF6B9354F0C8C1[/FONT]
[FONT=arial]depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath[/FONT]
[FONT=arial]parm:           debug:Debugging mask (uint)[/FONT]
[FONT=arial]parm:           nohwcrypt:Disable hardware encryption (int)[/FONT]
[FONT=arial]parm:           blink:Enable LED blink on activity (int)[/FONT]
[FONT=arial]parm:           btcoex_enable:Enable wifi-BT coexistence (int)[/FONT]
[FONT=arial]parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)[/FONT]
[FONT=arial]parm:           ps_enable:Enable WLAN PowerSave (int)[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial][ath9k_common][/FONT]
[FONT=arial]filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko[/FONT]
[FONT=arial]srcversion:     696B00A6C59713EC0966997[/FONT]
[FONT=arial]depends:        ath,ath9k_hw[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial][ath9k_hw][/FONT]
[FONT=arial]filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko[/FONT]
[FONT=arial]srcversion:     4809F3842A0542CD6B556D3[/FONT]
[FONT=arial]depends:        ath[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial][ath][/FONT]
[FONT=arial]filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/ath/ath.ko[/FONT]
[FONT=arial]srcversion:     88A67C5359B02C5A710AFCF[/FONT]
[FONT=arial]depends:        cfg80211[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial][mac80211][/FONT]
[FONT=arial]filename:       /lib/modules/3.13.0-34-generic/kernel/net/mac80211/mac80211.ko[/FONT]
[FONT=arial]srcversion:     8ADA881D348148A3358334C[/FONT]
[FONT=arial]depends:        cfg80211[/FONT]
[FONT=arial]parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)[/FONT]
[FONT=arial]parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)[/FONT]
[FONT=arial]parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)[/FONT]
[FONT=arial]parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)[/FONT]
[FONT=arial]parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial][cfg80211][/FONT]
[FONT=arial]filename:       /lib/modules/3.13.0-34-generic/kernel/net/wireless/cfg80211.ko[/FONT]
[FONT=arial]srcversion:     E786D076B61F97809B04B64[/FONT]
[FONT=arial]depends:        [/FONT]
[FONT=arial]parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)[/FONT]
[FONT=arial]parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]# PCI device 0x168c:0x0034 (ath9k)[/FONT]
[FONT=arial]SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Custom files/entries ~~~~~~~~~~~~~~~[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]/etc/modules        : Default[/FONT]
[FONT=arial]/etc/rc.local       : Default[/FONT]
[FONT=arial]/etc/modprobe.d     : Not Default[/FONT]
[FONT=arial]/etc/pm/(cnf|pw|sl) : Default[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial][/etc/modprobe.d][/FONT]
[FONT=arial]iwlwifi.conf      : remove iwlwifi \[/FONT]
[FONT=arial]                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \[/FONT]
[FONT=arial]                    && /sbin/modprobe -r mac80211[/FONT]
[FONT=arial]mlx4.conf         : softdep mlx4_core post: mlx4_en[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Kernel boot line ~~~~~~~~~~~~~~~~~~~[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]BOOT_IMAGE=/boot/vmlinuz-3.13.0-34-generic root=UUID=c7dfda25-92c9-47aa-9724-d5f3f1536291 ro quiet splash vt.handoff=7[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial][    0.614741] microcode: Microcode Update Driver: v2.00 <[EMAIL="tigran@aivazian.fsnet.co.uk"]tigran@aivazian.fsnet.co.uk[/EMAIL]>, Peter Oruba[/FONT]
[FONT=arial][    0.615038] audit: initializing netlink socket (disabled)[/FONT]
[FONT=arial][   55.631583] Bluetooth: BNEP (Ethernet Emulation) ver 1.3[/FONT]
[FONT=arial][   55.734368] ath: phy0: ASPM enabled: 0x43[/FONT]
[FONT=arial][   55.734374] ath: EEPROM regdomain: 0x6c[/FONT]
[FONT=arial][   55.734376] ath: EEPROM indicates we should expect a direct regpair map[/FONT]
[FONT=arial][   55.734379] ath: Country alpha2 being used: 00[/FONT]
[FONT=arial][   55.734380] ath: Regpair used: 0x6c[/FONT]
[FONT=arial][   58.394164] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready[/FONT]
[FONT=arial][   58.397705] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready[/FONT]
[FONT=arial][   65.302817] wlan0: authenticate with <MAC C-01 BTHomeHub-CCA7>[/FONT]
[FONT=arial][   65.325092] wlan0: send auth to <MAC C-01 BTHomeHub-CCA7> (try 1/3)[/FONT]
[FONT=arial][   65.327058] wlan0: authenticated[/FONT]
[FONT=arial][   65.328127] ath9k 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use[/FONT]
[FONT=arial][   65.329170] wlan0: associate with <MAC C-01 BTHomeHub-CCA7> (try 1/3)[/FONT]
[FONT=arial][   65.331932] wlan0: RX AssocResp from <MAC C-01 BTHomeHub-CCA7> (capab=0x411 status=0 aid=3)[/FONT]
[FONT=arial][   65.332217] wlan0: associated[/FONT]
[FONT=arial][   65.332242] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready[/FONT]
[FONT=arial][   65.337448] wlan0: deauthenticating from <MAC C-01 BTHomeHub-CCA7> by local choice (reason=2)[/FONT]
[FONT=arial][   65.351708] wlan0: authenticate with <MAC C-01 BTHomeHub-CCA7>[/FONT]
[FONT=arial][   65.365083] wlan0: send auth to <MAC C-01 BTHomeHub-CCA7> (try 1/3)[/FONT]
[FONT=arial][   65.367473] wlan0: authenticated[/FONT]
[FONT=arial][   65.371992] ath9k 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use[/FONT]
[FONT=arial][   65.373073] wlan0: associate with <MAC C-01 BTHomeHub-CCA7> (try 1/3)[/FONT]
[FONT=arial][   65.375793] wlan0: RX AssocResp from <MAC C-01 BTHomeHub-CCA7> (capab=0x411 status=0 aid=3)[/FONT]
[FONT=arial][   65.376073] wlan0: associated[/FONT]
[FONT=arial][   75.381710] wlan0: deauthenticating from <MAC C-01 BTHomeHub-CCA7> by local choice (reason=3)[/FONT]
[FONT=arial][   78.919686] wlan0: authenticate with <MAC C-01 BTHomeHub-CCA7>[/FONT]
[FONT=arial][   78.930232] wlan0: send auth to <MAC C-01 BTHomeHub-CCA7> (try 1/3)[/FONT]
[FONT=arial][   78.933341] wlan0: authenticated[/FONT]
[FONT=arial][   78.933656] ath9k 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use[/FONT]
[FONT=arial][   78.934845] wlan0: associate with <MAC C-01 BTHomeHub-CCA7> (try 1/3)[/FONT]
[FONT=arial][   78.937692] wlan0: RX AssocResp from <MAC C-01 BTHomeHub-CCA7> (capab=0x411 status=0 aid=3)[/FONT]
[FONT=arial][   78.937974] wlan0: associated[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]    ======== Done ========
[/FONT]
```

---

### Post by jeremy31 on 2014-08-31
> **c720 said:**
> Hey all,

I have an Acer C720 Chromebook, running a dual boot of Chrome OS and Ubuntu 14.04.



I find it strange that I **can **use certain networks with no problems, but not others. The only difference I have noticed is that one which worked was WPA protected, while others are WEP (this may be an irrelevant point).

Here is the result of my wireless script.

Thanks in advance!



The helpers here have advised against using WEP and TKIP, you might find that everything works if you set things to WPA2/AES on the router

---

### Post by c720 on 2014-08-31
> **jeremy31 said:**
> The helpers here have advised against using WEP and TKIP, you might find that everything works if you set things to WPA2/AES on the router

Sure, thanks. But this won't sort out routers that I can't access (an office one, for example), or public networks (should be pointed out that Ubuntu will connect, but not work with public networks as well).

If anyone has any diagnostic thoughts from the wireless script, any help would be appreciated.

EDIT: Have changed the router to WPA. All other devices are working fine on it, but Ubuntu still doesn't.

---

### Post by Hadaka on 2014-08-31
Hi, it looks like your /etc/resolv.conf file may have some issues
Let's rummage around in your files and see whats in there. Please
do and post..
```
ifconfig lo
cat /etc/hosts
echo "nameserver 8.8.8.8" | sudo tee -a /etc/resolv.conf
```
thanks.

---

### Post by c720 on 2014-08-31
> **Hadaka said:**
> Hi, it looks like your /etc/resolv.conf file may have some issues
Let's rummage around in your files and see whats in there. Please
do and post..
```
ifconfig lo
cat /etc/hosts
echo "nameserver 8.8.8.8" | sudo tee -a /etc/resolv.conf
```
thanks.

Thanks. Is this what you wanted to see? (Apologies if not -- I'm new to the command line).

```

user@chrubuntu:~$ ifconfig lo
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:275 errors:0 dropped:0 overruns:0 frame:0
          TX packets:275 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:40669 (40.6 KB)  TX bytes:40669 (40.6 KB)


user@chrubuntu:~$ cat /etc/hosts


127.0.1.1       chrubuntu
user@chrubuntu:~$ echo "nameserve 8.8.8.8" | sudo tee -a /etc/resolv.conf
[sudo] password for user: 
nameserve 8.8.8.8

```

---

### Post by Hadaka on 2014-08-31
Hi, thanks, im trying to figure out where
/etc/resolv.conf is getting 
[FONT=arial]nameserver 192.168.200.1
.......................................
Let's look at some more stuff,,
please post the output of,,
Copy and paste ..
```
cat /etc/resolvconf/resolv.conf.d/tail

```[/FONT]```
[FONT=arial][FONT=arial]cat /etc/resolvconf/resolv.conf.d/original
cat /etc/network/interfaces[/FONT][/FONT]
```[FONT=arial]
then copy and paste and post
```
sudo su
cat /etc/NetworkManager/system-connections/BTHomeHub-CCA7 | grep -iA6 ipv4
exit 0
```
[/FONT]thanks.

---

### Post by c720 on 2014-09-01
Here you go. Thanks.

```

user@chrubuntu:~$ cat /etc/resolvconf/resolv.conf.d/tail
cat: /etc/resolvconf/resolv.conf.d/tail: No such file or directory
user@chrubuntu:~$ cat /etc/resolvconf/resolv.conf.d/original
cat: /etc/resolvconf/resolv.conf.d/original: No such file or directory
user@chrubuntu:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
# Include files from /etc/network/interfaces.d:
source-directory /etc/network/interfaces.d
user@chrubuntu:~$ sudo su
[sudo] password for user: 
root@chrubuntu:/home/user# cat /etc/NetworkManager/system-connections/BTHomeHub-CCA7 | grep -iA6 ipv4
[ipv4]
method=auto


[ipv6]
method=auto

```

---

### Post by Hadaka on 2014-09-01
Hi, thanks for being patient,this churbuntu does things a little
differently than regular ubuntu so we need to keep digging untill
we find the file with the odd ip #. please do and post..
```
cat/etc/network/interfaces.d
cat /etc/hosts
```
also plesase use code tags..its the ' # ' on the second row of icons
on the reply page its next to < >. so click the # then copy and paste
the output  between [ CODE ]here[ /CODE]
thanks

---

### Post by c720 on 2014-09-01
Thanks.

```
user@chrubuntu:~$ cat /etc/network/interfaces.dcat: /etc/network/interfaces.d: Is a directory
user@chrubuntu:~$ cat /etc/hosts


127.0.1.1       chrubuntu
user@chrubuntu:~$ 
```

---

### Post by Hadaka on 2014-09-01
Hi, as you can see, we still havent found [FONT=arial]192.168.200.1
that is in your /etc/resolv.conf file and has nothing do do with 
anything...it should be nameserver 127.0.0.1  Do you remember
entering 192.168.200.1 ? also is your chrombook dual boot?
if so, we can try to delete /etc/resolv.conf and hopefully network
manager will rebuild it correctly. Im not familure with the files in
chrubuntu or exactly how it's resolv.conf file works so if anyone out there
can see what im trying to do here and knows the chrubuntu os, please feel
free to chime in.
Give this a try.,,,
```
[/FONT][FONT=arial]sudo apt-get remove --purge resolvconf && sudo apt-get install resolvconf
```
answer yes to the questions then boot
thanks.
[/FONT]

---

### Post by c720 on 2014-09-01
Just to answer the question quickly: yes, it's a dual boot (either Chrome OS or Ubuntu). Chrome OS works absolutely fine with wifi.

I can't try that step just yet. I'll edit this post when I've done it. Thanks for your help on this.

EDIT: It works!!!

Deleted that file, it tried to update (obviously couldn't, because it doesn't have internet access), rebooted, and it connected. Guess, as you said, that network manager did the rest.

Thanks!

---

### Post by lmhirvonen on 2014-11-08
Worked for me too, thank you!

---

### Post by Russell_Abbott on 2015-01-10
I had the same problem and this solved it - Thank you!!

---

### Post by jay15 on 2015-08-07
Another one that post #10 worked for.  Thanks Hadaka!

---

