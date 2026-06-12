---
title: "Wireless packet loss"
date: 2014-09-18
forum: Networking &amp; Wireless
---

### Post by jdanoz on 2014-09-18
Hello,

I have a Dell XPS 13 Developer (sputnik2) with Ubuntu 14.04.
Recently I changed the DSL router w/ wifi at home, and then using this laptop I am getting a lot of packet loss and high latency.

From a desktop with Ethernet everything is perfect. From another laptop with Wifi is perfect.

Any ideas?

Thanks

---

### Post by varunendra on 2014-09-20
Hello jdanoz,

Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by tgalati4 on 2014-09-20
Use WiFi-Analyzer app on a smartphone and check your wireless neighborhood.  You might be stepping on each others' toes.  A simple frequency change can improve things.

I moved my wireless-G frequency to channel 4 because all of the nearby modems hop between channels 1, 6, or 11.  But I get better signal and throughput by using 4.

Of course antenna placement is important.  Your modem should be 5 to 6' high and way from metal and wires.  Moisture will attenuate signals, so every piece of sheetrock your signal goes through will knock it down quite a bit.  You will be lucky to go through 3 walls.

The other thing that helps to to use a dual-band router (2.4 and 5 GHz) and put as many devices on the 5 GHz band because it is generally less crowded.

---

### Post by jdanoz on 2014-09-28
> **tgalati4 said:**
> Use WiFi-Analyzer app on a smartphone and check your wireless neighborhood.  You might be stepping on each others' toes.  A simple frequency change can improve things.

I moved my wireless-G frequency to channel 4 because all of the nearby modems hop between channels 1, 6, or 11.  But I get better signal and throughput by using 4.

Of course antenna placement is important.  Your modem should be 5 to 6' high and way from metal and wires.  Moisture will attenuate signals, so every piece of sheetrock your signal goes through will knock it down quite a bit.  You will be lucky to go through 3 walls.

The other thing that helps to to use a dual-band router (2.4 and 5 GHz) and put as many devices on the 5 GHz band because it is generally less crowded.

Hi tgalati4,

From another laptop using wifi everything is OK. I changed the frequency and problem is still the same.

---

### Post by Vladlenin5000 on 2014-09-28
Please follow the instruction in post #2.

---

### Post by jdanoz on 2014-10-04
Hello

I ran the script (please find it attached to this post).

Notes: This morning I started my laptop and tried to use the WiFi with no luck. A lot of packet loss. A lot of delay/lag with packets (trying to do a ping to the router => 192.168.0.1).
After 20 minutes aprox, restarted the system and then the connection began to be OK. Before that I tried to disconnect and reconnect several times.

Maybe after the restart the system cleared some "cache". I don't know.

Anyway, I post here the results of the wireles script.

Thanks in advance.

Regards
Jorge

---

