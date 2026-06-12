---
title: "ar9287, acer-4750g, can't restart wireless"
date: 2014-08-04
forum: Networking &amp; Wireless
---

### Post by wulong710 on 2014-08-04
When i use wireless. I can connect internet ..But after a few hours, the wireless disconnect,  can't can't see wirelsss routers in wicd or network-manager  ,unless i reboot my computer.
Errors as follow:
```
Aug  2 14:12:08 andrew-pc NetworkManager[1307]: message repeated 2 times: [ <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted]Aug  2 14:17:20 andrew-pc NetworkManager[1307]: <info> (eth0): DHCPv4 state changed renew -> renew
Aug  2 14:17:20 andrew-pc NetworkManager[1307]: <info>   address 192.168.10.197
Aug  2 14:17:20 andrew-pc NetworkManager[1307]: <info>   prefix 24 (255.255.255.0)
Aug  2 14:17:20 andrew-pc NetworkManager[1307]: <info>   gateway 192.168.10.1
Aug  2 14:17:20 andrew-pc NetworkManager[1307]: <info>   nameserver '202.96.128.86'
Aug  2 14:17:20 andrew-pc NetworkManager[1307]: <info>   nameserver '202.96.134.33'
Aug  2 14:17:20 andrew-pc dbus[1129]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Aug  2 14:17:20 andrew-pc dbus[1129]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Aug  2 14:24:08 andrew-pc NetworkManager[1307]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Aug  2 14:29:17 andrew-pc kernel: [ 5107.835297] irq 17: nobody cared (try booting with the "irqpoll" option)
Aug  2 14:29:17 andrew-pc kernel: [ 5107.835304] CPU: 0 PID: 0 Comm: swapper/0 Tainted: GF          O 3.13.0-32-generic #57-Ubuntu
Aug  2 14:29:17 andrew-pc kernel: [ 5107.835306] Hardware name: Acer Aspire 4750/Aspire 4750, BIOS V2.15 12/05/2011
Aug  2 14:29:17 andrew-pc kernel: [ 5107.835308]  00000000 00000000 f6c0bf54 c1650cd3 f2001c00 f6c0bf74 c10a7999 c1830644
Aug  2 14:29:17 andrew-pc kernel: [ 5107.835315]  00000011 f2001c54 f23ea00c f2001c00 00000011 f6c0bf98 c10a7d93 00000000
Aug  2 14:29:17 andrew-pc kernel: [ 5107.835320]  00000b9c ff77dd58 001250f9 f2001c00 f2001c54 00000000 f6c0bfd4 c10a5cd5
Aug  2 14:29:17 andrew-pc kernel: [ 5107.835326] Call Trace:
Aug  2 14:29:17 andrew-pc kernel: [ 5107.835334]  [<c1650cd3>] dump_stack+0x41/0x52
Aug  2 14:29:17 andrew-pc kernel: [ 5107.835339]  [<c10a7999>] __report_bad_irq+0x29/0xd0
Aug  2 14:29:17 andrew-pc kernel: [ 5107.835343]  [<c10a7d93>] note_interrupt+0x153/0x1a0
Aug  2 14:29:17 andrew-pc kernel: [ 5107.835347]  [<c10a5cd5>] handle_irq_event_percpu+0xc5/0x1a0
Aug  2 14:29:17 andrew-pc kernel: [ 5107.835351]  [<c10a5de1>] handle_irq_event+0x31/0x50
Aug  2 14:29:17 andrew-pc kernel: [ 5107.835353]  [<c10a8710>] ? unmask_irq+0x30/0x30
Aug  2 14:29:17 andrew-pc kernel: [ 5107.835356]  [<c10a875e>] handle_fasteoi_irq+0x4e/0xe0
Aug  2 14:29:17 andrew-pc kernel: [ 5107.835357]  <IRQ>  [<c165f6ec>] ? do_IRQ+0x3c/0xb0
Aug  2 14:29:17 andrew-pc kernel: [ 5107.835365]  [<c165f4b3>] ? common_interrupt+0x33/0x38
Aug  2 14:29:17 andrew-pc kernel: [ 5107.835369]  [<c152f090>] ? cpuidle_enter_state+0x40/0xd0
Aug  2 14:29:17 andrew-pc kernel: [ 5107.835372]  [<c152f1b5>] ? cpuidle_idle_call+0x95/0x1c0
Aug  2 14:29:17 andrew-pc kernel: [ 5107.835376]  [<c10174dd>] ? arch_cpu_idle+0xd/0x30
Aug  2 14:29:17 andrew-pc kernel: [ 5107.835379]  [<c10a5439>] ? cpu_startup_entry+0x1c9/0x210
Aug  2 14:29:17 andrew-pc kernel: [ 5107.835383]  [<c1647042>] ? rest_init+0x62/0x70
Aug  2 14:29:17 andrew-pc kernel: [ 5107.835388]  [<c19b4af1>] ? start_kernel+0x3b3/0x3b9
Aug  2 14:29:17 andrew-pc kernel: [ 5107.835391]  [<c19b4575>] ? repair_env_string+0x51/0x51
Aug  2 14:29:17 andrew-pc kernel: [ 5107.835394]  [<c19b439c>] ? i386_start_kernel+0x137/0x13a
Aug  2 14:29:17 andrew-pc kernel: [ 5107.835395] handlers:
Aug  2 14:29:17 andrew-pc kernel: [ 5107.835409] [<f88ce320>] ath_isr [ath9k]
Aug  2 14:29:17 andrew-pc kernel: [ 5107.835411] Disabling IRQ #17
Aug  2 14:29:17 andrew-pc kernel: [ 5107.968796] ath: phy0: Failed to stop TX DMA, queues=0x18f!
Aug  2 14:29:17 andrew-pc kernel: [ 5107.982939] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Aug  2 14:29:17 andrew-pc kernel: [ 5107.983008] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
Aug  2 14:29:17 andrew-pc kernel: [ 5108.107153] ath: phy0: Chip reset failed
Aug  2 14:29:17 andrew-pc kernel: [ 5108.107161] ath: phy0: Unable to reset channel, reset status -22
Aug  2 14:29:17 andrew-pc kernel: [ 5108.107192] ath: phy0: Unable to set channel
Aug  2 14:29:17 andrew-pc kernel: [ 5108.231909] ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Aug  2 14:29:17 andrew-pc kernel: [ 5108.245234] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Aug  2 14:28:06 andrew-pc wpa_supplicant[1471]: message repeated 44 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Aug  2 14:29:17 andrew-pc wpa_supplicant[1471]: wlan0: CTRL-EVENT-DISCONNECTED bssid=20:0c:c8:0a:08:c7 reason=4 locally_generated=1
Aug  2 14:28:08 andrew-pc NetworkManager[1307]: message repeated 2 times: [ <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted]
Aug  2 14:29:17 andrew-pc NetworkManager[1307]: <warn> Connection disconnected (reason -4)
Aug  2 14:29:17 andrew-pc kernel: [ 5108.287626] ath: phy0: Failed to wakeup in 500us
Aug  2 14:29:17 andrew-pc kernel: [ 5108.413815] ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Aug  2 14:29:17 andrew-pc kernel: [ 5108.428340] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Aug  2 14:29:17 andrew-pc kernel: [ 5108.428717] cfg80211: Calling CRDA to update world regulatory domain
Aug  2 14:29:17 andrew-pc NetworkManager[1307]: <info> (wlan0): supplicant interface state: completed -> scanning
Aug  2 14:29:17 andrew-pc kernel: [ 5108.460989] ath: phy0: Failed to wakeup in 500us
Aug  2 14:29:17 andrew-pc kernel: [ 5108.531737] ath: phy0: Failed to stop TX DMA, queues=0x18f!
Aug  2 14:29:17 andrew-pc kernel: [ 5108.545708] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff



```

---