### Post by jdanoz on 2014-10-04
```



	======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

jdanoz-Dell-System-XPS-L322X 3.13.0-36-generic x86_64,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Core(TM) i7-3537U CPU @ 2.00GHz
Memory : 7421 MB
Uptime : 09:27:49 up 2 min,  2 users,  load average: 0,25, 0,14, 0,05


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

01:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6235 [8086:088e] (rev 24)
	Subsystem: Intel Corporation Centrino Advanced-N 6235 AGN [8086:4460]
	Kernel driver in use: iwlwifi


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 003: ID 8087:07da Intel Corp. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0c45:644d Microdia 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 003 Device 003: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 003 Device 002: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11abgn  ESSID:"vodafoneBG9G"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: <MAC C-01 vodafoneBG9G>   
          Bit Rate=65 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-37 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:59   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: hci0: Bluetooth         yes           no
1: phy0: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

dell_wmi               12761  0 
sparse_keymap          13948  1 dell_wmi
iwldvm                232285  0 
mac80211              630653  1 iwldvm
iwlwifi               169932  1 iwldvm
cfg80211              484040  3 iwlwifi,mac80211,iwldvm
wmi                    19177  1 dell_wmi


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
iwlwifi      (11): 11n_disable=0 | amsdu_size_8K=0 | antenna_coupling=0 | bt_coex_active=Y | fw_restart=Y | led_mode=0 | nvm_file=(null) | power_level=0 | power_save=N | swcrypto=0 | wd_disable=1
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
=======================o=============o=========o===========o=========o===========o==============o===========
 Interface & ID        | Type        | Driver  | State     | Default | Speed     | Support      | HW Addr   
=======================o=============o=========o===========o=========o===========o==============o===========
 wlan0  [vodafoneBG9G] | 802.11 WiFi | iwlwifi | connected | yes     | 65 Mb/s   | WEP/WPA/WPA2 | <MAC wlan0>

    MOVISTAR_91DE:   Infra, <MAC C-NA MOVISTAR_91DE 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 50 WPA
    vodafoneE5C8:    Infra, <MAC C-02 vodafoneE5C8>, Freq 2452 MHz, Rate 54 Mb/s, Strength 45 WPA
    *vodafoneBG9G:   Infra, <MAC C-01 vodafoneBG9G>, Freq 2427 MHz, Rate 54 Mb/s, Strength 83 WPA

    Address:         192.168.0.154
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1
    DNS:             192.168.0.1
-----------------------+-------------+---------+-----------+---------+-----------+--------------+-----------


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

APSANTIAGO_P         : ssid=APSANTIAGO_P | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
APTOS_SANTIAGO       : ssid=APTOS_SANTIAGO | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Cegedim_Guest        : ssid=Cegedim_Guest | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
CGDM_DSL             : ssid=CGDM_DSL | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
iPhone de Jorge-Carlos : ssid=iPhone de Jorge-Carlos | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
JAZZTEL_FCF4         : ssid=JAZZTEL_FCF4 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
vodafoneBG9G         : ssid=vodafoneBG9G | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1
search Home

domain buildd
nameserver 10.122.37.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Tabla de rutas IP del núcleo
Destino         Pasarela        Genmask         Indic Métric Ref    Uso Interfaz
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

--- 192.168.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 65.701/77.272/88.843/11.571 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.046/0.054/0.062/0.008 ms

--- 10.122.37.1 ping statistics ---
2 packets transmitted, 0 received, 100% packet loss, time 1007ms



iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "es_ES.UTF-8")
country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     32 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)
          Channel 36 (5.18 GHz)
          Channel 40 (5.2 GHz)
          Channel 44 (5.22 GHz)
          Channel 48 (5.24 GHz)
          Channel 52 (5.26 GHz)
          Channel 56 (5.28 GHz)
          Channel 60 (5.3 GHz)
          Channel 64 (5.32 GHz)
          Channel 100 (5.5 GHz)
          Channel 104 (5.52 GHz)
          Channel 108 (5.54 GHz)
          Channel 112 (5.56 GHz)
          Channel 116 (5.58 GHz)
          Channel 120 (5.6 GHz)
          Channel 124 (5.62 GHz)
          Channel 128 (5.64 GHz)
          Channel 132 (5.66 GHz)
          Channel 136 (5.68 GHz)
          Channel 140 (5.7 GHz)

          Current Frequency:2.427 GHz (Channel 4)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 vodafoneBG9G>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=67/70  Signal level=-43 dBm  
                    Encryption key:on
                    ESSID:"vodafoneBG9G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000782f4257
                    Extra: Last beacon: 88ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 vodafoneE5C8>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"vodafoneE5C8"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001fc96f038e3
                    Extra: Last beacon: 88ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 Orange-a7f6>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"Orange-a7f6"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000215ce4c293
                    Extra: Last beacon: 6020ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[dell_wmi]
filename:       /lib/modules/3.13.0-36-generic/kernel/drivers/platform/x86/dell-wmi.ko
srcversion:     0ED3A43A5709CF19B7DFD19
depends:        wmi,sparse-keymap

[iwldvm]
filename:       /lib/modules/3.13.0-36-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
version:        in-tree:
srcversion:     CC4D1BA11C1EF73A6ABDE53
depends:        iwlwifi,mac80211,cfg80211

[mac80211]
filename:       /lib/modules/3.13.0-36-generic/kernel/net/mac80211/mac80211.ko
srcversion:     B822641624778B987844F6F
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.13.0-36-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
version:        in-tree:
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-7265-7.ucode
firmware:       iwlwifi-3160-7.ucode
firmware:       iwlwifi-7260-7.ucode
srcversion:     C2D0F3DFCA289585C100E36
depends:        cfg80211
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           nvm_file:NVM file name (charp)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)

[cfg80211]
filename:       /lib/modules/3.13.0-36-generic/kernel/net/wireless/cfg80211.ko
srcversion:     C2478077E22138832B71659
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[wmi]
filename:       /lib/modules/3.13.0-36-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# USB device 0x0424:0x7500 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Not Default

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en

[/etc/pm/sleep.d/99bcmbluetooth] [executable]
#!/bin/sh
# hack for fix BCM43142 Can not search any bluetooth devices after resume from suspend

case "$1" in
	hibernate|suspend)
	        service bluetooth stop
		sleep 2
		hciconfig hci0 down
		sleep 2
		rmmod btusb
		;;
	thaw|resume)
		modprobe btusb
		sleep 2
		service bluetooth start
		;;
	*) exit $NA
		;;
esac


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-36-generic root=UUID=05a63bd2-d6f6-4619-93ae-86dc14929a84 ro quiet splash crashkernel=384M-:128M vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.724580] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.724942] audit: initializing netlink socket (disabled)
[    1.605202] wmi: Mapper loaded
[    5.703326] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    5.769011] iwlwifi 0000:01:00.0: can't disable ASPM; OS doesn't have ASPM control
[    5.769273] iwlwifi 0000:01:00.0: irq 44 for MSI/MSI-X
[    5.783569] iwlwifi 0000:01:00.0: loaded firmware version 18.168.6.1 op_mode iwldvm
[    5.810348] iwlwifi 0000:01:00.0: CONFIG_IWLWIFI_DEBUG disabled
[    5.810350] iwlwifi 0000:01:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[    5.810352] iwlwifi 0000:01:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[    5.810354] iwlwifi 0000:01:00.0: Detected Intel(R) Centrino(R) Advanced-N 6235 AGN, REV=0xB0
[    5.810808] iwlwifi 0000:01:00.0: L1 Enabled; Disabling L0S
[    5.830799] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[    6.285854] iwlwifi 0000:01:00.0: L1 Enabled; Disabling L0S
[    6.292328] iwlwifi 0000:01:00.0: Radio type=0x2-0x1-0x0
[    6.564978] iwlwifi 0000:01:00.0: L1 Enabled; Disabling L0S
[    6.571944] iwlwifi 0000:01:00.0: Radio type=0x2-0x1-0x0
[    6.657812] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    6.658050] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    9.985992] wlan0: authenticate with <MAC C-01 vodafoneBG9G>
[    9.990887] wlan0: send auth to <MAC C-01 vodafoneBG9G> (try 1/3)
[    9.993814] wlan0: authenticated
[    9.995257] wlan0: associate with <MAC C-01 vodafoneBG9G> (try 1/3)
[   10.000618] wlan0: RX AssocResp from <MAC C-01 vodafoneBG9G> (capab=0x411 status=0 aid=2)
[   10.003443] wlan0: associated
[   10.003461] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

	======== Done ========


```

---

### Post by jdanoz on 2014-10-04
Now the connection seems to be "better". Note better with quotes. 

Let me explain:

When it is impossible to navigate the ping to the router losses a lot of packets, with pings of 600ms and more.
RIght now, when I try to ping the router, the packets have times from 20ms to 100ms.

When I try this from a Macbook Pro connected to the same WiFi the packets have times of about 2ms (1 to 2ms).

I don't know what's happening. It seems that the wireless network card is trying to do some extra work...

---

### Post by tgalati4 on 2014-10-04
I remember that there are some issues with "N" mode using the *iwlwifi* wireless driver.  I suggest you search the forums for how to turn it off and just use "G" mode.  Your laptop wireless can handle 2.4 GHz (G-band) and 5 GHz (A-band).  Does your wireless router support A-Band?  If so, it might be less crowded than G-Band.  Also, the MacBook Pro generally has better wireless reception (and interference control) than any Dell product.  So it is not surprising for the Mac to connect and the Dell to have issues in a crowded neighborhood.

---

### Post by varunendra on 2014-10-04
A heap of changes that I'd like to see -
> **jdanoz said:**
> ```
iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11abgn  ESSID:"vodafoneBG9G"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: <MAC C-01 vodafoneBG9G>   
          Bit Rate=65 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          **Power Management:[COLOR="#FF0000"]on[/COLOR]**
....
....
module parameters ~~~~~~~~~~~~~~~~~~
....
iwlwifi      (11): 11n_disable=0 | amsdu_size_8K=0 | antenna_coupling=0 | bt_coex_active=Y | fw_restart=Y | led_mode=0 | nvm_file=(null) | power_level=0 | power_save=N | swcrypto=0 | wd_disable=1
....

NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~
....
vodafoneBG9G         : ssid=vodafoneBG9G | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
....

iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "es_ES.UTF-8")
**country 00:**
....

iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~
....
          Current Frequency:2.427 GHz (Channel 4)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 vodafoneBG9G>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=67/70  Signal level=-43 dBm  
                    Encryption key:on
                    ESSID:"vodafoneBG9G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000782f4257
                    Extra: Last beacon: 88ms ago
               **     IE: WPA Version 1**
                        Group Cipher : **[COLOR="#FF0000"]CCMP[/COLOR]**
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


```