### Post by wulong710 on 2014-08-04
[COLOR=#000000]i will try this:  [http://ubuntuforums.org/showthread.php?t=1986064&highlight=ar9287](http://ubuntuforums.org/showthread.php?t=1986064&highlight=ar9287)

Create a new file /etc/modprobe.d/ath9k.conf:[/COLOR]

[COLOR=#000000]sudo nano /etc/modprobe.d/ath9k.conf[/COLOR]

[COLOR=#000000]Add the following line to it:[/COLOR]

[COLOR=#000000]options ath9k nohwcrypt=1[/COLOR]

---

### Post by wulong710 on 2014-08-04
test this :[http://ubuntuforums.org/showthread.php?t=2181558](http://ubuntuforums.org/showthread.php?t=2181558)
1.  [COLOR=#000000][FONT=Ubuntu Mono]lspci -nnk | grep -A2 0280
 i can see : "[/FONT][/COLOR][COLOR=#000000]Kernel driver in use: ath9k"
2. [/COLOR][COLOR=#000000][FONT=Ubuntu Mono]lsmod | grep -e ath9k -e acer
> [/FONT][/COLOR]andrew@andrew-pc:~$ lsmod | grep -e ath9k -e aceracer_wmi               31735  0 
sparse_keymap          13708  1 acer_wmi
ath9k                 144602  0 
ath9k_common           13359  1 ath9k
ath9k_hw              438205  2 ath9k_common,ath9k
ath                    23922  3 ath9k_common,ath9k,ath9k_hw


[COLOR=#000000][FONT=Ubuntu Mono]
can not see [/FONT][/COLOR][COLOR=#800000]acer_nb_wmi.   but find [/COLOR]acer_wmi , is it right?

3. rfkill list 
> andrew@andrew-pc:~$ rfkill list0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no
wirless unlocked.
4.  echo "options asus_nb_wmi wapf=4" | sudo tee /etc/modprobe.d/asus_nb_wmi.conf
what should i write in?

---

### Post by wulong710 on 2014-08-04
try this get laptop information:
> [COLOR=#000000][FONT=Ubuntu Mono]wget -N -t 5 -T 10 [https://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script](https://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script) && chmod +x wireless_script && ./wireless_script[/FONT][/COLOR]

---

### Post by varunendra on 2014-08-04
Welcome to the forums wulong710!

> **wulong710 said:**
> can't can't see wirelsss routers in wicd or network-manager  ,unless i reboot my computer.
If you are using WICD and Network Manager simultaneously, this itself is a problem. Please remove one to try other without issues. I recommend removing WICD if Network Manager is still installed and working -
```
sudo apt-get purge wicd
```

> **wulong710 said:**
> test this :[http://ubuntuforums.org/showthread.php?t=2181558](http://ubuntuforums.org/showthread.php?t=2181558)
No, don't test that, that is specifically meant for only Asus laptops/netbooks, not for Acer models. So the suggestion there won't work for you.

> **wulong710 said:**
> try this get laptop information:```
wget -N -t 5 -T 10 https://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script && chmod +x wireless_script && ./wireless_script
```
Yes, that script can help us determining the problem and possibly find out a solution.

Please follow the instructions in this post to see how to run it : [http://ubuntuforums.org/showthread.php?p=13024222#post13024222](http://ubuntuforums.org/showthread.php?p=13024222#post13024222)

That script will generate a file named "wireless-info.txt" or "wireless-info.tar.gz" in the same place where you have downloaded the script. We need to see that report file, either copy-paste its contents here in your next post, or attach the file itself.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by wulong710 on 2014-08-05
> **varunendra said:**
> Welcome to the forums wulong710!


If you are using WICD and Network Manager simultaneously, this itself is a problem. Please remove one to try other without issues. I recommend removing WICD if Network Manager is still installed and working -
```
sudo apt-get purge wicd
```


No, don't test that, that is specifically meant for only Asus laptops/netbooks, not for Acer models. So the suggestion there won't work for you.


Yes, that script can help us determining the problem and possibly find out a solution.

Please follow the instructions in this post to see how to run it : [http://ubuntuforums.org/showthread.php?p=13024222#post13024222](http://ubuntuforums.org/showthread.php?p=13024222#post13024222)

That script will generate a file named "wireless-info.txt" or "wireless-info.tar.gz" in the same place where you have downloaded the script. We need to see that report file, either copy-paste its contents here in your next post, or attach the file itself.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

When i use network-manager, laptop often froze after wireless disconnect.   So i remove network-manger and install wicd.
I run your shell script, get information as this : [ATTACH]255285[/ATTACH]

---

### Post by wulong710 on 2014-08-05
```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

andrew-pc 3.13.0-32-generic i686,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Core(TM) i5-2450M CPU @ 2.50GHz
Memory : 3847 MB
Uptime : 23:15:40 up  1:13,  2 users,  load average: 0.46, 0.67, 0.72


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

03:00.0 Network controller [0280]: Qualcomm Atheros AR9287 Wireless Network Adapter (PCI-Express) [168c:002e] (rev 01)
    Subsystem: Quanta Microsystems, Inc Device [1a32:2309]
    Kernel driver in use: ath9k
04:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)
    Subsystem: Acer Incorporated [ALI] Device [1025:0500]
    Kernel driver in use: tg3


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 004: ID 17ef:6025 Lenovo 
Bus 002 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 058f:b002 Alcor Micro Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:"wulong"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: <MAC C-01 wulong>   
          Bit Rate=270 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-29 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:5  Invalid misc:660   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface                 Soft blocked  Hard blocked
0: phy0: Wireless LAN               no            no
1: acer-wireless: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

acer_wmi               31735  0 
sparse_keymap          13708  1 acer_wmi
ath9k                 144602  0 
ath9k_common           13359  1 ath9k
ath9k_hw              438205  2 ath9k_common,ath9k
ath                    23922  3 ath9k_common,ath9k,ath9k_hw
mac80211              546051  1 ath9k
cfg80211              409394  3 ath,ath9k,mac80211
mxm_wmi                12893  1 nouveau
wmi                    18673  3 acer_wmi,mxm_wmi,nouveau
video                  18903  3 i915,acer_wmi,nouveau


module parameters ~~~~~~~~~~~~~~~~~~

acer_wmi      (5): brightness=-1 | ec_raw_mode=N | force_series=0 | mailled=-1 | threeg=-1
ath9k         (5): blink=0 | bt_ant_diversity=0 | btcoex_enable=0 | nohwcrypt=1 | ps_enable=0
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
video         (3): allow_duplicates=N | brightness_switch_enabled=Y | use_native_backlight=-1
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
=================o=============o========o=========  ====o=========o===========o==============o========  ===
 Interface & ID  | Type        | Driver | State       | Default | Speed     | Support      | HW Addr   
=================o=============o========o=========  ====o=========o===========o==============o========  ===
 eth0            | Wired       | tg3    | unavailable | no      |           |              | <MAC eth0>
-----------------+-------------+--------+-------------+---------+-----------+--------------+-----------
 wlan0  [wulong] | 802.11 WiFi | ath9k  | connected   | yes     | 270 Mb/s  | WEP/WPA/WPA2 | <MAC wlan0>

    TP-LINK_B396F4:  Infra, <MAC C-06 TP-LINK_B396F4>, Freq 2437 MHz, Rate 54 Mb/s, Strength 79 WPA WPA2
    iTV-FAFe:        Infra, <MAC C-04 iTV-FAFe>, Freq 2412 MHz, Rate 54 Mb/s, Strength 59 WPA WPA2
    ChinaNet-FAFe:   Infra, <MAC C-02 ChinaNet-FAFe>, Freq 2412 MHz, Rate 54 Mb/s, Strength 55 WPA WPA2
    MERCURY_1302:    Infra, <MAC C-07 MERCURY_1302>, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    *wulong:         Infra, <MAC C-01 wulong>, Freq 2447 MHz, Rate 54 Mb/s, Strength 86 WPA
    MERCURY_32152C:  Infra, <MAC C-03 MERCURY_32152C>, Freq 2412 MHz, Rate 54 Mb/s, Strength 52 WPA WPA2
    Phicomm_1EB880:  Infra, <MAC C-11 Phicomm_1EB880>, Freq 2467 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    Netcore1:        Infra, <MAC C-16 Netcore1>, Freq 2442 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    lixiaotong:      Infra, <MAC C-09 lixiaotong>, Freq 2437 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2
    ChinaNet-ihwc:   Infra, <MAC C-14 ChinaNet-ihwc>, Freq 2442 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    Tenda_323000:    Infra, <MAC C-NA Tenda_323000 1>, Freq 2442 MHz, Rate 54 Mb/s, Strength 42 WPA
    YULIN:           Infra, <MAC C-NA YULIN 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    360WiFi-1043:    Infra, <MAC C-NA 360WiFi-1043 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WPA2
    TP-LINK_423694:  Infra, <MAC C-NA TP-LINK_423694 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    Tenda_456:       Infra, <MAC C-12 Tenda_456>, Freq 2447 MHz, Rate 54 Mb/s, Strength 29 WPA
    nihaoma:         Infra, <MAC C-NA nihaoma 1>, Freq 2432 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    lee dee:         Infra, <MAC C-NA lee dee 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    TP-LINK_1104:    Infra, <MAC C-NA TP-LINK_1104 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    zhengfu:         Infra, <MAC C-NA zhengfu 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    FAST_B709C2:     Infra, <MAC C-NA FAST_B709C2 1>, Freq 2442 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    John:            Infra, <MAC C-10 John>, Freq 2462 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    4M50yuan13418934066B4D: Infra, <MAC C-08 4M50yuan13418934066B4D>, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    MERCURY_360D7E:  Infra, <MAC C-05 MERCURY_360D7E>, Freq 2417 MHz, Rate 54 Mb/s, Strength 42

    Address:         192.168.0.106
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1
    DNS:             211.162.78.3
    DNS:             211.162.78.1
-----------------+-------------+--------+-------------+---------+-----------+--------------+-----------


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

dooyogame1           : ssid=dooyogame1 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
TP-LINK_408          : ssid=TP-LINK_408 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
wulong               : ssid=wulong | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

--- 192.168.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 1.379/1.402/1.425/0.023 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.025/0.031/0.038/0.008 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : zh_CN.UTF-8)
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)

          Current Frequency=2.447 GHz (Channel 8)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 wulong>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=70/70  Signal level=-24 dBm  
                    Encryption key:on
                    ESSID:"wulong"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000002c97c3
                    Extra: Last beacon: 12ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 ChinaNet-FAFe>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"ChinaNet-FAFe"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000001a1d5371a
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 MERCURY_32152C>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"MERCURY_32152C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000621061e69
                    Extra: Last beacon: 21540ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC C-04 iTV-FAFe>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"iTV-FAFe"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000001a1d55221
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC C-05 MERCURY_360D7E>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:off
                    ESSID:"MERCURY_360D7E"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000029b7669145
                    Extra: Last beacon: 23492ms ago
          Cell 06 - Address: <MAC C-06 TP-LINK_B396F4>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"TP-LINK_B396F4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001a3fc84f6
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC C-07 MERCURY_1302>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"MERCURY_1302"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000305713f33
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC C-08 4M50yuan13418934066B4D>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"4M50yuan13418934066B4D"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000798a06a7f8
                    Extra: Last beacon: 22832ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC C-09 lixiaotong>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"lixiaotong"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000dd335d3f81
                    Extra: Last beacon: 1296ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC C-10 John>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"John"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000104bcf4d180
                    Extra: Last beacon: 21876ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC C-11 Phicomm_1EB880>
                    Channel:12
                    Frequency:2.467 GHz (Channel 12)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"Phicomm_1EB880"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000182595f16d
                    Extra: Last beacon: 56ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC C-12 Tenda_456>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"Tenda_456"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000007193183
                    Extra: Last beacon: 21752ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC C-13 FANG SAN>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"FANG SAN"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000582e6b917e
                    Extra: Last beacon: 2196ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC C-14 ChinaNet-ihwc>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"ChinaNet-ihwc"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000163305b615f
                    Extra: Last beacon: 1732ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC C-15 belkin.746>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"belkin.746"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000108fd67176
                    Extra: Last beacon: 1576ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 16 - Address: <MAC C-16 Netcore1>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"Netcore1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000104bd3b2183
                    Extra: Last beacon: 1048ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[acer_wmi]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/platform/x86/acer-wmi.ko
srcversion:     15371DC0E403E93954B38E5
depends:        wmi,sparse-keymap,video
parm:           mailled:Set initial state of Mail LED (int)
parm:           brightness:Set initial LCD backlight brightness (int)
parm:           threeg:Set initial state of 3G hardware (int)
parm:           force_series:Force a different laptop series (int)
parm:           ec_raw_mode:Enable EC raw mode (bool)

[ath9k]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
srcversion:     7EAAD420ADF6B9354F0C8C1
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)

[ath9k_common]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
srcversion:     696B00A6C59713EC0966997
depends:        ath,ath9k_hw

[ath9k_hw]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
srcversion:     4809F3842A0542CD6B556D3
depends:        ath

[ath]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath.ko
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211

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

[mxm_wmi]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/platform/x86/mxm-wmi.ko
srcversion:     62CBD37DE87DF0C4CD7FBA3
depends:        wmi

[wmi]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)

[video]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/acpi/video.ko
srcversion:     274A2250DEAB415D412A67C
depends:        
parm:           brightness_switch_enabled:bool
parm:           allow_duplicates:bool
parm:           use_native_backlight:int


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x14e4:0x16b5 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:0x002e (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Not Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/rc.local]
echo IGD > /sys/kernel/debug/vgaswitcheroo/switch
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
mount -t ntfs /dev/sda1  /mnt/c
mount -t ntfs /dev/sda2  /mnt/d
mount -t vfat -o codepage=936,iocharset=utf8,umask=000 /dev/sda3  /mnt/e
exit 0

[/etc/modprobe.d]
ath9k.conf        : options ath9k nohwcrypt=1
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/vmlinuz-3.13.0-32-generic root=UUID=cce550a5-342e-4350-a10a-16d0b7af2a81 ro acpi_backlight=vendor acpi_osi=Linux quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.738646] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.739000] audit: initializing netlink socket (disabled)
[    1.270838] wmi: Mapper loaded
[    1.370703] tg3 0000:04:00.0 eth0: attached PHY is 57765 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[1])
[   36.915341] ath: phy0: ASPM enabled: 0x42
[   36.915345] ath: EEPROM regdomain: 0x65
[   36.915346] ath: EEPROM indicates we should expect a direct regpair map
[   36.915349] ath: Country alpha2 being used: 00
[   36.915350] ath: Regpair used: 0x65
[   37.016511] acer_wmi: Acer Laptop ACPI-WMI Extras
[   37.016531] acer_wmi: Function bitmap for Communication Button: 0x1
[   37.016850] acer_wmi: Disabling ACPI video driver
[   40.892339] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   41.794373] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   41.797503] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   43.166177] wlan0: authenticate with <MAC C-01 wulong>
[   43.185939] wlan0: send auth to <MAC C-01 wulong> (try 1/3)
[   43.189499] wlan0: authenticated
[   43.193432] wlan0: associate with <MAC C-01 wulong> (try 1/3)
[   43.198846] wlan0: RX AssocResp from <MAC C-01 wulong> (capab=0x411 status=0 aid=2)
[   43.198896] wlan0: associated
[   43.198906] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

    ======== Done ========
```

---

### Post by wulong710 on 2014-08-06
The wireless disconnect just now. I run  ./wireless_script and get information as follow:
```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

andrew-pc 3.13.0-32-generic i686,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Core(TM) i5-2450M CPU @ 2.50GHz
Memory : 3847 MB
Uptime : 12:20:16 up  2:07,  6 users,  load average: 0.90, 0.71, 0.59


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

03:00.0 Network controller [0280]: Qualcomm Atheros AR9287 Wireless Network Adapter (PCI-Express) [168c:002e] (rev 01)
    Subsystem: Quanta Microsystems, Inc Device [1a32:2309]
    Kernel driver in use: ath9k
04:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)
    Subsystem: Acer Incorporated [ALI] Device [1025:0500]
    Kernel driver in use: tg3


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 006: ID 0b05:7772 ASUSTek Computer, Inc. 
Bus 002 Device 004: ID 17ef:6025 Lenovo 
Bus 002 Device 005: ID 0e8f:0022 GreenAsia Inc. 
Bus 002 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 058f:b002 Alcor Micro Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface                 Soft blocked  Hard blocked
0: phy0: Wireless LAN               no            no
1: acer-wireless: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

acer_wmi               31735  0 
sparse_keymap          13708  1 acer_wmi
ath9k                 144602  0 
ath9k_common           13359  1 ath9k
ath9k_hw              438205  2 ath9k_common,ath9k
ath                    23922  3 ath9k_common,ath9k,ath9k_hw
mac80211              546051  1 ath9k
cfg80211              409394  3 ath,ath9k,mac80211
mxm_wmi                12893  1 nouveau
wmi                    18673  3 acer_wmi,mxm_wmi,nouveau
video                  18903  3 i915,acer_wmi,nouveau


module parameters ~~~~~~~~~~~~~~~~~~

acer_wmi      (5): brightness=-1 | ec_raw_mode=N | force_series=0 | mailled=-1 | threeg=-1
ath9k         (5): blink=0 | bt_ant_diversity=0 | btcoex_enable=0 | nohwcrypt=1 | ps_enable=0
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
video         (3): allow_duplicates=N | brightness_switch_enabled=Y | use_native_backlight=-1
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
============================o=============o=======  =o==============o=========o===========o===========  ===o===========
 Interface & ID             | Type        | Driver | State        | Default | Speed     | Support      | HW Addr   
============================o=============o=======  =o==============o=========o===========o===========  ===o===========
 eth0  [Wired connection 1] | Wired       | tg3    | connected    | yes     | 100 Mb/s  |              | <MAC eth0>

    Address:         192.168.10.120
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.10.1
    DNS:             202.96.128.86
    DNS:             202.96.134.33
----------------------------+-------------+--------+--------------+---------+-----------+--------------+-----------
 wlan0                      | 802.11 WiFi | ath9k  | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>

    ALDF-SZ:         Infra, <MAC C-NA ALDF-SZ 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 94 WPA WPA2
    jiamei:          Infra, <MAC C-NA jiamei 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 94 WPA WPA2
    ChinaNet-244n:   Infra, <MAC C-NA ChinaNet-244n 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 77 WPA WPA2
    iTV-244n:        Infra, <MAC C-NA iTV-244n 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    TAL-SZ:          Infra, <MAC C-NA TAL-SZ 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 42 WPA2
    rich:            Infra, <MAC C-NA rich 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 55 WPA2
    ChinaNet-4hQQ:   Infra, <MAC C-NA ChinaNet-4hQQ 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    wybgs:           Infra, <MAC C-NA wybgs 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 72 WPA WPA2
    NTKO:            Infra, <MAC C-NA NTKO 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 74 WPA WPA2
    ChinaNet-rEsr:   Infra, <MAC C-NA ChinaNet-rEsr 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 82 WPA WPA2
    WAM-WIFI:        Infra, <MAC C-NA WAM-WIFI 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 70 WPA2
    A01:             Infra, <MAC C-NA A01 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    alisa:           Infra, <MAC C-NA alisa 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2
    HP-Print-41-Deskjet 4640 series: Infra, <MAC C-NA HP-Print-41-Deskjet 4640 series 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 57 WPA2
    A52:             Infra, <MAC C-NA A52 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    hailian5F-B:     Infra, <MAC C-NA hailian5F-B 1>, Freq 2472 MHz, Rate 54 Mb/s, Strength 40 WPA2
----------------------------+-------------+--------+--------------+---------+-----------+--------------+-----------


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

dooyogame1           : ssid=dooyogame1 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
TP-LINK_408          : ssid=TP-LINK_408 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
wulong               : ssid=wulong | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.10.1    0.0.0.0         UG    0      0        0 eth0
192.168.10.0    0.0.0.0         255.255.255.0   U     1      0        0 eth0

--- 192.168.10.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 0.458/0.538/0.618/0.080 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.029/0.032/0.036/0.006 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : zh_CN.UTF-8)
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

[acer_wmi]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/platform/x86/acer-wmi.ko
srcversion:     15371DC0E403E93954B38E5
depends:        wmi,sparse-keymap,video
parm:           mailled:Set initial state of Mail LED (int)
parm:           brightness:Set initial LCD backlight brightness (int)
parm:           threeg:Set initial state of 3G hardware (int)
parm:           force_series:Force a different laptop series (int)
parm:           ec_raw_mode:Enable EC raw mode (bool)

[ath9k]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
srcversion:     7EAAD420ADF6B9354F0C8C1
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)

[ath9k_common]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
srcversion:     696B00A6C59713EC0966997
depends:        ath,ath9k_hw

[ath9k_hw]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
srcversion:     4809F3842A0542CD6B556D3
depends:        ath

[ath]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath.ko
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211

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

[mxm_wmi]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/platform/x86/mxm-wmi.ko
srcversion:     62CBD37DE87DF0C4CD7FBA3
depends:        wmi

[wmi]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)

[video]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/acpi/video.ko
srcversion:     274A2250DEAB415D412A67C
depends:        
parm:           brightness_switch_enabled:bool
parm:           allow_duplicates:bool
parm:           use_native_backlight:int


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x14e4:0x16b5 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:0x002e (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Not Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/rc.local]
echo IGD > /sys/kernel/debug/vgaswitcheroo/switch
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
mount -t ntfs /dev/sda1  /mnt/c
mount -t ntfs /dev/sda2  /mnt/d
mount -t vfat -o codepage=936,iocharset=utf8,umask=000 /dev/sda3  /mnt/e
exit 0

[/etc/modprobe.d]
ath9k.conf        : options ath9k nohwcrypt=1
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/vmlinuz-3.13.0-32-generic root=UUID=cce550a5-342e-4350-a10a-16d0b7af2a81 ro acpi_backlight=vendor acpi_osi=Linux quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.738664] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.739015] audit: initializing netlink socket (disabled)
[    1.276345] wmi: Mapper loaded
[    1.370953] tg3 0000:04:00.0 eth0: attached PHY is 57765 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[1])
[   31.400174] ath: phy0: ASPM enabled: 0x42
[   31.400178] ath: EEPROM regdomain: 0x65
[   31.400180] ath: EEPROM indicates we should expect a direct regpair map
[   31.400183] ath: Country alpha2 being used: 00
[   31.400184] ath: Regpair used: 0x65
[   31.598720] acer_wmi: Acer Laptop ACPI-WMI Extras
[   31.598740] acer_wmi: Function bitmap for Communication Button: 0x1
[   31.599390] acer_wmi: Disabling ACPI video driver
[   36.469430] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   37.534538] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   37.538025] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   38.855307] wlan0: authenticate with <MAC ID removed>
[   38.874742] wlan0: send auth to <MAC ID removed> (try 1/3)
[   38.879522] wlan0: authenticated
[   38.880587] wlan0: associate with <MAC ID removed> (try 1/3)
[   38.888239] wlan0: RX AssocResp from <MAC ID removed> (capab=0x11 status=0 aid=4)
[   38.888317] wlan0: associated
[   38.888326] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 7518.344654] [<f899f320>] ath_isr [ath9k]
[ 7518.775816] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7518.788890] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7518.788967] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7518.904465] ath: phy0: Chip reset failed
[ 7518.904473] ath: phy0: Unable to reset channel, reset status -22
[ 7518.904495] ath: phy0: Unable to set channel
[ 7519.019462] ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
[ 7519.032457] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7519.165787] ath: phy0: Failed to wakeup in 500us
[ 7519.231262] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7519.244273] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7519.244318] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7519.359234] ath: phy0: Chip reset failed
[ 7519.359239] ath: phy0: Unable to reset channel, reset status -22
[ 7519.359332] ath: phy0: Unable to set channel
[ 7519.425567] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7519.438856] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7519.438902] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7519.554804] ath: phy0: Chip reset failed
[ 7519.554814] ath: phy0: Unable to reset channel, reset status -22
[ 7519.620122] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7519.633168] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7519.633215] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7519.748142] ath: phy0: Chip reset failed
[ 7519.748148] ath: phy0: Unable to reset channel, reset status -22
[ 7519.748162] ath: phy0: Unable to set channel
[ 7519.813409] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7519.826417] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7519.826450] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7519.941388] ath: phy0: Chip reset failed
[ 7519.941394] ath: phy0: Unable to reset channel, reset status -22
[ 7519.941406] ath: phy0: Unable to set channel
[ 7520.006649] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7520.019653] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7520.019677] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7520.134621] ath: phy0: Chip reset failed
[ 7520.134627] ath: phy0: Unable to reset channel, reset status -22
[ 7520.134642] ath: phy0: Unable to set channel
[ 7520.199894] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7520.212895] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7520.212920] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7520.327899] ath: phy0: Chip reset failed
[ 7520.327905] ath: phy0: Unable to reset channel, reset status -22
[ 7520.327920] ath: phy0: Unable to set channel
[ 7520.394011] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7520.407151] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7520.407189] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7520.523517] ath: phy0: Chip reset failed
[ 7520.523524] ath: phy0: Unable to reset channel, reset status -22
[ 7520.523583] ath: phy0: Unable to set channel
[ 7520.588871] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7520.601860] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7520.601881] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7520.716835] ath: phy0: Chip reset failed
[ 7520.716839] ath: phy0: Unable to reset channel, reset status -22
[ 7520.716869] ath: phy0: Unable to set channel
[ 7520.782139] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7520.795129] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7520.795151] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7520.910105] ath: phy0: Chip reset failed
[ 7520.910109] ath: phy0: Unable to reset channel, reset status -22
[ 7520.910142] ath: phy0: Unable to set channel
[ 7520.975397] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7520.988399] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7520.988420] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7521.103331] ath: phy0: Chip reset failed
[ 7521.103335] ath: phy0: Unable to reset channel, reset status -22
[ 7521.103368] ath: phy0: Unable to set channel
[ 7521.168642] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7521.181643] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7521.181664] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7521.296636] ath: phy0: Chip reset failed
[ 7521.296640] ath: phy0: Unable to reset channel, reset status -22
[ 7521.296671] ath: phy0: Unable to set channel
[ 7521.361942] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7521.374936] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7521.374958] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7521.489908] ath: phy0: Chip reset failed
[ 7521.489915] ath: phy0: Unable to reset channel, reset status -22
[ 7521.490007] ath: phy0: Unable to set channel
[ 7521.555279] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7521.568275] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7521.568297] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7521.683239] ath: phy0: Chip reset failed
[ 7521.683243] ath: phy0: Unable to reset channel, reset status -22
[ 7521.683274] ath: phy0: Unable to set channel
[ 7521.748529] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7521.761518] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7521.761537] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7521.876458] ath: phy0: Chip reset failed
[ 7521.876462] ath: phy0: Unable to reset channel, reset status -22
[ 7521.876490] ath: phy0: Unable to set channel
[ 7521.941767] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7521.954759] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7521.954779] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7522.069711] ath: phy0: Chip reset failed
[ 7522.069715] ath: phy0: Unable to reset channel, reset status -22
[ 7522.069754] ath: phy0: Unable to set channel
[ 7522.070187] wlan0: authenticate with <MAC ID removed>
[ 7522.135027] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7522.148038] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7522.148054] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7522.263006] ath: phy0: Chip reset failed
[ 7522.263010] ath: phy0: Unable to reset channel, reset status -22
[ 7522.263056] ath: phy0: Unable to set channel
[ 7522.377855] ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
[ 7522.390880] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7522.401795] ath: phy0: Failed to wakeup in 500us
[ 7522.467487] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7522.480487] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7522.480513] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7522.595447] ath: phy0: Chip reset failed
[ 7522.595453] ath: phy0: Unable to reset channel, reset status -22
[ 7522.595479] ath: phy0: Unable to set channel
[ 7522.660706] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7522.673702] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7522.673723] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7522.788720] ath: phy0: Chip reset failed
[ 7522.788726] ath: phy0: Unable to reset channel, reset status -22
[ 7522.788750] ath: phy0: Unable to set channel
[ 7522.788809] wlan0: send auth to <MAC ID removed> (try 1/3)
[ 7522.855267] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7522.868425] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7522.868456] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7522.984488] ath: phy0: Chip reset failed
[ 7522.984499] ath: phy0: Unable to reset channel, reset status -22
[ 7523.050025] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7523.063032] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7523.063058] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7523.178062] ath: phy0: Chip reset failed
[ 7523.178068] ath: phy0: Unable to reset channel, reset status -22
[ 7523.243450] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7523.256460] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7523.256482] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7523.371429] ath: phy0: Chip reset failed
[ 7523.371434] ath: phy0: Unable to reset channel, reset status -22
[ 7523.436755] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7523.449762] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7523.449785] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7523.564781] ath: phy0: Chip reset failed
[ 7523.564786] ath: phy0: Unable to reset channel, reset status -22
[ 7523.630081] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7523.643088] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7523.643109] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7523.758139] ath: phy0: Chip reset failed
[ 7523.758145] ath: phy0: Unable to reset channel, reset status -22
[ 7523.823486] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7523.836524] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7523.836544] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7523.951533] ath: phy0: Chip reset failed
[ 7523.951538] ath: phy0: Unable to reset channel, reset status -22
[ 7524.016950] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7524.029943] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7524.029968] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7524.144955] ath: phy0: Chip reset failed
[ 7524.144960] ath: phy0: Unable to reset channel, reset status -22
[ 7524.210357] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7524.223380] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7524.223403] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7524.338357] ath: phy0: Chip reset failed
[ 7524.338363] ath: phy0: Unable to reset channel, reset status -22
[ 7524.338417] wlan0: send auth to <MAC ID removed> (try 2/3)
[ 7524.404738] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7524.417876] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7524.417915] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7524.534343] ath: phy0: Chip reset failed
[ 7524.534356] ath: phy0: Unable to reset channel, reset status -22
[ 7524.599939] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7524.612949] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7524.612977] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7524.727972] ath: phy0: Chip reset failed
[ 7524.727979] ath: phy0: Unable to reset channel, reset status -22
[ 7524.793308] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7524.806305] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7524.806328] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7524.921244] ath: phy0: Chip reset failed
[ 7524.921249] ath: phy0: Unable to reset channel, reset status -22
[ 7524.986545] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7524.999540] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7524.999559] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7525.114481] ath: phy0: Chip reset failed
[ 7525.114486] ath: phy0: Unable to reset channel, reset status -22
[ 7525.179757] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7525.192753] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7525.192782] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7525.307797] ath: phy0: Chip reset failed
[ 7525.307803] ath: phy0: Unable to reset channel, reset status -22
[ 7525.307837] wlan0: send auth to <MAC ID removed> (try 3/3)
[ 7525.373136] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7525.386133] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7525.386156] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7525.501195] ath: phy0: Chip reset failed
[ 7525.501201] ath: phy0: Unable to reset channel, reset status -22
[ 7525.566540] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7525.579550] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7525.579574] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7525.694601] ath: phy0: Chip reset failed
[ 7525.694607] ath: phy0: Unable to reset channel, reset status -22
[ 7525.760035] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7525.773035] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7525.773058] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7525.888099] ath: phy0: Chip reset failed
[ 7525.888105] ath: phy0: Unable to reset channel, reset status -22
[ 7525.953524] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7525.966553] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7525.966578] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7526.081560] ath: phy0: Chip reset failed
[ 7526.081566] ath: phy0: Unable to reset channel, reset status -22
[ 7526.146893] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7526.159906] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7526.159932] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7526.274994] ath: phy0: Chip reset failed
[ 7526.275001] ath: phy0: Unable to reset channel, reset status -22
[ 7526.275035] wlan0: authentication with <MAC ID removed> timed out
[ 7526.365383] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7526.378579] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7526.378617] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7526.494760] ath: phy0: Chip reset failed
[ 7526.494769] ath: phy0: Unable to reset channel, reset status -22
[ 7526.494882] ath: phy0: Unable to set channel
[ 7526.609731] ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
[ 7526.622706] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7527.134850] ath: phy0: Failed to wakeup in 500us
[ 7527.201373] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7527.214499] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7527.214643] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7527.330764] ath: phy0: Chip reset failed
[ 7527.330772] ath: phy0: Unable to reset channel, reset status -22
[ 7527.330800] ath: phy0: Unable to set channel
[ 7527.396885] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7527.410031] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7527.410068] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7527.525958] ath: phy0: Chip reset failed
[ 7527.525967] ath: phy0: Unable to reset channel, reset status -22
[ 7527.592363] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7527.605484] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7527.605518] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7527.721822] ath: phy0: Chip reset failed
[ 7527.721829] ath: phy0: Unable to reset channel, reset status -22
[ 7527.721850] ath: phy0: Unable to set channel
[ 7527.788294] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7527.801362] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7527.801400] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7527.917357] ath: phy0: Chip reset failed
[ 7527.917365] ath: phy0: Unable to reset channel, reset status -22
[ 7527.917401] ath: phy0: Unable to set channel
[ 7527.982637] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7527.995632] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7527.995657] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7528.110584] ath: phy0: Chip reset failed
[ 7528.110589] ath: phy0: Unable to reset channel, reset status -22
[ 7528.110603] ath: phy0: Unable to set channel
[ 7528.175818] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7528.188823] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7528.188849] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7528.303785] ath: phy0: Chip reset failed
[ 7528.303791] ath: phy0: Unable to reset channel, reset status -22
[ 7528.303806] ath: phy0: Unable to set channel
[ 7528.369014] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7528.382012] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7528.382039] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7528.496961] ath: phy0: Chip reset failed
[ 7528.496966] ath: phy0: Unable to reset channel, reset status -22
[ 7528.496980] ath: phy0: Unable to set channel
[ 7528.562181] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7528.575180] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7528.575209] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7528.690112] ath: phy0: Chip reset failed
[ 7528.690118] ath: phy0: Unable to reset channel, reset status -22
[ 7528.690132] ath: phy0: Unable to set channel
[ 7528.755326] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7528.768330] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7528.768359] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7528.883298] ath: phy0: Chip reset failed
[ 7528.883303] ath: phy0: Unable to reset channel, reset status -22
[ 7528.883319] ath: phy0: Unable to set channel
[ 7528.948531] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7528.961528] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7528.961554] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7529.076516] ath: phy0: Chip reset failed
[ 7529.076522] ath: phy0: Unable to reset channel, reset status -22
[ 7529.076539] ath: phy0: Unable to set channel
[ 7529.141740] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7529.154760] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7529.154786] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7529.269781] ath: phy0: Chip reset failed
[ 7529.269787] ath: phy0: Unable to reset channel, reset status -22
[ 7529.269803] ath: phy0: Unable to set channel
[ 7529.335047] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7529.348055] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7529.348080] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7529.463087] ath: phy0: Chip reset failed
[ 7529.463094] ath: phy0: Unable to reset channel, reset status -22
[ 7529.463115] ath: phy0: Unable to set channel
[ 7529.528405] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7529.541405] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7529.541432] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7529.656364] ath: phy0: Chip reset failed
[ 7529.656369] ath: phy0: Unable to reset channel, reset status -22
[ 7529.656491] ath: phy0: Unable to set channel
[ 7529.721690] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7529.734692] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7529.734716] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7529.849640] ath: phy0: Chip reset failed
[ 7529.849644] ath: phy0: Unable to reset channel, reset status -22
[ 7529.849660] ath: phy0: Unable to set channel
[ 7529.914867] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7529.927865] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7529.927892] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7530.042825] ath: phy0: Chip reset failed
[ 7530.042830] ath: phy0: Unable to reset channel, reset status -22
[ 7530.042848] ath: phy0: Unable to set channel
[ 7530.043474] wlan0: authenticate with <MAC ID removed>
[ 7530.108063] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7530.121065] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7530.121084] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7530.236011] ath: phy0: Chip reset failed
[ 7530.236016] ath: phy0: Unable to reset channel, reset status -22
[ 7530.236032] ath: phy0: Unable to set channel
[ 7530.350890] ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
[ 7530.363875] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7530.374627] ath: phy0: Failed to wakeup in 500us
[ 7530.440480] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7530.453555] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7530.453591] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7530.568915] ath: phy0: Chip reset failed
[ 7530.568922] ath: phy0: Unable to reset channel, reset status -22
[ 7530.568974] ath: phy0: Unable to set channel
[ 7530.634253] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7530.647313] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7530.647339] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7530.762350] ath: phy0: Chip reset failed
[ 7530.762356] ath: phy0: Unable to reset channel, reset status -22
[ 7530.762424] ath: phy0: Unable to set channel
[ 7530.762482] wlan0: direct probe to <MAC ID removed> (try 1/3)
[ 7530.827825] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7530.840831] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7530.840859] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7530.955801] ath: phy0: Chip reset failed
[ 7530.955807] ath: phy0: Unable to reset channel, reset status -22
[ 7531.021071] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7531.034072] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7531.034091] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7531.149019] ath: phy0: Chip reset failed
[ 7531.149025] ath: phy0: Unable to reset channel, reset status -22
[ 7531.149056] wlan0: direct probe to <MAC ID removed> (try 2/3)
[ 7531.214251] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7531.227256] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7531.227280] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7531.342200] ath: phy0: Chip reset failed
[ 7531.342206] ath: phy0: Unable to reset channel, reset status -22
[ 7531.407506] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7531.420503] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7531.420525] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7531.535477] ath: phy0: Chip reset failed
[ 7531.535483] ath: phy0: Unable to reset channel, reset status -22
[ 7531.535514] wlan0: direct probe to <MAC ID removed> (try 3/3)
[ 7531.600692] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7531.613693] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7531.613717] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7531.728620] ath: phy0: Chip reset failed
[ 7531.728625] ath: phy0: Unable to reset channel, reset status -22
[ 7531.793812] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7531.806799] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7531.806822] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7531.921727] ath: phy0: Chip reset failed
[ 7531.921733] ath: phy0: Unable to reset channel, reset status -22
[ 7531.921759] wlan0: authentication with <MAC ID removed> timed out
[ 7532.005469] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7532.018631] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7532.018672] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7532.134975] ath: phy0: Chip reset failed
[ 7532.134983] ath: phy0: Unable to reset channel, reset status -22
[ 7532.135020] ath: phy0: Unable to set channel
[ 7532.249918] ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
[ 7532.262901] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7533.276088] ath: phy0: Failed to wakeup in 500us
[ 7533.341361] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7533.354380] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7533.354499] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7533.469428] ath: phy0: Chip reset failed
[ 7533.469435] ath: phy0: Unable to reset channel, reset status -22
[ 7533.469469] ath: phy0: Unable to set channel
[ 7533.535685] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7533.548831] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7533.548877] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7533.664836] ath: phy0: Chip reset failed
[ 7533.664846] ath: phy0: Unable to reset channel, reset status -22
[ 7533.730146] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7533.743148] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7533.743175] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7533.858113] ath: phy0: Chip reset failed
[ 7533.858119] ath: phy0: Unable to reset channel, reset status -22
[ 7533.858135] ath: phy0: Unable to set channel
[ 7533.923422] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7533.936419] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7533.936444] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7534.051393] ath: phy0: Chip reset failed
[ 7534.051399] ath: phy0: Unable to reset channel, reset status -22
[ 7534.051413] ath: phy0: Unable to set channel
[ 7534.116688] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7534.129732] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7534.129759] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7534.244906] ath: phy0: Chip reset failed
[ 7534.244913] ath: phy0: Unable to reset channel, reset status -22
[ 7534.244933] ath: phy0: Unable to set channel
[ 7534.310373] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7534.323388] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7534.323420] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7534.438380] ath: phy0: Chip reset failed
[ 7534.438386] ath: phy0: Unable to reset channel, reset status -22
[ 7534.438399] ath: phy0: Unable to set channel
[ 7534.503686] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7534.516687] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7534.516719] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7534.631678] ath: phy0: Chip reset failed
[ 7534.631683] ath: phy0: Unable to reset channel, reset status -22
[ 7534.631711] ath: phy0: Unable to set channel
[ 7534.696975] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7534.709965] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7534.710003] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7534.824930] ath: phy0: Chip reset failed
[ 7534.824936] ath: phy0: Unable to reset channel, reset status -22
[ 7534.824948] ath: phy0: Unable to set channel
[ 7534.890246] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7534.903230] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7534.903266] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7535.018180] ath: phy0: Chip reset failed
[ 7535.018186] ath: phy0: Unable to reset channel, reset status -22
[ 7535.018200] ath: phy0: Unable to set channel
[ 7535.045857] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7535.083535] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7535.096541] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7535.096565] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7535.211484] ath: phy0: Chip reset failed
[ 7535.211490] ath: phy0: Unable to reset channel, reset status -22
[ 7535.211525] ath: phy0: Unable to set channel
[ 7535.276905] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7535.289931] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7535.289959] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7535.405091] ath: phy0: Chip reset failed
[ 7535.405097] ath: phy0: Unable to reset channel, reset status -22
[ 7535.405115] ath: phy0: Unable to set channel
[ 7535.470463] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7535.483499] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7535.483534] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7535.598516] ath: phy0: Chip reset failed
[ 7535.598522] ath: phy0: Unable to reset channel, reset status -22
[ 7535.598535] ath: phy0: Unable to set channel
[ 7535.663808] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7535.676807] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7535.676839] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7535.791773] ath: phy0: Chip reset failed
[ 7535.791778] ath: phy0: Unable to reset channel, reset status -22
[ 7535.791792] ath: phy0: Unable to set channel
[ 7535.857090] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7535.870142] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7535.870172] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7535.985102] ath: phy0: Chip reset failed
[ 7535.985107] ath: phy0: Unable to reset channel, reset status -22
[ 7535.985121] ath: phy0: Unable to set channel
[ 7536.050423] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7536.063428] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7536.063457] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7536.178384] ath: phy0: Chip reset failed
[ 7536.178390] ath: phy0: Unable to reset channel, reset status -22
[ 7536.178405] ath: phy0: Unable to set channel
[ 7536.243710] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7536.256729] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7536.256754] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7536.371711] ath: phy0: Chip reset failed
[ 7536.371716] ath: phy0: Unable to reset channel, reset status -22
[ 7536.371730] ath: phy0: Unable to set channel
[ 7536.487571] ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
[ 7536.500676] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7536.511559] ath: phy0: Failed to wakeup in 500us
[ 7536.626548] ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
[ 7536.639540] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7538.213908] ath: phy0: Failed to wakeup in 500us
[ 7538.281306] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7538.294486] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7538.294645] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7538.410652] ath: phy0: Chip reset failed
[ 7538.410662] ath: phy0: Unable to reset channel, reset status -22
[ 7538.410732] ath: phy0: Unable to set channel
[ 7538.477044] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7538.490217] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7538.490271] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7538.606341] ath: phy0: Chip reset failed
[ 7538.606350] ath: phy0: Unable to reset channel, reset status -22
[ 7538.671600] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7538.684597] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7538.684622] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7538.799529] ath: phy0: Chip reset failed
[ 7538.799534] ath: phy0: Unable to reset channel, reset status -22
[ 7538.799553] ath: phy0: Unable to set channel
[ 7538.864775] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7538.877766] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7538.877791] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7538.992710] ath: phy0: Chip reset failed
[ 7538.992716] ath: phy0: Unable to reset channel, reset status -22
[ 7538.992730] ath: phy0: Unable to set channel
[ 7539.057998] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7539.070998] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7539.071024] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7539.185984] ath: phy0: Chip reset failed
[ 7539.185990] ath: phy0: Unable to reset channel, reset status -22
[ 7539.186007] ath: phy0: Unable to set channel
[ 7539.251229] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7539.264230] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7539.264257] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7539.379294] ath: phy0: Chip reset failed
[ 7539.379299] ath: phy0: Unable to reset channel, reset status -22
[ 7539.379419] ath: phy0: Unable to set channel
[ 7539.444737] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7539.457765] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7539.457791] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7539.572740] ath: phy0: Chip reset failed
[ 7539.572745] ath: phy0: Unable to reset channel, reset status -22
[ 7539.572762] ath: phy0: Unable to set channel
[ 7539.638039] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7539.651065] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7539.651092] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7539.766062] ath: phy0: Chip reset failed
[ 7539.766068] ath: phy0: Unable to reset channel, reset status -22
[ 7539.766083] ath: phy0: Unable to set channel
[ 7539.831272] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7539.844270] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7539.844293] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7539.959221] ath: phy0: Chip reset failed
[ 7539.959227] ath: phy0: Unable to reset channel, reset status -22
[ 7539.959245] ath: phy0: Unable to set channel
[ 7540.024426] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7540.037423] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7540.037450] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7540.152377] ath: phy0: Chip reset failed
[ 7540.152387] ath: phy0: Unable to reset channel, reset status -22
[ 7540.152405] ath: phy0: Unable to set channel
[ 7540.217609] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7540.230626] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7540.230653] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7540.345560] ath: phy0: Chip reset failed
[ 7540.345565] ath: phy0: Unable to reset channel, reset status -22
[ 7540.345581] ath: phy0: Unable to set channel
[ 7540.411655] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7540.424821] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7540.424851] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7540.540687] ath: phy0: Chip reset failed
[ 7540.540693] ath: phy0: Unable to reset channel, reset status -22
[ 7540.540777] ath: phy0: Unable to set channel
[ 7540.607100] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7540.620321] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7540.620374] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7540.736274] ath: phy0: Chip reset failed
[ 7540.736282] ath: phy0: Unable to reset channel, reset status -22
[ 7540.736308] ath: phy0: Unable to set channel
[ 7540.801768] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7540.814812] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7540.814839] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7540.929977] ath: phy0: Chip reset failed
[ 7540.929983] ath: phy0: Unable to reset channel, reset status -22
[ 7540.930002] ath: phy0: Unable to set channel
[ 7540.995211] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7541.008209] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7541.008233] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7541.123188] ath: phy0: Chip reset failed
[ 7541.123193] ath: phy0: Unable to reset channel, reset status -22
[ 7541.123207] ath: phy0: Unable to set channel
[ 7541.188402] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7541.201401] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7541.201420] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7541.316352] ath: phy0: Chip reset failed
[ 7541.316357] ath: phy0: Unable to reset channel, reset status -22
[ 7541.316479] ath: phy0: Unable to set channel
[ 7541.431323] ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
[ 7541.444312] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7545.206591] ath: phy0: Failed to wakeup in 500us
[ 7545.322588] ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
[ 7545.335705] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7550.220340] ath: phy0: Failed to wakeup in 500us
[ 7550.336118] ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
[ 7550.349234] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7555.218074] ath: phy0: Failed to wakeup in 500us
[ 7555.334156] ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
[ 7555.347272] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7560.231810] ath: phy0: Failed to wakeup in 500us
[ 7560.347595] ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
[ 7560.360710] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7561.240965] ath: phy0: Failed to wakeup in 500us
[ 7561.306411] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7561.319415] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7561.319802] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7561.434790] ath: phy0: Chip reset failed
[ 7561.434796] ath: phy0: Unable to reset channel, reset status -22
[ 7561.434848] ath: phy0: Unable to set channel
[ 7561.501304] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7561.514444] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7561.514455] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7561.630622] ath: phy0: Chip reset failed
[ 7561.630631] ath: phy0: Unable to reset channel, reset status -22
[ 7561.695889] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7561.708895] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7561.708904] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7561.823810] ath: phy0: Chip reset failed
[ 7561.823815] ath: phy0: Unable to reset channel, reset status -22
[ 7561.823832] ath: phy0: Unable to set channel
[ 7561.889049] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7561.902041] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7561.902050] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7562.016957] ath: phy0: Chip reset failed
[ 7562.016963] ath: phy0: Unable to reset channel, reset status -22
[ 7562.016982] ath: phy0: Unable to set channel
[ 7562.082181] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7562.095182] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7562.095190] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7562.210104] ath: phy0: Chip reset failed
[ 7562.210110] ath: phy0: Unable to reset channel, reset status -22
[ 7562.210124] ath: phy0: Unable to set channel
[ 7562.275319] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7562.288325] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7562.288334] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7562.403232] ath: phy0: Chip reset failed
[ 7562.403237] ath: phy0: Unable to reset channel, reset status -22
[ 7562.403251] ath: phy0: Unable to set channel
[ 7562.468436] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7562.481441] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7562.481451] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7562.596372] ath: phy0: Chip reset failed
[ 7562.596378] ath: phy0: Unable to reset channel, reset status -22
[ 7562.596393] ath: phy0: Unable to set channel
[ 7562.661592] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7562.674593] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7562.674601] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7562.789523] ath: phy0: Chip reset failed
[ 7562.789529] ath: phy0: Unable to reset channel, reset status -22
[ 7562.789545] ath: phy0: Unable to set channel
[ 7562.854745] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7562.867742] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7562.867750] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7562.982641] ath: phy0: Chip reset failed
[ 7562.982646] ath: phy0: Unable to reset channel, reset status -22
[ 7562.982662] ath: phy0: Unable to set channel
[ 7563.047849] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7563.060886] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7563.060896] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7563.175796] ath: phy0: Chip reset failed
[ 7563.175801] ath: phy0: Unable to reset channel, reset status -22
[ 7563.175816] ath: phy0: Unable to set channel
[ 7563.241006] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7563.254009] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7563.254017] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7563.368913] ath: phy0: Chip reset failed
[ 7563.368918] ath: phy0: Unable to reset channel, reset status -22
[ 7563.369038] ath: phy0: Unable to set channel
[ 7563.434222] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7563.447217] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7563.447226] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7563.562117] ath: phy0: Chip reset failed
[ 7563.562122] ath: phy0: Unable to reset channel, reset status -22
[ 7563.562135] ath: phy0: Unable to set channel
[ 7563.627315] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7563.640313] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7563.640321] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7563.755212] ath: phy0: Chip reset failed
[ 7563.755217] ath: phy0: Unable to reset channel, reset status -22
[ 7563.755232] ath: phy0: Unable to set channel
[ 7563.820415] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7563.833419] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7563.833428] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7563.948323] ath: phy0: Chip reset failed
[ 7563.948328] ath: phy0: Unable to reset channel, reset status -22
[ 7563.948341] ath: phy0: Unable to set channel
[ 7564.013525] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7564.026530] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7564.026538] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7564.141428] ath: phy0: Chip reset failed
[ 7564.141433] ath: phy0: Unable to reset channel, reset status -22
[ 7564.141451] ath: phy0: Unable to set channel
[ 7564.206647] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7564.219635] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7564.219643] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7564.334563] ath: phy0: Chip reset failed
[ 7564.334569] ath: phy0: Unable to reset channel, reset status -22
[ 7564.334583] ath: phy0: Unable to set channel
[ 7564.449422] ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
[ 7564.462399] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7565.229530] ath: phy0: Failed to wakeup in 500us
[ 7565.345298] ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
[ 7565.358407] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7570.243260] ath: phy0: Failed to wakeup in 500us
[ 7570.359051] ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
[ 7570.372168] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7575.240929] ath: phy0: Failed to wakeup in 500us
[ 7575.356688] ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
[ 7575.369804] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7580.254706] ath: phy0: Failed to wakeup in 500us
[ 7580.370484] ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
[ 7580.383601] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7585.252412] ath: phy0: Failed to wakeup in 500us
[ 7585.368188] ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
[ 7585.381295] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7590.266142] ath: phy0: Failed to wakeup in 500us
[ 7590.381925] ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
[ 7590.395048] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7594.277160] ath: phy0: Failed to wakeup in 500us
[ 7594.342627] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7594.355626] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7594.355636] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7594.470555] ath: phy0: Chip reset failed
[ 7594.470560] ath: phy0: Unable to reset channel, reset status -22
[ 7594.470579] ath: phy0: Unable to set channel
[ 7594.536999] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7594.550144] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7594.550157] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7594.666081] ath: phy0: Chip reset failed
[ 7594.666090] ath: phy0: Unable to reset channel, reset status -22
[ 7594.731245] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7594.744260] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7594.744269] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7594.859323] ath: phy0: Chip reset failed
[ 7594.859328] ath: phy0: Unable to reset channel, reset status -22
[ 7594.859345] ath: phy0: Unable to set channel
[ 7594.924547] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7594.937539] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7594.937548] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7595.052441] ath: phy0: Chip reset failed
[ 7595.052446] ath: phy0: Unable to reset channel, reset status -22
[ 7595.052461] ath: phy0: Unable to set channel
[ 7595.117650] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7595.130647] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7595.130655] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7595.245546] ath: phy0: Chip reset failed
[ 7595.245551] ath: phy0: Unable to reset channel, reset status -22
[ 7595.245565] ath: phy0: Unable to set channel
[ 7595.310732] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7595.323742] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7595.323751] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7595.438648] ath: phy0: Chip reset failed
[ 7595.438653] ath: phy0: Unable to reset channel, reset status -22
[ 7595.438771] ath: phy0: Unable to set channel
[ 7595.503943] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7595.516945] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7595.516954] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7595.631874] ath: phy0: Chip reset failed
[ 7595.631880] ath: phy0: Unable to reset channel, reset status -22
[ 7595.631895] ath: phy0: Unable to set channel
[ 7595.697077] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7595.710074] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7595.710082] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7595.824974] ath: phy0: Chip reset failed
[ 7595.824980] ath: phy0: Unable to reset channel, reset status -22
[ 7595.824993] ath: phy0: Unable to set channel
[ 7595.890163] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7595.903157] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7595.903166] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7596.018075] ath: phy0: Chip reset failed
[ 7596.018080] ath: phy0: Unable to reset channel, reset status -22
[ 7596.018096] ath: phy0: Unable to set channel
[ 7596.083275] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7596.096270] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7596.096279] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7596.211169] ath: phy0: Chip reset failed
[ 7596.211174] ath: phy0: Unable to reset channel, reset status -22
[ 7596.211188] ath: phy0: Unable to set channel
[ 7596.276389] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7596.289398] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7596.289407] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7596.404293] ath: phy0: Chip reset failed
[ 7596.404298] ath: phy0: Unable to reset channel, reset status -22
[ 7596.404313] ath: phy0: Unable to set channel
[ 7596.470309] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7596.483447] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7596.483457] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7596.599397] ath: phy0: Chip reset failed
[ 7596.599405] ath: phy0: Unable to reset channel, reset status -22
[ 7596.599424] ath: phy0: Unable to set channel
[ 7596.666098] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7596.679274] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7596.679285] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7596.795254] ath: phy0: Chip reset failed
[ 7596.795262] ath: phy0: Unable to reset channel, reset status -22
[ 7596.795284] ath: phy0: Unable to set channel
[ 7596.860745] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7596.873785] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7596.873794] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7596.988929] ath: phy0: Chip reset failed
[ 7596.988934] ath: phy0: Unable to reset channel, reset status -22
[ 7596.988949] ath: phy0: Unable to set channel
[ 7597.054155] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7597.067153] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7597.067162] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7597.182063] ath: phy0: Chip reset failed
[ 7597.182069] ath: phy0: Unable to reset channel, reset status -22
[ 7597.182082] ath: phy0: Unable to set channel
[ 7597.247275] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7597.260269] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7597.260277] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7597.375172] ath: phy0: Chip reset failed
[ 7597.375177] ath: phy0: Unable to reset channel, reset status -22
[ 7597.375303] ath: phy0: Unable to set channel
[ 7597.490148] ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
[ 7597.503127] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7600.277591] ath: phy0: Failed to wakeup in 500us
[ 7600.393607] ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
[ 7600.406724] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7605.275263] ath: phy0: Failed to wakeup in 500us
[ 7605.391041] ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
[ 7605.404166] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7610.288982] ath: phy0: Failed to wakeup in 500us
[ 7610.404780] ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
[ 7610.417894] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7615.286720] ath: phy0: Failed to wakeup in 500us
[ 7615.402635] ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
[ 7615.415760] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7620.300520] ath: phy0: Failed to wakeup in 500us
[ 7620.416356] ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
[ 7620.429477] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7625.298147] ath: phy0: Failed to wakeup in 500us
[ 7625.414036] ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
[ 7625.427152] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7630.311885] ath: phy0: Failed to wakeup in 500us
[ 7630.428034] ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
[ 7630.441139] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7635.309599] ath: phy0: Failed to wakeup in 500us
[ 7635.425391] ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
[ 7635.438513] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7637.326004] ath: phy0: Failed to wakeup in 500us
[ 7637.391441] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7637.404446] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7637.404455] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7637.519610] ath: phy0: Chip reset failed
[ 7637.519616] ath: phy0: Unable to reset channel, reset status -22
[ 7637.519665] ath: phy0: Unable to set channel
[ 7637.586128] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7637.599301] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7637.599314] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7637.715222] ath: phy0: Chip reset failed
[ 7637.715232] ath: phy0: Unable to reset channel, reset status -22
[ 7637.780566] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7637.793572] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7637.793580] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7637.908511] ath: phy0: Chip reset failed
[ 7637.908517] ath: phy0: Unable to reset channel, reset status -22
[ 7637.908534] ath: phy0: Unable to set channel
[ 7637.973813] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7637.986813] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7637.986822] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7638.101742] ath: phy0: Chip reset failed
[ 7638.101747] ath: phy0: Unable to reset channel, reset status -22
[ 7638.101759] ath: phy0: Unable to set channel
[ 7638.167039] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7638.180036] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7638.180045] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7638.294959] ath: phy0: Chip reset failed
[ 7638.294966] ath: phy0: Unable to reset channel, reset status -22
[ 7638.294980] ath: phy0: Unable to set channel
[ 7638.360219] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7638.373242] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7638.373252] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7638.488216] ath: phy0: Chip reset failed
[ 7638.488222] ath: phy0: Unable to reset channel, reset status -22
[ 7638.488237] ath: phy0: Unable to set channel
[ 7638.553515] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7638.566539] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7638.566550] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7638.681483] ath: phy0: Chip reset failed
[ 7638.681489] ath: phy0: Unable to reset channel, reset status -22
[ 7638.681502] ath: phy0: Unable to set channel
[ 7638.746778] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7638.759793] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7638.759803] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7638.874749] ath: phy0: Chip reset failed
[ 7638.874755] ath: phy0: Unable to reset channel, reset status -22
[ 7638.874768] ath: phy0: Unable to set channel
[ 7638.940080] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7638.953080] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7638.953089] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7639.068068] ath: phy0: Chip reset failed
[ 7639.068074] ath: phy0: Unable to reset channel, reset status -22
[ 7639.068113] ath: phy0: Unable to set channel
[ 7639.133391] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7639.146438] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7639.146447] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7639.261370] ath: phy0: Chip reset failed
[ 7639.261377] ath: phy0: Unable to reset channel, reset status -22
[ 7639.261415] ath: phy0: Unable to set channel
[ 7639.326675] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7639.339668] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7639.339677] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7639.454594] ath: phy0: Chip reset failed
[ 7639.454600] ath: phy0: Unable to reset channel, reset status -22
[ 7639.454613] ath: phy0: Unable to set channel
[ 7639.519945] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7639.532945] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7639.532953] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7639.647889] ath: phy0: Chip reset failed
[ 7639.647895] ath: phy0: Unable to reset channel, reset status -22
[ 7639.647906] ath: phy0: Unable to set channel
[ 7639.713194] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7639.726189] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7639.726198] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7639.841109] ath: phy0: Chip reset failed
[ 7639.841114] ath: phy0: Unable to reset channel, reset status -22
[ 7639.841128] ath: phy0: Unable to set channel
[ 7639.906433] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7639.919449] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7639.919458] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7640.034407] ath: phy0: Chip reset failed
[ 7640.034412] ath: phy0: Unable to reset channel, reset status -22
[ 7640.034424] ath: phy0: Unable to set channel
[ 7640.099708] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7640.112717] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7640.112726] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7640.227686] ath: phy0: Chip reset failed
[ 7640.227692] ath: phy0: Unable to reset channel, reset status -22
[ 7640.227706] ath: phy0: Unable to set channel
[ 7640.293021] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7640.306040] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7640.306048] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7640.421040] ath: phy0: Chip reset failed
[ 7640.421046] ath: phy0: Unable to reset channel, reset status -22
[ 7640.421059] ath: phy0: Unable to set channel
[ 7640.537119] ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
[ 7640.550220] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7645.321050] ath: phy0: Failed to wakeup in 500us
[ 7645.436916] ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
[ 7645.450029] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7650.334785] ath: phy0: Failed to wakeup in 500us
[ 7650.455032] ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
[ 7650.470032] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7651.494829] ath: phy0: Failed to wakeup in 500us
[ 7651.560151] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7651.573155] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7651.573163] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7651.688146] ath: phy0: Chip reset failed
[ 7651.688151] ath: phy0: Unable to reset channel, reset status -22
[ 7651.688172] ath: phy0: Unable to set channel
[ 7651.754481] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7651.767619] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7651.767633] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7651.883739] ath: phy0: Chip reset failed
[ 7651.883752] ath: phy0: Unable to reset channel, reset status -22
[ 7651.949024] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7651.962022] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7651.962031] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7652.076965] ath: phy0: Chip reset failed
[ 7652.076973] ath: phy0: Unable to reset channel, reset status -22
[ 7652.077000] ath: phy0: Unable to set channel
[ 7652.142260] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7652.155264] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7652.155273] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7652.270217] ath: phy0: Chip reset failed
[ 7652.270222] ath: phy0: Unable to reset channel, reset status -22
[ 7652.270240] ath: phy0: Unable to set channel
[ 7652.335475] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7652.348471] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7652.348480] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7652.463403] ath: phy0: Chip reset failed
[ 7652.463408] ath: phy0: Unable to reset channel, reset status -22
[ 7652.463424] ath: phy0: Unable to set channel
[ 7652.529790] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7652.542934] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7652.542945] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7652.658787] ath: phy0: Chip reset failed
[ 7652.658796] ath: phy0: Unable to reset channel, reset status -22
[ 7652.658815] ath: phy0: Unable to set channel
[ 7652.724969] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7652.738106] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7652.738118] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7652.854428] ath: phy0: Chip reset failed
[ 7652.854436] ath: phy0: Unable to reset channel, reset status -22
[ 7652.854460] ath: phy0: Unable to set channel
[ 7652.919680] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7652.932683] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7652.932692] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7653.047587] ath: phy0: Chip reset failed
[ 7653.047592] ath: phy0: Unable to reset channel, reset status -22
[ 7653.047608] ath: phy0: Unable to set channel
[ 7653.112773] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7653.125772] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7653.125780] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7653.240711] ath: phy0: Chip reset failed
[ 7653.240717] ath: phy0: Unable to reset channel, reset status -22
[ 7653.240837] ath: phy0: Unable to set channel
[ 7653.305999] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7653.318995] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7653.319003] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7653.433896] ath: phy0: Chip reset failed
[ 7653.433901] ath: phy0: Unable to reset channel, reset status -22
[ 7653.433915] ath: phy0: Unable to set channel
[ 7653.499113] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7653.512108] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7653.512118] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7653.627012] ath: phy0: Chip reset failed
[ 7653.627017] ath: phy0: Unable to reset channel, reset status -22
[ 7653.627031] ath: phy0: Unable to set channel
[ 7653.692211] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7653.705201] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7653.705209] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7653.820105] ath: phy0: Chip reset failed
[ 7653.820109] ath: phy0: Unable to reset channel, reset status -22
[ 7653.820123] ath: phy0: Unable to set channel
[ 7653.885302] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7653.898298] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7653.898306] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7654.013203] ath: phy0: Chip reset failed
[ 7654.013207] ath: phy0: Unable to reset channel, reset status -22
[ 7654.013220] ath: phy0: Unable to set channel
[ 7654.078398] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7654.091405] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7654.091414] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7654.206323] ath: phy0: Chip reset failed
[ 7654.206329] ath: phy0: Unable to reset channel, reset status -22
[ 7654.206345] ath: phy0: Unable to set channel
[ 7654.272327] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7654.285446] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7654.285454] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7654.401308] ath: phy0: Chip reset failed
[ 7654.401315] ath: phy0: Unable to reset channel, reset status -22
[ 7654.401375] ath: phy0: Unable to set channel
[ 7654.467723] ath: phy0: Failed to stop TX DMA, queues=0x18f!
[ 7654.480921] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 7654.480931] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 7654.597240] ath: phy0: Chip reset failed
[ 7654.597249] ath: phy0: Unable to reset channel, reset status -22
[ 7654.597273] ath: phy0: Unable to set channel
[ 7654.712562] ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
[ 7654.725584] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff

    ======== Done ========
```

---

### Post by wulong710 on 2014-08-07
No reply. Seems it is a difficult problem.

---

### Post by varunendra on 2014-08-08
I usually state clearly in a post before giving up on threads. The really 'difficult' part of 'My' current problem is that I am being haunted badly by deadlines for last couple of weeks (and still behind schedules). In last 4 days, it was only last night when I slept all night long (else it was - 'leave the desk at 2 am in the night, wake up at alarm @ 4 am :(). I couldn't even find time to ask someone else to pick your (and other) threads while I was away.

Anyway, about 'Your' problem, the first one I can see is that you are using **[COLOR="#FF0000"]AES (CCMP) with WPA[/COLOR]** encryption in your router/access-point "wulong". Originally, the WPA (1) encryption didn't even support AES, only **WPA[COLOR="#0000CD"]2[/COLOR]** did. I don't know if it is some kind of 'development' or a weird patchwork that some routers now seem to support AES with WPA. In any case, I have seen only problems with such non-standard combinations.

So.. I strongly suggest you change the encryption type in your router to **WPA2-PSK with AES (CCMP)** (please refer to your router's user-manual to see how to login and change its settings). Remember - no WPA, no WPA/WPA2 mixed mode, and certainly not TKIP.

Additionally, also change the channel from its current channel '8' (or 'auto') to channel 1 or 11 as they usually offer better signal quality. Reboot the router after saving the changes.

Just try these two changes, and I hope your problem should be gone. If not, feel free to ask other experts (via PM) to take a look at your thread if I couldn't respond in time.

By the way, it only makes me happier if others join the threads I'm posting in, and share their ideas. :)

---

### Post by wulong710 on 2014-09-25
thankyou . I buy a new laptop ,and have change to debian os for months. Have not login this forum for months . I give my AES computer to my girl friend with win7 installed in it, and it have not met with network error.   Thanks for your help. Now i want install ubuntu amd64 in my new computer, because you are a so kind man .

---

### Post by varunendra on 2014-09-25
Thank you so much for your generous comments about me, but as you already saw, I'm not such a reliable person. I can be away from forums for days or weeks, and even when I'm available, I'm not always successful with troubleshooting. I can only try, and that part I do honestly. But then the OS/driver/hardware may not be always cooperative.

Anyway, if you wish to install Ubuntu on your new computer, I recommend downloading the ISO of either 14.04.1, or 12.04.5 via torrent, since torrents not only ensure higher download speeds, but the integrity of the downloaded data too. Official link to the torrents can be found here : [http://www.ubuntu.com/download/alternative-downloads](http://www.ubuntu.com/download/alternative-downloads)

Create a Live DVD or USB with the ISO, and try it in Live mode first to make sure everything works as expected. Sometimes somethings may not work perfectly but can be made to work, and overall performance will be faster once installed. If you need help with anything, feel free to start a new thread with relevant title in a relevant section.

---