Starting with the most important ones, please change the encryption in your router to WPA2-PSK with AES (CCMP). WPA(1)+AES(CCMP) is a non-standard combination that may be the cause of the troubles. "Others work fine" is no excuse to carry on with a non-standard combination.

Also try changing the channel to 1 or 11 if other suggestions here don't seem to help much. Reboot the router after saving any changes.

In Ubuntu, please try a parameter -
```
echo "options iwlwifi 11n_disable=8" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
```
..followed by a reboot.

Then, check -
```
iwconfig
```
..if "Power Management" seems to be "on" as in the report, please try turning it off -
```
sudo iwconfig wlan0 power off
```
Then keep checking the outputs of 'iwconfig' after regular intervals to make sure it remains off. If not, wll try other solutions.

We'll discuss the other changes/possibilities if the above ones don't work. Please try these for now and report back. Thanks.

---

### Post by jdanoz on 2014-11-11
Hello,

Thanks for all the support received on this topic.

Sorry for the late answer, today following the last message from "varunendra", I tried the following suggestions (in order):

1.  Changed WPA2-PSK with AES on the router.
2. Set the option 11n_disable=8

After tha rebooted the system.

Same problem after that, so I set the power management off and this did the trick.

In order to verify and isolate that this did the trick, I set power management back to on, and same problem again. Packet loss, and latency.

So, I don't know why with power management on there are several packets loss (I think this is a bug in the wireless driver implementation), but now everything is okay.

So thanks to all, and specially to "varunendra", as I followed the instructions in his last post. Anyway thank all for the information.

Best regards.

Jorge

---

### Post by jdanoz on 2014-12-02
Hi all,

Just one more thing:

In order to disable power management on boot/reboot I followed the steps detailed here:

[http://itechscotland.wordpress.com/2011/09/25/how-to-permanently-turn-off-wi-fi-power-management-in-ubuntu/]("http://itechscotland.wordpress.com/2011/09/25/how-to-permanently-turn-off-wi-fi-power-management-in-ubuntu/")

Regards

---

